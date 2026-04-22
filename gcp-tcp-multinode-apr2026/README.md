# NYDUX GCP Multi-Node TCP Benchmark — April 22, 2026

## Cluster
- 2 nodes: nydux-nccl-node-1, nydux-nccl-node-2
- Zone: us-central1-a
- Network: GCP internal TCP (10.128.0.x)
- Tool: OSU Micro-Benchmarks v7.3

## Key Findings

### Latency
- Min latency: 0.25 us (4B)
- 64KB latency: 5.42 us (no MTU cliff on TCP fabric)
- Contrast: InfiniBand shows 7x cliff at 64KB (21us to 158us)

### Bandwidth
- Peak: 17,143 MB/s at 262KB
- 4KB anomaly: 5,764 to 3,299 MB/s (43% drop)
- Recovery at 8KB: 5,739 MB/s

## Significance
TCP fabric shows no MTU cliff — confirming the 7x latency jump
in the InfiniBand benchmark is fabric-specific. The 4KB bandwidth
dip appears across both fabrics confirming buffer boundary effects
are universal regardless of interconnect type.
