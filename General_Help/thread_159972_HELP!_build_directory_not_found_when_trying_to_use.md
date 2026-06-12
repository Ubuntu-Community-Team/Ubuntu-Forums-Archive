---
title: "HELP! build directory not found when trying to use the &quot;make&quot; command!"
date: 2006-04-13
forum: General Help
---

### Post by Elif Tymes on 2006-04-13
Here's the output I get from the "make" command.
> 
Checking in /lib/modules/2.6.12-10-386 for ieee80211 components...
find: /lib/modules/2.6.12-10-386/build/: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//.config: No such file or directory
grep: /lib/modules/2.6.12-10-386/build//include/linux/autoconf.h: No such file or directory
make -C /lib/modules/2.6.12-10-386/build M=/home/zspencer/Desktop/ieee80211-1.1.12 MODVERDIR=/home/zspencer/Desktop/ieee80211-1.1.12 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

The weird thing is, this is for any application I want to build. Currently I'm trying to install the ieee80211-1.1.12 application so that I may install my drivers for my WLAN card.

Any help would be appreciated.

---

### Post by Sutekh on 2006-04-13
You need the appropriate kernel headers, do you have any sort of internet connection in Ubuntu, or are you relying on getting the WLAN card installed?

To start have you installed the build-essential package?  It's availble on the Install CD, use
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```To install it.

How did you get the 2.6.12-10-386 kernel installed? (The default one is 2.6.12-9-386)

You need the kernel headers for that particular kernel.

If you have any kind of connection in Ubuntu, use
```
sudo apt-get install linux-headers-2.6.12-10-386
```
If you have no net connection, then you can download them from here

[Ubuntu Packages - linux-headers-2.6.12-10](http://packages.ubuntu.com/breezy/devel/linux-headers-2.6.12-10)

Then you need get that package into Ubuntu and install it using this command from the folder containing the headers .deb file```
sudo dpkg -i linux-headers-2.6.12-10_2.6.12-10.30_i386.deb
```

---

### Post by Elif Tymes on 2006-04-13
Ooooh! THank you so much! I assumed that installing the upgraded file system would install the headers.

I've actually got the 686-smp kernel installed(Woo+! Core Duo!) but I thought that may be part of the problem so I went back to the 386 normal.

Thanks for the help :)

(I'll apt-get that as soon as I'm done copying dataish files from my desktop to my fat32 partition... I *think* I've got it set up for my username, but I want the mount to be useable by all usergroups(yes, dangerous, but this is just the one partition, which won't have any apps on it)

Switching the ownership to"nobody" should do that, right?

---

### Post by Sutekh on 2006-04-13
Wait.  Is the 686-smp kernel the same version (2.6.12-10) as the 386?  

If they are different you will need to compile the driver for each version of the kernel (I mean different **version numbers**, ie 2.6.12-10/2.6.12-11/etc **not different architectures** like 386/686/etc.)

You will also need to do this when new kernel updates are applied.


For the FAT partition; how is it mounted?  Through the configuration file /etc/fstab?  To be usable by everyone, make sure that the entry for the FAT partition looks like (a general example)
```
/dev/hda1   /media/fat_files   vfat   iocharset=utf8,umask=0000   0   0
```If you ever want to change the access, modify the umask option, according to this table
[quote= Gentoo-Wiki]
umask: octal file permissions

You can change permissions using the parameter umask. But be aware that it must be the bitmask of permissions that are not present for the mountpoint. It is an octal number, formed like this:

* character '0': Indicates that this is an octal number, not decimal.
* first digit: owner user permissions
* second digit: owner group permissions
* third digit: world permissions (every other user on the system)

The modes are as follows (the first column is the mode octal number):

M | R W X
-------------
0 | * * *
1 | * * -
2 | * - *
3 | * - -
4 | - * *
5 | - * -
6 | - - *
7 | - - -

For example, if you want that everybody be able to read, write, and execute every file in your /mnt/c, you should specify the mask 0000: [/quote]

---

### Post by Elif Tymes on 2006-04-13
Ok, one quick last question...

I'm to the line where you run this line..

[QUOTE]DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p \
/etc/hotplug/firmware.agent)
[QUOTE]

However, the DIR variable doesn't get defined, if I echo it, (echo $DIR) it puts a blank line, and if I use it in the next couple lines it's the same deal.

---

### Post by Sutekh on 2006-04-13
That was so far over my head I didn't even notice it.

What instructions are you using to install this driver?  Can you link them?

---

### Post by Elif Tymes on 2006-04-13
Dunno about linking, as it's in their INSTALL file they include....

As for over your head, I can understand that. I think I get most of it... assign the results of a regular expression to the DIR variable, however for some reason the regular expression seems to be returning blank... Gonna try some more tweaking/reading through the man after I post this.

```
 
