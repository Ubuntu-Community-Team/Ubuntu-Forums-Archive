---
title: "HostAP drivers"
date: 2004-10-22
forum: General Help
---

### Post by phin on 2004-10-22
Im at a lost on how to install these.  Could anyone post up some instructions?

I would like to use these with my Linksys WAP11 v3.

Thanks in advance.

---

### Post by phin on 2004-10-23
bump.

any help, please :)

---

### Post by cseg on 2004-10-23
I have a dlink-dwl-520 which uses the hostap drivers.  Here are the two scripts which I run (as root) to get the host-ap kernel patches and module installed.  This first patches the kernel, then reboots.  The second configures the hostap_pci driver proper.

Hope this helps.

```
#!/bin/sh
#
# This script applies the dlink-dwl520 patches
# to the 2.6.8.1 ubuntu/debian kernel,
# grub-installs the new kernel and
# reboots.
#
# The 03-kernel-dlink-dwl520-config.sh
# scripts should be run after this to configure the card.
#
# It is based on documentation found at these web sites:
#    http://home.columbus.rr.com/andrewbarr/linux/dwl520e1.html
#    http://www.linuxquestions.org/questions/archive/41/2004/08/1/211186
#    http://www.sentinel.dk/cookbook/?Linux_wireless_access_point
#    http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/HOTPLUG.txt
#

thisversion=dlink-dwl520

hostap_driver_version=0.2.5
hostap_utils_version=0.2.4
hostap_kernel_patch_version=2.6.2 # this works with 2.6.8.1

oldversion=`uname -r`
newversion=$oldversion-$thisversion
extraversion=`echo $newversion | sed 's@[0-9]*[.][0-9]*[.][0-9]*@@'`
timestamp=`date +%F_%H_%M_%S`

cd /usr/src || { echo Cannot change to /usr/src; exit 1; }

# this is needed for the next script
echo "
hostap_driver_version=$hostap_driver_version
hostap_utils_version=$hostap_utils_version
hostap_kernel_patch_version=$hostap_kernel_patch_version
oldversion=$oldversion
newversion=$newversion
extraversion=$extraversion
timestamp=`date +%F_%H_%M_%S`
" > env-$thisversion.txt

# update the system
apt-get update
apt-get upgrade

# You will need to have the kernel sources in /usr/src/linux
# to the kernel you are running,
apt-get -y install linux-source-2.6.8.1 gcc
# what to do about the prompt for cdrom?

[ ! -d linux-source-2.6.8.1 ] && tar jxf linux-source-2.6.8.1.tar.bz2
ln -sf linux-source-2.6.8.1 linux

# source code for the Host AP driver, i.e., driver/modules/hostap*.[ch], needs
# to be copied to Linux kernel's directory drivers/net/wireless
[ ! -f hostap-driver-$hostap_driver_version.tar.gz ] &&
   wget "http://hostap.epitest.fi/releases/hostap-driver-$hostap_driver_version.tar.gz"
[ ! -d hostap-driver-$hostap_driver_version ] && tar zxf hostap-driver-$hostap_driver_version.tar.gz
cp hostap-driver-$hostap_driver_version/driver/modules/hostap*.[ch] linux/drivers/net/wireless/

# building the kernel
cd /usr/src/linux || { echo Cannot change to /usr/src/linux; exit 1; }
apt-get -y install gcc
apt-get -y install libncurses5-dev

# patch the kernel
patch -N -p1 < ../hostap-driver-$hostap_driver_version/kernel-patches/hostap-linux-$hostap_kernel_patch_version.patch

# name the kernel
[ ! -f Makefile-pre-$thisversion ] && cp Makefile Makefile-pre-$thisversion
sed < Makefile-pre-$thisversion > Makefile \
      -e 's@^EXTRAVERSION = [-.0-9a-z]*$@EXTRAVERSION = '"$extraversion"'@'

# backup an existing .config file before mrproper
[ -f .config ] && cp .config ../config-$timestamp

# start with clean build environment
make mrproper

# set up .config file
if [ -f ../config-$timestamp ]; then
   cp ../config-$timestamp .config
else
   cp /boot/config-$oldversion .config
fi

make oldconfig < /dev/null > oldconfig.1.out

#
# Kernel configuration options for Host AP are in
# Network device support / Wireless LAN (non-hamradio).
# You will need to select both the common code "Host AP support .."
# and the hardware model specific drivers "Host AP driver ..".
# This patches a stock Xandros OCE201 kernel:
#

[ ! -f .config-$thisversion-not-set ] &&
        cp .config .config-$thisversion-not-set
sed < .config-$thisversion-not-set > .config \
   -e 's@.*CONFIG_HOSTAP[= ].*@CONFIG_HOSTAP=m@' \
   -e 's@.*CONFIG_HOSTAP_FIRMWARE[= ].*@CONFIG_HOSTAP_FIRMWARE=y@' \
   -e 's@.*CONFIG_HOSTAP_PCI[= ].*@CONFIG_HOSTAP_PCI=m@' \
# this line is necessary: do not remove

make oldconfig < /dev/null > oldconfig.2.out

time make bzImage modules modules_install install # (~2.7 hours on 1Gig C3)

##
## we still need to:
## 1) save .config file
## 2) configure initrd
## 3) fix up /vmlinuz and /initrd links
## 4) update grub menu
## 5) reboot
##

# 1) save .config file
cp .config /boot/config-$newversion

# 2) configure initrd
(cd /lib/modules/$oldversion/initrd
modules=`find|grep -v '^[.]$'|sed 's@^[.]/@@'`
mkdir -p /lib/modules/$newversion/initrd
cd /lib/modules/$newversion/initrd
for module in $modules
do
   location=`find .. -name $module`
   [ "$location" ] || continue
   cp "$location" .
done
)
mkinitrd -o /boot/initrd.img-$newversion $newversion

## 3) fix up /vmlinuz and /initrd links
mv /vmlinuz /vmlinuz.$timestamp
ln -s /boot/vmlinuz-$newversion /vmlinuz
mv /initrd.img /initrd.img.$timestamp
ln -s /boot/initrd.img-$newversion /initrd.img

# 4) grub update menu
[ ! -f /boot/grub/menu.lst-pre-$thisversion ] &&
   cp /boot/grub/menu.lst /boot/grub/menu.lst-pre-$thisversion
awk </boot/grub/menu.lst-pre-$thisversion '
BEGIN{cacheFirstStanza=0}
/^title/{
   if (cacheFirstStanza==0) {
      cacheFirstStanza = 1 # start caching 1st stanza
      stanzaLineNum=0
      stanza[stanzaLineNum++]=$0
      sub(/'"$oldversion"'/,"'"$newversion"'")
      print
      next
   }
}
/^(root|savedefault|boot|kernel|initrd)/{
   if (cacheFirstStanza==1) {
      stanza[stanzaLineNum++]=$0
      sub(/'"$oldversion"'/,"'"$newversion"'")
      print
      next
   }
}
/^$/{
   if (cacheFirstStanza==1) {
      print
      for (i=0; i<stanzaLineNum; ++i) {
         print stanza[i]
      }
      cacheFirstStanza = 2 # stop caching 1st stanza
   }
}
{
   if (cacheFirstStanza!=1) print
}
' >/boot/grub/menu.lst
grub-install /dev/hda

# 5) reboot here to get the new kernel up so that modprobe will work
reboot

```
```
#!/bin/sh
#
# This script configures the dlink-dwl-520
# having run the 02-kernel-dlink-dwl520-patch.sh script
# to patch the kernel, install the modules, and reboot.
#
# It is based on documentation found at these web sites:
#    http://home.columbus.rr.com/andrewbarr/linux/dwl520e1.html
#    http://www.linuxquestions.org/questions/archive/41/2004/08/1/211186
#    http://www.sentinel.dk/cookbook/?Linux_wireless_access_point
#    http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/HOTPLUG.txt
#

# make sure we are not running on a drive using eth0 :)
[ `dirname $0` != /tmp ] && {
   cp $0 /tmp
   cd /tmp
   exec /tmp/`basename $0` $*
}
thisversion=dlink-dwl520

cd /usr/src || { echo Cannot change to /usr/src; exit 1; }

. env-$thisversion.txt

# Building kernel modules
(cd hostap-driver-$hostap_driver_version; make; make install)

# Building User-Space Programs
[ ! -f hostap-utils-$hostap_utils_version.tar.gz ] &&
   wget http://hostap.epitest.fi/releases/hostap-utils-$hostap_utils_version.tar.gz
[ ! -d hostap-utils-$hostap_utils_version ] &&
   tar zxf hostap-utils-$hostap_utils_version.tar.gz
(cd /usr/src/hostap-utils-$hostap_utils_version; make)
cp /usr/src/hostap-utils-$hostap_utils_version/prism2_srec /usr/local/bin

# firmware repository
firmwareDir=/usr/local/firmware
mkdir -p $firmwareDir

# primary firmware
[ ! -f primary.tar.gz ] &&
   wget http://www.red-bean.com/~proski/firmware/primary.tar.gz
primaryFirmware=`tar ztf primary.tar.gz | grep /pm | tail -1`
primaryFirmwareFile=`expr $primaryFirmware : '.*/\(.*\)'`
[ ! -d primary ] &&
   tar zxf primary.tar.gz $primaryFirmware
mv $primaryFirmware $firmwareDir/
rm -rf primary

# the latest version of the station firmware
station_firmware_version=1.8.3
station_hex_version=`echo 0$station_firmware_version | sed 's@[.]@0@g'`
[ ! -f $station_firmware_version.tar.gz ] &&
   wget http://www.red-bean.com/~proski/firmware/$station_firmware_version.tar.gz
[ ! -d $station_firmware_version ] &&
   tar zxf $station_firmware_version.tar.gz $station_firmware_version/rf$station_hex_version.hex
mv $station_firmware_version/rf$station_hex_version.hex $firmwareDir/
rm -rf $station_firmware_version

# edit the hostap_fw_load script to point to
# the proper locations of the firmware and prism2_srec by
# changing the three variables at the top:
sed < /usr/src/hostap-utils-$hostap_utils_version/hostap_fw_load > /usr/local/sbin/hostap_fw_load  \
   -e 's@PRI=.*@PRI='"$firmwareDir"'/'"$primaryFirmwareFile"'@' \
   -e 's@STA=.*@STA='"$firmwareDir"'/rf'"$station_hex_version"'.hex@' \
   -e 's@PRISM2_SREC=.*@PRISM2_SREC=/usr/local/bin/prism2_srec@'
chmod --reference=/usr/src/hostap-utils-$hostap_utils_version/hostap_fw_load \
      /usr/local/sbin/hostap_fw_load

# the modprobe should load the HostAP driver and create a wlan0: interface
modprobe hostap_pci

# this loads the firmware into the card for wlan0
# the last line should say:
# "The card is now ready with PRI and STA firmware images."
/usr/local/sbin/hostap_fw_load wlan0 |
   grep 'Card is ready with both PRI and STA firmware images' || {
      echo "======================================"
      echo "03-kernel-dlink-dwl520-config.sh:"
      echo "/usr/local/sbin/hostap_fw_load FAILED:"
      echo "Could not load firmware into card."
      echo "======================================"
      exit 1
   }

##
## Now fix up the kernel configuration files
## so that hostap_pci get loaded at boot time.
##

# /etc/modules forces hostap_pci to be loaded
grep -q "hostap_pci" /etc/modules ||
   echo "hostap_pci" >> /etc/modules
/etc/init.d/modutils

# pick up the local gateway (assuming eth0 and wlan0 share a gateway)
gateway=`route | grep "^default .* eth0" | awk '{print $2}'`

# /etc/network/interfaces should config wlan0
[ ! -f /etc/network/interfaces-pre-$thisversion ] &&
   cp /etc/network/interfaces /etc/network/interfaces-pre-$thisversion
sed < /etc/network/interfaces-pre-$thisversion > /etc/network/interfaces \
   -e 's@^auto eth0@#auto eth0@'
grep -q wlan0 /etc/network/interfaces ||
echo >> /etc/network/interfaces "
auto wlan0

iface wlan0 inet dhcp
        pre-up /usr/local/sbin/hostap_fw_load wlan0
        wireless_nick    DWL-520
        wireless_essid   Wireless
        wireless_channel 1
        wireless_mode    Managed
        wireless_ap      any
        wireless_rate    auto
"
/etc/init.d/networking restart

# now, to make sure wlan0 is working, and not eth0,
# turn off eth0
ifdown eth0
# you can also remove the route if you want with:
# route del -net 192.168.22.0/24 dev eth0
# but it should already be deleted

# make sure wlan0 has a default route
route | grep -q '^default.*wlan0$' ||
   route add -net default gw $gateway metric 0 dev wlan0

# Set up additional DNS servers
[ ! -f /etc/resolv.conf.pre-$thisversion ] &&
   mv /etc/resolv.conf /etc/resolv.conf.pre-$thisversion
cat <<EOF > /etc/resolv.conf
search nv.cox.net
nameserver 68.10.16.25
nameserver 68.10.16.30
nameserver 68.100.16.30
nameserver 192.168.22.1
EOF

# see if we're on the net
ping -c 3 x.org || {
echo ==================================
echo I was not able to ping x.org.
echo Something is not quite right.
echo ----------ifconfig wlan0----------
ifconfig wlan0
echo ----------iwconfig wlan0----------
iwconfig wlan0
echo --------------route---------------
route
echo ----------------------------------
echo You may want to look at this
echo troubleshooting section:
echo 'http://home.columbus.rr.com/andrewbarr/linux/dwl520e1.html#tshoot'
echo ==================================
exit 1
}

{
echo ==================================
echo 'CONGRATULATIONS!'
echo Your D-Link DWL-520 is on the net!
echo ----------------------------------
echo 'Visit Computer->System Configuration->Networking'
echo and confirm your settings on all tabs.
echo ----------------------------------
echo Then reboot and make sure your
echo wireless connection comes up as
echo expected.
echo ==================================
}


```

