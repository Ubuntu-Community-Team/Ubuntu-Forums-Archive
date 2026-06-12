---
title: "USB devices not recognized in Lubuntu 10.04"
date: 2010-05-25
forum: General Help
---

### Post by cmccullough on 2010-05-25
I'm running Lubuntu 10.04 on a Thinkpad T41. I had been running it for a week before realizing that my USB devices (card reader and thumb drive) were not being recognized. I thought that the issue might be related to my aging Thinkpad but I installed the hard drive that is running Slackware and I had no issues with USB devices. I reinserted the hard drive with Lubuntu and was unable to recognize any USB devices.

Has anyone else noticed this issue? If so, is there a fix for this issue?

Thanks for your help.

---

### Post by egeezer on 2010-05-25
I noticed it too, and posted a question a few days ago - no successful answers.  Mine won't acknowledge the presence of the two other OSs (U9.10 and SliTaz) on the drive, either.  I found no mention of this on the Known Issues, or other sufferers, until you!

---

### Post by cmccullough on 2010-05-25
Hmmm....Very strange indeed.

Thanks for responding. It makes me feel better knowing that I'm not going crazy. :-)

Other than this issue, I absolutely love Lubuntu. It's brought some life back to my favorite laptop.

Thanks!

---

### Post by frenziedfemale on 2010-05-25
Have you tried booting up the computer with the usb device already plugged in? I found that my laptop will recognize the drive if it's plugged in when I boot up but not if I plug it in after.

---

### Post by egeezer on 2010-05-25
Didn't work for me, but thanks anyway - at this point I'll try just about anything.  In my case the already-there USB will just  look like another partition.  If your laptop was a double-boot, I think you'd be able to access the other one.

Edited to add information:
My other in-use partitions are sda1 and sda3, but neither one of them is in either /etc/fstab or /etc/mtab.  Clearly that's my problem, but how can I get those files in there?

---

### Post by cmccullough on 2010-05-26
I've tried just about everything I can think of to get the USB devices working.

---

### Post by dino99 on 2010-05-26
reinstall pmount and usbmount with synaptic

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by cmccullough on 2010-05-26
I'll give that a shot. I didn't think to try that.

Thanks!

---

### Post by cmccullough on 2010-05-26
No luck. Still can't seem to mount/access USB devices. 

This reminds of the days back when I first started using Linux....12 years ago. :-)

---

### Post by demosthene1 on 2010-05-26
I had problems with Lubuntu and thought it not ready yet for release. Switched to the officially recognized Xubuntu and love it! I am thinking of installing Xubuntu to my main laptop, not just my netbook. I prefer the default software selections to mainline Ubuntu and I like that Xubuntu does not include the social networking stuff, plus an annoying Ubuntu bug seems to have disappeared.

---

### Post by Jose Catre-Vandis on 2010-05-26
Conversely (to demosthene1) I had the same problem on Xubuntu 10.04. Was fixed by installing and running **hald** on boot. (You can add it to rc.local)

---

### Post by cmccullough on 2010-05-26
Funny you should mention Xubuntu. I just downloaded it and I'm getting ready to replace Lubuntu with it. I have a 10 year old Thinkpad T41 and the lower resource distributions are perfect for it. I really like Lubuntu so I'll check it out, again, after the next update. Give them a little time to work the bugs out.

---

### Post by cmccullough on 2010-05-26
> **Jose Catre-Vandis said:**
> Conversely (to demosthene1) I had the same problem on Xubuntu 10.04. Was fixed by installing and running **hald** on boot. (You can add it to rc.local)

Hmmm...The same issue? Here I am blaming Lubuntu and that might not be correct. 

Thanks for letting us know.

---

### Post by alexfish on 2010-05-26
> **Jose Catre-Vandis said:**
> Conversely (to demosthene1) I had the same problem on Xubuntu 10.04. Was fixed by installing and running **hald** on boot. (You can add it to rc.local)

there are three files named "rc.local"

one in the /etc
one in the /etc/init.d
one in the /var/lib/update-rc.d

can you say which one

thanks in advance

alexfish

---

### Post by cmccullough on 2010-05-26
Is hald a daemon that is already part of the system? I can't seem to find it to get it running.

