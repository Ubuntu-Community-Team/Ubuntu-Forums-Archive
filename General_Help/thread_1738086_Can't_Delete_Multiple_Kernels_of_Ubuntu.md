---
title: "Can't Delete Multiple Kernels of Ubuntu"
date: 2011-04-24
forum: General Help
---

### Post by Richiegs on 2011-04-24
After I used Ubuntu Tweak to delete several kernels (versions) of Ubuntu under Package Cleaner, all these deleted kernels in Ubuntu still show up whenever I start my PC as if nothing was deleted. Does anyone know how to fix it? Thank you very much in advance.

---

### Post by Atamisk on 2011-04-24
did you run:
```
sudo update-grub
```
after deleting the old kernel? Grub doesn't update its list automatically, so after any add/remove, this command must be run, if i'm not mistaken. FYI, the installer runs update-grub automatically, but apparently the removal process doesn't.

---

### Post by Vaphell on 2011-04-24
try
```
sudo update-grub
```

---

### Post by KegHead on 2011-04-24
Hi!

You could also check;

system...admin...synaptic

KegHead

---

### Post by Richiegs on 2011-04-24
> **Vaphell said:**
> try
```
sudo update-grub
```

 I tried sudo update-grub, but it did not update to a new list.

---

### Post by Richiegs on 2011-04-24
> **KegHead said:**
> Hi!

You could also check;

system...admin...synaptic

KegHead

What is KegHead? Is it a software in Synaptic Package Manager? I could not find it in Synaptic Package Manager.

---

### Post by brpylko on 2011-04-24
```
sudo remove all other ubuntu kernels
``` ;)

try starting up GRUB then pressing (is it C or E?) to edit the commands and delete the startup options.

---

### Post by KegHead on 2011-04-24
Hi!

Yes, your search parameter will be "linux".

KegHead

---

### Post by Richiegs on 2011-04-24
I no longer am able to delete those kernels again in Ubuntu Tweak even thought it still shows up whenever I start my PC.

---

### Post by KegHead on 2011-04-24
Hi!

See post #8.

KegHead

---

### Post by Richiegs on 2011-04-24
> **KegHead said:**
> Hi!

Yes, your search parameter will be "linux".

KegHead
Did you mean "linux-keghead'? Nothing show up.

---

### Post by WorMzy on 2011-04-24
Copy and paste the output from the following command here:

```
ls -l /boot
```

Also, do you have more than one installation of Ubuntu on your PC?

---

### Post by Richiegs on 2011-04-24
> **WorMzy said:**
> Copy and paste the output from the following command here:

```
ls -l /boot
```Also, do you have more than one installation of Ubuntu on your PC?

Yes, I have Windows XP and Ubuntu in my PC.

---

### Post by KegHead on 2011-04-24
Hi!

No,just:

"linux"

KegHead

---

### Post by Richiegs on 2011-04-24
> **KegHead said:**
> Hi!

Yes, your search parameter will be "linux".

KegHead

Did u mean the name of the software is called "Linux"? Thanks for your help

---

### Post by KegHead on 2011-04-24
Hi!

Yes,

Type in linux

KegHead

---

### Post by Richiegs on 2011-04-24
> **KegHead said:**
> Hi!

No,just:

"linux"

KegHead

By the way what does "Linux" do?

---

### Post by MooPi on 2011-04-24
I seems as if the Ubuntu Tweak left something behind ? You could just do it the old fashion way and navigate to the boot folder and delete any info regarding older kernel.
From terminal ```
gksudo nautilus /boot
``` Then all you need do is remove old kernel and the associated files
```
abi-2.6.35-**-generic
config-2.6.35-**-generic
initrd.img-2.6.35-**-generic
System.map-2.6.35-**-generic
vmcoreinfo-2.6.35-**-generic
vmlinuz-2.6.35-**-generic
```
Be sure to leave at least one previous kernel to fall back to in case of problems with a current kernel.
Now issue the command 
```
sudo update-grub
```

---

### Post by KegHead on 2011-04-24
Hi!

Linux is like a manager...it manages many parameters such as heat...disks etc.

[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

KegHead

---

### Post by Timmer1240 on 2011-04-24
To remove all the unused Linux Kernel headers, images and modules, simply run this command: dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

---

### Post by Richiegs on 2011-04-24
> **MooPi said:**
> I seems as if the Ubuntu Tweak left something behind ? You could just do it the old fashion way and navigate to the boot folder and delete any info regarding older kernel.
From terminal ```
gksudo nautilus /boot
``` Then all you need do is remove old kernel and the associated files
```
abi-2.6.35-**-generic
config-2.6.35-**-generic
initrd.img-2.6.35-**-generic
System.map-2.6.35-**-generic
vmcoreinfo-2.6.35-**-generic
vmlinuz-2.6.35-**-generic
```Be sure to leave at least one previous kernel to fall back to in case of problems with a current kernel.
Now issue the command 
```
sudo update-grub
```

The version that I want to delete is 2.6.32-21, but it is not in the boot folder

---

### Post by KegHead on 2011-04-24
Hi!

What are you showing in:

system..admin...system monitor...system.

Post a screenshot if you can.

KegHead

---

### Post by flemur13013 on 2011-04-24
> **Richiegs said:**
> After I used Ubuntu Tweak to delete several kernels (versions) of Ubuntu under Package Cleaner, all these deleted kernels in Ubuntu still show up whenever I start my PC as if nothing was deleted. Does anyone know how to fix it? Thank you very much in advance.

Some of the responses are telling, or trying to tell, you how to remove the kernels: I gather they're removed but they still show up in the boot menu.

If "update-grub" isn't working, make a backup copy then edit /boot/grub/grub.cfg (the boot menu is here) and remove the entries you don't want. (Or for older ubuntu using grub1, edit the file menu.lst).  Suposedly you shouldn't do this, and your editing changes to grub.cfg might disappear from another "update", but it's a lot easier than doing it the right way.

---

### Post by KegHead on 2011-04-24
Hi!

Have you performed post #8?

KegHead

---

### Post by domu on 2011-04-26
What version of ubuntu are you using?

You can try my remove-kernel script which can be run (with sudo) from a terminal window (or if you have Ubuntu Server i.e. no GUI). See TimeDicer [http://www.timedicer.co.uk](http://www.timedicer.co.uk) - in the 'My Programs' section. It's easier than synaptic, here is the help:
```
Shows installed Linux kernels in a Debian-based distro, and can remove
superfluous ones, including related packages, updating Grub appropriately. Does
not require a GUI. You are prompted before any dangerous stuff happens, and it
will not allow removal of the kernel that is currently in use, but should still
be used with care: once a kernel is gone, it's gone!

Tested under Ubuntu 10.04 and 10.10. Does not work under Lubuntu (because
kernel packages are differently named).

Usage    : remove-kernel [options] [kernelnumbertoremove-filter]
Example 1: ./remove-kernel              # list kernel packages and exit
Example 2: ./remove-kernel 2.6.32-24    # remove 2.6.32-24 kernel
Example 3: ./remove-kernel 2.6.32       # remove all 2.6.32-* kernels
```

---

### Post by 73ckn797 on 2011-04-26
The simple way that I do it is to go into Synaptic Package manager and look for the linux-* kernel listings. Then select those for complete removal that are not what you want, such as: linux-headers-(version number), linux-image-(version number) & linux-image-(version number)-generic (or also pae).

Then run in terminal:
```
sudo update-grub
```Works every time for me.

---