Intel(R) PRO/Wireless 3945ABG Network Connection driver for Linux* in 
support of:

Intel(R) PRO/Wireless 3945ABG Network Connection Adapter
Intel(R) PRO/Wireless 3945BG Network Connection Adapter

Copyright (C) 2005 - 2006, Intel Corporation

INSTALL

Version: 1.0.0
Date   : March 20, 2006


Index
-----------------------------------------------
0.  IMPORTANT INFORMATION BEFORE USING THIS DRIVER
1.  QUICK INSTALL STEPS
2.  INSTALLING IN YOUR DISTRIBUTION
3.  AUTOMATIC DAEMON LOADING VIA MODPROBE
4.  BUILD/INSTALLATION OVERVIEW
5.  GETTING THE SOURCE
6.  KERNEL REQUIREMENTS - 2.6.13+
7.  KERNEL REQUIREMENTS - Configuration
8.  SYSFS
9.  UPGRADING FROM PRIOR VERSIONS
10. BUILDING EXTERNAL (outside of the kernel tree)
11. INSTALLING MICROCODE
12. INSTALLING REGULATORY DAEMON
13. LOADING THE DRIVER


0.   IMPORTANT INFORMATION BEFORE USING THIS DRIVER
-----------------------------------------------

Important Notice FOR ALL USERS OR DISTRIBUTORS!!!!

Intel wireless LAN adapters are engineered, manufactured, tested, and
quality checked to ensure that they meet all necessary local and
governmental regulatory agency requirements for the regions that they
are designated and/or marked to ship into. Since wireless LANs are
generally unlicensed devices that share spectrum with radars,
satellites, and other licensed and unlicensed devices, it is sometimes
necessary to dynamically detect, avoid, and limit usage to avoid
interference with these devices. In many instances Intel is required to
provide test data to prove regional and local compliance to regional and
governmental regulations before certification or approval to use the
product is granted. Intel's wireless LAN's EEPROM, firmware, and
software driver are designed to carefully control parameters that affect
radio operation and to ensure electromagnetic compliance (EMC). These
parameters include, without limitation, RF power, spectrum usage,
channel scanning, and human exposure.

For these reasons Intel cannot permit any manipulation by third parties
of the software provided in binary format with the wireless WLAN
adapters (e.g., the EEPROM and firmware). Furthermore, if you use any
patches, utilities, or code with the Intel wireless LAN adapters that
have been manipulated by an unauthorized party (i.e., patches,
utilities, or code (including open source code modifications) which have
not been validated by Intel), (i) you will be solely responsible for
ensuring the regulatory compliance of the products, (ii) Intel will bear
no liability, under any theory of liability for any issues associated
with the modified products, including without limitation, claims under
the warranty and/or issues arising from regulatory non-compliance, and
(iii) Intel will not provide or be required to assist in providing
support to any third parties for such modified products.

Note: Many regulatory agencies consider Wireless LAN adapters to be
modules, and accordingly, condition system-level regulatory approval
upon receipt and review of test data documenting that the antennas and
system configuration do not cause the EMC and radio operation to be
non-compliant.

The drivers available for download from SourceForge are provided as a
part of a development project.  Conformance to local regulatory
requirements is the responsibility of the individual developer.  As
such, if you are interested in deploying or shipping a driver as part of
solution intended to be used for purposes other than development, please
obtain a tested driver from Intel Customer Support at:

http://support.intel.com/support/notebook/sb/CS-006408.htm


2. QUICK INSTALL STEPS
-----------------------------------------------

The following provides steps that can be used to manually install and 
load the driver.  

Lines beginning with % can be run as any user.  Lines beginning with # 
must be run as root.

First, we build and install the ieee80211 subsystem.  You can obtain 
the latest ieee80211 subsystem from http://ieee80211.sf.net.  We 
recommend version 1.1.12 or newer:

	% tar xzvf ieee80211-1.1.12.tgz
	% cd ieee80211-1.1.12
	% make 
	# make install   <--- You may need to be root
	% cd ..

