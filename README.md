# Gravity-SPHINCS

Submission to NIST's Post-Quantum Cryptography Project, structured as per
<http://csrc.nist.gov/groups/ST/post-quantum-crypto/submission-requirements/digital-optical-media.html>.

Gravity-SPHINCS is a stateless hash-based signature scheme designed by Jean-Philippe Aumasson and Guillaume Endignoux while working in Kudelski Security's research team.

## Content of this submission package

### Documentation

* [Supporting_Documentation/submission.pdf](Supporting_Documentation/submission.pdf): Reference documentation of Gravity-SPHINCS, include specification, security analysis, performance analysis.

* [Supporting_Documentation/latex_source/](Supporting_Documentation/latex_source/): LaTeX source of the reference documentation.

* [Supporting_Documentation/master_thesis_endignoux_guillaume.pdf](Supporting_Documentation/master_thesis_endignoux_guillaume.pdf): Masters thesis of Guillaume Endignoux, containing detailed analyses related to Gravity-SPHINCS' security.

* [Supporting_Documentation/parameters.py](Supporting_Documentation/parameters.py): Python script to compute the security of a Gravity-SPHINCS instance given a set of parameters.

### Implementations

* [Reference_Implementation/](Reference_Implementation): Our reference C89 implementation, without AES-NI nor SIMD instructions.

* [Additional_Implementations/fast](Additional_Implementations/fast): Our fast C89 implementation, with AES-NI and SIMD instructions.

* [Additional_Implementations/debug](Additional_Implementations/debug): A version of the reference implementation that prints intermediate values. This directory includes intermediate values files for each of the three Gravity-SPHINCS versions.

The directory [Optimized_Implementation/](Optimized_Implementation) contains a placeholder referring to the code under [Reference_Implementation/](Reference_Implementation).

The [Makefile](Reference_Implementation/Makefile) included in the [reference](Reference_Implementation) implementation has the following targets:

```bash
$ make
Please choose a target:
        analyze          runs static analyzers
        bench            runs speed benchmarks
        clean            cleans up
        format           formats the code using .clang-format rules
```

The [Makefile](Additional_Implementations/debug/Makefile) of the [debug](Additional_Implementations/debug) implementation in addition provides `make ivs` and `make check` targets.

### KATs

* [KAT/](KAT): Includes NIST's s [PQCgenKAT_sign.c](KAT/PQCgenKAT_sign.c), [rng.c](rng.c), and [rnc.h], as well as a [Makefile](KAT/Makefile) that we created to generate the files PQCsignKAT_64.req and PQCsignKAT_64.rsp required by NIST, using our fast implementation in [Reference_Implementation/](Reference_Implementation).

* [KAT/PQCsignKAT_all.req](KAT/PQCsignKAT_64_all.req): .req KAT file generated by running `make`, same for all Gravity-SPHINCS versions.

* [KAT/PQCsignKAT_65568.rsp](KAT/PQCsignKAT_65568.rsp), [KAT/PQCsignKAT_2097184.rsp](KAT/PQCsignKAT_2097184.rsp), [KAT/PQCsignKAT_1048608.rsp](KAT/PQCsignKAT_1048608.rsp): .rsp KAT file generated by running `make`, for the Gravity-SPHINCS versions S, M, and L, respectively.

## Intellectual property

Copyright notices are included in the header of each source code file.
Our original source code of Gravity-SPHINCS is copyright © 2017 Nagravision S.A., and was written by Jean-Philippe Aumasson and Guillaume Endignoux.

The fast, AES-NI-based Haraka implementation is copyright © 2016 Stefan Kölbl.

Our source code is released under [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license.

Patent situation: We haven't filed any patent related to Gravity-SPHINCS nor are we aware of existing patent or patent application covering Gravity-SPHINCS.

## Acknowledgments

Thanks to Samuel Neves for helping optimize our code.
