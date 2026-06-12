---
title: "Mounting a Samsung Galaxy S3"
date: 2012-09-08
forum: General Help
---

### Post by 98cwitr on 2012-09-08
Sad day when the girlfriends iPhone mounts right up in 12.04 and the Android needs me to jump through flaming hoops.

Trying to use MTP to mount and get this:

> 

libmtp version: 1.1.3

Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note.
   Found 1 device(s):
   Samsung: GT-P7310/P7510/N7000/I9100/Galaxy Tab 7.7/10.1/S2/Nexus/Note (04e8:6860) @ bus 2, dev 4
Attempting to connect device(s)
PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0
OK.


Not sure what the next step is...thanks in advance guys and gals! :D

Shotwell sees the phone, then freezes and I have to kill the process. :(

---

### Post by 98cwitr on 2012-09-08
Changed from MTP to PTP on the phone...connected now, but I'd love to know why MTP doesn't work!

---

### Post by jaithehulk on 2012-09-10
Even I had to change the Phone from MTP to PTP... but the problem here i can only browse music and photo folders... what abt other folders?

---

### Post by Mark Phelps on 2012-09-10
> **jaithehulk said:**
> Even I had to change the Phone from MTP to PTP... but the problem here i can only browse music and photo folders... what abt other folders?

Far as I know -- you can't.

Android OS 4.x (ICS) changed so that you can no longer mount the partitions a Mass Storage -- which denies you access to hidden files and directories.

---

### Post by jaithehulk on 2012-09-10
So what you r saying is.. I can only access photos and music...what about sms backups and stuff?

---

### Post by cortman on 2012-09-10
MTPFS is SUPPOSED to work on Ubuntu- this is a problem I've yet to overcome thought with either Ubuntu or Debian. If anyone gets anything working, I'd sure be interested in the procedure!

---

### Post by jaithehulk on 2012-09-11
ok Thanks cortman...probably this problem is going to be handled in the next release of Ubuntu?

---

### Post by cortman on 2012-09-11
Not sure. It's not entirely Ubuntu's fault; I've found MTP mounting to be pretty flaky in Windows 7 as well (with my PPC Mac it's non-existent).
PTP in the meanwhile, I guess.

---

### Post by Mark Phelps on 2012-09-11
> **jaithehulk said:**
> So what you r saying is.. I can only access photos and music...what about sms backups and stuff?

It's a little better in Win7.  I can access all the "non-hidden" folders and files -- but it's still mounted as a multimedia device, not as a filesystem.

---

### Post by jaithehulk on 2012-09-13
> **Mark Phelps said:**
> It's a little better in Win7.  I can access all the "non-hidden" folders and files -- but it's still mounted as a multimedia device, not as a filesystem.

Yes Mark, it is better.. I am asking for a solution in Linux..because just for the sake of my S3 I need to boot into Win-7.

---

### Post by bleutyler on 2012-09-20
Hello everyone.

This is a solution I came across.

I have a Samsung Galaxy S, and when I connect the USB, I see the first level of folders, but when browsing them, then are empty.

There is a little USB symbol on the top left of the phone screen, which tells me everything is connected.

To fix this, I had to go to the settings, then under "Wireless and Networks" then to "USB utilities" 

This brings me to a screen titled "USB mass storage".  Tapped the button, and then the little android guy turned from green to orange, and my browsing works properly now.

Hope it helps all

---

### Post by Aitaix on 2012-10-06
I don't get it. Isn't Android, an operating system based on Linux? Then take Ubuntu 10.04 x64 an operating system based Linux. They just don't work together! Shouldn't this work out of the box?

---

### Post by 98cwitr on 2012-10-13
> **Aitaix said:**
> I don't get it. Isn't Android, an operating system based on Linux? Then take Ubuntu 10.04 x64 an operating system based Linux. They just don't work together! Shouldn't this work out of the box?

makes too much sense...haha:lolflag:

---

