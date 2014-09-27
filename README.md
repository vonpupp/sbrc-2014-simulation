********************
SBRC-2014-SIMULATION
********************

This repository contains the source code to reproduce the experiments for the
paper entitled ["Energy-Efficient Virtual Machines
Placement"](http://www.albertdelafuente.com/lib/exe/fetch.php/home/academic/2014a-energy-efficient-vm-placement-sbrc.pdf),
which has been accepted to SBC [32nd Brazilian Symposium on Computer Networks
and Distributed Systems](http://www.sbrc2014.ufsc.br/).

## Using Vagrant: Installing from a base box

You can easily setup a Vagrant box to reproduce the simulation. The requirements
to run the box are [Vagrant](https://www.vagrantup.com/downloads.html), and
[VirtualBox](https://www.virtualbox.org/wiki/Downloads). Once installed run:

### Get the box

```shell
# Initialize the box:
vagrant init jfredett/arch-chef

# Start the box:
vagrant up

# Ssh into the box:
vagrant ssh
```

### Install the dependencies

```shell
# To install the base packages run:
wget --no-check-certificate https://raw.githubusercontent.com/vonpupp/sbrc-2014-simulation/master/setup/arch-setup.sh -O - | sh
```

### Clone the repository

```shell
# First, clone the repository and initialize the submodules:
git clone https://github.com/vonpupp/sbrc-2014-simulation.git
cd sbrc-2014-simulation
./00submodules.sh

# Then execute the experiments (Note that you can customize the ``scenariosvar.py`` to change the simulation parameters):
python 01simulate.py

# And summarize the data and generate the figures with:
python 02summarizedata.py
```

## Alternative method: Using the sbrc14-pycloudsim pre-built box

There is also a pre-built box also in case you prefer this method.

```shell
# Initialize the box:
vagrant init vonpupp/sbrc14-pycloudsim

# Start the box:
vagrant up

# Ssh into the box:
vagrant ssh
```

The workload data have been obtained from the CoMon project, a monitoring
infrastructure for PlanetLab (http://comon.cs.princeton.edu/). The data used in
the simulations in the CSV format are available at
https://github.com/vonpupp/planetlab-workload-traces which is a fork from Dr.
Anton Beloglazov.

## License

Copyright (C) 2014 Albert De La Fuente Vigliotti
