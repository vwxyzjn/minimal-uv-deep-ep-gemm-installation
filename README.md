# Minimal uv deep ep gemm installation

This is a minimal uv project that installs [deep_ep](https://github.com/deepseek-ai/DeepEP) and [deep_gemm](https://github.com/deepseek-ai/DeepGEMM) with the minimal dependencies.

See https://github.com/astral-sh/uv/issues/15316#issuecomment-3193922948 for more details.

## Usage

```bash
# Install ninja
sudo apt-get update
sudo apt-get install ninja-build
sudo apt-get -y install cuda-toolkit-12

# Install dependencies
uv sync

# Automatically discover NVIDIA nvshmem directory
export NVSHMEM_DIR=$(uv run python -c "import importlib.util; print(importlib.util.find_spec('nvidia.nvshmem').submodule_search_locations[0])")  # Use for DeepEP installation
export LD_LIBRARY_PATH="${NVSHMEM_DIR}/lib:$LD_LIBRARY_PATH"
uv run test_low_latency.py
```

<img width="681" height="646" alt="image" src="https://github.com/user-attachments/assets/6c0ea997-845d-4ff8-a5d2-f1e4f2930e78" />

<img width="1361" height="751" alt="image" src="https://github.com/user-attachments/assets/e67322b5-03b5-4247-b55c-e7ff5f970351" />