If you encounter problems with the above, you may need to install the 
ieee80211 sources into your kernel and then build it as part of your 
kernel image.  See the INSTALL and README.ieee80211 files provided in 
the ieee80211 subsystem package for more information.

Once the ieee80211 subsystem is installed, we build the ipw3945.ko module:

	% tar xzvf ipw3945-1.0.0.tgz
	% cd ipw3945-1.0.0
	% make

Now we install the firmware files (first finding where to install them):

	% wgetcd . http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.13.tgz .
	% DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
		/etc/hotplug/firmware.agent)
	% tar xzvf ipw3945-ucode-1.13.tgz 
	% less ipw3945-ucode-1.13/LICENSE.ipw3945-ucode
	# cp ipw3945-ucode-1.13/ipw3945.ucode $DIR

NOTE:  'DIR' above typically works out to /lib/firmware.

Now we obtain the regulatory daemon:

	% wget http://bughost.org/ipw3945/daemon/ipw3945d-1.7.18.tgz .
	% tar xzvf ipw3945d-1.7.18.tgz
	% less ipw3945d-1.7.18/LICENSE.ipw3945d

Depending on your architecture perform one of the following	

For 32-bit systems:

	# cp ipw3945d-1.7.18/x86/ipw3945d /sbin

or for 64-bit systems:

	# cp ipw3945d-1.7.18/x86_64/ipw3945d /sbin

And now we can try to load the module, first clearing the kernel log:

	# ./load debug=0

Finally we can check to see if things worked:

	# iwconfig eth1

You should see something like:

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And now you are ready to go.  Configure your AP using iwconfig:

	# iwconfig eth1 essid Whatever
	# iwconfig eth1 key DEADBEEF00
	# iwconfig eth1

eth1      IEEE 802.11g  ESSID:"Whatever"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:18:18:30
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:DEAD-BEEF-00   Security mode:open
          Power Management:off
          Link Quality=98/100  Signal level=-53 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The specifics of how to bring up the interface is heavily dependent on 
the specific distribution you are using from here on out.


2.  INSTALLING IN YOUR LINUX DISTRIBUTION
-----------------------------------------------
Since each distribution is different, we can not cover all of the steps that
may be required to install and configure your device for the particular 
distribution you are using.

Please refer to your distribution's documentation for information on how
to configure a wireless network driver within your environment.


3.  AUTOMATIC DAEMON LOADING VIA MODPROBE
-----------------------------------------------

There are some typical steps that are fairly generic in order 
to automate the launching of the daemon you can use your 
distribution's modprobe configuration.  To do this, you need to copy 
ipw3945.ko into your depmod path.  This is typically done via:

	# cp ipw3945.ko /lib/modules/$(uname -r)
	# depmod -a

Now, when you run modprobe it will load the module (and any dependencies, 
such as ieee80211.ko) and modprobe -r will remove the module.  The next 
step is to automate the launching and unloading of the regulatory 
daemon.  To do this, you typically place the following two lines into 
your /etc/modprobe.conf or into a new file /etc/modules.d/ipw3945:

	# echo install ipw3945 /sbin/modprobe --ignore-install ipw3945 ; \
sleep 0.5 ; /sbin/ipw3945d --quiet >> /etc/modules.d/ipw3945

	# echo remove ipw3945  /sbin/ipw3945d --kill ; \
/sbin/modprobe -r --ignore-remove ipw3945 >> /etc/modules.d/ipw3945

NOTE:  The \ above is to continue the entered line to the next line (the 
lines added to the file are wider than 80 columns and so would wrap)

On some distributions you then may need to run the 'modules-update' 
script.

To verify if the above is working, you can type:

	# modprobe ipw3945
	# ps -C ipw3945d

If you see a running 'ipw3945d' then it launched the daemon for you.


4.  BUILD/INSTALLATION OVERVIEW 
-----------------------------------------------

Installation of the current Intel PRO/Wireless 3945ABG Network Connection
driver for Linux involves several steps:

1)  Get the source, microcode, and regulatory daemon.

2)  Check for certain capabilities in your kernel, and rebuild the kernel
    if necessary.

3)  Remove any old ieee80211 or ipw3945 drivers, and remove any kernel
    configurations relating to them.

4)  Build and install the current ieee80211 module.

5)  Build and install the current ipw3945 module (uses files from ieee80211).

