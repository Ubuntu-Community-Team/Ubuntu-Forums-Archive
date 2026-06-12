---
title: "Canon LIDE 60 Scanner on Ubuntu 5.10  Pls help.."
date: 2006-04-02
forum: General Help
---

### Post by Bevan-L on 2006-04-02
Im having trouble getting my Scanner to work on Ubuntu 5.10.
I have the Latest Sane backends loaded, and have also followed a guide from here
[http://ubuntuforums.org/showthread.php?t=117966](http://ubuntuforums.org/showthread.php?t=117966)

But I still have no joy. 
I've run the sane-find-scanner command and this was the ouput:

[B]
  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04a9 [Canon], product=0x221c [CanoScan], chip=GL841) at libusb:003:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
[/B]

I then ran scanimage -L  and this was the output:

[B]No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).[/B]

Would really like to get it working on my PC as I just bought it 2 months ago.

Thanks!

---

### Post by bluetoad on 2006-04-03
That is probably a permissions problem.  If you do

sudo scanimage -L

it will probably give you

$ sudo scanimage -L
device `genesys:libusb:005:002' is a Canon LiDE 60 flatbed scanner

so you need to set up the permissions...

Create the following 2  files in /etc/hotplug/usb/

libsane
--------
# This script changes the permissions and ownership of a USB device under
# /proc/bus/usb to grant access to this device to users in the scanner group.
#
# Ownership is set to saned:scanner, permissions are set to 0660.
#
# Arguments :
# -----------
# ACTION=[add|remove]
# DEVICE=/proc/bus/usb/BBB/DDD
# TYPE=usb

# latest hotplug doesn't set DEVICE on 2.6.x kernels
if [ -z "$DEVICE" ] ; then
  IF=`echo $DEVPATH | sed 's/\(bus\/usb\/devices\/\)\(.*\)-\(.*\)/\2/'`

  DEV=$(cat /sys/${DEVPATH}/devnum)
  DEVICE=`printf '/proc/bus/usb/%.03d/%.03d' $IF $DEV`
fi
echo $DEVICE >/tmp/scanner
if [ "$ACTION" = "add" -a "$TYPE" = "usb" ]; then
  chown saned:scanner "$DEVICE"
  chmod 0660 "$DEVICE"
fi


libsane.usermap
-------------------
#Canon Inc.|LIDE 60
libsane 0x0003  0x4a9   0x221c  0x0000  0x0000  0x00    0x00    0x00    0x00
0x00    0x00    0x00000000


also make sure you have an entry in /etc/udev/rules.d/45-libsane.rules
# Canon Inc.|LIDE 60
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="221c", MODE="664", GROUP="scanner"

Restart hotplug and udev

sudo /etc/init.d/hotplug restart
sudo /etc/init.d/udev restart


I got the LiDE 60 working on Breezy  using debs from Dapper.  With dependencies I ended up installing these

libsane_1.0.17-1ubuntu3_i386.deb
sane-utils_1.0.17-1ubuntu3_i386.deb
libexif10_0.6.9-4ubuntu1_i386.deb
libexif-dev_0.6.9-4ubuntu1_i386.deb
libgphoto2-2_2.1.6-5.2ubuntu5_i386.deb
libgphoto2-2-dev_2.1.6-5.2ubuntu5_i386.deb
libgphoto2-port0_2.1.6-5.2ubuntu5_i386.deb
libusb-0.1-4_0.1.8-17ubuntu2_i386.deb
pkg-config_0.20-1_i386.deb


If you would like to set the scanner up so that you can access it from other machines on your network, I have further instructions but will probably put all of this on a Wiki page.

**_Note:_**
A better way of installing the sane 1.0.17 debs from Dapper is to build the packages yourself.  This way you do not need to install all the above packages from Dapper and make your Breezy system difficult to update.

# Make sure that you have the prerequisites installed
sudo apt-get install libieee1284-3-dev dpatch libusb-dev debhelper libgphoto2-2-dev tetex-bin tetex-extra

# Get the source files
wget [http://librarian.launchpad.net/1956177/sane-backends_1.0.17-1ubuntu4.dsc](http://librarian.launchpad.net/1956177/sane-backends_1.0.17-1ubuntu4.dsc)
wget [http://librarian.launchpad.net/1956176/sane-backends_1.0.17-1ubuntu4.diff.gz](http://librarian.launchpad.net/1956176/sane-backends_1.0.17-1ubuntu4.diff.gz)
wget [http://librarian.launchpad.net/1956175/sane-backends_1.0.17.orig.tar.gz](http://librarian.launchpad.net/1956175/sane-backends_1.0.17.orig.tar.gz)

# Extract and build the packages
dpkg-source -x sane-backends_1.0.17-1ubuntu4.dsc
cd sane-backends-1.0.17/
dpkg-buildpackage -rfakeroot -b

# Install the packages
cd ..
# Following should be on one line
sudo dpkg -i libsane_1.0.17-1ubuntu4_i386.deb libsane-dev_1.0.17-1ubuntu4_i386.deb sane-utils_1.0.17-1ubuntu4_i386.deb

---

### Post by Bevan-L on 2006-04-03
Hi Bluetoad,

I've done everything that you have mentioned but i still get the same error while running sane-find-scanner and scanimage -L. I've run it with the sudo command with the same message. If I run sudo scanimage -L i get the same error:

[b]No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).[/b]

Do you need any log files from me which could help?

Thanks for the help so far.
Bevan.

---

### Post by bluetoad on 2006-04-03
This might seem a little obvious, but we should probably check the version of
scanimage

$ scanimage -V
scanimage (sane-backends) 1.0.17; backend version 1.0.17

It needs to be 1.0.17.

If the version is correct ensure that "genesys" is in /etc/sane.d/dll.conf and uncommented

If the version is not correct, you'll need to download the .deb files from the
latest (test, no formally released) version of Ubuntu called Dapper.
I did that manually by pointing at a mirror and grabbing them rather than point my sources.list (or synaptic) at Dapper.  
So look in /etc/apt/sources.list and see where you are pointing E..g. 

for
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted

go to

[http://au.archive.ubuntu.com/ubuntu/pool/main/](http://au.archive.ubuntu.com/ubuntu/pool/main/)

then for the sane .deb files go to

[http://au.archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/](http://au.archive.ubuntu.com/ubuntu/pool/main/s/sane-backends/)

and pick out the versions I listed in my previous post.  The versions might have changed, since Dapper is a moving target - go for later versions.

Download the list I specified (or later versions).  You'll need to use the directory after 'main' in the above URL as a clue to find teh .deb files.

Then install them with 

dpkg -i file1 file2 etc

Then the configuration steps, previously mentioned need to be done.

Hope this helps

---

### Post by Bevan-L on 2006-04-03
Hi Bluetoad.

Funny enough it was 1.0.15. 
I upgraded to 1.0.17 but unfortunatelly im still having the same issues :(

EDIT: if I run  sudo scanimage -L then i do get 
device `genesys:libusb:003:003' is a Canon LiDE 60 flatbed scanner

