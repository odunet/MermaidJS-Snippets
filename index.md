# Mermaid Markdown Practice

### Order Process - Entity Relationship
```mermaid
erDiagram
  Customer ||--o{ Order : places
  Order ||--|{ LineItem : contains
  Customer {
    String id
    String name
  }
  Order {
    String id
    OrderStatus status
  }
  LineItem {
    String code
    String description
    Number quantity
  }
```

### Payment Process - Class Diagram
```mermaid
classDiagram
  class Order {
    +OrderStatus status
  }
  class OrderStatus {
    <<enumeration>>
    FAILED
    PENDING
    SUCCESS
  }
  class PaymentProcessor {
    <<interface>>
    -String apiKey
    #connect(String url, JSON header)
    +processPayment(Order order) OrderStatus
  }
  class Customer {
    +String name
  }
  Customer <|-- PrivateCustomer
  Customer <|-- BusinessCustomer
  PaymentProcessor <|-- StripePaymentProcessor
  PaymentProcessor <|-- PaypalPaymentProcessor
  Order o-- Customer_Agregation
  Car *-- Engine_Composition
```
### Animal Class - Class Diagram
```mermaid
classDiagram
  Animal <|-- Duck
  Animal <|-- Fish
  Animal <|-- Zebra
  Animal : +int age
  Animal : +String gender
  Animal: +isMammal()
  Animal: +mate()
  class Duck{
      +String beakColor
      +swim()
      +quack()
  }
  class Fish{
      -int sizeInFeet
      -canEat()
  }
  class Zebra{
      +bool is_wild
      +run()
  }
```

### Pie Chart
```mermaid
pie
    title Key elements in Product X
    "Calcium" : 42.96
    "Potassium" : 50.05
    "Magnesium" : 10.01
    "Iron" :  5
```

### OAUTH Process - Sequence Diagram
```mermaid
sequenceDiagram
  autonumber
  participant Client
  participant OAUTHProvider
  participant Server
  Client->>OAUTHProvider: Request access token
  activate OAUTHProvider
  OAUTHProvider->>Client: Send access token
  deactivate OAUTHProvider
  Client->>Server: Request resource
  activate Server
  Server->>OAUTHProvider: Validate token
  activate OAUTHProvider
  OAUTHProvider->>Server: Token valid
  deactivate OAUTHProvider
  Server->>Client: Send resource
  deactivate Server
```

### Login Process - Flowchart
```mermaid
flowchart
  S[Start] --> A
  A(Enter our email address) --> B{Existing user?}
  B -->|No| C(Enter name)
  C --> D{Accept condition?}
  D -->|No| A
  D -->|Yes| E(Send email with magic link)
  B -->|Yes| E
  E --> End
```