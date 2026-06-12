---
title: "Install QEMU 0.8.0 and KQEMU 0.7.2 and KQEMU GUI 0.3"
date: 2006-04-02
forum: General Help
---

### Post by adamkane on 2006-04-02
[SIZE=5]Simple Install Script for QEMU 0.8.0 and KQEMU 0.7.2 and KDE QEMU GUI 0.3[/SIZE]

References:

[http://oui.com.br/n/content.php?article.23]("http://oui.com.br/n/content.php?article.23")
[http://www.ubuntuforums.org/showthread.php?t=39513]("http://www.ubuntuforums.org/showthread.php?t=39513")
[http://kqemu.sourceforge.net/]("http://kqemu.sourceforge.net/")

Before you begin, you need to make sure your system is set up correctly.:

```

uname -r

``` If you have a Pentium PC, the result should be:

> 
2.6.12-10-686
 If you have an AMD PC, the result should be:

> 
2.6.12-10-k7
 If you have an older legacy PC, the result should be:

> 
2.6.12-10-386
 If the result doesn't match your system, then you need to install some system-dependent packages before proceeding:

If you have a Pentium PC:

```

sudo apt-get install linux-686 linux-headers-686 linux-image-686 linux-restricted-modules-686

``` If you have an AMD PC:

```

sudo apt-get install linux-k7 linux-headers-k7 linux-image-k7 linux-restricted-modules-k7

``` If you have an older legacy PC:

```

sudo apt-get install linux-386 linux-headers-386 linux-image-386 linux-restricted-modules-386

``` There is also an option for multi-processor PCs, but I'm not an expert in that area.

Reboot to take advantage of the packages you've just installed, then continue to the next step.

After you've rebooted, do this again, and make sure it matches your system:

```

uname -r

``` 

Create a insQEMU.sh script, then install:

```

cd ~/Desktop
gedit insQEMU.sh

``` 

Enter fhe following code, if you have a Pentium PC:

```

#!/bin/sh
#
# How to write a shell script
# http://vertigo.hsrl.rutgers.edu/ug/shell_help.html
#

# Script configuration
# ====================
  BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
    SRC_DIR=qemu-src
    QEMUVERSION=0.8.0
    KQEMUVERSION=0.7.2
    PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz

# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to nandoflorestan@gmail.com"
echo

if [ $USER != "root" -o $UID != 0 ]; then
    echo "This script must be run as root. Type this to become root:"
    echo "sudo -s"
    echo "...then run this script again."
    echo
    exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Breezy 5.10 and Debian Sid come with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential checkinstall libsdl1.2-dev zlib1g-dev || exit 2

echo


cd   ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd    ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
    echo "Downloading QEMU..."
    wget -nv ${PKGSOURCE}  || exit 5
    echo
    echo "Downloading KQEMU..."
    wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${KQEMUVERSION}.tar.gz || exit 6
    echo
    echo "Uncompressing QEMU..."
    tar zxvf qemu-${QEMUVERSION}.tar.gz     || exit 7
    echo
    echo "Entering source dir."
    cd qemu-${QEMUVERSION}                  || exit 8
    echo
    echo "Uncompressing KQEMU..."
    tar zxvf ../kqemu-${KQEMUVERSION}.tar.gz || exit 9
else
    echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
    echo "I will use its files instead of downloading them from the internet."
    cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure  || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
mv     /usr/bin/gcc.bak /usr/bin/gcc
echo

if [ $EXITCODE != 0 ]; then
    echo "PROBLEM IN MAKE: ${EXITCODE}"
    exit 14
fi

echo "Now let us remove Qemu if it is installed..."
apt-get remove qemu  || exit 15
echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu/install.sh                || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh           || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/2.6.12-10-686/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-686/misc && depmod -a
modprobe kqemu           || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu     || exit 21 # Make it accessible to all users  
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0

``` Save the file, and close it:

If you have an AMD PC, enter the following code ino the insQEMU.sh file:

```

#!/bin/sh
#
# How to write a shell script
# http://vertigo.hsrl.rutgers.edu/ug/shell_help.html
#

# Script configuration
# ====================
  BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
    SRC_DIR=qemu-src
    QEMUVERSION=0.8.0
    KQEMUVERSION=0.7.2
    PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz

# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to nandoflorestan@gmail.com"
echo

if [ $USER != "root" -o $UID != 0 ]; then
    echo "This script must be run as root. Type this to become root:"
    echo "sudo -s"
    echo "...then run this script again."
    echo
    exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Breezy 5.10 and Debian Sid come with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential checkinstall libsdl1.2-dev zlib1g-dev || exit 2

echo

cd   ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd    ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
    echo "Downloading QEMU..."
    wget -nv ${PKGSOURCE}  || exit 5
    echo
    echo "Downloading KQEMU..."
    wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${KQEMUVERSION}.tar.gz || exit 6
    echo
    echo "Uncompressing QEMU..."
    tar zxvf qemu-${QEMUVERSION}.tar.gz     || exit 7
    echo
    echo "Entering source dir."
    cd qemu-${QEMUVERSION}                  || exit 8
    echo
    echo "Uncompressing KQEMU..."
    tar zxvf ../kqemu-${KQEMUVERSION}.tar.gz || exit 9
else
    echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
    echo "I will use its files instead of downloading them from the internet."
    cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure  || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
mv     /usr/bin/gcc.bak /usr/bin/gcc
echo

if [ $EXITCODE != 0 ]; then
    echo "PROBLEM IN MAKE: ${EXITCODE}"
    exit 14
fi

echo "Now let us remove Qemu if it is installed..."
apt-get remove qemu  || exit 15
echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu/install.sh                || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh           || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/2.6.12-10-k7/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-k7/misc && depmod -a
modprobe kqemu           || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu     || exit 21 # Make it accessible to all users  
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0

``` 
Save the file, and close it.

Enter fhe following code, if you have an older legacy PC:

```

#!/bin/sh
#
# How to write a shell script
# http://vertigo.hsrl.rutgers.edu/ug/shell_help.html
#

# Script configuration
# ====================
  BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
    SRC_DIR=qemu-src
    QEMUVERSION=0.8.0
    KQEMUVERSION=0.7.2
    PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz

# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to nandoflorestan@gmail.com"
echo

if [ $USER != "root" -o $UID != 0 ]; then
    echo "This script must be run as root. Type this to become root:"
    echo "sudo -s"
    echo "...then run this script again."
    echo
    exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Breezy 5.10 and Debian Sid come with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential checkinstall libsdl1.2-dev zlib1g-dev || exit 2

echo

cd   ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd    ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
    echo "Downloading QEMU..."
    wget -nv ${PKGSOURCE}  || exit 5
    echo
    echo "Downloading KQEMU..."
    wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${KQEMUVERSION}.tar.gz || exit 6
    echo
    echo "Uncompressing QEMU..."
    tar zxvf qemu-${QEMUVERSION}.tar.gz     || exit 7
    echo
    echo "Entering source dir."
    cd qemu-${QEMUVERSION}                  || exit 8
    echo
    echo "Uncompressing KQEMU..."
    tar zxvf ../kqemu-${KQEMUVERSION}.tar.gz || exit 9
else
    echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
    echo "I will use its files instead of downloading them from the internet."
    cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure  || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
mv     /usr/bin/gcc.bak /usr/bin/gcc
echo

if [ $EXITCODE != 0 ]; then
    echo "PROBLEM IN MAKE: ${EXITCODE}"
    exit 14
fi

echo "Now let us remove Qemu if it is installed..."
apt-get remove qemu  || exit 15
echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu/install.sh                || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh           || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/2.6.12-10-386/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-386/misc && depmod -a
modprobe kqemu           || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu     || exit 21 # Make it accessible to all users  
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0

``` 

Save the file and close it.

Execute the QEMU install script:

```

sudo chmod +x insQEMU.sh
sudo ./insQEMU.sh

``` 
If you make a mistake, and need to re-start the install script, you must remove the temporary files that were created, and begin again:

```

sudo rm -R /root/qemu-src
sudo ./insQEMU.sh

``` 
If the installation succeeds, do the following to have the kqemu module restart after reboot:

```

sudo modprobe kqemu
sudo gedit /etc/modules

``` 
Add this line to the end of the /etc/modules file:

```

kqemu

``` Save the file and close it.

Now use QEMU to create a virtual hard disc for the new OS:

```

cd ~
mkdir qemu
cd qemu
qemu-img create hd1.img 1000M

``` I chose 1000M (1 Gb), but you may need more.

For more options:

```

qemu-img --help

``` 
Install Kommander:

```

sudo apt-get install kommander

``` 

If you use KDE, download KDE Qemu GUI 0.3 to your desktop:
[http://kqemu.sourceforge.net/]("http://kqemu.sourceforge.net/")

Extract the files and execute with Kommander:

```

cd ~/Desktop
tar xzf kqemu-0.3Alpha.tgz
kmdr-executor kqemu.kmdr

``` 
If you use Gnome, I've translated KDE Qemu GUI 0.3 for Gnome. Save the attached file at the end of the post to your desktop, extract it, and execute with Kommander:

```

cd ~/Desktop
gzip -d kqemu-0.3-gnome.gz
kmdr-executor kqemu-0.3-gnome.kmdr

``` 
KDE Qemu GUI: 
 Now that you have the KQEmu GUI open, go to the disks tab, find HDA, and browse to the virtual hard disk image, hd1.img.

Check the enable CDROM button. Insert your CDROM, if you have one. If your installation CD is a CDROM image, then browse to the image. Select d: as your boot drive. 

Go to the Network section. Add a network device, and choose a MAC address between 00:00:00:00:00:00 and FF:FF:FF:FF:FF:FF.

VLAN:0
MAC Address: 01:23:45:67:89:AB
Mode: USER

With the KQEmu GUI, you have the option of creating a startup script for your new OS with the SAVE button.

Press the play button to begin the installation of the new OS.
[URL="http://www.ubuntuforums.org/showthread.php?t=66694"]
[/URL]See here for some pre-configured disk images:
[http://free.oszoo.org/download.html]("http://free.oszoo.org/download.html")

---

### Post by adamkane on 2006-04-03
A note about upgrades.

You may want to keep 
linux-386, linux-headers-386, linux-image-386, linux-restricted-modules-386 
installed along with your new  
linux-686, linux-headers-686, linux-image-686, linux-restricted-modules-686
or
linux-k7, linux-headers-k7, linux-image-k7, linux-restricted-modules-k7
packages.

This way you can always boot with the original 386 packages, if you have problems upgrading your Pentium- or K7-specific packages.

To boot up with your backup 386 kernel, press "ESC" to load GRUB, when Ubuntu first starts to boot up.

---

### Post by drpepper on 2006-04-09
This is a great tutorial! I had problems with CheckInstall and had to get it from synaptic but that wasnt difficult.

Thanks!

---

### Post by adamkane on 2006-04-09
I added checkinstall to the insQEMU.sh script. 

I'm hoping that the author of insQEMU.sh will make some of these minor necessary changes, so that I can retire this thread.

---

### Post by omega13a on 2006-04-23
I'm having problems installing kqemu with this script.  Even it get to the part to start kqemu, I get this error:

> 
Loading the KQEMU kernel module...
cp: cannot stat `kqemu/kqemu.ko': No such file or directory
FATAL: Module kqemu not found.


Can someone help me here?

Edit: I found the problem.  I don't have a /usr/src/linux-headers-2.6.12-10-386 directory.  I have /usr/src/linux-headers-2.6.12-10-686 .  I created a symbolic link to my /usr/src/linux-headers-2.6.12-10-686.  However, now it gives me thise error:
> 
Loading the KQEMU kernel module...
FATAL: Module kqemu not found.


---

### Post by adamkane on 2006-04-23
Did you install the linux-686 linux-headers-686 linux-image-686 linux-restricted-modules-686?

My guess is that you have a mixed installation.

Can you offer any details about which steps you've followed/haven't followed?

---

### Post by omega13a on 2006-04-23
I'm not sure.  I'll try installing those packages and see what happens.

---

### Post by dmizer on 2006-04-26
Okay, i had the same problem as omega13a

in the legacy version of the script there is a typo.

    echo "Uncompressing KQEMU..."
    tar zxvf ../kqemu-[COLOR="Red"]${KEMUVERSION}[/COLOR].tar.gz || exit 9

should be ${KQEMUVERSION}

lol, messed with this script for hours trying to figure that one out ... off i go to try this again.

and before i try again ... in this line:
```
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/2.6.12-10-386/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-386/misc && depmod -a
```

where does the kqemu.ko file come from?  when i unpack kqemu as dowloaded from [http://fabrice.bellard.free.fr](http://fabrice.bellard.free.fr), there is no kqemu.ko file in the package and there's nothing in the script to build the source for kqemu.

---

### Post by adamkane on 2006-04-26
Fixed the typo. Thanks.

Here's my understanding of **kqemu.ko**. It's a poorly documented issue, so forgive my lack of understanding.

It is very easy to install qemu alone, but qemu is slow. To get some speed, you have to compile qemu and kqemu at the same time. You can't install them separately, if you want some speed. The script downloads and extracts the kqemu source into the qemu source directory, and compiles them both together at the same time. kqemu becomes a part of qemu. The 2 become 1.

Just to be clear: qemu/kqemu is slow, but qemu by itself is extremely slow.

The **kqemu.ko** module will **only** be created, if you have the correct headers, etc, installed. If you don't have the correct headers, etc, installed, then there is no way this script is going to work, and you will get the famous **can't stat kqemu.ko error** message.

Some people try to skip the **linux linux-headers linux-image linux-restricted-modules** step, so please be sure you've installed all 4 packages, and have rebooted.

If you really do have an Intel Pentium Pro or 486, then let us know if you have any success. I am only able to test the 686 and k7 install. If you have a modern Intel PC, then you need to use the 686 packages. If you have an AMD PC, then you need to use the k7 packages.

---

### Post by dmizer on 2006-04-26
okay ... in that case perhaps a bit more description is warrented about processor types.  when i did uname -r the result was this: 2.6.12-10-386 so i assumed that i needed the corresponding package.

processor is an intel pentium III 1ghz.  is that not the correct package?

edit to add: was missing the linux headers.  after installing the linux headers, i was sucessfull.

---

### Post by adamkane on 2006-04-26
For Intell Pentium III:

```

sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

```

Reboot.

---

### Post by dmizer on 2006-04-28
okay ... i've gotten a bit farther with this now, but a couple more issues.

first the attached file for the KDE qemu gnome translation extracts without the kmdr extention.  no big deal, i just had to add the extension and it worked.

now, i followed the rest of the directions and it's giving me an error when i push play.  it says "you do not have enough space in /dev/shm for the 128M of QEMU virtual ram"

i do have 256m of ram installed in this machine.

---

### Post by adamkane on 2006-04-28
128MB may be too much for your system, but you can try the following.

Hardware emulation with QEMU:
[http://www.linux.com/article.pl?sid=05/10/24/1845248](http://www.linux.com/article.pl?sid=05/10/24/1845248)

> 
You do not have enough space in '/dev/shm' for the 256 MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
umount /dev/shm
mount -t tmpfs -o size=272m none /dev/shm


You probably need to do this:

```

umount /dev/shm
mount -t tmpfs -o size=156m none /dev/shm

```

Then run kde qemu gui kommander script.

---

### Post by el_Salmon on 2006-04-30
[QUOTE=adamkane]
Before you begin, you need to make sure your system is set up correctly.:

```

uname -r

``` If you have a Pentium PC, the result should be:

 If you have an AMD PC, the result should be:

 If you have an older legacy PC, the result should be:

 If the result doesn't match your system, then you need to install some system-dependent packages before proceeding:

If you have a Pentium PC:

```

sudo apt-get install linux-686 linux-headers-686 linux-image-686 linux-restricted-modules-686

``` If you have an AMD PC:

```

sudo apt-get install linux-k7 linux-headers-k7 linux-image-k7 linux-restricted-modules-k7

``` If you have an older legacy PC:

```

sudo apt-get install linux-386 linux-headers-386 linux-image-386 linux-restricted-modules-386

``` There is also an option for multi-processor PCs, but I'm not an expert in that area.

Reboot to take advantage of the packages you've just installed, then continue to the next step.
[/QUOTE]

It's a great script but I disagree with kernel-sources installation. I think it's better and cleaner the way like in my [HOWTO: Orinoco Monitor Mode]("https://wiki.ubuntu.com/OrinocoMonitorMode")

      Install tools and sources:

```
$ apt-get install linux-source build-essential gcc-3.4 apt-get install linux-headers-<arch> 

```
where <arch> is replaced by your running kernel architechture: 386, 386-smp, 686, 686-smp, k7, k7-smp

      Prepare linux sources (replace 2.6.12 for current version) :
```

$ cd /usr/src 
$ tar -jxvf linux-source-2.6.12.tar.bz2
$ ln -s /usr/src/linux-source-2.6.12 /usr/src/linux

```

---

### Post by adamkane on 2006-05-01
Thanks for the link. I'll install and post any thoughts.

It looks like your are installing linux-source from source so that you may patch the kernel. Kernel patching isn't necessary to install and run qemu/kqemu.

In any case, many advanced users prefer to install the "latest" kernel or kernel-headers from source, or argue that you do not need all the packages that I describe. I argue that my way is simple, consistent and easy, which is best for new users. 

If a user only installs one of the 4 packages I describe, they will end up with a "mixed"  installation. That is to say, some of their packages will be 386, and some will be 686 or k7. This leads to installation issues later, and I try to prevent that without going into details that new users really don't care about. Advanced users will as they wish anyway.

I'm not an expert, so I realize that I won't have the last word on this issue.

---

### Post by el_Salmon on 2006-05-01
[QUOTE=adamkane]
It looks like your are installing linux-source from source so that you may patch the kernel. Kernel patching isn't necessary to install and run qemu/kqemu.
[/QUOTE]
Yes, but patching or not, you need linux source files.
[QUOTE=adamkane]
In any case, many advanced users prefer to install the "latest" kernel or kernel-headers from source, or argue that you do not need all the packages that I describe. I argue that my way is simple, consistent and easy, which is best for new users. 

If a user only installs one of the 4 packages I describe, they will end up with a "mixed"  installation. That is to say, some of their packages will be 386, and some will be 686 or k7. This leads to installation issues later, and I try to prevent that without going into details that new users really don't care about. Advanced users will as they wish anyway.

I'm not an expert, so I realize that I won't have the last word on this issue.[/QUOTE]

My way is simple too. The most important reason is that I DON'T want to install "linux-restricted-modules" in my Ubuntu if I don't need.

---

### Post by dmizer on 2006-05-03
well, i got so far as to begin the install.  i am attempting to run win 2000, so i ran the script with the win2k option checked in kqemu.  the initial part of the setup goes fine, and the system fakes a reboot fine.  but on reboot, the system appears to hang while detecting hardware.

edit to add:
got it to work finally.  i used the following to create my win2000 image.
```
dd of=hd.img bs=1024 seek=2000000 count=0
```

---

### Post by DarkManX4lf on 2006-05-08
has anyone managed to get a usb drive to work in qemu? i am emulating winxp and i just cant get the usb drive to detect...does anyone know how?

---

### Post by DarkManX4lf on 2006-05-08
bump

---

### Post by shof2k on 2006-05-08
The script works a charm on my standard 2.6.12-9 kernel, but I need to tweak it to get kqemu working on my custom suspend2 kernel.

As for gkt GUI's, there is qemu-launcher from [http://emeitner.f2o.org/qemu_launcher](http://emeitner.f2o.org/qemu_launcher) which is very nice.

USB / net support seems to be flaky for me, but then I'm on a usb wireless connection and can't find an easy way to share it.

---

### Post by shof2k on 2006-05-08
The script works a charm on my standard 2.6.12-9 kernel, but I need to tweak it to get kqemu working on my custom suspend2 kernel.

As for gkt GUI's, there is qemu-launcher from [http://emeitner.f2o.org/qemu_launcher](http://emeitner.f2o.org/qemu_launcher) which is very nice.

USB / net support seems to be flaky for me, but then I'm on a usb wireless connection and can't find an easy way to share it.

---

### Post by carlao2005 on 2006-05-08
Hello All,

After  spending the whole day, I could get the triple qemu/kqemu/kqemu_gui to work. And at the same time I am writing this text, it is installing windows 98 Se.

Below are  the problems I had and how I could resolve them, wishing I help anybody.

1) although my computer is a Pentium 4 2.66, the command "uname -r" reported
2.6.12-9-386
Note the "9" (not "10"), and "386" (I am sure a Pentium 4 is not legacy PC!! :)  )

2) I have tried all the steps for the "legacy PC" (trying not to hear my computer shouting that it was not legacy!  :)   ), but I allways had the error that says:

Loading the KQEMU kernel module...
FATAL: Module kqemu not found.

3) Trying to solve this problem, and although the uname was saying "386", I have done the instructions for the "686", using these commands, as the author guided:

sudo apt-get install linux-686 linux-headers-686 linux-image-686 linux-restricted-modules-686

I rebooted, and when I used the uname again, the answer now is:
2.6.12-9-686 (!!!) (note that the "386" changed to "686")

4) With a happier computer :D , I have used the "686" script, but have reached the same error stated above (item 2)

5) Looking at the script (for 686), I have found this part:

echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/2.6.12-10-686/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-686/misc && depmod -a
modprobe kqemu
mknod /dev/kqemu c 250 0
chmod 666 /dev/kqemu

I have type it manually (you have to go to the right directory to do it!), changing
"2.6.12-10-686" for "2.6.12-9-686", and BINGO! everything worked.

6) I have the error of "no memory" too. But I have just made what kqemu-gui said (umount /dev/shm, then mount -t tmpfs -o size=144m none /dev/shm), and everything worked

7) just a final note... everybody says that vmware is the best... but it was my first option (today's morning), in another distribution (a brazilian one, called kurumin 6), but it have halted several times, when I tried to install de win98. I have switched to Ubuntu 5.10, installed qemu as I have said above, and the windows 98 is still running without problems.

Since english is not my mother language, my text above is a little (?) bit fuzzy. But if you want more information, just drop a line.

Kind regards!
Carlos
Ilhéus/Bahia/Brasil

---

### Post by DarkManX4lf on 2006-05-08
so no one got a usb drive to work?

---

### Post by DarkManX4lf on 2006-05-08
ahh bump

---

### Post by DarkManX4lf on 2006-05-08
ok...so far i managed to install winxp with no problems...i installed one of my engineering apps on the emulated winxp and it runs with no problems.....the only problem is that i cant use files from ubuntu to the emulated winxp...if someone can help me out with that, that would be great...or if someone can help me out with getting a usb drive to work in the emulated windows that would be even better....so does anyone know how to do this?

---

### Post by Cadeucean on 2006-05-09
Thanks so much for the tutorial. I have it up and running with Win2k installed. My only problem is that I constantly get pop-up windows with a message that says "This version work only with qemu >= 0.8.0" with an "OK" buttton. 

Any idea how to make these not show up?

Thanks,

Glen

---

### Post by DarkManX4lf on 2006-05-09
[QUOTE=DarkManX4lf]ok...so far i managed to install winxp with no problems...i installed one of my engineering apps on the emulated winxp and it runs with no problems.....the only problem is that i cant use files from ubuntu to the emulated winxp...if someone can help me out with that, that would be great...or if someone can help me out with getting a usb drive to work in the emulated windows that would be even better....so does anyone know how to do this?[/QUOTE]

bump

---

### Post by dmizer on 2006-05-10
for sharing files, just make sure you have samba set up correctly on your ubuntu box so that ubuntu can share files across your network such that other computers can see them.  there are many tutorials on this site for that.

once you have accomplished that, in windows just click start > run and type \\computername(ubuntubox)\foldername <-- usually "homes"

replacing computername and foldername with their respective equivelants on your network.

usb is possible with qemu alone, but i have not yet been able to get it to work inside the kqemu accelerator.

as for the error, i believe the code says something about that being a necessary hack in order to make a specific part of the code work.  just keep clicking on "ok" and ignore it.

---

### Post by 4ebees on 2006-05-16
Hi,

Thanks for the work you've done. It is much appreciated.

I have a P4 3.0GHz 1Gb RAM machine. Approx 15 months old.


My problem is kqemu will not install. I get the following error

**************************************************
 Done. The new package has been installed and saved to
 /root/qemu-src/qemu-0.8.0/qemu_0.8.0-1_i386.deb

 You can remove it from your system anytime using:

      dpkg -r qemu

**********************************************************************

QEMU is now installed.

Loading the KQEMU kernel module...
FATAL: Module kqemu not found.
patrick@ubuntu:~/Desktop$  

******************************

I have an SMP kernel

Linux ubuntu 2.6.12-10-686-smp

with the relevant headers and images installed.

I'm not quite sure where to go from here.

Any assistance, advice or re/directions would be most appreciated.

Many thanks for any assistance offered.

---

### Post by dmizer on 2006-05-16
edit ... nevermind.  wrong answer.

it would seem that the script didn't compile kqemu correctly.  really, if you've gotten that far, the only thing that could cause this is that one of the headers is not installed correctly.

is there a file in /root/qemu-src/qemu-0.8.0/kqemu called kqemu.ko?

---

### Post by adamkane on 2006-05-16
The following loads the kqemu module:
```

sudo modprobe kqemu

``` 

This allows you to use kqemu right away without rebooting.

---

### Post by 4ebees on 2006-05-17
Hi dmizer,

>  is there a file in /root/qemu-src/qemu-0.8.0/kqemu called kqemu.ko?

There is actually... is this good??? <crossing fingers>

---

### Post by 4ebees on 2006-05-17
[QUOTE=4ebees]Hi dmizer,



There is actually... is this good??? <crossing fingers>[/QUOTE]

Addendum:

This is what I get if I look up kernel image and headers in Synaptic

Does this help?

---

### Post by dmizer on 2006-05-17
yes actually, it is good that you have a kqemu.ko ... that at least means that kqemu was compiled correctly with qemu.

[[[[[but i think i see a different problem.  in your previous post, you indicated that you saw the following:
> Done. The new package has been installed and saved to
/root/qemu-src/qemu-0.8.0/qemu_0.8.0-1_i386.deb
which version of the script did you use?  because it appears to me that you used the legacy script rather than the pentium script.  the pentium script should produce a qemu_0.8.0-1_i[COLOR="Red"]6[/COLOR]86.deb

that's probably why you get the error.  try deleting everything and starting over with the pentium script (first of the three listed in the first post).]]]]]
above information is wrong ... see next post.

edit to add information regarding your kernel headers.
if uname -r output shows i686, that is the kernel you are using.  in reality, you can actually delete the i386 headers if you like (i did on mine).  but it's not really hurting anything to have them there.  the important thing is what shows in the output of uname -r.

if you leave the i386 headers in place, you will be able to select them from grub if you go into the grub menu.  i really don't know if this is an advantage or not.

---

### Post by adamkane on 2006-05-17
The qemu deb file is going to have 386 in the filename, even if you are doing everything correctly to install it on your 686 or k7 architecture.

---

### Post by 4ebees on 2006-05-19
[QUOTE=adamkane]The qemu deb file is going to have 386 in the filename, even if you are doing everything correctly to install it on your 686 or k7 architecture.[/QUOTE]

Oh, okay guys. So the suggestion here is??? 

(Sorry if it's obvious, but unfortunately not to me at the moment) :(

I'm not clear what it is that I need to edit - sorry for the "DUH!"  factor.

---

### Post by adamkane on 2006-05-19
SMP is outside my area of understanding. You may have to do some research. I had to do some research myself to get insQEMU to work on my K7 hardware. Here are some observations.

You just need the packages that end in "-686-smp." You will not be using the "-386" or the "-686" packages.

First make sure you are booting with the "-smp" packages. So reboot, and press "ESC" to load GRUB, when Ubuntu first starts to boot up. You will be offered a GRUB menu with several choices. Log in with the 686-smp kernel. Do not login with the 686 kernel or the 386 kernel.

Once you log in with the correct kernel, you can go ahead and  uninstall the unnecessary -386 and -686 packages, if you want. (Keep the -686-smp packages.)

You also want to edit GRUB to automatically select the -686-smp kernel each time you log in:
```

sudo gedit /boot/grub/menu.lst

``` 
The end of the file should look like this, but with -686-smp, instead of -686:
> [FONT=Courier New]
## ## End Default Options ##

title        Ubuntu, kernel 2.6.12-10-686 
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-686
savedefault
boot

title        Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.12-10-686
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST[/FONT]    
 
After you are sure that you have logged in with the -686-smp kernel, then try to install QEMU/KQEMU with a modified insQEMU install script. Look for anything in the script that ends in -686, and change it to -686-smp, then execute the script.

Again, I am not an SMP expert, so you'll be flying solo. I've already spent several weeks getting the insQEMU script to function on K7 architecture. It is up to the SMP community to modify the script for SMP architecture.

---

### Post by 4ebees on 2006-05-20
[QUOTE=adamkane]"SMP is outside my area of understanding...I am not an SMP expert..., so you'll be flying solo."[/QUOTE]

Nah Mate, change your self-perception :)

I made the changes in the script and WORKED FIRST TIME :) :)

Add another qualification to your list.

> "It is up to the SMP community to modify the script for SMP architecture.

?? Didn't know there was one.

That said, please accept my appreciation for your very welcome assistance.
Regards,
Patrick

---

### Post by adamkane on 2006-05-20
I'm pushy and opinionated. This has already been established on other threads. 

I'm not an SMP expert, so I'll be as helpful as I can, but you'll get the credit for making QEMU function on SMP architecture. (I didn't say the SMP community was very large. ;) ) Please share your script once you get it working. I'll add it to the first post, if you want, or you can start your own thread. 

The only reason I created this thread is because the author of the insQEMU script didn't respond to my posts about the script not functioning on K7 architecture. The reason there isn't a single script for all architectures is because, there doesn't seem to be a way to detect a user's architecture correctly. The code "uname -m" doesn't work! It tells me that I have a 686 machine, when I know very well that it is a k7 machine, and the script would fail to create the kqemu.ko module. Hopefully some day there will be a single script that does everything correctly.

It sounds like you've done all the hard parts correctly.

You've run the script. 
The install finished successfully.
The install created the kqemu.ko file.

Now there are 2 ways to load the kqemu module.

1. This method loads kqemu for the current session only.
```

sudo modprobe kqemu

``` 

2. This method loads kqemu at startup.
```

sudo gedit /etc/modules

``` 

The /etc/modules file will open. Add a kqemu line. The /etc/modules file should look similar to this:
> [FONT=Courier New]
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
fuse
kqemu[/FONT]
 

Close the /etc/modules file, and reboot.

After the kqemu module is loaded, then you can execute the kqemu qui kommander script to run qemu, or you can run qemu from the command line.

To run qemu, first you need to create an empty image, or find an OS image online somewhere. Then load the image into qemu using kqemu gui or using the command line.

---

### Post by 4ebees on 2006-05-20
Hi all,

Per my discussions with adamkane, here is the insQEMU.sh script modified for the 2.6.12-10-686-smp kernel.

*********************
#!/bin/sh
#
# How to write a shell script
# [http://vertigo.hsrl.rutgers.edu/ug/shell_help.html](http://vertigo.hsrl.rutgers.edu/ug/shell_help.html)
#

# Script configuration
# ====================
  BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
    SRC_DIR=qemu-src
    QEMUVERSION=0.8.0
    KQEMUVERSION=0.7.2
    PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz

# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to [email]nandoflorestan@gmail.com[/email]"
echo

if [ $USER != "root" -o $UID != 0 ]; then
    echo "This script must be run as root. Type this to become root:"
    echo "sudo -s"
    echo "...then run this script again."
    echo
    exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Breezy 5.10 and Debian Sid come with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential checkinstall libsdl1.2-dev zlib1g-dev || exit 2

echo


cd   ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd    ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
    echo "Downloading QEMU..."
    wget -nv ${PKGSOURCE}  || exit 5
    echo
    echo "Downloading KQEMU..."
    wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${KQEMUVERSION}.tar.gz || exit 6
    echo
    echo "Uncompressing QEMU..."
    tar zxvf qemu-${QEMUVERSION}.tar.gz     || exit 7
    echo
    echo "Entering source dir."
    cd qemu-${QEMUVERSION}                  || exit 8
    echo
    echo "Uncompressing KQEMU..."
    tar zxvf ../kqemu-${KQEMUVERSION}.tar.gz || exit 9
else
    echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
    echo "I will use its files instead of downloading them from the internet."
    cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure  || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
mv     /usr/bin/gcc.bak /usr/bin/gcc
echo

if [ $EXITCODE != 0 ]; then
    echo "PROBLEM IN MAKE: ${EXITCODE}"
    exit 14
fi

echo "Now let us remove Qemu if it is installed..."
apt-get remove qemu  || exit 15
echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu/install.sh                || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh           || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/2.6.12-10-686-smp/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-686-smp/misc && depmod -a
modprobe kqemu           || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu     || exit 21 # Make it accessible to all users  
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0

*********************

The modification was made to this line:

mkdir -p /lib/modules/2.6.12-10-686-smp/misc && cp kqemu/kqemu.ko /lib/modules/2.6.12-10-686-smp/misc && depmod -a

All that was required was to add: 

-smp

at the end of the section that read: 

2.6.12-10-686

Regards,

Patrick

---

### Post by bodhi.zazen on 2006-05-22
Very nice, I just got it all istalled. I did not use your script, but your how to was invaluable regarding the linux source code (headers).

Your script does not install kqemu, just qemu (at least to my read).

Also your script will need to change depending on the kernel that is installed, perhpas you shoud add a variable and read the kernel. 

To 4ebees:

go to your kqemu folder.
just type:
  ./configure
  make
  make install

Note: Check install did not work for me at this step, it failed with an error code. make install worked fine.

Note: to check if kqemu is working:

1. start an emulation
2. type the sseuence of <control> <Alt> and <2> [yes, the number 2]

This brings up the qemu "shell"
type -> info kqemu
should see it is either installed, or not

3. Type  <control> <Alt> and <1> to return to the emulation.


THANK YOU !!!!!!!!!

---

### Post by 4ebees on 2006-05-22
Hey bodhi.zazen,

Thanks for the info.

Regards.

---

### Post by adamkane on 2006-05-22
The script isn't mine. I only made it work on non-Intel architecture. The script saves the kqemu source inside the qemu source folder, and compiles them together. It's easy to miss.

I don't know a way to accurately detect a user's architecture. Like I said earlier, "uname -m" doesn't work, and that's supposed to be how to differentiate 686 from k7, etc.

Since "uname -m" doesn't work for all architectures, I just have the user install the correct headers manually, then proceed to install qemu/kqemu.

The original author of the insQEMU script tried to make an all-in-one script, and failed, because he relied on "uname -m". He didn't reply to my posts, so that's why I created this thread.

---

### Post by bodhi.zazen on 2006-05-23
thank you adamkane

here is a interesting web site Re: QEMU advice:

[http://www.slackware.com/~alien/dokuwiki/doku.php?id=slackware:qemu](http://www.slackware.com/~alien/dokuwiki/doku.php?id=slackware:qemu)

Enjoy !!

---

### Post by adamkane on 2006-05-23
Thanks for the post. I'm hoping that Xen will be an improvement over qemu, but I don't think Xen is available yet.

---

### Post by Olivier olejniczak on 2006-06-26
The install script (insQemu.sh) that did it for me (dapper on kernel 2.6.15-25-k7)

=====================================


#!/bin/sh
#
# How to write a shell script
# [http://vertigo.hsrl.rutgers.edu/ug/shell_help.html](http://vertigo.hsrl.rutgers.edu/ug/shell_help.html)
#

# Script configuration
# ====================
  BASE_DIR=/root
# BASE_DIR=/usr/local
# BASE_DIR=/tmp
	SRC_DIR=qemu-src
	QEMUVERSION=0.8.1
	KQEMUVERSION=1.3.0pre7
	PKGSOURCE=http://fabrice.bellard.free.fr/qemu/qemu-${QEMUVERSION}.tar.gz

echo "Now let us remove Qemu if it is installed..."
apt-get -y remove qemu  || exit 15



# Script starts executing here
# ============================
echo
echo "InsQEMU - version 0.1 (2005-12-15)"
echo "======= by Nando Florestan -- http://oui.com.br/n"
echo "This script downloads and installs QEMU ${QEMUVERSION},"
echo "with the KQEMU accellerator, verions ${KQEMUVERSION} in Ubuntu 6.04 Dapper Drake."
echo "Based on:"
echo "http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation"
echo
echo "If this script succeeds, you will see a message at the end saying:"
echo "\"InsQEMU SUCCEEDED!\""
echo "...else you have some problem."
echo
echo "If you have any difficulties, you can edit the script yourself."
echo "It is heavily commented so as to help."
echo "Please send any bug corrections to [email]nandoflorestan@gmail.com[/email]"
echo

if [ $USER != "root" -o $UID != 0 ]; then
	echo "This script must be run as root. Type this to become root:"
	echo "sudo -s"
	echo "...then run this script again."
	echo
	exit 1
fi

echo "First of all, we install the dependencies."
# Ubuntu Dapper comes with GCC 4.0 by default, but
# Qemu 0.72 will not compile with GCC 4.0 so we need to install GCC 3.4
# The SDL packages should provide sound support
# zlib is a compression library
# checkinstall is for generating .deb packages
apt-get install gcc-4.0 g++-4.0 gcc-3.4 g++-3.4 libsdl1.2debian libsdl1.2debian-all build-essential libsdl1.2-dev zlib1g-dev checkinstall || exit 2

echo
echo "Finding out whether your kernel is i386 or i686 or k7."
# Run "uname -m" and store the result in the variable KERNEL
KERNEL=`uname -m` || exit 10
KERNELK7=`uname -r | grep "k7$"`

# Depending on KERNEL, get a package
if [ $KERNELK7 ]; then
	echo "Downloading Linux headers for k7..."
	apt-get install linux-headers-k7  || exit 11
elif [ $KERNEL == "i686" ]; then
	echo "Downloading Linux headers for i686..."
	apt-get install linux-headers-686  || exit 11
elif [ $KERNEL == "i386" ]; then
	echo "Downloading Linux headers for i386..."
	apt-get install linux-headers-386  || exit 12
fi
echo

cd   ${BASE_DIR} || exit 3
mkdir ${SRC_DIR} || echo
cd    ${SRC_DIR} || exit 4
echo

# If the directory does NOT exist yet
if [ ! -d qemu-${QEMUVERSION}/kqemu ]; then
	echo "Downloading QEMU..."
	wget -nv ${PKGSOURCE}  || exit 5
	echo
	echo "Downloading KQEMU..."
	wget -nv http://fabrice.bellard.free.fr/qemu/kqemu-${KQEMUVERSION}.tar.gz || exit 6
	echo
	echo "Uncompressing QEMU..."
	tar zxvf qemu-${QEMUVERSION}.tar.gz     || exit 7
	echo
	echo "Entering source dir."
	cd qemu-${QEMUVERSION}                  || exit 8
	echo
	echo "Uncompressing KQEMU..."
	tar zxvf ../kqemu-${KQEMUVERSION}.tar.gz || exit 9
else
	echo "Directory already exists: ${BASE_DIR}/qemu-src/qemu-${QEMUVERSION}"
	echo "I will use its files instead of downloading them from the internet."
	cd qemu-${QEMUVERSION}
fi

echo "BEGINNING CONFIGURE !"
# sh configure  || exit 13
export CPP=g++-3.4
export CC=gcc-3.4
sh ./configure --prefix=/usr --cc=gcc-3.4 --host-cc=gcc-3.4 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo

echo "BUILDING QEMU !"
# In Ubuntu Breezy, if you just `make`, it will use GCC 4.0
# even though we configured for GCC 3.4. So we need this workaround:
# Change the symlink, compile, then change the symlink back
mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
make
EXITCODE=$?
echo

if [ $EXITCODE != 0 ]; then
	echo "PROBLEM IN QEMU MAKE: ${EXITCODE}"
	exit 14
fi

mv     /usr/bin/gcc.bak /usr/bin/gcc


export CPP=g++-4.0
export CC=gcc-4.0
cd	kqemu-${KQEMUVERSION}
sh ./configure --prefix=/usr --cc=gcc-4.0 --host-cc=gcc-4.0 --kernel-path=/usr/src/linux-headers-$(uname -r)/ || exit 13
echo
echo
echo "BUILDING KQEMU !"

mv     /usr/bin/gcc     /usr/bin/gcc.bak
ln -sf /usr/bin/gcc-4.0 /usr/bin/gcc
make
cd ..
EXITCODE=$?
echo

if [ $EXITCODE != 0 ]; then
	echo "PROBLEM IN KQEMU MAKE: ${EXITCODE}"
	exit 14
fi


echo

# Now make the PACKAGE. Using checkinstall is a great way to
# install applications because it makes '.deb' packages.
# This means Qemu can later be removed via apt-get or Synaptic.
echo "QEMU is a generic processor emulator. This package was compiled by InstQEMU.sh and also contains the KQEMU accellerator. http://fabrice.bellard.free.fr/qemu" > description-pak || exit 16
# The reason for overwriting install.sh so it is empty is
# to ensure the package made with checkinstall can install cleanly
cat /dev/null > kqemu-${KQEMUVERSION}/install.sh                || exit 17
# Create the .deb package
checkinstall -y --pkgname=qemu --pkgversion=${QEMUVERSION} --pkgrelease=1 --pkglicense=Restricted --pkggroup="Miscellaneous - Text Based" --pkgsource=$PKGSOURCE --exclude=kqemu/install.sh           || exit 18

echo "QEMU is now installed."
echo
echo "Loading the KQEMU kernel module..."
mkdir -p /lib/modules/$(uname -r)/misc && cp kqemu-${KQEMUVERSION}/kqemu.ko /lib/modules/$(uname -r)/misc && depmod -a
modprobe kqemu           || exit 19 # Load the kernel module
mknod /dev/kqemu c 250 0 || exit 20 # Create the KQEMU device
chmod 666 /dev/kqemu     || exit 21 # Make it accessible to all users    
echo

echo "When you reboot, the KQEMU accellerator will not load anymore."
echo "But you can add a few lines to a boot script to fix this."
echo "For more details, please refer to:"
echo "http://fabrice.bellard.free.fr/qemu/kqemu-doc.html"
echo
echo "InsQEMU SUCCEEDED!"
exit 0

=====================================

the run scrip i use to install win98 (win98.sh)

=====================================
sudo umount /dev/shm
sudo mount -t tmpfs -o size=144m none /dev/shm
sudo modprobe kqemu
sudo mknod /dev/kqemu c 250 0
sudo chmod 666 /dev/kqemu
sudo qemu -boot d -hda win98.img -cdrom WINDOWS_98.iso

=====================================

---

### Post by adamkane on 2006-07-24
I created this thread for breezy. I haven't updated it for dapper yet.

---

### Post by orangedangila on 2007-01-04
i tried to install that one.. and i got this following errors..

BUILDING QEMU !
gcc-3.4 -Wall -O2 -g -fno-strict-aliasing  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o dyngen dyngen.c
gcc-3.4 -DQEMU_TOOL -Wall -O2 -g -fno-strict-aliasing  -g -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -o qemu-img qemu-img.c block.c block-cow.c block-qcow.c aes.c block-vmdk.c block-cloop.c block-dmg.c block-bochs.c block-vpc.c block-vvfat.c -lz 
for d in i386-user arm-user armeb-user sparc-user ppc-user mips-user mipsel-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu arm-softmmu; do \
        make -C $d all || exit 1 ; \
        done
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/i386-user'
gcc-3.4 -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/root/qemu-src/qemu-0.8.0/target-i386 -I/root/qemu-src/qemu-0.8.0 -I/root/qemu-src/qemu-0.8.0/linux-user -I/root/qemu-src/qemu-0.8.0/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/root/qemu-src/qemu-0.8.0/fpu -DHAS_AUDIO -I/root/qemu-src/qemu-0.8.0/slirp -c -o elfload.o /root/qemu-src/qemu-0.8.0/linux-user/elfload.c
gcc-3.4 -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/root/qemu-src/qemu-0.8.0/target-i386 -I/root/qemu-src/qemu-0.8.0 -I/root/qemu-src/qemu-0.8.0/linux-user -I/root/qemu-src/qemu-0.8.0/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/root/qemu-src/qemu-0.8.0/fpu -DHAS_AUDIO -I/root/qemu-src/qemu-0.8.0/slirp -c -o main.o /root/qemu-src/qemu-0.8.0/linux-user/main.c
gcc-3.4 -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/root/qemu-src/qemu-0.8.0/target-i386 -I/root/qemu-src/qemu-0.8.0 -I/root/qemu-src/qemu-0.8.0/linux-user -I/root/qemu-src/qemu-0.8.0/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/root/qemu-src/qemu-0.8.0/fpu -DHAS_AUDIO -I/root/qemu-src/qemu-0.8.0/slirp -c -o syscall.o /root/qemu-src/qemu-0.8.0/linux-user/syscall.c
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:215: error: syntax error before "gettid"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:221: error: syntax error before "sys_uname"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:222: error: syntax error before "sys_getcwd1"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:223: error: syntax error before "sys_getdents"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:223: warning: type defaults to `int' in declaration of `_syscall3'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:223: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:224: error: syntax error before "sys_getdents64"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:224: warning: type defaults to `int' in declaration of `_syscall3'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:224: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:225: error: syntax error before "_llseek"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:226: warning: type defaults to `int' in declaration of `_syscall5'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:226: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:227: error: syntax error before "sys_rt_sigqueueinfo"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:229: error: syntax error before "exit_group"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:232: warning: return type defaults to `int'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c: In function `_syscall1':
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:232: error: storage class specified for parameter `personality'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:233: error: storage class specified for parameter `flock'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:234: error: storage class specified for parameter `setfsuid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:235: error: storage class specified for parameter `setfsgid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:236: error: storage class specified for parameter `setresuid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:237: error: storage class specified for parameter `getresuid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:238: error: storage class specified for parameter `setresgid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:239: error: storage class specified for parameter `getresgid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:240: error: storage class specified for parameter `setgroups'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:243: error: storage class specified for parameter `get_errno'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:243: error: syntax error before '{' token
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:256: error: storage class specified for parameter `target_original_brk'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:259: error: syntax error before '{' token
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:270: error: syntax error before "if"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:404: error: syntax error before "rfds_ptr"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: error: parameter `target_cmsg' is initialized
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: error: `target_msgh' undeclared (first use in this function)
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: error: (Each undeclared identifier is reported only once
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: error: for each function it appears in.)
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: confused by earlier errors, bailing out
make[1]: *** [syscall.o] Error 1
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/i386-user'
make: *** [all] Error 1

PROBLEM IN MAKE: 2
wahandoy@wahandoy-desktop:~/Desktop$ sudo modprobe kqemu
FATAL: Module kqemu not found.
wahandoy@wahandoy-desktop:~/Desktop$ sudo ./insQEMU.sh 

InsQEMU - version 0.1 (2005-12-15)
======= by Nando Florestan -- [http://oui.com.br/n](http://oui.com.br/n)
This script downloads and installs QEMU 0.8.0,
with the KQEMU accellerator, in Ubuntu 5.10 Breezy Badger.
Based on:
[http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation](http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation)

If this script succeeds, you will see a message at the end saying:
"InsQEMU SUCCEEDED!"
...else you have some problem.

If you have any difficulties, you can edit the script yourself.
It is heavily commented so as to help.
Please send any bug corrections to [email]nandoflorestan@gmail.com[/email]

[: 42: 0: unexpected operator
First of all, we install the dependencies.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc-3.4 is already the newest version.
g++-3.4 is already the newest version.
libsdl1.2debian is already the newest version.
libsdl1.2debian-all is already the newest version.
build-essential is already the newest version.
checkinstall is already the newest version.
libsdl1.2-dev is already the newest version.
zlib1g-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libvte2.0-cil libglitz1 libfile-mmagic-perl python-wxversion libconfig-inifiles-perl python-wxgtk2.6
  linux-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

mkdir: cannot create directory `qemu-src': File exists


Directory already exists: /root/qemu-src/qemu-0.8.0
I will use its files instead of downloading them from the internet.
BEGINNING CONFIGURE !
Install prefix    /usr
BIOS directory    /usr/share/qemu
binary directory  /usr/bin
Manual directory  /usr/share/man
ELF interp prefix /usr/gnemul/qemu-%M
Source path       /root/qemu-src/qemu-0.8.0
C compiler        gcc-3.4
Host C compiler   gcc-3.4
make              make
host CPU          i386
host big endian   no
target list       i386-user arm-user armeb-user sparc-user ppc-user mips-user mipsel-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu arm-softmmu
gprof enabled     no
static build      no
SDL support       yes
SDL static link   yes
mingw32 support   no
Adlib support     no
CoreAudio support no
ALSA support      no
DSound support    no
FMOD support      no
kqemu support     yes

KQEMU Linux module configuration:
kernel sources    /usr/src/linux-headers-2.6.17-10-386/
kbuild type       2.6


BUILDING QEMU !
for d in i386-user arm-user armeb-user sparc-user ppc-user mips-user mipsel-user i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu mips-softmmu arm-softmmu; do \
        make -C $d all || exit 1 ; \
        done
make[1]: Entering directory `/root/qemu-src/qemu-0.8.0/i386-user'
gcc-3.4 -Wall -O2 -g -fno-strict-aliasing -fomit-frame-pointer -I. -I/root/qemu-src/qemu-0.8.0/target-i386 -I/root/qemu-src/qemu-0.8.0 -I/root/qemu-src/qemu-0.8.0/linux-user -I/root/qemu-src/qemu-0.8.0/linux-user/i386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -I/root/qemu-src/qemu-0.8.0/fpu -DHAS_AUDIO -I/root/qemu-src/qemu-0.8.0/slirp -c -o syscall.o /root/qemu-src/qemu-0.8.0/linux-user/syscall.c
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:215: error: syntax error before "gettid"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:221: error: syntax error before "sys_uname"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:222: error: syntax error before "sys_getcwd1"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:223: error: syntax error before "sys_getdents"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:223: warning: type defaults to `int' in declaration of `_syscall3'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:223: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:224: error: syntax error before "sys_getdents64"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:224: warning: type defaults to `int' in declaration of `_syscall3'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:224: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:225: error: syntax error before "_llseek"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:226: warning: type defaults to `int' in declaration of `_syscall5'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:226: warning: data definition has no type or storage class
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:227: error: syntax error before "sys_rt_sigqueueinfo"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:229: error: syntax error before "exit_group"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:232: warning: return type defaults to `int'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c: In function `_syscall1':
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:232: error: storage class specified for parameter `personality'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:233: error: storage class specified for parameter `flock'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:234: error: storage class specified for parameter `setfsuid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:235: error: storage class specified for parameter `setfsgid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:236: error: storage class specified for parameter `setresuid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:237: error: storage class specified for parameter `getresuid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:238: error: storage class specified for parameter `setresgid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:239: error: storage class specified for parameter `getresgid'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:240: error: storage class specified for parameter `setgroups'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:243: error: storage class specified for parameter `get_errno'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:243: error: syntax error before '{' token
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:256: error: storage class specified for parameter `target_original_brk'
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:259: error: syntax error before '{' token
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:270: error: syntax error before "if"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:404: error: syntax error before "rfds_ptr"
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: error: parameter `target_cmsg' is initialized
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: error: `target_msgh' undeclared (first use in this function)
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: error: (Each undeclared identifier is reported only once
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: error: for each function it appears in.)
/root/qemu-src/qemu-0.8.0/linux-user/syscall.c:447: confused by earlier errors, bailing out
make[1]: *** [syscall.o] Error 1
make[1]: Leaving directory `/root/qemu-src/qemu-0.8.0/i386-user'
make: *** [all] Error 1

PROBLEM IN MAKE: 2

any ideas???

---

### Post by adamkane on 2007-01-04
This howto was written for breezy. You may need to look for a howto known to work with dapper/edgy.

I've been working on other things lately.

---

