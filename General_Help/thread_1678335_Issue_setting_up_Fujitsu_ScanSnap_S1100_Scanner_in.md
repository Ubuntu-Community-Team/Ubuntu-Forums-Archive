---
title: "Issue setting up Fujitsu ScanSnap S1100 Scanner in Ubuntu 10.04"
date: 2011-01-30
forum: General Help
---

### Post by ghaner on 2011-01-30
I'm trying to configure an S1100 ScanSnap scanner on Ubuntu 10.04.

As far as I can tell the unit is NOT supported by SANE yet; I thought I could adapt instructions I found for the S300 here: 
  [http://candland.net/blog/2010/10/28/...-ubuntu-10-10/]("http://candland.net/blog/2010/10/28/setting-up-my-fujitsu-scansnap-s300-in-ubuntu-10-10/") that are:

*Make a directory for the file at /usr/share/sane/epjitsu/*
  *Copy from C:\Windows\SSDriver\S300\300_0c00.nal to /usr/share/sane/epjitsu*
  *chmod 755 /usr/share/sane/epjitsu/300_0c00.nal*
  *Make sure you scanner is found using*
  *sane-find-scanner*
  *If it is you can do scanimage -L or sudo scanimage -L to see if things are working.*

The S300 works great [using one OR the other to test with; I'm not  configuring the same machine for use with both; just the S1100].

What I've done to try and get the S1100  to work [is to stare at Google for about 12 hours, or I mean] I used the  file: 1100_0a00.nal instead of 300_0c00.nal and I created an entry in  /etc/sane.d/epjitsu.conf [also experimented with fujitsu.conf] like  this:

#ScanSnap S1100
firmware /usr/share/sane/epjitsu/1100_0A00.nal
usb 0x04c5 0x1200

using the values from *sane-find-scanner *

The S300 will work fine, but the S1100 won't do anything; [the blue button doesn't stop flashing like it does on the S300] and scanimage -L and xsane both fail.

Ideas? Thank you! :)

---

### Post by ghaner on 2011-01-30
I'm trying to configure an S1100 ScanSnap scanner on Ubuntu 10.04.

As far as I can tell the unit is NOT supported by SANE yet; I thought I could adapt instructions I found for the S300 here: 
  [http://candland.net/blog/2010/10/28/setting-up-my-fujitsu-scansnap-s300-in-ubuntu-10-10/](http://candland.net/blog/2010/10/28/setting-up-my-fujitsu-scansnap-s300-in-ubuntu-10-10/) that are:

*Make a directory for the file at /usr/share/sane/epjitsu/*
  *Copy from C:\Windows\SSDriver\S300\300_0c00.nal to /usr/share/sane/epjitsu*
  *chmod 755 /usr/share/sane/epjitsu/300_0c00.nal*
  *Make sure you scanner is found using*
  *sane-find-scanner*
  *If it is you can do scanimage -L or sudo scanimage -L to see if things are working.*

The S300 works great [using one OR the other to test with; I'm not configuring the same machine for use with both; just the S1100].

What I've done to try and get the S1100 to work [is to stare at Google for about 12 hours, or I mean] I used the file: 1100_0a00.nal instead of 300_0c00.nal and I created an entry in /etc/sane.d/epjitsu.conf [also experimented with fujitsu.conf] like this:

#ScanSnap S1100
firmware /usr/share/sane/epjitsu/1100_0A00.nal
usb 0x04c5 0x1200

using the values from *sane-find-scanner *

The S300 will work fine, but the S1100 won't do anything; [the blue button doesn't stop flashing like it does on the S300] and scanimage -L and xsane both fail.

Ideas? Thank you! :)

---

### Post by K.Mandla on 2011-01-30
Similar threads merged.

---

### Post by howefield on 2011-01-30
Edit : too slow :)

---

### Post by ghaner on 2011-02-28
I don't suppose there were any similar "[solved!]" threads looming about to merge with this as well ... ;-)

The S1100 is a cute little thing though [still can't use it]; but  it looks absolutely fabulous sitting next to the S300; and ... well sometimes I take it out so it can get some exercise [a little walk around the office] telling it it's still my favorite [even though it's useless to me] so that it doesn't get jealous;  then often it and I will just sit for hours enjoying the silent serenity of eaches company ... imagining scanning together someday [have nostalgic moments about old AIO devices] ...

---

### Post by boirax on 2011-06-18
Hi Ghaner,

Did you have any further luck with the S1100?  I was thinking of using it on Ubuntu 10.04 too, ... but I don't want to buy it before seeing a successful implementation. :)

Thank you for any tips,
Boirax

---

### Post by irwinr on 2011-07-06
I am also waiting to purchase... Waiting to see some kind of confirmation somewhere that it works on Ubuntu.

-Jeremy

---

### Post by evolution124 on 2011-07-11
Hi guys,

I just registered here to share this with you, because if someone else would have solved that problem I would like him to share this, too.

I HAVE GOT WORKING SCANSNAP S1100 ON UBUNTU AND IT MOST PROBABLY WILL WORK WITH OTHER DISTRIBUTIONS AS WELL.

I contacted one of the driver developers and the guy explained to me that there is an unofficial driver version for xsane that works, but it breaks the other fujitsu models that are supported by sane-epjitsu. That's why it's not included in the official sane release.

THIS IS UNOFFICIAL, AT YOUR OWN RISK, NOT AT MY CREDIT, NOT CLASSIFIED AS STABLE AND I'M NOT RESPONSIBLE FOR ANY OF YOUR ACTIONS.

Here are the instructions:

1. install the libusb-dev package or libusb-devel, depending what your
version of linux calls it

2. install gcc package and its required dependencies (though it's probably
already installed)

3. download latest sane-backends from [http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/)

4. tar xzf sane-backends...

5. cd sane-backends...

6. Download and unpack the attached diff, then run:
cat [whereEverYouPutFile]/epjitsu-21.diff | patch -p1

7. run (all on one line):

BACKENDS=epjitsu ./configure --prefix=/usr --sysconfdir=/etc --disable-locking

8. run: make (then wait awhile)

9. copy the file backend/.libs/libsane-epjitsu.so.1.0.23 over top of
the copy provided by your distro, probably
/usr/lib/sane/libsane-epjitsu.so.1.0.21 (or .20 or .22...) You can save the old one before you overwrite it if you want.

10. Update the link in /usr/lib/sane that is called something like libsane-epjitsu.so.1. It will link to your old libsane-epjitsu.so.1.0.21, but you have just replaced it. Update the link so it points to the new file libsane-epjitsu.so.1.0.23

11. copy backend/epjitsu.conf over the copy from your distro, probably
/etc/sane.d/epjitsu.conf

12. extract the firmware file from the windows driver, and place it in
the correct directory. see epjitsu.conf for details. For me and S1100 it is the file 1100_0A00.nal and I had to copy it to /usr/share/sane/epjitsu (create a new folder 'epjitsu' there). 

You can find 1100_0A00.nal in three ways:
-If you have a windows driver installation, you can find it under C:/Windows/SSDriver/S300
-You can search for it on the driver CD (I didn't check if it's there just like this)
-Otherwise you can use wine to install the ScanSnap Manager and search in the files created
-If you tell me that it's legal to upload the file like this, I can upload it here

12. Voila!!! :)

---

### Post by complience on 2011-10-01
I get no sign of power from the scanner when plugged into the usb
Do the drivers need to be loaded first?

update - It helps if you openup the covers first

---

### Post by complience on 2011-10-01
its completely legal - please send me :)

---

### Post by complience on 2011-10-02
Its showing as possibly working in the latest development release of xsane? anyone know whats what?

[http://www.sane-project.org/cgi-bin/driver.pl?manu=fujitsu&model=scansnap&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=fujitsu&model=scansnap&bus=any&v=&p=)

---

### Post by complience on 2011-10-03
10. Update the link in /usr/lib/sane that is called something like libsane-epjitsu.so.1. It will link to your old libsane-epjitsu.so.1.0.21, but you have just replaced it. Update the link so it points to the new file libsane-epjitsu.so.1.0.23

How do I update this file?

---

### Post by complience on 2011-10-04
Started again from scratch to see i could crack this
Now im getting the following error when I try to patch the file


$ sudo cat ~/Downloads/epjitsu-21.diff|patch -p1
patching file backend/epjitsu-cmd.h
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 26.
Hunk #3 FAILED at 38.
Hunk #4 FAILED at 457.
4 out of 4 hunks FAILED -- saving rejects to file backend/epjitsu-cmd.h.rej
patching file backend/epjitsu.c
Hunk #1 FAILED at 126.
Hunk #2 FAILED at 174.
Hunk #3 FAILED at 343.
Hunk #4 FAILED at 369.
Hunk #5 FAILED at 403.
Hunk #6 FAILED at 565.
Hunk #7 FAILED at 581.
Hunk #8 FAILED at 593.
Hunk #9 FAILED at 632.
Hunk #10 FAILED at 655.
Hunk #11 FAILED at 679.
Hunk #12 FAILED at 701.
Hunk #13 FAILED at 722.
Hunk #14 FAILED at 741.
Hunk #15 FAILED at 753.
Hunk #16 FAILED at 806.
Hunk #17 FAILED at 819.
Hunk #18 FAILED at 874.
Hunk #19 FAILED at 946.
Hunk #20 FAILED at 983.
Hunk #21 FAILED at 1026.
Hunk #22 FAILED at 1045.
Hunk #23 FAILED at 1064.
Hunk #24 FAILED at 1083.
Hunk #25 FAILED at 1421.
Hunk #26 FAILED at 1544.
Hunk #27 FAILED at 1569.
Hunk #28 FAILED at 1632.
Hunk #29 FAILED at 1685.
Hunk #30 FAILED at 1709.
Hunk #31 FAILED at 1789.
Hunk #32 FAILED at 1885.
Hunk #33 FAILED at 1912.
Hunk #34 FAILED at 1930.
Hunk #35 FAILED at 2120.
Hunk #36 FAILED at 2164.
Hunk #37 FAILED at 2184.
Hunk #38 FAILED at 2365.
Hunk #39 FAILED at 2399.
Hunk #40 FAILED at 2694.
Hunk #41 FAILED at 2707.
Hunk #42 FAILED at 2718.
Hunk #43 FAILED at 2818.
Hunk #44 FAILED at 2835.
Hunk #45 FAILED at 2891.
Hunk #46 FAILED at 2910.
Hunk #47 FAILED at 2929.
Hunk #48 FAILED at 3075.
Hunk #49 FAILED at 3092.
Hunk #50 FAILED at 3247.
Hunk #51 FAILED at 3289.
Hunk #52 FAILED at 3299.
Hunk #53 FAILED at 3386.
Hunk #54 FAILED at 3398.
Hunk #55 FAILED at 3414.
Hunk #56 FAILED at 3434.
Hunk #57 FAILED at 3467.
Hunk #58 FAILED at 3526.
Hunk #59 FAILED at 3544.
Hunk #60 FAILED at 3587.
Hunk #61 FAILED at 3683.
Hunk #62 FAILED at 3787.
Hunk #63 FAILED at 3832.
Hunk #64 FAILED at 3858.
Hunk #65 FAILED at 3983.
Hunk #66 FAILED at 4104.
Hunk #67 FAILED at 4296.
67 out of 67 hunks FAILED -- saving rejects to file backend/epjitsu.c.rej
patching file backend/epjitsu.conf.in
Hunk #1 FAILED at 32.
1 out of 1 hunk FAILED -- saving rejects to file backend/epjitsu.conf.in.rej
patching file backend/epjitsu.h
Hunk #1 FAILED at 18.
Hunk #2 FAILED at 56.
Hunk #3 FAILED at 68.
Hunk #4 FAILED at 87.
Hunk #5 FAILED at 112.
Hunk #6 FAILED at 127.
Hunk #7 FAILED at 151.
Hunk #8 FAILED at 213.
Hunk #9 FAILED at 257.
Hunk #10 FAILED at 353.
Hunk #11 FAILED at 362.
Hunk #12 FAILED at 380.
12 out of 12 hunks FAILED -- saving rejects to file backend/epjitsu.h.rej
patching file doc/descriptions/epjitsu.desc
Hunk #1 FAILED at 42.
1 out of 1 hunk FAILED -- saving rejects to file doc/descriptions/epjitsu.desc.rej

---

### Post by CarlFK on 2011-12-22
Here is a script that does the above steps.  well, you need to dig up 1100_0A00.nal on your own and drop it in the same dir as this script.  and this was only tested on precise.  the libs on natty are in a different dir.

```
juser@trist:~/snapscan$ md5sum 1100_0A00.nal epjitsu-21.diff.zip 
231b40b58a7a913a76b9d2485e552f28  1100_0A00.nal
8f2cc23eea6375fa6b688de291d8f604  epjitsu-21.diff.zip

```
```

#!/bin/bash -xe

# files to be in the same dir as this script:
# epjitsu-21.diff.zip
# 1100_0A00.nal

sudo apt-get install sane build-essential git libusb-dev
git clone git://git.debian.org/sane/sane-backends.git
cd sane-backends
unzip ../epjitsu-21.diff.zip 
patch -p1 < epjitsu-21.diff
BACKENDS=epjitsu ./configure --prefix=/usr --sysconfdir=/etc --disable-locking
make

sudo cp backend/.libs/libsane-epjitsu.so.1.0.23 /usr/lib/x86_64-linux-gnu/sane
sudo ln -s -f /usr/lib/x86_64-linux-gnu/sane/libsane-epjitsu.so.1.0.23 \
     /usr/lib/x86_64-linux-gnu/sane/libsane-epjitsu.so.1
sudo cp backend/epjitsu.conf /etc/sane.d/
sudo mkdir -p /usr/share/sane/epjitsu
sudo cp ../1100_0A00.nal /usr/share/sane/epjitsu
```

---

### Post by complience on 2012-01-20
So I had this running sweetly on 10.10 but after upgrading to Oneiric ocelot 11.10 and it all came crashing down.

I now get an 'out of memory error' whenever I try to connect and scan with the device..

Any ideas?

---

### Post by complience on 2012-01-27
I am worried because although updating ubuntu to 11.10 should mean the previous library paths are wrong I wouldn't have expected this 'out of memory' issue.

Can anyone help - i really need this scanner back working now I rely on it.

---

### Post by organica on 2012-06-14
I second this.  I tried installing the drivers on 10.04 and 12.04 with no luck.  Is there an update from the developer?

---

### Post by clstal on 2012-09-15
I can confirm that out of the box the scan snap s1100 does NOT work with Natty. I plug it in and get a blinking blue light... 

My question is about wine and the scan snap management software - I've installed the software using wine, and it completed just fine. 

However - now what? How to open the program in wine to do a test scan? Trying to initiate a scan at the scanner itself doesn't work (just get that blinking blue light). 

I don't care how the scanner works - wine or SANE, I'm not picky, but my knowledge of Ubuntu is limited so I'm hesitant to go mucking around with the instructions outlined above. 

Help?

---

### Post by complience on 2012-10-07
So ive gone through all the steps again within ubuntu 12.04 and am still getting the out of memory error!

This is a real shame because it was working a treat in 10.10
Can anyone help me debug why the drivers won't work in latest release.

---

### Post by complience on 2012-10-08
Okay Guys

Thanks to the helpful genius that is Allan Noah from the Sane Project - I now have this working in 12.10 32bit ubuntu desktop

The documented patching steps work although there is a different path for the sane libraries in the latest versions of ubuntu

The symbolic link needed between libsane-epjitsu.so.1 and your patched libsane-epjitsu.so.1.0.23 (or whatever version your on) is now found at --> /usr/lib/i386-linux-gnu/sane

I know the steps look time consuming but they DO work and I can help you out if you get stuck.

---

### Post by h3n5y on 2012-12-08
Thanks a lot complience!

In order to change the lib, I ran the command from the backend/.libs dir:

# cp libsane-epjitsu.so.1.0.24 /usr/lib/i386-linux-gnu/sane

Then:

# cd /usr/lib/i386-linux-gnu/sane/
# ln -sf libsane-epjitsu.so.1.0.24 libsane-epjitsu.so.1

which gives me:

root@srv95:/usr/lib/i386-linux-gnu/sane# ls -l  libsane-epj*
-rw-r--r-- 1 root root    991 Dec  5  2011 libsane-epjitsu.la
lrwxrwxrwx 1 root root     25 Dec  8 16:11 libsane-epjitsu.so.1 -> libsane-epjitsu.so.1.0.24
-rw-r--r-- 1 root root  87084 Dec  5  2011 libsane-epjitsu.so.1.0.22
-rwxr-xr-x 1 root root 235725 Dec  8 16:06 libsane-epjitsu.so.1.0.24

All good and well, but: 

# scanimage -d epjitsu:libusb:002:003 >/tmp/foo
scanimage: sane_start: Out of memory


still fails. My guess is that the nal driver might be 32 bit only?

# Fujitsu S1100
firmware /usr/share/sane/epjitsu/1100_0A00.nal
usb 0x04c5 0x1200


Any ideas?

---

### Post by bilekbp on 2013-01-04
Does anyone have this working in 12.10 64-bit?

---

### Post by cr45h on 2013-04-20
> **bilekbp said:**
> Does anyone have this working in 12.10 64-bit?

Bumping this thread. I'm using 13.04 64-bit and I'm hoping someone has figured this out and will be willing to tell the rest of us how to do it. I really want to get this scanner working.

---

### Post by complience on 2013-04-21
Hi Crash

No need to bump...
Your on the bleeding edge running 13.04 - but you new that before you upgraded...
I got it working with 12.10 but haven't looked into any higher yet.

Although no reason why it shouldn't work.. the location of the libraries will have changed and just will need to be updated.\
/usr/lib/x86_64-linux-gnu/sane/

Whats the actual error your seeing?

---

### Post by cr45h on 2013-04-26
Thanks for the answer. I'm actually fairly new to Linux and I'm a bit confused by all the different instructions in this thread. If you don't mind, can you point me what instructions you followed to get it working? Thanks!

---

### Post by jmlholdings on 2013-11-29
Good day all.  I have been running a 4 week soak test on Ubuntu 13.10 and have decided to abandon Windows.  Yes, I know its about time right?  :)
The Desktop version with my s1500 scanner works fine.  I ended up getting Vuescan to handle my scanning needs.  It works great.
Now for the laptop... The only thing I cannot get to work is the S1100 I have for travel.
After reading this thread and working on a few projects already to get Ubuntu where I need it, (in order to abandon Windows), I have decided to bite off on this project and see if I can get this SOLVED.

I am running 13.10-64 bit, and it has caused more than a few problems in getting everything I wanted working properly.  I stumbled across this website link ( for you 64-bit users) that puts back all the 32-bit dependencies at once, without having to trace down every single one of them.  This is my first step in getting this 1100 scanner working.

The link is here:
[http://xpressrazor.wordpress.com/2013/10/18/ubuntu-13-10-32-bit-packages/](http://xpressrazor.wordpress.com/2013/10/18/ubuntu-13-10-32-bit-packages/)

Thanks to xpressrazor for putting this up.  It made my life so much easier.  HUGE THANKS!
I am also posting it in the thread in case the site removes it some time in the future.

---

### Post by jmlholdings on 2013-11-29
[TABLE="width: 500"]
[TR]
[TD]sudo apt-get install bluez-alsa:i386 esound-common gcc-4.7-base:i386 glib-networking glib-networking:i386 glib-networking-common glib-networking-services gstreamer0.10-plugins-base:i386 gstreamer0.10-plugins-good:i386 gstreamer0.10-x:i386 gtk2-engines:i386 gtk2-engines-murrine:i386 gtk2-engines-oxygen:i386 gtk2-engines-pixbuf:i386 gvfs gvfs:i386 gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs gvfs-libs:i386 ibus-gtk:i386 libaa1:i386 libacl1:i386 libaio1:i386 libao-common libao4:i386 libasn1-8-heimdal libasn1-8-heimdal:i386 libasound2 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libatk1.0-0:i386 libattr1:i386 libaudio2 libaudio2:i386 libaudiofile1:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libbz2-1.0:i386 libc6:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcanberra-gtk-module:i386 libcanberra-gtk0:i386 libcanberra0:i386 libcap2:i386 libcapi20-3:i386 libcdparanoia0:i386 libcomerr2:i386 libcroco3:i386 libcups2:i386 libcupsfilters1 libcupsfilters1:i386 libcupsimage2:i386 libcurl3 libcurl3:i386 libdatrie1:i386 libdb5.1:i386 libdbus-1-3 libdbus-1-3:i386 libdbus-glib-1-2:i386 libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2 libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libdv4:i386 libegl1-mesa libegl1-mesa-drivers libesd0:i386 libexif12:i386 libexpat1:i386 libffi6:i386 libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgail-common:i386 libgail18:i386 libgcc1:i386 libgconf-2-4:i386 libgcrypt11 libgcrypt11:i386 libgdbm3:i386 libgdk-pixbuf2.0-0:i386 libgettextpo0:i386 libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 libglib2.0-0:i386 libglu1-mesa:i386 libgnome-keyring0:i386 libgnutls26 libgnutls26:i386 libgpg-error0:i386 libgphoto2-6:i386 libgphoto2-l10n libgphoto2-6 libgpm2:i386 libgssapi-krb5-2:i386 libgssapi3-heimdal libgssapi3-heimdal:i386 libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgtk2.0-0:i386 libgudev-1.0-0 libgudev-1.0-0:i386 libharfbuzz0a libharfbuzz0a:i386 libhcrypto4-heimdal libhcrypto4-heimdal:i386 libheimbase1-heimdal libheimbase1-heimdal:i386 libheimntlm0-heimdal libheimntlm0-heimdal:i386 libhx509-5-heimdal libhx509-5-heimdal:i386 libice6:i386 libicu48 libicu48:i386 libidn11:i386 libiec61883-0:i386 libieee1284-3:i386 libjack-jackd2-0:i386 libjasper1:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libjson0:i386 libk5crypto3:i386 libkeyutils1:i386 libkrb5-26-heimdal libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386 libldap-2.4-2 libldap-2.4-2:i386 libllvm3.2:i386 libltdl7:i386 liblzma5:i386 libmad0:i386 libmikmod2:i386 libmng1:i386 libmpg123-0:i386 libmysqlclient18:i386 libncurses5:i386 libncursesw5:i386 libnspr4:i386 libnss3:i386 libodbc1:i386 libogg0:i386 libopenal-data libopenal1:i386 liborc-0.4-0:i386 libp11-kit0:i386 libpango1.0-0:i386 libpciaccess0:i386 libpcre3:i386 libpixman-1-0:i386 libpng12-0:i386 libproxy1:i386 libpulse-mainloop-glib0:i386 libpulse0:i386 libpulsedsp:i386 libqt4-dbus libqt4-dbus:i386 libqt4-declarative libqt4-declarative:i386 libqt4-designer libqt4-designer:i386 libqt4-help libqt4-network libqt4-network:i386 libqt4-opengl libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-script libqt4-script:i386 libqt4-scripttools libqt4-scripttools:i386 libqt4-sql libqt4-sql:i386 libqt4-sql-mysql:i386 libqt4-sql-sqlite libqt4-svg libqt4-svg:i386 libqt4-test libqt4-test:i386 libqt4-xml libqt4-xml:i386 libqt4-xmlpatterns libqt4-xmlpatterns:i386 libqtcore4 libqtcore4:i386 libqtgui4 libqtgui4:i386 libqtwebkit4:i386 libraw1394-11:i386 libroken18-heimdal libroken18-heimdal:i386 librsvg2-2:i386 librsvg2-common:i386 librtmp0:i386 libsamplerate0:i386 libsane:i386 libsasl2-2 libsasl2-2:i386 libsasl2-modules libsasl2-modules:i386 libsdl-image1.2:i386 libsdl-mixer1.2:i386 libsdl-net1.2:i386 libsdl-ttf2.0-0:i386 libsdl1.2debian:i386 libsecret-1-0:i386 libselinux1:i386 libshout3:i386 libslang2:i386 libsm6:i386 libsndfile1:i386 libsoup-gnome2.4-1:i386 libsoup2.4-1:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl0.9.8:i386 libssl1.0.0 libssl1.0.0:i386 libstdc++5:i386 libstdc++6:i386 libtag1-vanilla:i386 libtag1c2a:i386 libtasn1-3:i386 libtdb1:i386 libthai0:i386 libtheora0:i386 libtiff5 libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1 libudev1:i386 libunistring0:i386 libusb-0.1-4:i386 libusb-1.0-0:i386 libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libvisual-0.4-0:i386 libvisual-0.4-plugins:i386 libvorbis0a:i386 libvorbisenc2:i386 libvorbisfile3:i386 libwavpack1:i386 libwebp4:i386 libwhoopsie0 libwind0-heimdal libwind0-heimdal:i386 libwrap0:i386 libx11-6 libx11-6:i386 libx11-xcb1 libx11-xcb1:i386 libxau6:i386 libxaw7:i386 libxcb-dri2-0 libxcb-dri2-0:i386 libxcb-glx0 libxcb-glx0:i386 libxcb-render0 libxcb-render0:i386 libxcb-shm0 libxcb-shm0:i386 libxcb1 libxcb1:i386 libxcomposite1:i386 libxcursor1 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6 libxext6:i386 libxfixes3 libxfixes3:i386 libxft2:i386 libxi6 libxi6:i386 libxinerama1 libxinerama1:i386 libxml2 libxml2:i386 libxmu6:i386 libxp6 libxp6:i386 libxpm4:i386 libxrandr2 libxrandr2:i386 libxrender1 libxrender1:i386 libxslt1.1:i386 libxss1:i386 libxt6 libxt6:i386 libxtst6 libxtst6:i386 libxv1 libxv1:i386 libxxf86vm1 libxxf86vm1:i386 mysql-common odbcinst odbcinst1debian2 odbcinst1debian2:i386 qdbus whoopsie xaw3dg:i386 zlib1g:i386[/TD]
[/TR]
[/TABLE]

---

### Post by jmlholdings on 2013-11-29
Now for the homework....

There is reference to 1100_0a00.nal.  I will be using that file that I pulled from my windows directory.  (Maybe someone can tell me if it is legal or not to post that file here for use?)
Now in doing some additional digging today, I installed the S1100 windows install fresh on my Windows PC and it makes reference NOT to the 1100_0a00.nal file but to 1100_0039.nal.
I copied that file as well and will be trying it to see if results are the same.

---

### Post by u-jason on 2013-11-29
Fresh Install Ubuntu 13.10 64-bit (with 32-bit dependencies reinstalled, using above reference)
Folder created in "Home" directory.  I called it S1100.
In that folder I copied the script I created, 1100_0a00.nal, and the .zip file from page 1 of this thread (epjitsu-21.diff).  I ran the script by typing into a "terminal" window, "./name of script".  

After the script completed, I had the following errors:

cc1: some warnings being treated as errors
make[1]: *** [scanimage.o] Error 1
make[1]: Leaving directory `/home/nameofuser/S1100/sane-backends/frontend'
make: *** [all-recursive] Error 1
cp: cannot stat ‘backend/.libs/libsane-epjitsu.so.1.0.23’: No such file or directory
./fj_s1100_ubuntu_fix: line 21: /usr/lib/x86_64-linux-gnu/sane/libsane-epjitsu.so.1: Permission denied


I am now going to correct the probable folder directory errors and rerun the script again.

---

### Post by u-jason on 2013-12-16
OK Finally got this working.... Well I didn't, but a friend I got to help me out who knows Linux better than I do did get it working in 12.04, 12.10, 13.04, and 13.10    32 & 64 bit versions.
I will post a final on this as it is NOW solved for you S1100 scanner fans.  

I will get it up before Xmas.

---

### Post by tjcqqnea on 2013-12-19
> **u-jason said:**
> OK Finally got this working.... Well I didn't, but a friend I got to help me out who knows Linux better than I do did get it working in 12.04, 12.10, 13.04, and 13.10    32 & 64 bit versions.
I will post a final on this as it is NOW solved for you S1100 scanner fans.  

I will get it up before Xmas.

Please do! :), I've tried gathering up all the information in this thread prior to yours and I haven't been able to get it to work. If you can write something up then that would be great!

This scanner is the only thing keeping me from deleting my Windows partition :). I'm glad you got it working on your set up at least, it's a little encouraging.

---

### Post by c3646729 on 2014-01-01
Here's some instructions of what I did to get my S1100 somewhat working. I'm getting an Out of Memory error now when I try to scan with gscan2pdf but I'll try some other apps and I can look into that one further. At least now my scanner is detected.
-----------------
I haven't cleaned these up too much so some items may not be necessary but it'll at least give some ideas for those who are still having issues.

_**S1100 scanner on Debian Wheezy 64bit**_

sudo apt-get install libusb-dev (if you don't already have it)

**Download zip file from **[https://github.com/miurahr/sane-backends](https://github.com/miurahr/sane-backends) **or specifically** [https://github.com/miurahr/sane-backends/archive/upstream.zip](https://github.com/miurahr/sane-backends/archive/upstream.zip)[B]
Extract all the files somewhere, open the folder in terminal and run these commands.[/B]

**sudo ./configure BACKENDS="epson2 futjisu" PRELOADABLE_BACKENDS="epson2"**
**sudo make**
**sudo make install**
**sudo apt-get install sane** (if you don't already have it), install any dependencies using ***sudo apt-get -f install*** if prompted

***sudo scanimage -L ***or ***scanimage -L*** (run without sudo/root to see if scanning works under your user account or root only.) 
**sudo sane-find-scanner** (this will get the make/model numbers - 0x04c5 and 0x1200)
-----
**_Add these lines below to /etc/sane.d/epjitsu.conf_**
# Fujitsu S1100
firmware /usr/share/sane/epjitsu/1100_0039.nal
usb 0x04c5 0x1200
-----
**Create folder /usr/share/sane/epjitsu**
Copied **1100_0039.nal** (somewhere in this thread another number is mentioned but I couldn't find it) from Windows install (C:\Windows\SSDriver) or I got mine in C:\Windows\System32\DriverStore\FileRepository\s1100-x64.inf_amd64_...\1100_0039.nal
-----------------------------------------------------------
**Permission issue (scanner works under root but not user for me)**
---
Made sure my user is in scanner and saned groups /etc/group (edited group file as root and modified it).
---
Create** /etc/udev/rules.d/40-scanner.rules **and add 1 line below (I did a copy/paste of one of the files in the directory and blanked out the content so that it had the same permissions).

[I]SUBSYSTEMS=="usb", ATTRS{idVendor}=="04c5", ATTRS{idProduct}=="1200", ENV{libsane_matched}="yes", GROUP="scanner"

[/I]------

sudo /etc/init.d/udev restart (restarts udev so that it reloads rules)

**Unplug/replug scanner and try scanning from user account.**

On my PC it now detects the scanner from my user account and the scanning software can find it no problems but I'm getting that out of memory error in the scanning software which I'll try to figure out..

Hope this helps someone.

---

### Post by c3667970 on 2014-01-01
**Out of memory error** (continuation of previous post)

I've attached the .diff file I used to compile the 1.0.25 file. I've attached the firmware/nal file for steps in post #31, my epjitsu config file (post #31), the udev rules file for post #31  and the patched libsane-epjitsu.so.1.0.25 for this post (renamed to 1.0.22 in the instructions below) so  you don't have to compile it (you can ignore the .diff instructions). I've listed what I've done below but you could try extracting the libsane-epjitsu.so.1.0.25 file in the attached S1100 files.zip and drop it into the **/usr/lib/x86_64-linux-gnu/sane/ **folder. Rename the existing file to old and rename the patched 1.0.25 to match the old filename.

-----
Followed instructions in post #7 and paths on page 2 (what I did below)
----
downloaded latest sane-backends from [http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/)
extracted somewhere
download epjitsu-21.diff file from [http://ubuntuforums.org/showthread.php?t=1678335&p=11036817#post11036817](http://ubuntuforums.org/showthread.php?t=1678335&p=11036817#post11036817)

Copied extracted .diff file into sane-backends folder. Browsed to it in terminal and ran "sudo cat epjitsu-21.diff | patch -p1"

sudo BACKENDS=epjitsu ./configure --prefix=/usr --sysconfdir=/etc --disable-locking

sudo make

sudo make install

Still didn't work..

Copied the now patched **/sane-backends/backend/.libs/libsane-epjitsu.so.1.0.25** to **/usr/lib/x86_64-linux-gnu/sane/libsane-epjitsu.so.1.0.22**

My existing version was 1.0.22, I simply **renamed it** to oldlibsane-epjitsu and renamed 1.0.25 to 1.0.22.

Tried scanner and everything works fine now. These instructions are messy but at the very least it's documented.. some day when I feel the need to reinstall Debian I'll go through them again and try to do it the proper way :). Ideally just installing the latest backend 1.0.25 and dropping in the patched 1.0.25 file (attached in S1100 files.zip) or patching the diff file again from post #7 in this thread. Following the steps in post #31 but starting off with the latest sane-backend instead of the modified ones to see if it works.

Hope this helps someone.. I'm sooo tired of playing with this stuff.. it works for me and I'll leave it at that for now :).