### Post by pedro.nariyoshi on 2012-10-14
I'm having trouble with my Android phone as well. I've found that if I enable "USB Debugging", Ubuntu will be able to recognize it (by using mtp-detect on the terminal), but Rhythmbox won't recognize it.

I remember that in Gnome 2.32, Rhythmbox recognized my MTP mp3 player. I don't know if something has changed. Has anyone tried this on Lucid or Natty or some of the older Ubuntu versions?

---

### Post by dom134 on 2012-10-25
Hello, I haven't tried older distros with my S2, but I believe MTP has become more problematic with upgrades from Froyo > Gingerbread > ICS > JB.

From what I recall, ever since ICS I have had to activate the USB Mass Storage on the Android. Ubuntu will then happily detect the folders.  I recently tried Slimroms JB (Slim Beans), but that did not have  USB Mass Storage so was a no-no and I am now happily on CyanogenMod.

---

### Post by Mark Phelps on 2012-10-25
Don't know about the S or S2, but on my S3, USB Mass Storage is NOT offered as an option.  Everything I've found on this claims that Google removed this option from ICS.

---

### Post by burpootus on 2012-10-27
I've had a Galaxy S3 since mid-summer and I've had trouble with this from the beginning. I run Xubuntu 12.04 and have never had a method to reliably connect the phone and transfer pictures. I've tried many suggestions from the forums, mounting scripts, gphotofs, using Shotwell, changing from MTP to PTP, etc.. Right now I need to transfer some pics and I can't get the computer to connect at all and the phone is listed under lsusb. Extremely frustrating, almost a deal breaker.

---

### Post by atomicspin on 2012-11-06
So, I know it's a semi-pain in the ***, but I did it via ES File Explorer.  I just shared the drives on my laptop that had the stuff I wanted on it (Music, pictures) and then just transferred everything across the network.

---

### Post by emastro on 2013-03-09
> **Mark Phelps said:**
> Far as I know -- you can't.

Android OS 4.x (ICS) changed so that you can no longer mount the partitions a Mass Storage -- which denies you access to hidden files and directories.

I'm not sure that's entirely correct. It mounts perfectly well under Windows, while under Ubuntu (Kubuntu 12.10, actually) it does not mount at all or mounts read-only. Having to sftp my files to the Windows box to copy them over to the S3 is really, really infuriating

---

### Post by SeijiSensei on 2013-03-09
I spent $1.40 and installed the [WiFi File Transfer Pro]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransferpro&hl=en") app which turns the phone into a web server.  Then I can upload files using a web browser.

I've tried a variety of SMB clients on the phone as well, but I find the other approach easier to use.  And I have yet to see any method to use an NFS client since I don't have permissions to create a mount point on the phone.  For that, it appears you need to root the device.

---

### Post by Mark Phelps on 2013-03-09
> **emastro said:**
> I'm not sure that's entirely correct. 

Sorry, that IS entirely correct.  Check the various Android forums if you don't believe me.  USB Mass Storage was REMOVED from Android OS as a mounting option, starting with ICS.

I, too, can mount the filesystems in Windows -- but that's because Samsung provides drivers to do this.  But ... it still only provides the options of MTP or PTP on the phone itself -- the option to choose "disk drive" has been removed from Android.

---

### Post by azmand01 on 2013-03-09
I felt the same here.. it is a sad day indeed.. and most amazing thing.. Have you found a solution? tks

---

### Post by nonbeing on 2013-03-24
I'm using Ubuntu 12.04.2 

Here are two solutions that I use for transferring files to/from my SGS3:
[LIST]
[*][AirDroid]("https://play.google.com/store/apps/details?id=com.sand.airdroid&feature=nav_result#?t=W251bGwsMSwyLDNd"): A free, fantastic app for transferring files wirelessly. Very easy to use. You don't need to know anything about SMB/NFS/HTTP/blah. Your device will run a mini web server that you can access in your laptop's browser. You can also use the S3's WiFi HotSpot feature in cases where you can't connect to a WLAN. The UI is fricking beautiful. Honestly, I can't believe they can make something so elegant and powerful and give it away for free. I would gladly pay $$ for this app if I had to.
[*][go-mtpfs]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html"): For folks who are comfortable with the command line. Mount your SGS3 (in MTP mode) on Ubuntu with one simple command. So far I've had no issues. This is faster for transferring large files, since it's over the wire (as compared to AirDroid or other wireless-based solutions).
[/LIST]

