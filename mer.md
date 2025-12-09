```mermaid
usecaseDiagram
    actor C as "고객 (Customer)"
    actor A as "관리자 (Admin)"
    actor PA as "인쇄 에이전트 (Print Agent)"
    actor CS as "카드사 시스템 (Card System)"
    actor S as "공급업체 (Supplier)"

    package "주문형 인쇄 서비스 (Print-on-Demand Service)" {
        usecase "계정 생성" as UC1
        usecase "주문하기" as UC2
        usecase "필수 정보 확인" as UC3
        usecase "결제 처리" as UC4
        usecase "PDF 파일 검사" as UC5
        usecase "재고 모니터링" as UC6
        usecase "자재 주문" as UC7
    }

    C --> UC1
    C --> UC2
    UC2 ..> UC3 : <<include>>
    UC2 ..> UC4 : <<include>>
    UC4 -- CS : 승인 요청
    PA --> UC5 : 품질 검사
    A --> UC6
    A --> UC7 : 재고 부족 시
    UC7 -- S : 발주
```