---

### Post by jim_smyth on 2014-05-15
Thanks!  Worked first time.

---

### Post by jim_smyth on 2014-06-03
Well - it *did* work.  Since then an ubuntu upgrade has provided a new kernel and now I get the following:

[+30.48s] DEBUG: scanner.vala:1209: sane_start (page=0, pass=0) -> SANE_STATUS_NO_MEM
[+30.48s] WARNING: scanner.vala:1216: Unable to start device: Out of memory


boohoo.  I'll have a look around and see if I can work out what happened.

---

### Post by jim_smyth on 2014-06-03
Schoolboy error :-(

 libsane-epjitsu.so.1 -> libsane-epjitsu.so.1.0.25 had been replaced with  libsane-epjitsu.so.1 -> libsane-epjitsu.so.1.0.23

Just corrected the symlink and all working again! :-)

---

### Post by robert108 on 2014-07-09
I'm currently trying to install the S1100 on Mint 17. I tried all the instruction above. The diff file throws up hundreds of errors and failures. I tried copying everything over as best I could. Nothing doing as far as I can tell.

I'm on a 64-bit laptop.

Anybody done this on Mint?

Thanks!

Also having problems with Wine as it needs .NET 3,5

---

### Post by mrphconnor on 2015-01-04
Im running ubuntu 14.04 32 bit

Xsane has previously been working fine for years but after a recent update I now see this option screen on startup to selected a device and get an out of memory errors when scanning

'sudo sane-find-scanner' returns this

found USB scanner (vendor=0x04c5 [FUJITSU], product=0x1200 [ScanSnap S1100]) at libusb:002:003


And I have these details in my [B][U]/etc/sane.d/epjitsu.conf

[/U][/B]but a  'scanimage -L' returns this

device `v4l:/dev/video0' is a Noname 1.3M WebCam virtual device

---

