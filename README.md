# OpenTelemetry Collector for ELK Stack

This repository contains example manifests and configurations to deploy the **OpenTelemetry Collector** in Kubernetes environments, with the purpose of sending **logs, metrics, and traces** to an **ELK Stack (Elasticsearch, Logstash, Kibana)**.

---

## What is the OpenTelemetry Collector?

The **OpenTelemetry Collector** is a vendor-agnostic service that can receive, process, and export telemetry data (logs, metrics, and traces).  
It acts as a **pipeline** between your applications, Kubernetes infrastructure, and the backend systems that store and visualize observability data.

There are two main deployment patterns:

- **Agent**: runs as a deployment on each Kubernetes node, collecting telemetry directly from applications and system components.
- **Gateway**: runs as a centralized deployment, receiving telemetry from multiple agents and forwarding the data to external backends (e.g., Elasticsearch).

---

## Why use it with ELK?

By combining **OpenTelemetry Collector** with **ELK Stack**, you can:

- Collect application logs, Kubernetes metrics, and distributed traces in a standard format.
- Normalize and enrich the telemetry before sending it to Elasticsearch.
- Use **Kibana** to query, visualize, and correlate observability data across logs, metrics, and traces.
- Simplify integrations: instead of having each service send data directly to Elasticsearch/Logstash, everything flows through a flexible and scalable Collector pipeline.

---

## About this Repository

This repository provides **example Kubernetes manifests** to:

- Deploy the **OpenTelemetry Collector Agent** in a cluster (Deployment).
- Deploy the **OpenTelemetry Collector Gateway** as a centralized service.
- Configure pipelines to export telemetry data into an **ELK Stack**.

With these manifests, you can:

1. Collect telemetry from your applications and workloads running on a managed Kubernetes cluster (e.g., AKS, EKS, GKE, On-prem).
2. Send the telemetry to an **OpenTelemetry Gateway** inside the cluster.
3. Forward the processed data to your **Elasticsearch cluster**, where it becomes available in **Kibana**.

---

## Typical Flow

```text
Applications (logs/metrics/traces)
        │
        ▼
OpenTelemetry Collector Agent (Deployment)
        │
        ▼
OpenTelemetry Collector Gateway (Deployment)
        │
        ▼
Elasticsearch  →  Kibana (visualization)
```

---

## Use Cases

- Centralizing application logs across multiple namespaces and clusters.
- Forwarding Kubernetes system metrics to Elasticsearch.
- Capturing distributed traces from microservices and visualizing dependencies in Kibana.
- Acting as a **buffer and processor**, reducing coupling between your apps and your observability backend.

---

## How to Use

Clone the repository:

```bash
git clone https://github.com/rafa3lmonteiro/opentelemetry-collector.git
cd opentelemetry-collector
```
Make the necessary changes to adapt this deployment to your use case in your environment.

Apply the example manifests to your Kubernetes cluster:

```bash
kubectl apply -f manifests/
```

Check if everything went well and if the health of your Collector or Gateway is okay.

Update the **exporter configuration** to match your Elasticsearch endpoint and credentials.

---

## Next Steps

- Customize the processors to enrich telemetry with application/environment metadata.
- Secure the communication between Agents, Gateway, and ELK with TLS certificates.
- Scale the Gateway to handle production workloads.
- Extend with additional exporters (e.g., Prometheus, Jaeger, Grafana Loki, etc..).

---

## 📌 References

- [OpenTelemetry Collector Documentation](https://opentelemetry.io/docs/collector/)
- [Elastic Stack (ELK) Documentation](https://www.elastic.co/guide/index.html)
- [Kubernetes Observability with OpenTelemetry](https://opentelemetry.io/docs/kubernetes/)

---

✍️ Maintained by [Rafael Monteiro](https://github.com/rafa3lmonteiro)

---