6)  Download and install current microcode.

6)  Download and install current regulatory daemon.

7)  Read README.ipw3945 for much helpful information on how to use the
    Intel PRO/Wireless 3945ABG Network Connection driver for Linux.


5.  GETTING THE SOURCE AND FIRMWARE
-----------------------------------------------

You can get the latest driver source code tarball from:

	http://ipw3945.sf.net

You must also obtain the ieee80211 subsystem from a separate project:

	http://ieee80211.sf.net

Instructions for obtaining microcode and regulatory daemon can be found at:

	http://ipw3945.sf.net/binaries.php.

Each package contains installation steps on how to install the files 
onto your system.  You'll need to unpack the tarballs and then you 
can view the INSTALL files.

	% tar xzvf ipw3945-1.0.0.tgz
	% tar xzvf ipw3945d-1.7.18.tgz
	% tar xzvf ipw3945-ucode-1.13.tgz
	% tar xzvf ieee80211-1.1.12.tgz
	% less ipw3945-1.0.0/INSTALL  
	% less ipw3945d-1.7.18/INSTALL  
	% less ipw3945-ucode-1.13/INSTALL  



6.  KERNEL REQUIREMENTS - 2.6.13+
-----------------------------------------------

The Intel PRO/Wireless 3945ABG Network Connection driver for Linux is 
currently maintained only for 2.6.13+ versions of the Linux kernel, 
but may work in older versions.  We try (when possible) to provide 
backward compatibility patches to the driver to keep it working for as 
long as possible with legacy kernels.


7.  KERNEL REQUIREMENTS - Configuration
-----------------------------------------------

Your kernel must be configured and compiled to provide certain capabilities
needed by the ieee80211 and ipw3945 source files.

You can verify that your running kernel is configured properly by
searching the following file for the #define entries described below:

	/lib/modules/$(uname -r)/build/include/linux/autoconf.h

If you need to change anything in your kernel configuration (e.g. using
make menuconfig), make sure that you also rebuild, install, and reboot to the
new kernel image before proceding with your ipw3945 driver upgrade.  For help
or instructions on configuring and building the kernel, please consult the
documentation contained in your distribution.

MAKE SURE THAT THE FOLLOWING CAPABILITIES ARE ENABLED:

~~~~~~~~~~~~~~~~~~~~~~~~~~~
#define CONFIG_NET_RADIO 1
~~~~~~~~~~~~~~~~~~~~~~~~~~~
Failure to enable this will result in the Wireless Tools (iwconfig, iwlist,
etc.) not functioning.  This is enabled via menuconfig:

        Device Drivers ->
           Networking support ->
              Network device support ->
                 Wireless LAN (non-hamradio) ->
                    Wireless LAN drivers (non-hamradio)...


~~~~~~~~~~~~~~~~~~~~~~~~~~~
#define CONFIG_FW_LOADER 1
~~~~~~~~~~~~~~~~~~~~~~~~~~~
The driver loads the microcode image via the Linux firmware hotplug 
capability (see later section on loading microcode).  This is enabled 
via menuconfig:

        Device Drivers ->
           Generic Driver Options ->
              Hotplug firmware loading support


~~~~~~~~~~~~~~~~~~~~~~~~~~~
#define CONFIG_CRYPTO 1
#define CONFIG_CRYPTO_ARC4(_MODULE) 1
#define CONFIG_CRC32(_MODULE) 1
~~~~~~~~~~~~~~~~~~~~~~~~~~~
The driver uses the WEP encryption and decryption algorithms provided
by the Linux kernel.  To use WEP you must enable the crypto library support
(CONFIG_CRYPTO) and the ARC4 cipher algorithm (CONFIG_CRYPTO_ARC4) via:

        Cryptographic options ->
           ARC4 cipher algorithm

You also need to enable the CRC32 (CONFIG_CRC32) algorithm via:

        Library routines ->
                CRC32 functions


~~~~~~~~~~~~~~~~~~~~~~~~~~~
#define CONFIG_CRYPTO_MICHAEL_MIC(_MODULE) 1
#define CONFIG_CRYPTO_AES_586(_MODULE) 1
~~~~~~~~~~~~~~~~~~~~~~~~~~~
If you wish to enable (optional) WPA support, you also need to enable the
following crypto library modules (in addition to those required for WEP above):

        Cryptographic options ->
                Michael MIC keyed digest algorithm
                AES cipher algorithms (i586)


