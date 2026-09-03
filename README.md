# Fate Shears — 개인 기여 정리 포크

> 2D 메트로바니아 팀 프로젝트 (2025 GBGC 게임출시 협업, 팀 저장소: [GBGC1/Fate_Shears](https://github.com/GBGC1/Fate_Shears))

이 저장소는 팀 프로젝트 원본의 포크이며, 아래는 **강유민이 담당·구현한 부분**입니다. 원 저장소 커밋 히스토리에서 `yumin-beep` 커밋으로 확인할 수 있습니다.

## 게임 소개

그림자 힘을 다루는 주인공이 스테이지를 탐험하는 2D 메트로바니아입니다. 기획·아트·프로그래밍이 나뉜 4인+ 팀에서 게임 기획과 플레이어 시스템 일부 프로그래밍을 맡았습니다. (Unity, C#)

## 담당 구현

- **그림자 변신 시스템** (`PlayerShadowController`) — 평상시 ↔ 그림자 모드 전환. 변신 중 버프/디버프가 동시에 걸리는 트레이드오프 설계: 강해지는 대신 피로도가 차오르는 구조
- **피로도 시스템 연동** (`FatigueSystem`, `StatManager`) — 그림자 모드 유지 비용을 피로도로 환산, 한계 도달 시 강제 해제
- **전투 상태 UI** (`PlayerUIController`, `ShadowFragmentUI`, `AbilityUIManager`) — HP 바 · 피로도 바 · 그림자 조각 게이지. 능력창(`PlayerAbility` ↔ `AbilityWindow`) 리팩토링
- **맵 프레임 제작** — B3 구역 맵 골조 배치
- 상태 전환이 입력(`PlayerInput`)·이동(`PlayerLocomotion`)·공격(`AttackHandler`)에 흩어지지 않도록 그림자 관련 로직을 컨트롤러로 분리(`refactor shadow controller isolate` 커밋)

## 협업 방식

기능 단위 브랜치 → PR → 머지. 커밋 컨벤션(`feat:` / `refactor:`)을 지켜 히스토리에서 작업 단위가 읽히도록 했습니다.
