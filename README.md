# NIST Statistical Test Suite Results

This repository contains statistical test results for quantum, pseudorandom, and hybrid random-number datasets evaluated using the NIST Statistical Test Suite (STS).

## Datasets

The evaluation includes 15 datasets divided into three groups:

| Generator | Datasets | Description |
|---|---|---|
| QRNG | `qrng_q1`–`qrng_q3` | Three independently acquired quantum random datasets processed using Von Neumann extraction |
| PRNG | `prng_s1`–`prng_s3` | Three classical CLCG4 pseudorandom datasets using different seeds |
| HRNG | `hrng_q1_s1`–`hrng_q3_s3` | Nine datasets derived from the quantum datasets through classically seeded permutations |

The QRNG datasets originate from quantum measurements. The HRNG datasets reuse the quantum-derived data with different classical permutations.

## Test Configuration

Each dataset was evaluated using the following configuration:

| Parameter | Value |
|---|---|
| Test suite | NIST STS 2.1.2 |
| Bitstream length | 1,000,000 bits |
| Number of bitstreams | 1,000 |
| Total tested bits per dataset | 1,000,000,000 |
| Statistical test instances | 188 per dataset |
| Total datasets | 15 |

The reported tests evaluate statistical properties such as frequency balance, runs, linear complexity, and periodic patterns.

## Repository Structure

```text
nist_vn_results/
├── README.md
├── manifest.csv
├── nist_rows.csv
├── qrng_q1/
├── qrng_q2/
├── qrng_q3/
├── prng_s1/
├── prng_s2/
├── prng_s3/
├── hrng_q1_s1/
├── hrng_q1_s2/
├── hrng_q1_s3/
├── hrng_q2_s1/
├── hrng_q2_s2/
├── hrng_q2_s3/
├── hrng_q3_s1/
├── hrng_q3_s2/
└── hrng_q3_s3/
```

Each dataset directory contains NIST STS reports and detailed output files.

## Result Files

**`manifest.csv`** contains the dataset identifiers, input filenames, source file sizes, test configuration, and completion status.

**`nist_rows.csv`** contains the consolidated results for individual statistical test instances, including:

- `type`: Generator family
- `dataset`: Dataset identifier
- `test`: NIST statistical test
- `test_instance`: Instance number within the test
- `uniformity_pvalue`: Reported uniformity p-value
- `passed`: Number of passing bitstreams
- `tested`: Number of evaluated bitstreams
- `pass_proportion`: Fraction of passing bitstreams
- `uniformity_fail`: Uniformity assessment failure indicator
- `proportion_fail`: Pass-proportion assessment failure indicator

The individual dataset directories contain the corresponding detailed NIST STS outputs.

## Interpretation

The statistical tests examine whether the generated bitstreams exhibit properties expected of random sequences.

A high pass proportion does not establish that a sequence is truly random, cryptographically secure, or unpredictable. Similarly, isolated test failures do not necessarily imply that a generator is unsuitable.

The results should be interpreted across the complete set of tests and datasets rather than through individual favorable metrics.

## Reproducibility

The repository preserves the generated statistical test outputs and consolidated summaries. The original input bitstreams are not included. Input filenames in the manifests and test reports identify the datasets used during evaluation.

The QRNG datasets represent independent quantum data acquisitions. The PRNG and HRNG datasets use classical seed configurations.

Reproducing the exact statistical results requires the corresponding original input bitstreams and NIST STS configuration.
