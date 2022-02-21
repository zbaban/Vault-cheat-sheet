# Vault-cheat-sheet

### Vault Config File
#### vault-server.hcl

```
disable_mlock = true
ui            = true
log_level     = "trace"

listener "tcp" {
  address     = "127.0.0.1:8200"
  tls_disable = "true"
}

storage "file" {
  path = "/tmp/vault-data"
}

license_path="/etc/vault.d/license.hclic"
```
[parameters](https://www.vaultproject.io/docs/configuration)

--------------------------------------------------------------------------------
### Running Vault
Dev Mode
```
vault server -dev
````

FRom config file 


--------------------------------------------------------------------------------

### Operator init

```
vault operator init
```
More options [here](https://www.vaultproject.io/docs/commands/operator/init)
    
--------------------------------------------------------------------------------

### Login
```
vault login
```
[usage](https://www.vaultproject.io/docs/commands/login#usage)

--------------------------------------------------------------------------------
### Status
```
vault status
```
[Examples](https://www.vaultproject.io/docs/commands/status)
--------------------------------------------------------------------------------
### Enable the license - Per Predecense

1. Config file, as seen above: `license_path = "/<PATH>/license.hclic"`

2. Environmnet Variable: `export VAULT_LICENSE=02MV4UU43BK5....`
3. Read from a file: `echo "02MV4UU43BK5..." >> license.hclic`, then verify the content copied correctly `cat license.hclic`
4. Environment Variable Path: `export VAULT_LICENSE_PATH=/etc/vault.d/license.hclic`
[more info](https://learn.hashicorp.com/tutorials/nomad/hashicorp-enterprise-license?in=vault/enterprise)
--------------------------------------------------------------------------------
### token
Usage: vault token <subcommand> [options] [args]
  `vault token create`
  ` vault token revoke TOKEN`
  `vault token renew TOKEN`
  `vault token capabilities`
  vault token lookup`
  
