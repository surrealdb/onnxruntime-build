# NOTE: SurrealDB changes

The main repo is currently broken because the windows build fails. The issue was fixed in the onnxruntime repo by this PR (https://github.com/microsoft/onnxruntime/pull/17716), but they still need to make a new release so the original onnxruntime-build repo picks it up and triggers a new build.

Once the new release is out, we could use the onnxruntime-build's builds directly instead. The changes applied by us are in the `surrealdb` branch.

In case we want to trigger a new build out of that branch, you need to create a new tag:

```
$ git tag v1.16.3  && git push origin v1.16.3
```

This will trigger a new workflow and will create a release with the final artifacts.

# ONNX Runtime Build

This project is to build custom [ONNX Runtime](https://onnxruntime.ai) libraries which are not provided in [the official releases](https://github.com/microsoft/onnxruntime/releases).

Currently supports static library builds only with the default options.

## Building Libraries

### Prerequisites

- [Requirements for building ONNX Runtime for inferencing](https://onnxruntime.ai/docs/build/inferencing.html#prerequisites) (for native build)
- [Requirements for building ONNX Runtime for Web](https://onnxruntime.ai/docs/build/inferencing.html#prerequisites) (for Wasm build)
- Bash
  - On Windows, you can use Git Bash provided by [Git for Windows](https://git-scm.com/download/win).

### Build Scripts

Build for native:

```sh
./build-static_lib.sh
```

Build for Wasm:

```sh
./build-wasm-static_lib.sh
```
