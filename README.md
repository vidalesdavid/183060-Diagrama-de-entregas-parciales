# 183060-Diagrama-de-entregas-parciales
```mermaid
flowchart TD

    A["Sales Order<br/>Orden de Venta"] --> B{"¿Hay suficiente<br/>inventario?"}

    B -->|"Sí"| C["Delivery<br/>Entrega completa"]
    C --> D["A/R Invoice<br/>Factura de Cliente"]
    D --> E["Incoming Payment<br/>Pago recibido"]
    E --> F["Sales Order<br/>Cerrada"]

    B -->|"No"| G["Delivery<br/>Entrega parcial"]

    G --> H["A/R Invoice<br/>Facturar lo entregado"]
    H --> I["Incoming Payment<br/>Pago de lo entregado"]

    G --> J{"¿Qué ocurre con<br/>la cantidad pendiente?"}

    J -->|"Hay material disponible<br/>posteriormente"| K["Segunda Delivery<br/>Entrega de cantidad pendiente"]
    K --> L["A/R Invoice<br/>Factura restante"]
    L --> M["Incoming Payment<br/>Pago restante"]
    M --> N["Sales Order<br/>Cerrada"]

    J -->|"No hay material<br/>disponible actualmente"| O{"¿Se puede<br/>reponer inventario?"}

    O -->|"Sí"| P["Comprar / Producir / Reponer<br/>Inventario"]
    P --> K

    O -->|"No"| Q{"¿El cliente aún<br/>quiere la cantidad pendiente?"}

    Q -->|"Sí"| R["Sales Order permanece abierta<br/>Cantidad pendiente"]
    R --> S["Esperar reposición<br/>o nueva disponibilidad"]
    S --> O

    Q -->|"No"| T["Cancelar cantidad pendiente<br/>Cerrar línea / pedido"]
    T --> U["Sales Order<br/>Cerrada"]

    style A fill:#e8f4ff,stroke:#2563eb
    style C fill:#e8f4ff,stroke:#2563eb
    style G fill:#fff3cd,stroke:#d39e00
    style K fill:#e8f4ff,stroke:#2563eb
    style R fill:#f8d7da,stroke:#dc3545
    style T fill:#d1e7dd,stroke:#198754
    style F fill:#d1e7dd,stroke:#198754
    style N fill:#d1e7dd,stroke:#198754
    style U fill:#d1e7dd,stroke:#198754
  ```
