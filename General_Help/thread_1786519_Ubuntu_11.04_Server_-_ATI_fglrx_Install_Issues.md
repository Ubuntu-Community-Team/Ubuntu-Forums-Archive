---
title: "Ubuntu 11.04 Server - ATI fglrx Install Issues"
date: 2011-06-19
forum: General Help
---

### Post by jumping_snake on 2011-06-19
Here's my current situation:

I've installed Ubuntu 11.04 64-bit server version and now I'm trying to install the fglrx driver to get my ATI 5850 working. (Reasoning: I'm creating a BOINC cruncher and I'd like to get the ATI card to be available for BOINC to use)

I tried:
```
sudo apt-get install fglrx
```

but that gave me this error:
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle

I've found multiple articles/blogs discussing how to manually install the driver, so I decided to try that. I ran the following:

```

sudo apt-get purge fglrx
sudo apt-get install -f
wget <location for 11.4 ATI drivers>
sudo apt-get install libqtgui4
sudo sh ati-driver-installer-11-4-x86.x86_64.run --buildpkg Ubuntu/natty
sudo dpkg -i *.deb

```

and I'm continuing to get the same "Errors found while processing.." messages.

Could anyone point out what I'm doing wrong? I was trying to follow this: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
for the manual install of fglrx.

---

### Post by jumping_snake on 2011-06-20
I think I put this in the wrong area. If I don't get any replies today, I'll move it over into the hardware/laptops area.

---

### Post by Claus7 on 2011-06-20
Hello,

do you get that error only by installing the fglrx package? Is there any synaptic on the server edition? Could you install the packages from there?

Could you post exactly the commands you type and the results you get? Then a solution might be found more easier.

Regards!

---

### Post by jumping_snake on 2011-06-21
1) Did I get the error only when installing fglrx?
-- When I try to install any of the fglrx packages, I get the error.

2) Synaptic
-- Not installed by default, so I haven't installed it. It's possible that I might be able to install it this way, but I haven't tried it.

Here's the entire fallout of what I see:
```


sudo -s

root@MiniCrunch:~# apt-get purge fglrx
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  fglrx* fglrx-amdcccle*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 124 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 56483 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules

Error! There are no instances of module: fglrx
8.840 located in the DKMS tree.
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-server

root@MiniCrunch:~# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@MiniCrunch:~# apt-get install libqtgui4
Reading package lists... Done
Building dependency tree
Reading state information... Done
libqtgui4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@MiniCrunch:~# sh ati-driver-installer-11-4-x86.x86_64.run --buildpkg Ubuntu/natty
Created directory fglrx-install.qiJ1eG
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.841................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager
=====================================================================
Generating package: Ubuntu/natty
Package /home/clay/fglrx_8.841-0ubuntu1_amd64.deb has been successfully generated
Package /home/clay/fglrx-dev_8.841-0ubuntu1_amd64.deb has been successfully generated
Package /home/clay/fglrx-amdcccle_8.841-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.qiJ1eG

root@MiniCrunch:~# dpkg -i *.deb
Selecting previously deselected package fglrx.
(Reading database ... 56274 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.841-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.841-0ubuntu1_amd64.deb) ...
Selecting previously deselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.841-0ubuntu1_amd64.deb) ...
Setting up fglrx (2:8.841-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/xorg/modules/drivers/fglrx_drv.so.dpkg-tmp a symlink to /etc/alternatives/fglrx_drv: No such file or directory
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
root@MiniCrunch:~#

```

---

### Post by Claus7 on 2011-06-22
Hello,

not sure about it, yet have you tried to install the deb packages one by one with a specific order?

This might solve the problem of dependencies...

Just a thought,
Regards!

---

### Post by jumping_snake on 2011-06-24
I think I did try this at one point, but I'll try it again tonight once I get home from work.

---

### Post by jumping_snake on 2011-06-25
Well, I tried doing it by either fglrx-dev or fglrx-amdcccle, but it still doesn't work:

```

root@MiniCrunch:~# apt-get install fglrx-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up fglrx (2:8.841-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: error: unable to make /usr/lib/xorg/modules/drivers/fglrx_drv.so.dpkg-tmp a symlink to /etc/alternatives/fglrx_drv: No such file or directory
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
     Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@MiniCrunch:~#

```

Any other ideas? I'll try to move this over to the hardware forum if we can't come up with any ideas before Monday morning.

---

### Post by ravyne on 2011-07-11
So, it sounds simple, but I had the same problem and it seemed to do the trick.

Make sure the "/usr/lib/xorg/modules/drivers" directory exists, and if it doesn't, create it. Just navigate to modules, then do "sudo mkdir drivers".

Hope it works for you too.

---

### Post by jumping_snake on 2011-07-19
> 
So, it sounds simple, but I had the same problem and it seemed to do the trick.

Make sure the "/usr/lib/xorg/modules/drivers" directory exists, and if it doesn't, create it. Just navigate to modules, then do "sudo mkdir drivers".

Hope it works for you too.


I thought this thread might die, thanks for the idea! I'll give it a try later this evening and report back.

---

### Post by Negative Black on 2011-08-08
This will solve your nightmares...

```
sudo mkdir -p /usr/lib/xorg/modules/drivers
```

The bug should actually be reported so the maintainers can fix it, but i'am lazy today. :-\"

---

