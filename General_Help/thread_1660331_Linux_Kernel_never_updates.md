---
title: "Linux Kernel never updates?"
date: 2011-01-05
forum: General Help
---

### Post by PsyclonJohn on 2011-01-05
Is this happening to other people too?

The past few weeks now (every day) Ubuntu tries to update the Linux Kernel, but it always says it cannot and goes back to the one I current have. 

Is this a known bug?

---

### Post by wojox on 2011-01-05
Open a terminal and run:

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

See if that does anything.

---

### Post by PsyclonJohn on 2011-01-05
I've given it a try, and it seems like it was going well for the first few and at the end I received the following: 

The following packages have unmet dependencies:
 bsd-mailx : Depends: default-mta or
                      mail-transport-agent
E: Unmet dependencies. Try using -f.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 bsd-mailx : Depends: default-mta or
                      mail-transport-agent
E: Unmet dependencies. Try using -f.

Should I try what it says? ->  'apt-get -f install'

What exactly would that do?

---

### Post by cgroza on 2011-01-05
Try and if it works it might fix the dependency issue.

---

### Post by a-user on 2011-01-05
don't do the dist-upgrade!!!

except you want to become natty alpha/beta tester.

---

### Post by PsyclonJohn on 2011-01-05
I have not tried it yet, but I have this red circle on the top panel, when I click it 'Install All Updates" it says "1 broken package found" or something like that. 

> don't do the dist-upgrade!!!

except you want to become natty alpha/beta tester.

I hope it's not too late, last time I tried upgrading through Wubi, Grub stopped working. (upgrading from 9.10 to 10.04)

---

### Post by matt_symes on 2011-01-05
Hi

> don't do the dist-upgrade!!!

except you want to become natty alpha/beta tester.

Don't you have to update your sources.list before it will upgrade to a new distribution (i.e 10.04 -> 10.10) version? I might be wrong here though. I always perform a fresh install.

Kind regards

---

### Post by deserthowler on 2011-01-05
> **PsyclonJohn said:**
> Is this happening to other people too?

The past few weeks now (every day) Ubuntu tries to update the Linux Kernel, but it always says it cannot and goes back to the one I current have. 

Is this a known bug?

What are you using to do your updates, Update manager, synaptic, aptitude or apt?
Earl

---

### Post by snowpine on 2011-01-05
> **a-user said:**
> don't do the dist-upgrade!!!

except you want to become natty alpha/beta tester.

Incorrect; "upgrade" alone will not update the kernel, so "dist-upgrade" is necessary in this case. Type 'man apt-get' for more details.

---

### Post by lithopsian on 2011-01-05
Have you asked your Ubuntu to upgrade to a new version recently?  Or messed with adding new sources?  What you describe should not normally happen all on its own, and maybe before fixing it you should be sure you want to to.  Out of interest, which kernel do you have right now and which one is it trying to install?

---

### Post by PsyclonJohn on 2011-01-05
> **deserthowler said:**
> What are you using to do your updates, Update manager, synaptic, aptitude or apt?
Earl

Update Manager

> Don't you have to update your sources.list before it will upgrade to a  new distribution (i.e 10.04 -> 10.10) version? I might be wrong here  though. I always perform a fresh install.Yes. I read afterwards that grub doesn't update when using Wubi. Not sure if it was a bug in that edition or what. 

> Have you asked your Ubuntu to upgrade to a new version recently?  Or  messed with adding new sources?  What you describe should not normally  happen all on its own, and maybe before fixing it you should be sure you  want to to.  Out of interest, which kernel do you have right now and  which one is it trying to install?     I have not tried to upgrade, and my current is 2.6.35-22-generic. 

My package manager won't work at all now.. says it's broken, but gives me "bsd-mailx" I'm not sure if it has to do with me trying to install a mail server on LAMP earlier today, but the kernel problem has been going on for a few weeks now.

If this can't be fixed, I'll make a backup and re-install. There seems to be a problem with Tasksel as well.

---

### Post by PsyclonJohn on 2011-01-05
Ok, I tried to re-install bsd-mailx. I'm also realizing what it's trying to do. I'm pretty sure when I try to install something, it thinks I have the latest kernel when I don't. After it finds out I don't, it says going back to how settings were before I hit update or install.

This is what I got after I tried re-installing:

E: linux-image-2.6.35-23-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.35-24-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-headers-2.6.35-23-generic: subprocess installed post-installation script returned error exit status 2
E: linux-headers-2.6.35-24-generic: subprocess installed post-installation script returned error exit status 2
E: linux-headers-generic: dependency problems - leaving unconfigured

---

### Post by wojox on 2011-01-05
So 

```
sudo dpkg-reconfigure -a
```

```
sudo apt-get install -f
```

Doesn't do anything?

---

### Post by a-user on 2011-01-06
> **snowpine said:**
> Incorrect; "upgrade" alone will not update the kernel, so "dist-upgrade" is necessary in this case. Type 'man apt-get' for more details.
no, what i said is correct!

NEVER do dist-upgrade if you don't want become beta tester for the next release!

if the kernel does not get updated with apt-get upgrade then its due to some dependecies issues. i don't know the command line parameters to fix this but you can use synaptic to make the update.

but DON'T use dist-upgrade!!! it is not ment to upgrade such things!!! it is to upgrade your whole distribution to the next release! this includes the next unfinished one!!!

[b]
so please stop proposing others to use dist-upgrade to fix thigns. it is the very most reason people are ****ing up there system!!![/b]

---

### Post by matt_symes on 2011-01-06
Hi

> NEVER do dist-upgrade if you don't want become beta tester for the next release!

