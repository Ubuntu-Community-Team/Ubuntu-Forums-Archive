---
title: "Error booting after installing some packages"
date: 2010-01-14
forum: General Help
---

### Post by wakaru00 on 2010-01-14
To make a long story short, I am quite new to ubuntu and I was given a thin client (Siemens **[Futro S400]("http://uk.ts.fujitsu.com/rl/servicesupport/techsupport/ProfessionalPC/ThinClients/FutroSxx/FutroS400.htm")**) by a friend of mine with the idea of converting it in my home server to manage my downloads and my file sharing at home.

I the got a 6GB Hitachi microdrive, where I managed to install the server edition booting Koala Karmic NetBoot through a USB flashdisk. 

Everything was up and running after a few tries (Grub did not seem to like the microdrive disk I think, and it finally installed OK) and in no time I had managed to set a static IP, and a SSH server in order to get rid of the keyboard and screen monitor connected to the thin client.

Once I was controlling the server though SSH I decided to start installing some of the applications or packages that I intended to use in it, hence I used the following:

```

sudo su -
apt-get clean
apt-get update
apt-get install linux-image-server samba cups wget p7zip-full portmap nfs-kernel-server nmap mc  qemacs-nox unp arj unrar unzip usbmount mldonkey-server
apt-get clean
```I was asked if I wanted to run the mldonkey server automatically or manually, so I selected manually. No issues or error were shown on screen during the process. Then I decided to reboot the system.

This is the updated GRUB menu that I have after the packages were installed:

[IMG]http://freespace.virgin.net/big.xuxo/ubuntu/Grub_Menu_2.png[/IMG]


This is the error that I get when trying to boot with kernel 2.6.31.17

[IMG]http://freespace.virgin.net/big.xuxo/ubuntu/Error_2.6.31.17.Generic.Pae.png[/IMG]

The system seem to stay hung at that point (though I've only waited for a couple of minutes)

If I try to boot using the old kernel (2.6.24.26) I get the folowing error output,:

[IMG]http://freespace.virgin.net/big.xuxo/ubuntu/Error_2.6.24.26.Generic.png[/IMG]

However this one allows me access to the hard drive logged in as root so I can browse the filesystem.

I've also tried both recovery modes but the end result is exactly the same, however I get more information displayed on screen during the booting process.

I have done some research in order to find out where the problem is, but I am completely lost as to what I should do.

I know I could re-install the sytem again, however the very moment I install the packages again the same issue it is likely to re-occur, therefore I would rather know the reason why I got the error in the first place and sort it out this other way.

I hope there is someone out there who understand what the problem is and can shed a light on the issue to put me in the right direction to sort it out.

Thanks very much in advance :)

---

### Post by mk1w86 on 2010-01-14
> apt-get install linux-image-server

Why exactly are you installing another kernel?  I think that is most likely the package causing the problem although I am sure someone else will correct me if I'm wrong. ;)

If you do reinstall you could try installing the packages one at a time then you would be able to pinpoint which one is causing the problem.

Also for a server you might prefer to use Ubuntu 8.04 because it is an LTS release or Lucid Lynx (10.04) when it is released which will also be an LTS release.  For information on LTS releases have a look here:

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by wakaru00 on 2010-01-15
Thanks mk1w86 for making me aware of the Long Term Support releases, which I did not know about.
 
> **mk1w86 said:**
> Why exactly are you installing another kernel? I think that is most likely the package causing the problem although I am sure someone else will correct me if I'm wrong. ;)
 
Well I guess that I thought that it would be appropriate to update the kernel as well. O:) 
 
> **mk1w86 said:**
> If you do reinstall you could try installing the packages one at a time then you would be able to pinpoint which one is causing the problem.
 
I guess that will ultimately be the way to go, however I guess that I'll have to be a bit more cautious next time by making a full system backup every now and then to ensure I do not have to start from scratch again if something similar happens.
 
Thanks for your help. I am still looking if someone else has any other thoughts or knows how to resolve it (without having to re-install the system) even though I am know inclined to re-install the system but I'll use ubuntu-8.04.3-server-i386 this time.

---

### Post by wakaru00 on 2010-01-15
I think I've read of a possible solution [HERE]("http://ubuntuforums.org/showthread.php?t=1366591") for a problem that seems to be similar, therefore I'll try that up this evening when I get home and se what happens O:)

---

### Post by mk1w86 on 2010-01-15
> Well I guess that I thought that it would be appropriate to update the kernel as well.O:)


You might know this but to keep your system up to date run:

```
sudo apt-get update && sudo apt-get upgrade
```

Just be cautious if it updates the kernel. ;)

If you reinstall the system, do not install the linux-image-server package because there are many different types of kernel you can install and the kernel installed by this package is probably not suitable for what you want.  So to sum up just keep the default kernel that comes with Ubuntu Server and run the command above to keep everything updated. :D

---

### Post by wakaru00 on 2010-01-17
Tried the fsck command but that did not fix the issue, hence I finally re-installed Ubunto, but this time 8.04 :)

A backup of the system (/dev/sda) has just finished as we speak ([using dd | gzip]("http://www.linuxweblog.com/dd-image")) just in case O:)

Thanks very much for your advice. I'll make sure I take more caution when updating the kernel :)

---