If I'm transferring anything less than a GB, I just use AirDroid. It's painless, free and works beautifully. I don't think you'll want to use anything else once you've tried it :)

Hope this helps.

---

### Post by ChristopherMonahan on 2013-04-28
> **Mark Phelps said:**
> Sorry, that IS entirely correct.  Check the various Android forums if you don't believe me.  USB Mass Storage was REMOVED from Android OS as a mounting option, starting with ICS.

I, too, can mount the filesystems in Windows -- but that's because Samsung provides drivers to do this.  But ... it still only provides the options of MTP or PTP on the phone itself -- the option to choose "disk drive" has been removed from Android.

[http://www.reddit.com/r/Android/comments/mg14z/whoa_whoa_ics_doesnt_support_usb_mass_storage/c30q93p](http://www.reddit.com/r/Android/comments/mg14z/whoa_whoa_ics_doesnt_support_usb_mass_storage/c30q93p)

It would appear that ICS does have UMS support, but not for the phone's internal memory, only an external SD card. This is because UMS is a block level protocol.

Ubuntu not working great with Android over MTP may well be Ubuntu's fault.

Finally, the fact that these two operating systems share the same kernel (Linux) is simply no reason why they should interoperate at this level.

---

### Post by jenks on 2013-10-05
It looks like this problem was fixed in Ubuntu 13.04, and AirDroid and go-mtpfs are great solutions for 12.10 users. For anyone still on 12.10 who would like one more option without needing a wifi connection (as AirDroid seems to) or another PPA (as go-mtpfs does), I discovered last night that renaming a file (such as a .pdf) to have a .jpg extension allows it to be transferred via USB. I had to install another app to accomplish renaming files - OI File Manager - but it seems to work well.

---

### Post by ruudgosens on 2014-04-13
> **nonbeing said:**
> I'm using Ubuntu 12.04.2 

Here are two solutions that I use for transferring files to/from my SGS3:
[LIST]
[*][AirDroid]("https://play.google.com/store/apps/details?id=com.sand.airdroid&feature=nav_result#?t=W251bGwsMSwyLDNd"): A free, fantastic app for transferring files wirelessly. Very easy to use. You don't need to know anything about SMB/NFS/HTTP/blah. Your device will run a mini web server that you can access in your laptop's browser. You can also use the S3's WiFi HotSpot feature in cases where you can't connect to a WLAN. The UI is fricking beautiful. Honestly, I can't believe they can make something so elegant and powerful and give it away for free. I would gladly pay $$ for this app if I had to. 
[*][go-mtpfs]("http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html"): For folks who are comfortable with the command line. Mount your SGS3 (in MTP mode) on Ubuntu with one simple command. So far I've had no issues. This is faster for transferring large files, since it's over the wire (as compared to AirDroid or other wireless-based solutions). 
[/LIST]

If I'm transferring anything less than a GB, I just use AirDroid. It's painless, free and works beautifully. I don't think you'll want to use anything else once you've tried it :)

Hope this helps.

Hi, i know this is a older post. But i want to thank you anyway for this tip. I installed AirDroid on my SGS3 and connected it in notime with my Ubuntu 14.04 system. It was realy a peace of cake. You made my day. \\:D/

---

### Post by coffeecat on 2014-04-13
This thread dates back over a year. Closed to prevent further necromancy.

As far as I am aware, MTP mounting of Android systems mostly works, albeit with a file date/time issue, in currently supported versions of Ubuntu post 12.04. If anyone needs help with problems concerning mounting Android devices in Ubuntu, please start a new thread.

---

