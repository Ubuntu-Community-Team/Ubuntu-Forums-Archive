---
title: "Broken my Ubuntu! apt-get problems"
date: 2009-10-31
forum: General Help
---

### Post by bsmaat on 2009-10-31
Hey,

So I'm an ubuntu newbie. I installed fine, (9.04), backed up everything, and then tried to install the ATI proprietary drivers (System->Admin->Hardware Drivers) and tried to install ATI/AMD Proprietary FGLRX Graphics Drivers. That went fine. I restarted the computer. Everything was fine. Then I tried to play with the appearance so that I changed the Visual effects to Normal. Was fine. Restarted computer, and then it started lagging, so I changed it back to None, and restarted again. This time, i heard ubuntu load but nothing appeared on screen, so i pressed ctrl+alt+F2 to open up that terminal thing, logged in and extracted the tar file id backed up the system in. Loaded up ubuntu again and it loaded fine, and I tried to install the proprietary drivers again but now its not working!

Update manager tells me I need to update xorg-driver-fglrx, so I try, but I guess the following error:

You have 1 broken package on your system!
Use the Broken filter to locate it.
```

E: /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.600-0ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 2
```

So I open synaptic package manager and use the broken filter, and its fglrx_amdcccle that is broken. So i try to reinstall which also tries to reinstall xorg-driver-fglrx, and I get the same error again:

```
E: /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.600-0ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 2
```


Then I moved to the terminal:

```
billy@desktop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libamdxvba1
The following NEW packages will be installed
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/15.5MB of archives.
After this operation, 48.5MB of additional disk space will be used.
(Reading database ... 117578 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.600-0ubuntu2_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/fglrx/libGL.so.1.2.xlibmesa' with
  different file `/usr/lib/libGL.so.1.2', not allowed
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.600-0ubuntu2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.600-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
billy@desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  xorg-driver-fglrx
Suggested packages:
  libamdxvba1
The following NEW packages will be installed
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/15.5MB of archives.
After this operation, 48.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 117578 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.600-0ubuntu2_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/fglrx/libGL.so.1.2.xlibmesa' with
  different file `/usr/lib/libGL.so.1.2', not allowed
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.600-0ubuntu2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.600-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
billy@desktop:~$ sudo apt-get install emacs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  emacs: Depends: emacs22-gtk but it is not going to be installed or
                  emacs22 or
                  emacs22-nox but it is not going to be installed
  fglrx-amdcccle: Depends: xorg-driver-fglrx but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
billy@desktop:~$ sudo apt-get install fglrx-amdcccle 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx-amdcccle is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  fglrx-amdcccle: Depends: xorg-driver-fglrx but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


Any ideas how to fix this? Can't seem to install anything

---

### Post by Brandon Williams on 2009-11-01
My best guess is that a diversion from the previous fglrx install was not cleaned up when you deinstalled fglrx. The diversion renamed the version of libGL installed by xlibmesa-gl so that the fglrx driver could install its own version, but the diversion was not successfully reverted when the fglrx driver was deinstalled.

I would log in at a console prompt and attempt to deinstall fglrx again in order to revert the bad diversion. If that doesn't work, you may have to remove the diversion by hand. If you post your /var/lib/dpkg/diversions file contents, we might have an easier time suggesting a call to dpkg-divert that would work.

---

### Post by grandtoubab on 2009-11-01
Why don't you trust the system?
You might want to run 'apt-get -f install'

---

### Post by halj32 on 2009-11-01
try
sudo apt-get install -f
or
sudo apt-get -f install
you could try updating first
sudo apt-get update

---

