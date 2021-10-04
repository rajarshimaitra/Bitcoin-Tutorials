### Install Bitcoin core, on linux machine

- Move to a temp directory
  ```shell
  cd /tmp
  ```
  
- Download Core, shasum, Orionowl publickey
  ```shell
  wget https://bitcoincore.org/bin/bitcoin-core-0.21.2/bitcoin-0.21.2-x86_64-linux-gnu.tar.gz
  wget https://bitcoincore.org/bin/bitcoin-core-0.21.2/SHA256SUMS.asc
  wget https://bitcoin.org/laanwj-releases.asc
  chmod +x ./bitcoin-22.0-x86_64-linux-gnu.tar.gz
  ```
- check that the reference checksum matches the real checksum
  (ignore the "lines are improperly formatted" warning)
  ```
  $ sha256sum --check SHA256SUMS.asc --ignore-missing
  > bitcoin-0.22.0-x86_64-linux-gnu.tar.gz: OK
  ```
  
- import the public key of Wladimir van der Laan, verify the signed  checksum file
  and check the fingerprint again in case of malicious keys
  ```
  $ gpg --import ./laanwj-releases.asc
  $ gpg --refresh-keys
  $ gpg --verify SHA256SUMS.asc
  > gpg: Good signature from "Wladimir J. van der Laan ..."
  > Primary key fingerprint: 01EA 5486 DE18 A882 D4C2 6845 90C8 019E 36C2 E964
  ```
  
- Extract the binaries and install into `/usr/local/bin`
  ```
  $ tar -xvf bitcoin-0.21.1-arm-linux-gnueabihf.tar.gz
  $ sudo cp /usr/local/bin bitcoin-0.22.0/bin/*
  $ bitcoind --version
  ```
  
 
