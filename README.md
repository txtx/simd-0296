# SIMD-0296: Larger Transaction Sizes

## Quick Start

You can start sending larger transactions immediately using either @solana/kit
or @solana/web3.js.

If you're using @solana/web3.js, use:

```json
{
  "dependencies": {
    "@solana/web3.js": "1.98.4-experimental.3"
  }
}
```

If you're using @solana/kit, use:

```json
{
  "dependencies": {
    "@solana/kit": "5.1.0-experimental-20251205104522"
  }
}
```

The RPC URL for the SIMD-296 surfnet is:

```txt
https://simd-0296.surfnet.dev:8899
```

The WebSocket URL for the SIMD-296 surfnet is:

```txt
wss://simd-0296.surfnet.dev:8900
```

*NOTE*: While this test cluster enables larger transaction sizes for legacy type
transactions, the final live version of SIMD-296 will only be supported by v1 
transactions as specified in SIMD-0385.

## Overview

This Surfnet implements **SIMD-0296**, a Solana Improvement Document that increases the maximum transaction size from 1232 bytes to **4096 bytes**. This enables developers to build more complex on-chain applications without artificial constraints.

## The Problem

The current 1232-byte transaction limit is too restrictive for many legitimate developer use cases. This constraint artificially limits:

- Advanced cryptographic operations requiring larger proofs
- Complex multi-signature schemes
- Nested on-chain operations
- Zero-knowledge proof implementations
- Winternitz signatures and other post-quantum cryptography

Developers have been forced to work around these limits using fragmentation techniques or address lookup tables, adding unnecessary complexity.

## The Solution

SIMD-0296 increases the maximum transaction size to **4096 bytes** for v1 transactions (per SIMD-0385). This new limit:

- Leverages QUIC protocol capabilities for larger payloads
- Only applies to v1 transaction format
- Leaves legacy and v0 transactions unchanged (backward compatible)
- Covers 65% of real-world use cases based on bundle data analysis

## Use Cases Enabled

### Zero-Knowledge Proofs
Build privacy-preserving applications with ZK proofs that require larger transaction payloads.

### Advanced Multisig
Implement nested multisig schemes without fragmentation workarounds.

### Winternitz Signatures
Deploy post-quantum cryptographic schemes that require more transaction space.

### Complex DeFi Operations
Execute sophisticated DeFi strategies in single transactions without bundling.

## Resources

- [SIMD-0296 Full Specification](https://github.com/jacobcreech/solana-improvement-documents/blob/34241bb57aed6f51cc98c928c1b4fa8c6531d44a/proposals/0296-larger-transactions.md)
- [Solana Transaction Format Documentation](https://docs.solana.com/developing/programming-model/transactions)
- [SIMD-0385: Transaction Format v1](https://github.com/solana-foundation/solana-improvement-documents/pull/385)

## Support

Need help testing larger transactions? Reach out to the Solana community:
- [Solana Stack Exchange](https://solana.stackexchange.com/)
- [Developer Documentation](https://docs.solana.com/)
