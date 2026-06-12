---
title: "GRUB - excluding a hard drive"
date: 2011-06-15
forum: General Help
---

### Post by kroq-gar78 on 2011-06-15
Hello Ubuntu Forums Community,

I have an Ubuntu Server 10.04 on an external 2TB USB HDD. Whenever I bootup, GRUB shows me all of my kernels for my server, then Vista (YUCK) and Ubuntu Desktop on my laptop's internal HDD. I don't use my laptop's HDD when I use the server because the server is completely on the external drive, so how do I get rid of those extra entries? 

The main reason I don't want those extras is because I MIGHT (for whatever reason) need to move it from one computer to another (through usb), and if it can't find the UUID of the previous laptop's drives, it won't be able to boot up (from my previous experiences with external HDD's and GRUB).How do I make it so that whenever my server gets a kernel update, it  doesn't include all of the OS's on my laptop's drive (I'm pretty sure  that GRUB gets updated every kernel update; correct me if I'm wrong).

Tell me if you need any more info.

Sincerely,
kroq-gar78

---

### Post by oldfred on 2011-06-15
Do you have grub2's boot loader for the server in the external drive? And the loader for your desktop in the internal drive with the external set to boot first from BIOS?

You can turn off os-prober if you want and it will not search for other installs. If you want just some other installs you can manually add to 40_custom to boot or even just chain load to another MBR. I use that just when I have forgotten to hit f12 and have booted wrong MBR and want to switch without having to fully boot & reboot.

I still do it manually, but there is a new gui tool, link in drs305's thread:
Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by kroq-gar78 on 2011-06-15
oldfred,

Thanks for the info about GRUB and the link to drs305's HOWTO. I'm using a pure command line server (don't plan to install GUI anytime soon - too much space&RAM) but all my other computers are GUI's, so I can't use the GUI program to customize it, but I'll try it out on some of my other computers. 

As for os-prober: I thought I needed to do something with that, but I didn't know what. Thanks, I did
```
sudo chmod a-x /etc/grub.d/30_os-prober
```
but don't I need to update grub or something now?

Thanks for the help.

---

### Post by drs305 on 2011-06-15
> **kroq-gar78 said:**
> 
As for os-prober: I thought I needed to do something with that, but I didn't know what. Thanks, I did
```
sudo chmod a-x /etc/grub.d/30_os-prober
```
but don't I need to update grub or something now?

Thanks for the help.

You always have to run "sudo update-grub" to update grub.cfg (and the menu) unless you have edited that file manually. 

If you want to tinker with files via editing the scripts, you might find something of use in the [G2 Tittle Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") thread. When G2 first arrived I wrote up some ways to tweak the Grub menu (title changes, excluding OS's, etc). 

The arrival of GUI apps (especially Grub Customizer) has eliminated the need for most of them, but once in a while they still come in handy.

---

### Post by kroq-gar78 on 2011-06-15
So, does changing the permissions count as a manual file edit, or does  it require  a update-grub? Can i still use a GUI for GRUB configuration  through another computer (server has no gui)?

Also, I have GRUB on my external drive AND internal drive. I want the external to exclude the OSes from the internal.

Thanks for the help.

---

### Post by oldfred on 2011-06-15
The grub.cfg will not exclude the os-prober found files until you run the update. All changes to scripts or grub files require the sudo update grub. I still make changes and forget to run it and wonder why it has not changed the menu when I reboot.

If you want the same on both drives you have to edit both and run the update on both to exclude the other installs.

---

### Post by oldfred on 2011-06-15
Depending on how grub is installed to the external you may want to run this:

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

And if not sdb drive, then run this:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by kroq-gar78 on 2011-06-15
also, will disabling os-prober remove all of my server kernels from the GRUB list too? or will it just be the other OSes on the server's laptop? Sorry, for the lot of questions.

EDIT: Thanks for all the help guys! it now works! Marking thread as solved...

---