NOW MAKE SURE THAT THE FOLLOWING CAPABILITIES ARE *NOT* ENABLED!!

~~~~~~~~~~~~~~~~~~~~~~~~~~
#define CONFIG_IPW3945 1
~~~~~~~~~~~~~~~~~~~~~~~~~~~
If existing support is built into your kernel, you must disable that 
capability and rebuild your kernel before upgrading the drivers.  
This is *dis*abled via menuconfig (enter n for no):

        Device Drivers ->
           Network device support ->
              Network device support (NETDEVICES [=y]) ->
                 Wireless LAN (non-hamradio) ->
                    Intel PRO/Wireless 3945ABG Network Connection

NOTE:  If the driver is supported as a module (this would show up as
#define CONFIG_IPW3945_MODULE 1), you do not need to rebuild your kernel,
but you will need to remove the binary module and relevant include files
(see UPGRADING FROM PRIOR VERSIONS, below).

8.   SYSFS
-----------------------------------------------

You will also need to have sysfs mounted.  This facility is used to query
and control the operation of the driver (see the README.ipw3945,
found in the ipw3945-1.0.0 source directory).

You can mount sysfs this by adding an entry to /etc/fstab similar to this:

none            /sys            sysfs   defaults                0       0

If the directory /sys does not already exist, you will need to create it:

	% mkdir /sys

You can then mount the sysfs partition via:

	% mount -a



9.  UPGRADING FROM PRIOR VERSIONS
-----------------------------------------------

You may have an old version of the drivers (if your Linux distribution 
includes them,) or if you have installed an earlier ipw3945 driver
yourself.  

Before upgrading to a new driver, you should remove old driver modules 
(so so modprobe won't find them), as well as any related kernel 
configuration declarations (so that they don't affect the new build).  To 
do this most easily, you can use the 'remove-old' script, found in the 
ipw3945-1.0.0 source directory, as in the following example:

	% cd /your/path/to/ipw3945-1.0.0
	% chmod u+rx remove-old
	# ./remove-old   <--- You need to run this as root

Answer y to all of its questions.

Since this script may not work thoroughly and reliably for your particular
distribution, the following is a summary of what you can do manually to check
and/or complete its work.

1)  Remove old ipw3945.ko files from /lib/modules/{VERSION}.  

    Find them via: 

	% find /lib/modules/$(uname -r) -name "ipw3945.*"

    Remove whatever that finds, including directories and .h files (create
    backup files, unless you're feeling adventurous!).

    Failure to remove old modules may result in unresolved symbols
    when you try to load your new drivers.


2)  Comment out or remove any CONFIG_IPW3945 declarations
    in kernel's autoconf.h.  Find with:

	% grep CONFIG_IPW3945 \
            /lib/modules/$(uname -r)/build/include/linux/autoconf.h

    Use c-style comments (i.e. /* */) to comment out each line that it finds.
    Use a pair of /* */ for each line separately, instead of trying to comment
    out a block of several lines with a single pair of /* */.
    

3)  Comment out or remove any CONFIG_IPW3945 declarations
    in kernel's .config.  Find with:

	% grep CONFIG_IPW3945 \
                /lib/modules/$(uname -r)/build/.config

    Use shell-style comments (i.e. #) to comment out the entries it finds.

    Failure to comment out these lines in steps 2) and 3) may affect the 
    build of your new module; settings in the driver's Makefile are 
    overridden by settings in the kernel configuration.



10.  BUILDING EXTERNAL (outside kernel source tree)
-----------------------------------------------

First, you need to install the ieee80211 modules. You can find the modules
package and install instructions at http://ieee80211.sourceforge.net

Then, you need to unpack the ipw3945-1.0.0.tgz archive:

	% tar xzvf ipw3945-1.0.0.tgz
	% cd ipw3945-1.0.0

The driver package contains a Makefile that can be used for building the 
driver outside of the kernel tree.  To build it for the currently running 
kernel, simply type:

	% make  <--- You may need to run this as root

NOTE: If you see any errors during the build process be sure to check the
Issues section on the http://ipw3945.sf.net website as a patch may be 
available for your specific kernel configuration.  

To build it for a different kernel than the running one, use the KSRC
parameter:

	% make KSRC=/path/to/kernel

If you wish to install the modules into your currently running kernel you can
do so via:

	# make install <--- You need to run this as root

