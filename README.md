# phoenixminer

NVIDIA GPU miner for **Pearl** (`pearlhash`).

This repository is the **binary release channel** only. The source is
proprietary (see [LICENSE](LICENSE)); the source tree is not published here.
Every download is on the [**Releases**](../../releases) page.

Per-GPU hashrate and power figures are listed in each release's notes.

## Downloads

Each release ships three assets plus a `SHA256SUMS.txt`:

| Platform | Asset |
|---|---|
| HiveOS (custom miner) | `phoenixminer-<version>.tar.gz` |
| Linux x86-64 | `phoenixminer-<version>-linux-x86_64` |
| Windows x64 | `phoenixminer-<version>-windows-x64.zip` |

Requirements: an NVIDIA driver and (Linux) glibc 2.31+ - Ubuntu 20.04-based
HiveOS and newer. The CUDA runtime is linked statically, so no CUDA install is
needed on the rig. Native kernels cover Volta, Turing, Ampere, Ada and
Blackwell (SM 70 / 75 / 80 / 86 / 89 / 120).

### Verify your download

```sh
sha256sum -c SHA256SUMS.txt --ignore-missing
```

## HiveOS

1. Flight Sheet → Miner: **Custom**.
2. Installation URL: the `phoenixminer-<version>.tar.gz` asset URL from the
   release below.
3. Hash algorithm: `pearlhash`.
4. Pool URL: `host:port` (tick the SSL switch) or an explicit
   `stratum+ssl://host:port` (verified TLS).
5. Wallet template: `%WAL%.%WORKER_NAME%`, Pass: `x`.
6. Extra config args (optional, `;`-separated), e.g. `-keepalive`.

## Linux

```sh
tar xzf phoenixminer-<version>.tar.gz
cd phoenixminer
./phoenixminer -a pearlhash -pool HOST:PORT -wal WALLET.worker -pass x
```

`-help` lists all options. Prefix the pool with `stratum+ssl://` for verified
TLS (certificate checked against the system CA store).

## Dev fee

A **2%** dev fee is baked into each release binary and is disclosed in the
startup banner.

## Support

Setup help, tuning and announcements: [Discord](https://discord.gg/sDZPH3xf6).

## License

Proprietary. See [LICENSE](LICENSE). Binaries are provided "as is", without
warranty of any kind.