however im still not able to detect the scanner and I've set up all the neccesary configuration files as you mentioned.

---

### Post by jstritar on 2006-04-05
[QUOTE=bluetoad]That is probably a permissions problem.  If you do

sudo scanimage -L

it will probably give you

$ sudo scanimage -L
device `genesys:libusb:005:002' is a Canon LiDE 60 flatbed scanner
[/QUOTE]

I have this problem exactly. I created the files you described below, and have upgraded all the packages you named. I also added the line to the 45-libsane.rules file. [Here](http://jstritar.mit.edu/misc/) are my libsane, libsane.usermap and 45-libsane.rules files.

Have any ideas?

Also, do any of you know whether you *really* have to use the USB cable that they give you? I noticed it has those big round things on it. Does that have something to do with giving the scanner power (like changing voltages or something)? The cable they include isn't long enough for me...

---

### Post by toyfactory on 2006-04-05
Followed these instructions - same problem.  Something to do with permissions, as running xsane as root seems to work, although it warns me that terrible things are likely to happen.  The round things on the cable are some kind of interference suppressor by the way - a lot of computer cables seem to have them nowadays.

---

### Post by bluetoad on 2006-04-07
Bevan-Leigh and I followed this up offline and he got it working.  

Extra things to check

1. Make sure execute permissions are on /etc/hotplug/usb/libsane.
sudo chmod 755 /etc/hotplug/usb/libsane 
2. Uninstall the sane package (with xscanimage in it).  It has caused me problems in the past.  It will uninstall sane-utils and other dependancies.  You'll need to put those back.
3. Install xsane for when things are working 
sudo apt-get install xsane xsane-common
4. The line 
libsane 0x0003 0x4a9 0x221c 0x0000 0x0000 0x00 0x00 0x00 0x00
0x00 0x00 0x00000000
libsane.usermap should be unbroken.  A cut and paste problem on my part

---

### Post by Teo on 2006-04-13
[QUOTE=bluetoad]Bevan-Leigh and I followed this up offline and he got it working.  

Extra things to check

1. Make sure execute permissions are on /etc/hotplug/usb/libsane.
sudo chmod 755 /etc/hotplug/usb/libsane 
2. Uninstall the sane package (with xscanimage in it).  It has caused me problems in the past.  It will uninstall sane-utils and other dependancies.  You'll need to put those back.
3. Install xsane for when things are working 
sudo apt-get install xsane xsane-common
4. The line 
libsane 0x0003 0x4a9 0x221c 0x0000 0x0000 0x00 0x00 0x00 0x00
0x00 0x00 0x00000000
libsane.usermap should be unbroken.  A cut and paste problem on my part[/QUOTE]
I did exactly what u describe here but still can't get my LiDE 60 to work :(

I think there's some permissions problem:
- When running xsane as user: "no devices avalible"
- When running xsane as root: it working perfectly

Breezey 5.10.

---

### Post by pgell on 2006-04-14
Excuse my english.
Thank you very much for your help, bluetoad.
I've found in this page everything i needed to make my scanner (a Canon LIDE 35) work. I only had a few problems with the dependencies in the .deb files installation, but the "upgrade tool" of the ubuntu could repair all perfectly.
I only had to change de "idProduct" in the libsane.usermap

libsane.usermap
-------------------
#Canon Inc.|LIDE 50
libsane 0x0003 0x4a9 [COLOR="Red"]0x2213[/COLOR] 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00 0x00000000

(remember that the line should be unbroken)

---

### Post by bluetoad on 2006-04-18
[QUOTE=Teo]I did exactly what u describe here but still can't get my LiDE 60 to work :(

I think there's some permissions problem:
- When running xsane as user: "no devices avalible"
- When running xsane as root: it working perfectly

Breezey 5.10.[/QUOTE]

Is your user in the scanner group? System/Adminstration/Users and Groups etc

---

### Post by Teo on 2006-04-19
[QUOTE=bluetoad]Is your user in the scanner group? System/Adminstration/Users and Groups etc[/QUOTE]
Yes. My user is a member of group "scanner" and have priviliges to use scanner devices: "Use scanner devices" is chceked in "User priviliges" tab.

---

### Post by Teo on 2006-04-22
[QUOTE=Teo]Yes. My user is a member of group "scanner" and have priviliges to use scanner devices: "Use scanner devices" is chceked in "User priviliges" tab.[/QUOTE]
There's some bigger issue.
I cant import photos from my camera unless i start gThumb as root ](*,).

And I'm not alone with problems like that:
[http://ubuntuforums.org/showthread.php?t=107263&highlight=io-library](http://ubuntuforums.org/showthread.php?t=107263&highlight=io-library)
[http://ubuntuforums.org/showthread.php?t=101974&highlight=io-library](http://ubuntuforums.org/showthread.php?t=101974&highlight=io-library)
and many, many more...

Seems like some issue in Breezy with USB Storage :(.

---

