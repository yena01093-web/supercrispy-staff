# 🍗 슈퍼크리스피 직원 근태관리

Firebase Firestore + 순수 HTML/JS로 만든 직원 근태관리 웹앱입니다.  
GitHub Pages에서 바로 실행됩니다.

## 기능

| 탭 | 기능 |
|---|---|
| 🏠 대시보드 | 현재 근무중 인원, 오늘 출퇴근 현황, 이번달 급여 요약 |
| 👥 직원 관리 | 이름·시급 등록 / 수정 / 삭제 |
| 📷 QR 스캔 | 카메라로 QR 스캔 → 출근/퇴근 자동 처리 |
| 🪪 QR 카드 | 직원별 QR코드 표시 (인쇄 또는 화면 제시) |
| 💰 급여 내역 | 월별 직원별 근무시간 · 세전 · 3.3% 공제 · 실수령액 |

- **출퇴근 방식**: 직원이 자신의 QR카드를 스캔 → 처음 스캔은 출근, 두 번째 스캔은 퇴근
- **세금 계산**: 실수령 = 세전급여 × (1 − 3.3%)

---

## GitHub Pages 배포 방법

### 1단계 — Firebase Firestore 활성화

1. [Firebase Console](https://console.firebase.google.com) → `supercrispy-staff-9eefd` 프로젝트
2. 왼쪽 메뉴 **Firestore Database** → **데이터베이스 만들기**
3. **테스트 모드**로 시작 → 위치 선택 후 완료

### 2단계 — GitHub 저장소 생성 및 배포

```bash
# 1. 이 폴더에서 Git 초기화
cd supercrispy-staff
git init
git add index.html README.md

# 2. 첫 커밋
git commit -m "feat: 슈퍼크리스피 근태관리 앱 초기 배포"

# 3. GitHub에 새 저장소 만든 후 연결 (저장소명 예: supercrispy-staff)
git remote add origin https://github.com/YOUR_GITHUB_ID/supercrispy-staff.git
git branch -M main
git push -u origin main
```

### 3단계 — GitHub Pages 설정

1. GitHub 저장소 → **Settings** → **Pages**
2. Source: **Deploy from a branch**
3. Branch: `main` / `/ (root)` → **Save**
4. 잠시 후 `https://YOUR_GITHUB_ID.github.io/supercrispy-staff/` 에서 접속 가능

> **중요**: QR 스캔(카메라 접근)은 HTTPS에서만 동작합니다. GitHub Pages는 자동으로 HTTPS가 적용되어 있어 별도 설정 불필요합니다.

---

## Firebase 보안 규칙

현재 `firestore.rules`는 테스트용 전체 허용 설정입니다.  
실서비스 전환 시 Firebase Authentication을 연동하고 규칙을 강화하세요.

```bash
# Firebase CLI로 규칙 배포
npm install -g firebase-tools
firebase login
firebase deploy --only firestore:rules
```

---

## 로컬 실행

단순히 `index.html`을 브라우저에서 열면 됩니다.  
(카메라 기능은 localhost에서도 동작합니다)

```bash
# 또는 로컬 서버 실행
npx serve .
```

---

## Firebase 프로젝트 정보

| 항목 | 값 |
|---|---|
| 프로젝트 ID | `supercrispy-staff-9eefd` |
| Auth Domain | `supercrispy-staff-9eefd.firebaseapp.com` |