That's simply not true. You _are_ getting confused. You _do_ need to update your sources.list _first_.

```
matthew@matthew-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
matthew@matthew-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matthew@matthew-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
matthew@matthew-laptop:~$ 
```

See man update-manager with the --dist-upgrade switch

Kind regards

---

### Post by piquat on 2011-01-06
As a slightly confused newbie, am I getting this right:

If you add the repo for the upcoming release to your sources.list, dist-upgrade will see that and upgrade you to that distro.

If you don't have that in your sources list it just tries to get you the most current kernel for your distro.

That right?

---

### Post by matt_symes on 2011-01-06
Hi

> **piquat said:**
> As a slightly confused newbie, am I getting this right:

If you add the repo for the upcoming release to your sources.list, dist-upgrade will see that and upgrade you to that distro.

If you don't have that in your sources list it just tries to get you the most current kernel for your distro.

That right?

Yes. The easiest way to do it from the command line is to use update-manager 

Kind regards

---

### Post by TNT1 on 2011-01-06
apt-get dist-upgrade _does not_ upgrade you to another distribution.

---

### Post by a-user on 2011-01-06
seems i must apologies that i forgot about adding the sources to the list.

sorry for confusing others.

---

### Post by snowpine on 2011-01-06
> **piquat said:**
> As a slightly confused newbie, am I getting this right:

If you add the repo for the upcoming release to your sources.list, dist-upgrade will see that and upgrade you to that distro.

This part is slightly incorrect; the recommended method for upgrading Ubuntu to a new release [is described here]("https://help.ubuntu.com/community/UpgradeNotes") and does **not** involve manually editing your sources.list or using the dist-upgrade command. While it is possible that method might work some of the time (many Debian users do it that way) it is unsupported and unnecessarily complex (all you actually need to do is click one button in the Update Manager).

---

### Post by matt_symes on 2011-01-06
Hi

> This part is slightly incorrect; the recommended method for upgrading Ubuntu to a new release is described here and does not involve manually editing your sources.list or using the dist-upgrade command. While it is possible that method might work some of the time (many Debian users do it that way) it is unsupported and unnecessarily complex (all you actually need to do is click one button in the Update Manager).

I would go with that. Occam's razor. 

Kind regards

---

### Post by piquat on 2011-01-06
Thanks for the explanation.  That command has been kind of scary to me, out of ignorance I guess.

---

### Post by PsyclonJohn on 2011-01-06
Any new recommendations?

I can't install anything at all, neither any new updates. Just tried to download 7zip from Software Manager and it failed.

```

installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 222648 files and directories currently installed.) 
Preparing to replace dpkg 1.15.8.4ubuntu3 (using .../dpkg_1.15.8.4ubuntu3.1_i386.deb) ... 
Unpacking replacement dpkg ... 
Processing triggers for python-central ... 
Processing triggers for man-db ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--unpack): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 man-db 
Setting up linux-headers-2.6.35-23-generic (2.6.35-23.41) ... 
Examining /etc/kernel/header_postinst.d. 
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic 
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       virtualbox-ose (3.2.8)...         [ OK ] 
 *       nvidia-173 (173.14.28)...         [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1 
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-23-generic.postinst line 110. 
dpkg: error processing linux-headers-2.6.35-23-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-headers-2.6.35-24-generic (2.6.35-24.42) ... 
Examining /etc/kernel/header_postinst.d. 
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic 
 * dkms: running auto installation service for kernel 2.6.35-24-generic         
 *       virtualbox-ose (3.2.8)...         [ OK ] 
 *       nvidia-173 (173.14.28)...         [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1 
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-24-generic.postinst line 110. 
dpkg: error processing linux-headers-2.6.35-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up dpkg (1.15.8.4ubuntu3.1) ... 
dpkg: dependency problems prevent configuration of linux-headers-generic: 
 linux-headers-generic depends on linux-headers-2.6.35-24-generic; however: 
  Package linux-headers-2.6.35-24-generic is not configured yet. 
dpkg: error processing linux-headers-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic 
Warning: No support for locale: en_US.utf8 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic 
 * dkms: running auto installation service for kernel 2.6.35-24-generic         
 *       virtualbox-ose (3.2.8)...         [ OK ] 
 *       nvidia-173 (173.14.28)...         [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.35-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up man-db (2.5.7-4) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic 
Warning: No support for locale: en_US.utf8 
^CFailed to create initrd image. 
dpkg: error processing linux-image-2.6.35-23-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.35-24-generic; however: 
  Package linux-image-2.6.35-24-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.35.24.28); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 

```

---

### Post by PsyclonJohn on 2011-01-06
> **wojox said:**
> So 

```
sudo dpkg-reconfigure -a
``````
sudo apt-get install -f
```Doesn't do anything?

Ok, so I'm not sure what the first one was all about, but I kind of swifted through it accepting about everything that it asked. 

When I did the second code, I received this :

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by matt_symes on 2011-01-07
Hi

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
```

Make sure synaptic package manager, software centre and update manager are all closed before running sudo apt-get install -f

Kind regards

---

### Post by PsyclonJohn on 2011-01-09
> **matt_symes said:**
> Hi

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
```Make sure synaptic package manager, software centre and update manager are all closed before running sudo apt-get install -f

Kind regards

Okay, I just booted up my computer and touched nothing. I did what you said and I received this (last line): 

```
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dino99 on 2011-01-09
close everything
open a terminal:

sudo rm /var/cache/apt/archives/*

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo apt-get install ubuntu-desktop

---

### Post by PsyclonJohn on 2011-01-09
Thanks everyone, but I think I'm just going to re-install Ubuntu. Nothing seems to be working out.

---