If you wish to install the modules into other place, you can do so via:

	# make install KMISC=/path/to/install <--- You need to run as root




11. INSTALLING MICROCODE
-----------------------------------------------

Before you can load the driver, you need the microcode image.  You can find
instructions for obtaining the microcode by going to:

	http://ipw3945.sf.net/binaries.php

Once you have the microcode archive, untar it:

	% tar xzvf ipw3945-ucode-1.13.tgz

This will create a new directory.  In it you should find three files:

	LICENSE.ipw3945-ucode   A copy of the microcode license
	README.ipw3945-ucode    Information about the microcode
        ipw3945.ucode           Binary microcode file

You need to place the ipw3945.ucode file into the hotplug firmware directory,
e.g. /usr/lib/hotplug/firmware/  or  /lib/firmware/.  Check the contents
of the /etc/hotplug/firmware.agent to determine the specific location for 
your distribution.  Most newer systems default to /lib/firmware.

If you do not have /etc/hotplug/firmware.agent, then you need to upgrade your
hotplug scripts to something later than 2003_10_07.  You can obtain the latest
hotplug scripts via the following link (look for hotplug,
not firmwarehotplug): 

	http://sourceforge.net/project/showfiles.php?group_id=17679

Also, make sure that your kernel supports the hotplug firmware loader.  
See the section above, KERNEL REQUIREMENTS -- Configuration, on 
CONFIG_FW_LOADER .

NOTE:  Loading this microcode image will not affect the hardware in any other
operating systems you may boot.  Each OS keeps its own copy of the microcode,
and loads its own copy onto the hardware each time the OS initializes the
card.


12. INSTALLING REGULATORY DAEMON
-----------------------------------------------

In addition to the microcode mentioned above, you also need to install
the regulatory daemon responsible for calibrating and configuring the 
radio.  You can find instructions for obtaining the regulatory daemon by
going to:

	http://ipw3945.sf.net/binaries.php

Once you have the regulatory daemon archive, untar it:

	% tar xzvf ipw3945d-1.7.18.tgz

This will create a new directory.  In it you should find three files and two
directories:

	LICENSE.ipw3945d        A copy of the daemon license
        README.ipw3495d         Information on the regulatory deamon.

Please review the file README.ipw3945d for instructions on installing the
regulatory daemon.


12.  LOADING THE DRIVER
-----------------------------------------------

See the README.ipw3945 for instructions on loading and using the driver.

------------------------------
Copyright (C) 2005 - 2006, Intel Corporation

INFORMATION IN THIS DOCUMENT IS PROVIDED IN CONNECTION WITH INTEL PRODUCTS.  
EXCEPT AS PROVIDED IN INTEL'S TERMS AND CONDITIONS OF SALE FOR SUCH PRODUCTS, 
INTEL ASSUMES NO LIABILITY WHATSOEVER, AND INTEL DISCLAIMS ANY EXPRESS OR 
IMPLIED WARRANTY RELATING TO SALE AND/OR USE OF INTEL PRODUCTS, INCLUDING 
LIABILITY OR WARRANTIES RELATING TO FITNESS FOR A PARTICULAR PURPOSE, 
MERCHANTABILITY, OR INFRINGEMENT OF ANY PATENT, COPYRIGHT, OR OTHER 
INTELLECTUAL PROPERTY RIGHT. 

This document is subject to change without notice. 

* Other names and brands may be claimed as the property of others.


```

---

### Post by z3r0k00l on 2007-02-14
im also having this problem,

first i didnt have the /etc/hotplug/firmware.agent file... i installed hotplug from sourceforge thanks to section 11 of the install file contained in the driver and now the $DIR variable is being assigned to a path that doesnt exist...

anyone know what might solve this problem...?

it seems that getting this Wireless card to work is impossible :(

EDIT: ive found that you can copy the file to /lib/firmware instead, i continued following the instructions right up to where it says to Automate the loading and unloading of the module...

i have to edit a file called modules.conf, but i cant find it on the system, ive also tried looking for the alternative folder that they suggest (modules.d) but i cant find such folder either in the /etc/ folder...

anyone know why doesnt the modules config file doesnt appear?

EDIT2: ive found the alternative folder, its not named modules.d but modprobe.d... 

ive sucessfully installed the ipw3945 driver now, and although the connection is slow, its working fine at 11mbits/sec

---

