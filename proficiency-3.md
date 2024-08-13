# Proficiency-3

To configure multiple versions of Go (Golang) on your Ubuntu system, you can use the following steps:

#### 1. **Install Multiple Go Versions**

You can install different Go versions either manually or by using a version manager like `gvm` or `g`.

**Method 1: Using `gvm` (Go Version Manager)**

`gvm` is a popular tool for managing multiple versions of Go.

1.  **Install prerequisites**:

    ```bash
    sudo apt-get update
    sudo apt-get install curl git mercurial make binutils bison gcc
    ```
2.  **Install `gvm`**:

    ```bash
    bash < <(curl -sSL https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
    ```

    Then, source the `gvm` script:

    ```bash
    source ~/.gvm/scripts/gvm
    ```
3.  **Install Go versions**:

    ```bash
    gvm install go1.19
    gvm install go1.20
    ```
4.  **Use a specific Go version**:

    ```bash
    gvm use go1.20 --default
    ```

    This sets `go1.20` as the default version. To switch versions, use:

    ```bash
    gvm use go1.19
    ```

**Method 2: Using `g` (Golang Version Manager)**

`g` is another version manager for Go that is simpler to use.

1.  **Install `g`**:

    ```bash
    curl -sSL https://raw.githubusercontent.com/voidint/g/master/install.sh | bash
    ```
2.  **Install Go versions**:

    ```bash
    g install 1.19
    g install 1.20
    ```
3.  **Switch between versions**:

    ```bash
    g use 1.20
    ```

    To set a default version:

    ```bash
    g use 1.20 --default
    ```

**Method 3: Manually Download and Install**

If you prefer not to use a version manager, you can manually download and configure multiple Go versions.

1. **Download Go binaries**:
   * Visit [the Go download page](https://golang.org/dl/) and download the tarballs for the desired versions.
   *   Example for Go 1.19:

       ```bash
       wget https://golang.org/dl/go1.19.linux-amd64.tar.gz
       ```
2.  **Extract the binaries**:

    ```bash
    sudo tar -C /usr/local -xzf go1.19.linux-amd64.tar.gz
    sudo mv /usr/local/go /usr/local/go1.19

    wget https://golang.org/dl/go1.20.linux-amd64.tar.gz
    sudo tar -C /usr/local -xzf go1.20.linux-amd64.tar.gz
    sudo mv /usr/local/go /usr/local/go1.20
    ```
3.  **Create symbolic links**:

    * You can create symbolic links or modify your `PATH` to switch between versions.

    Example:

    ```bash
    sudo ln -sf /usr/local/go1.19/bin/go /usr/local/bin/go
    sudo ln -sf /usr/local/go1.20/bin/go /usr/local/bin/go
    ```

    To switch, change the symbolic link:

    ```bash
    sudo ln -sf /usr/local/go1.19/bin/go /usr/local/bin/go
    ```

#### 2. **Switch Between Versions**

Depending on the method you choose, you can easily switch between versions. If using a version manager (`gvm` or `g`), the command is straightforward (`gvm use go1.xx` or `g use 1.xx`). If you manually installed, you would update the symbolic link or adjust the `PATH` variable in your shell configuration file (`~/.bashrc` or `~/.zshrc`).

#### 3. **Verify the Active Version**

Check which version is currently active:

```bash
go version
```

#### 4. **Environment Variables**

Ensure your `GOPATH` and `GOROOT` are correctly set for the version you're using. These can be added to your shell configuration (`~/.bashrc`, `~/.zshrc`, etc.):

```bash
export GOROOT=/usr/local/go1.20
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```

#### Conclusion

With these methods, you can seamlessly manage and switch between multiple Go versions on Ubuntu. Using a version manager like `gvm` or `g` simplifies the process significantly.
