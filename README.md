# baedalsak-terraform-test

배달싹(baedalsak) AWS 인프라를 Terraform + GitHub Actions 로 만들고, 앱 배포 후 smoke test 까지 돌려 보는 **테스트 레포**입니다.

- `terraform/` — bootstrap(state 버킷·OIDC·Actions 역할) · persistent(ECR·Secrets Manager 등) · ephemeral(VPC·EKS·ALB·RDS·MQ·Valkey, 매일 up/down)
- `scripts/aws/` — 애드온 설치 · DB/MQ 초기화 · 배포 · smoke test · 정리 (워크플로가 호출)
- `.github/workflows/` — `infra`(plan / persistent / up / down), `images`(서버 레포 → ECR)
- `helm/` — 서비스 공통 차트와 환경별 values

환경마다 다른 값은 모두 환경변수로 받습니다 → [`.env.example`](.env.example)

실행 방법: [docs/aws-runbook.md](docs/aws-runbook.md)
