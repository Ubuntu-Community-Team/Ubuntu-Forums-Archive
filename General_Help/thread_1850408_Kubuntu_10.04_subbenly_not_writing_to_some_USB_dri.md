---
title: "Kubuntu 10.04 subbenly not writing to some USB drives and shell seems to be crashing"
date: 2011-09-26
forum: General Help
---

### Post by ubunutucyclotron on 2011-09-26
Hi all.

Dont understand how this happens, one day things are working and another its just suddenly a problem. Both these problems just started up, I think after security updates but you never know. I have an out of the box installation.

The most recent problem is now suddenly my perfectly working auto mount USB drives in read write mode seems to have broken down somewhat. First my flashdrive was now suddenly read only so I worked around the problem by re-formatting it as NTFS (wanna be windows readable too). Now I plug in my phone and the sdcard is also read only. This problem is about a week old. I cant re-format, my phone needs that particular filesystem! I searched around cannot find answers that work and cannot find answers as to why a perfectly working sub-system suddenly stops working - I swear its the updates! One guy mentioned pmount and this page [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) as a fix but why must I install new software when it was working and that pages only other clue is the section "USB-Device is, or become suddenly read only without errors" and gives a one line answer about the GID being wrong. How could the GID become wrong? What is a GID and how do I find it? Also where is that page for Kubuntu? All the instructions are about Nautilus and other non KDE apps. 

Oh yea one thing I do think is very significant, previously my USB devices would be in /media/thedriveslabel with my phone's sdcard showing up as /media/disk and now they all are in /media/usb0. How did this change? What caused this? Reversing this would probably fix the problem. Another new problem is now suddenly when unmounting (via the device notifier icon on the taskbar) the devices that I now cant write to I get an error message that the device is in use! Even if I close all open browser windows and I have (obviously) not made any writes to the drive! This is so windows... How did this change? What caused this?

Second problem I'm just throwing in as evidence that things suddenly stop working and dont come right even with more updates. Months ago my KDE shell just started crashing back to the login screen. No warning, no chance to save, no saving of the session, no clues in the text screen behind the shell of what is happening, it just closes down the shell and back to the login screen in a couple seconds. I have since re-installed Kubuntu and its still doing it every couple of weeks but it never did it when I first installed it so it must be some tainted update. Anyone ever hear of this one and how to get it right?

Please help, becoming very frustrated as I just cannot understand how things that were fine just stop working properly. Updates....?

Daryl

---

### Post by ubunutucyclotron on 2011-09-28
Adding in /media/usb0 to my searches has brought up more results relating this this problem such as. 

[http://ubuntuforums.org/showthread.php?t=1484042](http://ubuntuforums.org/showthread.php?t=1484042)
[http://ubuntuforums.org/showthread.php?t=1467117](http://ubuntuforums.org/showthread.php?t=1467117)
and
[http://ubuntuforums.org/showthread.php?t=1336847](http://ubuntuforums.org/showthread.php?t=1336847)

I've uninstalled usbmount and pmount and then it doesn't mount the drives at all. With usbmount the permissions are read only. I've installed pysdm and it didn't help... Any ideas?

---

### Post by audeojude on 2011-10-17
This is becoming a endemic issue. I think there has been a security update or something that has caused this behaviour. I am having read only problems with sata drives, usb drives etc... As I look around the forums I am finding more and more people reporting this exact same problem.

Lots of experts are telling people if its ntfs or fat drives to scan them with chkdsk /f to repair issues that would cause the Linux kernel to only mount  read only. However of the four drives I have checked only one had errors and even when fixed, my 11.10 installation will not mount the drives read write.

My guess is someone blew it big time and pushed out a security fix or kernel with major issues.

---

### Post by audeojude on 2011-10-17
let us know if someone has a solution to this.

---

### Post by audeojude on 2011-10-22
Ok I have fixed mine.. 

It seems to be a problem in ntfsprogs and the kernel. I have tried a couple kernels and no luck. Then I installed ntfs-3g which automatically un-installed and replaced ntfsprogs and my read write ability on my usb drives and even my ntfs sata drives came back.

so the solution was to go 

sudo apt-get install ntfs-3g 

allow it to uninstall ntfsprogs

it takes a while to un-install and install as it has to recompile a bunch of kernel drivers. I had upgraded to the latest stock 3.0.13 kernel in updates just before trying this.


what a pita though. in changing permissions and playing with settings I killed my ability to log into my user directory. I had to delete that and create a totally fresh user directory and then copy back into the new one all my data and application configurations. 

Mostly Ubuntu just works which is what I like. Years ago I loved digging under the hood and customising and tweaking. Nowadays I just want my applications and Internet to work.

---

### Post by ubunutucyclotron on 2012-01-12
Hi all.

Yea seems something weird is still going on. I had both ntfs-3g and ntfsprogs installed, seems installing the one did not un-install the other. Removed both, rebooted, installed ntfs-3g, rebooted, still having the same problem *sigh*

Really any patch or something available? I haven't been able to read my external HDDs for months now!

Oh yea, the flash drive that was viewable again, is suddenly not viewable either. FML

---

### Post by ubunutucyclotron on 2012-02-07
Hey wow this is totally crazy. Without me doing anything it started reading my drives again for a couple days and then stopped again! Hello pest control!?

---

### Post by audeojude on 2012-02-07
I haven't had a reacurance of this problem since m above fix. However I have noticed that there have been a few issues in general with stability in ubuntu the last year and a half. I have had this issue and reacurring issue with various apps killing X when I run them.

---

### Post by ubunutucyclotron on 2012-02-07
I dunno, I think I'm just going to have to get the latest version although I do prefer to stick to LTS releases. What do you think?

---

### Post by ubunutucyclotron on 2012-06-11
Laptop stolen in March, got a desktop, re-installed problem seems to have gone.

---

### Post by audeojude on 2012-06-11
Im on 11.10 now and my ntfs drives started being read only again a few weeks ago. Just had to run my fix from a while back again. See below command. I now have read/write on NTFS disks again.

sudo apt-get install ntfs-3g

---