---

### Post by phin on 2004-10-23
hmm the patching part complains it cannot find the proper file.

can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -udrNP linux-2.6.2.orig/MAINTAINERS linux-2.6.2/MAINTAINERS
|--- linux-2.6.2.orig/MAINTAINERS       2004-02-04 04:43:57.000000000 +0100
|+++ linux-2.6.2/MAINTAINERS    2004-02-07 12:47:05.000000000 +0100
--------------------------
File to patch: 


any clues?

---

### Post by cseg on 2004-10-23
You should have a file named MAINTAINERS in your linux source tree:

# cd /usr/src/linux
# find -name MAINTAINERS
./MAINTAINERS

If it's not there, your linux source tree probably wasn't created properly. Do the following steps:

cd /usr/src
ls -l
cd /usr/src/linux
ls -l

Post the output and I'll see if I can see anything wrong.

---

### Post by phin on 2004-10-23
never mind, my fault.  i had /usr/src/linux linked already and its all fixed.

welp its doing its thing now, i letcha know how it goes when its done! :)

---

### Post by phin on 2004-10-24
[QUOTE=cseg]You should have a file named MAINTAINERS in your linux source tree:

# cd /usr/src/linux
# find -name MAINTAINERS
./MAINTAINERS

If it's not there, your linux source tree probably wasn't created properly. Do the following steps:

cd /usr/src
ls -l
cd /usr/src/linux
ls -l

Post the output and I'll see if I can see anything wrong.[/QUOTE]
 works great!

finally 11mb/s ! and monitoring features are neeto ;)

---

### Post by Magneto on 2004-11-27
im gonna try this - seems that host-ap and wpa supplicant are the only ways for wpc11 v3 to use wpa

---

