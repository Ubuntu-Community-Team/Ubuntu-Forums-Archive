---
title: "Problem with nVidia driver install/DKMS"
date: 2010-02-15
forum: General Help
---

### Post by tracyandskye on 2010-02-15
I'm assuming it doesn't matter, but just in case, I'm doing all of the below over remote desktop viewer.

Mythbuntu 9.10.  I've had this strange problem that I can only get TV-Out with the nVidia 185 drivers installed.  So if I want to use a monitor I have to uninstall the nVidia driver & reboot.  The last time I did this, the uninstall (through the hardware drivers window) froze about ½ way.  When I rebooted though, I had video on the monitor.

So I used Clonezilla to clone my IDA hard drive to an SATA hd.  Everything came up & seemed OK but when I tried to load the 185 drivers I got the same result (stopped ½ way).  Then started a bunch of errors & I can't find my way out.  So the short version is below:

I try to load the 185 nVidia driver through the Hardware Drivers Window & it stops about ½ way through loading.

So I tried:

sudo apt-get install nvidia-glx-185

and got:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

So I tried:

sudo dpkg --configure -a

and got:

dpkg: error processing nvidia-185-kernel-source (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 nvidia-185-kernel-source

So I tried:

sudo apt-get install nvidia-185-kernal-source

and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-185-kernal-source

So I tried:

sudo apt-get install nvidia-common

and got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 fakeroot nvidia-settings nvidia-185-kernel-source
  dkms patch linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-190-modaliases nvidia-195-modaliases
The following NEW packages will be installed:
  nvidia-190-modaliases nvidia-195-modaliases
The following packages will be upgraded:
  nvidia-common
1 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/11.9MB of archives.
After this operation, 176kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 179506 files and directories currently installed.)
Preparing to replace nvidia-185-kernel-source 185.18.36-0ubuntu9 (using .../nvidia-185-kernel-source_185.18.36-0ubuntu9_i386.deb) ...
Removing all DKMS Modules

It just stays there.  If I close, reboot, whatever, some version of this story starts over again.

---

### Post by flippo on 2010-02-15
I'm not particularly familiar with the debian package system ubuntu uses (dpkg, apt-get) but I did find this page about dealing with broken packages:
[http://linux.derkeiler.com/Mailing-Lists/Debian/2005-02/0028.html]("http://linux.derkeiler.com/Mailing-Lists/Debian/2005-02/0028.html")

If that helps I can also try to help you get your video and nvidia graphics working at the same time then you can avoid this sort of thing all together in the future. :)

---

### Post by tracyandskye on 2010-02-19
OK, I tried option 1 from that link:  same problem.

I tried #2 & tried to reload 185 & got the initial error about dpkg getting interrupted.

So I ran the suggested entry & it seemed to work!  So I loaded 185 again & got this:

curley@curley-desktop:~$ sudo apt-get install nvidia-glx-185
[sudo] password for curley: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
curley@curley-desktop:~$ sudo dpkg --configure -a
curley@curley-desktop:~$ sudo apt-get install nvidia-glx-185
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-glx-185
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.6MB of archives.
After this operation, 28.7MB of additional disk space will be used.
Selecting previously deselected package nvidia-185-kernel-source.
(Reading database ... 179506 files and directories currently installed.)
Preparing to replace nvidia-185-kernel-source 185.18.36-0ubuntu9 (using .../nvidia-185-kernel-source_185.18.36-0ubuntu9_i386.deb) ...
Removing all DKMS Modules
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified.
dkms.conf: Error! No 'PACKAGE_NAME' directive specified.
dkms.conf: Error! No 'PACKAGE_VERSION' directive specified.

Error! Bad conf file.
File: /var/lib/dkms/nvidia/185.18.36/source/dkms.conf does not represent
a valid dkms.conf file.
Done.
Unpacking replacement nvidia-185-kernel-source ...
Selecting previously deselected package nvidia-glx-185.
Unpacking nvidia-glx-185 (from .../nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa6_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg: error processing /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa6_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libvdpau_nvidia.so.185.18.36', which is also in package nvidia-185-libvdpau 0:185.18.36-0ubuntu9
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-185_185.18.36-0ubuntu10~karmic~nvidiavdpauppa6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
curley@curley-desktop:~$ 

So I rebooted & just tried the updates that were in the update manager (mostly a bunch of nvidia driver stuff).  It gets to the point where it uninstalls dkms, then begins the uninstall of nvidia 185.18.36.  It says:

Status: This module was inactive for this kernal.
depmod..................................................................................................................................................................... keeps going forever, and I think this is right where I started.

---

### Post by tracyandskye on 2010-02-25
Bump...I really need help here.  This is my media center.  My wife can't watch Opra if you can dig it.

The brute force option of removing the offending files seems like it should work but it didn't.  Maybe I didn't do it right, I don't know.  This is killing me though.  Seems like a simple thing, can't load video driver...

---

### Post by OrangeVixen on 2010-06-21
I had the same problem, did you try upgrading dkms?

In Synaptic, go to the upgradable packages and type in dkms. I found my dkms to need upgrade and I upgraded it, everything works now. The nVidia 180 and 185 GLX drivers were installed.

---

