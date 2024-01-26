# Terraform usage
----------------
![terraform-lint](https://github.com/SebastianUA/terraform/workflows/terraform-lint/badge.svg) ![](https://img.shields.io/github/last-commit/sebastianua/terraform.svg) ![](https://img.shields.io/github/repo-size/sebastianua/terraform.svg)  ![LatestVer](https://img.shields.io/github/release/sebastianua/terraform.svg) ![License](https://img.shields.io/badge/License-GPLv3-blue.svg)

## Install Terraform

- If you're using MacOS, then you can run the next command to install TF:
```bash
$ brew install terraform
```
NOTE: you must install `HOMEBREW` to your host something like:
```bash
$ sudo /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
- For Unix/Linux OS you might go to the official Terraform site and download bin-file with software.

## Init

---------
First of all, you should clone this repo to your local machine. I provided modules with simple examples. After, go to needed example and run the next command:
```bash
$ terraform init
```

This command will init everything to provision module(s).


## Plan
---------
When you set `terraform init` you will be able to see which services are going to create with the next command:

```bash
$ terraform plan
```

If you're using `tfvars`, you can run the following command:

```bash
$ terraform plan -var-file terraform.tfvars
```

It's a good point to use `tfvars` for multiple environments, - as example.

## Apply
---------
To apply your stack, you can use:

```bash
$ terraform apply
```

Or:

```bash
$ terraform apply -var-file terraform.tfvars
```

Also, you can use `-auto-approve` command to automatically apply the stack.

## Destroy
---------
To terminate the stack, use:

```bash
$ terraform destroy
```

Or:

```bash
 $ terraform destroy -var-file terraform.tfvars
```

Also, you can use `-auto-approve` command to automatically terminate the stack.

## graph

If you're using mac OS, you must install the next package:
```bash
$ brew install graphviz
```

Then, run:
```bash
$ terraform graph | dot -Tsvg > graph.svg

$ terraform graph | dot -Tpng > graph.png
```

## state

If you would like to remove your stack from TF statefile, you can use this command:

```bash
$ terraform state rm "module.rds_single_mysql.aws_db_subnet_group.db_subnet_group[0]"
```

The structura is the next one: `module.<MODULE_NAME>.<RESOURCE_NAME>.<NAME_of_RESOURCE>[count.index]`.

Where:

- MODULE_NAME - The module name.
- RESOURCE_NAME - the resource name of provider.
- NAME_of_RESOURCE - The name of resource of created RESOURCE_NAME.
- [count.index] - Index of resource in loop.

That's it.

## import

If you would like to import some stack stack to TF, you can use this command:

```bash
$ terraform import --var 'db_password=PW_HERE' "module.rds_single_mysql.aws_db_subnet_group.db_subnet_group[0]" "terraform-20220711082550455200000001"
```

The structura is the next one: `module.<MODULE_NAME>.<RESOURCE_NAME>.<NAME_of_RESOURCE>[count.index] <IMPORTING_VALUE> ` .

Where:

- MODULE_NAME - The module name.
- RESOURCE_NAME - the resource name of provider.
- NAME_of_RESOURCE - The name of resource of created RESOURCE_NAME.
- [count.index] - Index of resource in loop.
- IMPORTING_VALUE - The value to import.

That's it.

## Help

---------

To get help, use:

```bash
$ terraform -help
Usage: terraform [global options] <subcommand> [args]

The available commands for execution are listed below.
The primary workflow commands are given first, followed by
less common or more advanced commands.

Main commands:
  init          Prepare your working directory for other commands
  validate      Check whether the configuration is valid
  plan          Show changes required by the current configuration
  apply         Create or update infrastructure
  destroy       Destroy previously-created infrastructure

All other commands:
  console       Try Terraform expressions at an interactive command prompt
  fmt           Reformat your configuration in the standard style
  force-unlock  Release a stuck lock on the current workspace
  get           Install or upgrade remote Terraform modules
  graph         Generate a Graphviz graph of the steps in an operation
  import        Associate existing infrastructure with a Terraform resource
  login         Obtain and save credentials for a remote host
  logout        Remove locally-stored credentials for a remote host
  output        Show output values from your root module
  providers     Show the providers required for this configuration
  refresh       Update the state to match remote systems
  show          Show the current state or a saved plan
  state         Advanced state management
  taint         Mark a resource instance as not fully functional
  test          Experimental support for module integration testing
  untaint       Remove the 'tainted' state from a resource instance
  version       Show the current Terraform version
  workspace     Workspace management

Global options (use these before the subcommand, if any):
  -chdir=DIR    Switch to a different working directory before executing the
                given subcommand.
  -help         Show this help output, or the help for a specified subcommand.
  -version      An alias for the "version" subcommand.
