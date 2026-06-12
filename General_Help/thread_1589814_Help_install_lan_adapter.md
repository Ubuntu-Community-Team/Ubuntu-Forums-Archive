---
title: "Help install lan adapter"
date: 2010-10-07
forum: General Help
---

### Post by hoosein on 2010-10-07
problem lan adapter Atheros L2 Fast Ethernet 10/100Base-T Controller



eror install

```
 make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/hossein/network/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/hossein/network/src/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/hossein/network/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

```

readme file

```
Linux* Base Driver for the Atheros(R) L2 Fast Ethernet Adapter
==========================================================================

Contents
========

- In This Release
- Building and Installation
- Command Line Parameters
- Additional Configurations
- Known Issues
- Support

In This Release
===============

This file describes the Linux* Base Driver for the Atheros(R) L2 Fast
Ethernet Adapter, version 1.0.x. This driver supports the 2.4.x and 2.6.x kernels.

This driver is only supported as a loadable module at this time. Atheros is not
supplying patches against the kernel source to allow for static linking of
the driver. For questions related to hardware requirements, refer to the
documentation supplied with your Atheros(R) adapter. All hardware
requirements listed apply to use with Linux.

Building and Installation
=========================

To build a binary RPM* package of this driver, run 'rpmbuild -tb
<filename.tar.gz>'. Replace <filename.tar.gz> with the specific filename of
the driver.

NOTE: For the build to work properly, the currently running kernel MUST match
      the version and configuration of the installed kernel sources. If you
      have just recompiled the kernel reboot the system now.

      RPM functionality has only been tested in Red Hat distributions.

1. Move the base driver tar file to the directory of your choice. For example,
   use /home/username/atl2 or /usr/local/src/atl2.

2. Untar/unzip archive:

     tar zxf atl2-x.x.x.tar.gz

3. Change to the driver src directory:

     cd atl2-x.x.x/src/

4. Compile the driver module:

     make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl2.[k]o

   The install locations listed above are the default locations. They might
   not be correct for certain Linux distributions. For more information,
   see the ldistrib.txt file included in the driver tar.

5. Install the module:

     insmod atl2 <parameter>=<value>

6. Assign an IP address to the interface by entering the following, where
   x is the interface number:

     ifconfig ethx <IP_address>

7. Verify that the interface works. Enter the following, where <IP_address>
   is the IP address for another machine on the same subnet as the interface
   that is being tested:

     ping  <IP_address>

Command Line Parameters
=======================

If the driver is built as a module, the  following optional parameters are
used by entering them on the command line with the modprobe or insmod command
using this syntax:

     modprobe atl2 [<option>=<VAL1>,<VAL2>,...]

     insmod atl2 [<option>=<VAL1>,<VAL2>,...]

For example, with two L001 PCIE adapters, entering:

     insmod atl2 TxMemSize=80,128
loads the atl2 driver with 8KB TX memory for the first adapter and 10KB TX memory
for the second adapter.

The default value for each parameter is generally the recommended setting,
unless otherwise noted.

    NOTES: A descriptor describes a data buffer and attributes related to the
           data buffer. This information is accessed by the hardware.

MediaType
Valid Range: 0-4
    0    - auto-negotiate at all supported speeds
    1    - only link at 100Mbps Full Duplex
    2    - only link at 100Mbps Half Duplex
    3    - only link at 10Mbps Full Duplex
    4    - only link at 10Mbps Half Duplex
Default Value: 0
    MediaType forces the line speed/duplex to the specified value in
    megabits per second(Mbps). If this parameter is not specified or is set
    to 0 and the link partner is set to auto-negotiate, the board will
    auto-detect the correct speed.

IntModTimer
Valid Range: 50-65000
Default Value: 100
    This value represents the minmum interval between interrupts controller
    generated.

RxMemBlock
Valid Range: 16-512
Default Value: 64
    This value is the number of receice memory block allocated by the driver.
    Increasing this value allows the driver to buffer more incoming packets.
    Each memory block is 1536 bytes.

    NOTE: Depending on the available system resources, the request for a
    higher number of receive descriptors may be denied.  In this case,
    use a lower number.

TxMemSize
Valid Range: 4-64
Default Value: 8
    This value is the number KB of transmit memory allocated by the driver.
    Increasing this value allows the driver to queue more transmits.

    NOTE: Depending on the available system resources, the request for a
    higher number of transmit descriptors may be denied.  In this case,
    use a lower number.

FlashVendor
Valid Range: 0-2
Default Value: 0
    This value standards on vendor of spi flash used by the adapter.
    0 for Atmel, 1 for SST, 2 for ST
    

Additional Configurations
=========================

  Configuring the Driver on Different Distributions
  -------------------------------------------------

  Configuring a network driver to load properly when the system is started is
  distribution dependent. Typically, the configuration process involves adding
  an alias line to /etc/modules.conf as well as editing other system startup
  scripts and/or configuration files. Many popular Linux distributions ship
  with tools to make these changes for you. To learn the proper way to
  configure a network device for your system, refer to your distribution
  documentation. If during this process you are asked for the driver or module
  name, the name for the Linux Base Driver for the Atheros L2 is atl2
  
  As an example, if you install the atl2 driver for two L2 adapters
  (eth0 and eth1) and set the speed and duplex to 10full and 100half, add the
  following to modules.conf:

       alias eth0 atl2
       alias eth1 atl2
       options atl2 Speed=10,100 Duplex=2,1

  Viewing Link Messages
  ---------------------

  Link messages will not be displayed to the console if the distribution is
  restricting system messages. In order to see network driver link messages
  on your console, set dmesg to eight by entering the following:

       dmesg -n 8

  NOTE: This setting is not saved across reboots.


Known Issues
============

NOTE: For distribution-specific information, see the ldistrib.txt file
      included in the driver tar.

  Driver Compilation
  ------------------

  When trying to compile the driver by running make install, the following
  error may occur:

      "Linux kernel source not configured - missing version.h"

  To solve this issue, create the version.h file by going to the Linux source
  tree and entering:

      make include/linux/version.h.


Support
=======

For general information, go to the Atheros support website at:

    http://support.atheros.com

If an issue is identified with the released source code on the supported
kernel with a supported adapter, email the specific information related to
the issue to xiong.huang@atheros.com

License
=======

This software program is released under the terms of a license agreement
between you ('License') and Atheros. Do not use or load this software or any
associated materials (collectively, the 'Software') until you have carefully
read the full terms and conditions of the LICENSE located in this software
package. By loading or using the Software, you agree to the terms of this
Agreement. If you do not agree with the terms of this Agreement, do not
install or use the Software.

* Other names and brands may be claimed as the property of others.

```

---

### Post by hoosein on 2010-10-07
help me!

---

