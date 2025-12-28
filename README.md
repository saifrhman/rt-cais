# rt-cais
Real- Time Conversation AI Inference System

## System Architecture

```mermaid
flowchart TD
    A[Client / Simulator<br/>(Live chat / text stream<br/>partial utterances)]
    
    B[API Gateway<br/>(FastAPI, async)<br/>• request validation<br/>• timeout handling<br/>• request tracing]
    
    C[Conversation Manager<br/>• rolling context window<br/>• session state<br/>• partial input handling<br/>(Redis / in-memory)]
    
    D[Inference Orchestrator<br/>• routing logic<br/>• confidence thresholds<br/>• fallback decisions]
    
    E[Intent ML Model<br/>(PyTorch)]
    F[Sentiment ML Model<br/>(PyTorch)]
    
    G[Post-Processing Layer<br/>• confidence calibration<br/>• business rules<br/>• safe defaults]
    
    H[Response Layer<br/>• intent<br/>• sentiment<br/>• confidence<br/>• fallback flag]
    
    I[Monitoring & Observability<br/>• latency (p50/p95)<br/>• error rates<br/>• drift signals<br/>• fallback frequency]

    A --> B
    B --> C
    C --> D
    D --> E
    D --> F
    E --> G
    F --> G
    G --> H
    H --> I
```