Thanks again!

---

### Post by MooPi on 2010-05-26
Have you tried to manually mount these drives in terminal or just through your file manager ? 
If not try fdisk to search for drives. ```
sudo fdisk -l
```If the drives are recognized you can create a mount point and mount on this directory.
It should look something like this, ```
/dev/sdb1
```The mount would look like this,with the sdb1 representing a possible drive designation. ```
sudo mount /dev/sdb1 /media/mountpoint
```If you still want to mount this drive without this process you can edit your fstab file.

---

### Post by cmccullough on 2010-05-26
I tried manually mounting them and that did not work.

For what it's worth, I just completed a fresh install of Xubuntu and the problem is not there. I was able to mount my USB devices. Lubuntu is definitely much faster on my T41 but not being able to mount USB devices is a problem.

---

### Post by MooPi on 2010-05-26
The core of Lubuntu desktop is Openbox and this is what I use. If your looking for something light and fast for an old computer Openbox and Ubuntu is the way to go. You mentioned having experience with Slackware so I'm going to assume you know your way around a Linux install. You should try the minimal install CD and add your desktop features after the base command line install.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by demosthene1 on 2010-05-26
After installing Xubuntu, do the update right away. It installs hal
and you are good to go. You will see your usb drives. There is nothing special to do - just do the update.

My ISO was fresh so later ones may include the updates that find usb...etc

---

### Post by chris1379 on 2010-05-26
See if this link helps.
[https://bugs.launchpad.net/bugs/539515](https://bugs.launchpad.net/bugs/539515)
This bug affects Ubuntu and Xubuntu and could affect Lubuntu as well.
Chris

---

### Post by cmccullough on 2010-05-26
Thanks for the link to the MinimalCD. I think I'll give that a shot. Yeah, I've been a Linux-only person for 12 or so years. Most of those years have been with Slackware. The Geek in me is always wanting to try new distributions but I always seem to find my way back to Slackware or a variant of Slackware. Recently, I tried SalixOS. I'm rather impressed with it.

---

### Post by aduplat on 2010-08-30
Hello there:

I found this:

[http://catlingmindswipe.blogspot.com/2010/03/mounting-usb-drives-in-lubuntu.html]("http://catlingmindswipe.blogspot.com/2010/03/mounting-usb-drives-in-lubuntu.html")

And it works for me.

---

### Post by SonicMetalMan on 2010-10-14
This is a general Ubuntu problem that nobody seems to have any real way to fix, but I do have a workaround that did the trick in Linux Mint 9 and Ubuntu 10.04. All the other suggestions that I've read here and other threads have been useless for me.

sudo gedit /etc/modules

add this at the bottom -
hid
usbhid
usb_storage

reboot, enjoy your _functioning_ automount.

---

### Post by angelsguitar on 2011-01-21
> **SonicMetalMan said:**
> This is a general Ubuntu problem that nobody seems to have any real way to fix, but I do have a workaround that did the trick in Linux Mint 9 and Ubuntu 10.04. All the other suggestions that I've read here and other threads have been useless for me.

sudo gedit /etc/modules

add this at the bottom -
hid
usbhid
usb_storage

reboot, enjoy your _functioning_ automount.

Brilliant! Worked like a charm in Lubuntu 10.10.  Thank you very much!

---

### Post by kouhinn on 2011-06-04
Hi,all
I use Ubuntu LTS 10.04 with gnome desktop environment.
**The USB mount worked well before**, but after I fully uninstalled the compiz packages, It's no longer worked.
When I plugin the USB2.0 storage device:
sudo fdisk -l //No info about my device

beffery@beffery-laptop:~$ lsusb  //Seems No info about my device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

cat /var/log/messages  //No info about my USB device

=====I tried :
1. add following lines at the tail of /etc/modules and reboot.
hid
usbhid
usb_storage

2.reinstall pmount and usbmount with synaptic
sudo apt-get install -f  pmount usbmount
sudo dpkg --configure -a

After that,my kindle device is able to be auto mounted with some broken characters.
But my MP3 player still couldn't be recognized.


Could someone give me some help about this ?

---

