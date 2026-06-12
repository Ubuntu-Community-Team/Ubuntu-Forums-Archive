---
title: "vmware modules compiled for wrong kernel???"
date: 2006-06-20
forum: General Help
---

### Post by pellgarlic on 2006-06-20
i installed vmware through synaptic, but got these errors when it tried to configure:

```
pell@pellopolis:~$ sudo dpkg --configure vmware-player
Setting up vmware-player (1.0.1-4) ...
Now configuring VMware Player.  (This may take some time...)
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.50.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install
already exists.  Overwrite? [yes] y

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.99.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to
install already exists.  Overwrite? [yes] y

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to
install already exists.  Overwrite? [yes] y

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player

```

checked that i have correct linux-headers, build-essential, g++ installed - ok. still no go.

modprobe vmmon and modprobe vmnet produce this:

```
FATAL: Module vmmon not found.
FATAL: Module vmnet not found.
```

searched for "vmnet.ko" and "vmmon.ko" and found them in "lib/modules/2.6.15-**25**-k7/misc" and "lib/modules/2.6.15-**25**-386/misc" and "lib/modules/2.6.15-**25**-686/misc". only problem is ... i'm running the "2.6.15-**23**-686" kernel. ](*,)  how has this happened? i tried a stab in the dark - copying the modules into the correct folder, and modprobe again, but no luck.

i guess i could just try upgrading to the "2.6.15-25-686" kernel, but i'd rather know what was going wrong. anyone got any ideas?

---

### Post by reztho on 2006-06-20
There was a kernel upgrade a week ago, so the current kernel modules of vmware you have installed don't work. But no problem, there are an updated kernel modules in the repositories. Install the vmware-player-kernel-modules-2.6.15-25 package and you are done.

Edit: I haven't read it all... why exactly you are running the "-23" kernel?... It seems than actually you have installed the package I recommended you. Uninstall it and install the previous version of it.

---

### Post by pellgarlic on 2006-06-20
ok, i've figured out why i'm having problems, but i can't figure out how to fix it, short of just installing the "2.6.15-25-686" kernel.

when i selected "vmware-player" for installation in synaptic, it detected and selected two other dependency packages for installation - "vmware-player-kernel-modules" and , wait for it ... "vmware-player-kernel-modules-2.6.15-**25**"!

try as i might, i couldn't get it to use the "vmware-player-kernel-modules-2.6.15-**23**" package instead. apt-get was the same story. so, i tried installing just the "vmware-player-kernel-modules-2.6.15-**23**" package through synaptic, then did a "sudo dpkg -i vmware-player_1.0.1-4_i386.deb" (i still had the deb in /var/cache/apt), but it didn't work:

```
Selecting previously deselected package vmware-player.
(Reading database ... 107242 files and directories currently installed.)
Unpacking vmware-player (from .../vmware-player_1.0.1-4_i386.deb) ...
vmware-player-v1-0-1 license has already been accepted
dpkg: dependency problems prevent configuration of vmware-player:
 vmware-player depends on vmware-player-kernel-modules; however:
  **Package vmware-player-kernel-modules is not installed.**
dpkg: error processing vmware-player (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vmware-player

```

it seems like the version of vmware-player in the repo expects the "2.6.15-**25**" version of its kernel modules package... as i only have dialup at home, and it's a real pain to have to drag my computer up to my work in order to make use of the broadband there, i'm hoping there's an alternative solution to switching to the "2.6.15-**25**" kernel - it's too big to download at home..

---

### Post by pellgarlic on 2006-06-20
hi reztho - was writing my second post at same time as you i think :)

i am using -23 kernel because i upgraded to it about 2 weeks ago. is there something wrong with it? as mentioned in my second post, i can't easily get new kernels, so i had hoped to "bandage" this one. i can't get the version of vmware-player in the repo to work with the -23 kernel modules package. any ideas? or can i just download a .deb of the new kernel, and the linux-headers for it at work, stick them on a cd, and install them locally?

---

### Post by pellgarlic on 2006-06-20
ok, apologies for keeping replying to my own posts here!

got it working :)

installing the -23 vmware-player kernel sources didn't help, so i reinstalled vmware-player (which automatically reinstalled the -25 vmware-player kernel sources) in lieu of getting the -25 kernel. 

this time, the vmware-player configuration (which ran every time i installed anything in synaptic, cos it never completed properly) worked! the -23 vmware-player kernel sources are still installed, so i guess that's what made the difference.

so my advice to anyone else having a similar problem: either (a) install the appropriate kernel sources after the vmware-player package, and it should conifgure correctly, or (b) install them before installing the vmware-player package.

phew! glad i got that sorted... :)

---

### Post by reztho on 2006-06-20
Yes, it's a possible solution. Just annotate somewhere what packages you need to upgrade the kernel and go here and download the .debs
[http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/)

Although i think synaptic can lock versions or force a package to stay installed. Investigate it. You only need the vmware kernel modules for your current kernel (vmware-player-kernel-modules-2.6.15-23). Perhaps uninstalling the vmware-player-kernel-modules package you can force it since it's a virtual package:

"vmware-player kernel module dependency package
 This empty package allows people to keep their VMware Player kernel modules up-to-date when upgrading their Linux kernel."

---

