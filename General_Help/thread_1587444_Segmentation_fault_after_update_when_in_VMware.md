---
title: "Segmentation fault after update when in VMware"
date: 2010-10-03
forum: General Help
---

### Post by ramicohen on 2010-10-03
Hi

I have been a Windows user for many years but heard lots of good things about Ubuntu and wanted to give it a shot. I have a VMware ESXi 4.1 server so I created a new VM (Ubuntu desktop 32-bit), downloaded the Ubuntu 10.4 32-bit desktop image, mounted it, and started the installation. Everything worked fine and I got a working Ubuntu system. I created a snapshot just in case I need to get back to this position.

I then saw a prompt from Update Manager and decided to update everything it told me to, which is 300 updates. At the end, I was asked to restart and I did. At that point, the system was not willing to start again. Here is what I get (... stands for omitted text):

Segmentation Fault
Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
- check root delay ...
- check root ....
- missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/... does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
...


I have no clue what to do at this point. I tried going back to the snapshot a few times but always ended up in the same state after installing updates. I tried installing VMware tools before the running the update but it didn't make a difference.

Any ideas? 

Thank you

Rami Cohen

---

### Post by TheCleaner on 2010-10-06
I have the EXACT same problem.

Hoping someone has an answer...

---

### Post by Patrick Debois on 2010-10-06
I'm experiencing the same problem. 

When you were upgrading your kernel: 
  [FONT=-moz-fixed][http://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/](http://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/)   

I'm doing preseed and it always take the latest kernel, you can override it with: 

d-i base-installer/kernel/override-image string linux-image-2.6.32-21-generic' in my preseed file

[/FONT]

---

### Post by TheCleaner on 2010-10-06
> **Patrick Debois said:**
> I'm experiencing the same problem. 

When you were upgrading your kernel: 
  [FONT=-moz-fixed][http://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/](http://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/)   

I'm doing preseed and it always take the latest kernel, you can override it with: 

d-i base-installer/kernel/override-image string linux-image-2.6.32-21-generic' in my preseed file

[/FONT]


So that fixed it for you?  I'm concerned about dealing with this everytime someone runs UPDATE on a Ubuntu VM on our ESX servers.

---

### Post by ramicohen on 2010-10-06
I isolated the problem to the kernel update which is in line with what Patrick points out. When you run update manager, deselect the component "linux-image-2.6.32-25-generic" which is under optional updates. This will also deselect two required updates "linux-generic" and "linux-image-generic". Update everything else and all is well.

---

### Post by TheCleaner on 2010-10-07
Yeah...I've got a ticket with vmware as well because I don't want to deal with this on every vm.

---

### Post by Techn0crat on 2010-10-12
Any updates on this?

---

### Post by jlmallard on 2010-10-18
Just experienced the same issue with ESXi 4.1 and a 32bit Ubuntu 10.0.4 LTS Desktop VM.
 
Kernel 2.6.32-25 installation causes a boot up segmentation fault.
Currently, I do not install updates using Update Manager for the following:
 
grub-common
grub-pc
linux kernel 2.6.32-25
linux generic kernel
 
Thanks for your confirmation, guys! Great help to know that you are not alone!

---

### Post by hennys on 2010-10-21
same here on ESX4 with Kernel 2.6.32-25.

Also segmentation fault. 

I am gonna raise an issue with vmware also.

Regards,

Hen

---

### Post by hennys on 2010-10-21
Got a reply from VMWare that it's a 3rd party guest issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659422](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/659422)

Now we have to wait for a fix ...

Kind regards,

Hen

---

### Post by Techn0crat on 2010-10-21
Thanks hennys

---

### Post by thany on 2010-11-03
Same problem here, but obviously the evil has already been done... What do I do to revert to the old kernel? Or whatever workaround?

Reinstall would be the third time I try 10.04, and 10.10 isn't working at all...

---

### Post by rainbow7of9 on 2010-12-01
Hello,

we had the same problem in our company and I found a workaround for this.
In ESXi 4.1 vSphere Client choose the VM Ware-Machine which starts with the "segmentation fault"
and go to the machine settings.
There you have to change the "host operating system" from "Ubuntu 32 bit" to "Another"
"Version 32 Bit".
VMI must also be deactivated.

After that run your Machine and start with the dist-upgrade.
Following the finished update reboot your system and it should work now.

---

### Post by Daywalker55 on 2010-12-27
Are there any news to that topic?
The 'workaround' from rainbow7of9 is not working for me.

---

### Post by ramicohen on 2010-12-28
It didn't work for me either. I just gave up and switched to VirtualBox.

---

### Post by anaspeople on 2011-01-31
> **ramicohen said:**
> It didn't work for me either. I just gave up and switched to VirtualBox.

It didn't work for me either I just hope someone manages to solve it soon...

---

### Post by cbkm on 2011-02-03
Worked for my colleague here - has to be set to Other/Other and not Ubuntu/Other.... (or some-such!) :-)

---

### Post by MaximumFish on 2011-03-18
I've just had the same problem on a bunch of production VMs after upgrading the host to ESXi 4.1. Luckily changing the machine type to other/other fixed it for me, too.

What I did notice is that it didn't seem to affect the x86 version of 10.10 or the x64 version of 10.04. Only 10.04 x86 had problems. Very strange!

---

### Post by Shesoff on 2011-04-07
I have the same problem. 
Changing the machine type not fixed it. :( Server booting if disable acceleration (Edit Settings, Options tab, Advanced - General, click Disable acceleration), but work very slow.
server VMware ESXi 4.1
virtual machine Ubuntu Server 10.04

---

### Post by jaredhallen on 2011-04-07
I had this same issue with ESXi 4.1 and 10.04 x86.

It seems that there's an incompatibility between ESXi 4.1 and the initramfs for the newer 2.6.32 kernels. Apparently, the 2.6.35 series (and newer) aren't affected.

I was able to boot my machine by disabling acceleration (as mentioned above), but because I'm still using the lucid repositories (in /etc/apt/sources.list), a dist-upgrade didn't get me the newer kernel series. What I ended up doing was adding the kernel ppa and installing 2.6.38-generic:

```

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo apt-get install linux-headers-2.6.38-1-generic linux-image-2.6.38-1-generic

```After this, I was able to turn acceleration back on, and everything seems to be working fine. Alternatively, you could probably just change your repositories in sources.list to maverick, and then run a dist-upgrade.

Thanks for all the help, guys!

---

