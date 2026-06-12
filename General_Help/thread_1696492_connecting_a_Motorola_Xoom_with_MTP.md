---
title: "connecting a Motorola Xoom with MTP"
date: 2011-02-27
forum: General Help
---

### Post by Clive McCarthy on 2011-02-27
I can't get my Motorola Xoom to 'mount' on Ubuntu 10.10

The Motorola Xoom has a USB connection that uses MTP (Media Transfer Protocol) and not MSC (Mass Storage Class). 
This allows file-level access as opposed to the whole media block. My Droid X mounts fine but it uses MSC.

I have loaded the MTP tools:
[INDENT][COLOR="Green"]sudo apt-get install mtp-tools[/COLOR][/INDENT]
and I have installed both [COLOR="green"]Qlix[/COLOR] and [COLOR="green"]gPodder[/COLOR] since these both use MTP.

The Xoom remains unrecognized. So instead of file-level access I have NO-level access. :(

---

### Post by sog on 2011-02-27
same problem here. that package enables rhythmbox access, but I have been unable to get fileseystem access working via mtpfs or anything else. any thoughts welcome.

connecting using a windows guest on virtualbox is also problematic, fyi.

---

### Post by sog on 2011-02-27
[http://forum.xda-developers.com/showthread.php?p=11691731#post11691731]("http://forum.xda-developers.com/showthread.php?p=11691731#post11691731")

this is a reported solution, but it was not successful here.

---

### Post by Clive McCarthy on 2011-02-27
> **sog said:**
> [http://forum.xda-developers.com/showthread.php?p=11691731#post11691731]("http://forum.xda-developers.com/showthread.php?p=11691731#post11691731")

this is a reported solution, but it was not successful here.

Yes, that "solution" looks rather clunky too. I'm _not_ willing to manually mount the Xoom. 
The purpose of MTP via USB is to make the whole thing automatic in the same way that MSC is automatic when a USB 'drive' is connected.

It could be something is wrong with Motorola's set up for MTP on the Zoom, though it works with XP and Media Player 11. 
I presume music players such as Microsoft Zune and those from Creative Labs successfully activate MTP on Ubuntu without going through a manual mount?

All I know about MTP has be learned from this Wikipedia article: [http://http://en.wikipedia.org/wiki/Media_Transfer_Protocol]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol")

---

### Post by windfix on 2011-03-05
I'd sure love to see a solution... really ticks me off that an Android device is giving me this headache.  wtf!

There is another suggested solution here:  [https://supportforums.motorola.com/message/332363](https://supportforums.motorola.com/message/332363)

However, gnomad2 does not appear to me in Synaptic or U Software Center.  Maybe a wiser guru can find some joy in the above post and inform us neophytes?

BTW, this thread talks about getting gnomad2 in 10.10

---

### Post by xzero1 on 2011-05-20
Apparently, there is a bug in the mtp code. I have gotten gMTP to work with the Asus Transformer on Lucid 64 bit, but you need to compile it yourself. See [http://packages.ubuntu.com/source/maverick-backports/gmtp]("http://packages.ubuntu.com/source/maverick-backports/gmtp")

---

### Post by wodenickel on 2011-06-29
ASUS Transformer on 32bit Lucid (10.04LTS) in a VMWare VM now works ALSO by manually compiling the mtpfs module. We followed these instructions:

[http://alldroid.org/tabid/40/g/posts/t/1125/Mount-Internal-Storage-of-Xoom-in-Ubuntu.aspx]("http://alldroid.org/tabid/40/g/posts/t/1125/Mount-Internal-Storage-of-Xoom-in-Ubuntu.aspx")

FYI - when cd'ing to the device, e.g. cd /media/asus, the system hangs for several seconds before it comes back. 

My office mate and I have worked through this together. His Ubuntu is also 10.04LTS but running directly on a Lenovo T61P laptop. His kernel is 2.6.32-32-generic.pae (in case that matters).

Thanks to all who share!

BTW - if you need the vendor ID, you can get it by using "lsusb" - look for your device. The first part of the double hex string is the vendor id, the second is the device ID. For the Transform it's: 0b05:4e0f

---

### Post by UeB on 2011-10-16
I also have a xoom (now running android 3.1) and when I start gMTP and connect the xoom via usb cable nothing happens although 
this shows up in dmesg:
[16325.204099] usb 1-1: new high speed USB device using ehci_hcd and address 4

I am using Ubuntu 11.04 with gMTP version 0.9 (version in repository).

I find the manuals to get it mounted quit complicated. And I do not understand in this thread what I am exaclty supposed to to to get gMTP to work with the xoom. What sould I recompile, which source from where???

thanks in advance and kind regards

---

### Post by happyisland on 2011-10-17
I also have a xoom (wifi only) and I can't get it to connect to my laptop, even though I've tried pretty much all the googleable solutions out there. So weird that an Android device can be connected to an ubuntu laptop by USB cable and be impossible to mount.

---

### Post by UeB on 2011-10-18
yeah it is weired. I have installed sshdroid and my default method of transfaing files form my laptop to the xoom at the moment is the sftp feature of nautilus...

---

### Post by vmsman on 2011-11-01
I've been struggling to get my Xoom to automount under 11.10 and I finally have it going.

The Xoom does not provide the usb mass storage protocol and so you need to use Microsoft Transfer Protocol (MTP) which was originally designed for media devices like cameras and portable music players.  

                                 To enable MTP protocol and mount the xoom:
 

 Simply go to a Terminal window  (CTRL-ALT-T) and type this command:
 **sudo apt-get install mtpfs**


**That installs MTP.**
In the same terminal window invoke the editor as follows:

**[COLOR=#777777][FONT=Arial, sans-serif]sudo gedit /etc/udev/rules.d/51-android.rules[/FONT][/COLOR]**

Enter the following two lines of code.

                                  **[COLOR=#777777][FONT=Arial, sans-serif]ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="22b8", MODE="0777", RUN+="/bin/bash -c 'mkdir -p /media/Xoom && mtpfs /media/Xoom -o allow_other'" [/FONT][/COLOR]** 
 **[COLOR=#777777][FONT=Arial, sans-serif]ACTION=="remove", RUN+="/bin/fusermount -u /media/Xoom/", RUN+="/bin/rmdir /media/Xoom/" [/FONT][/COLOR]** 
 
Save the file and reboot.  Your Xoom will automount when connected and autodismount when disconnected.


[B][COLOR=#777777][FONT=Arial, sans-serif]
[/FONT][/COLOR][/B]

---

### Post by UeB on 2011-11-01
I followed your instructions but they did not change anything for me.
I am using Ubuntu 11.04 maybe this makes a difference ...

---

### Post by windfix on 2011-11-01
Is it possible to modify this to do the same for an Asus Transformer?  It has the same MTP need as the Xoom (I have had both).  Seems like the ATTR and MODE settings will likely be different?

---

### Post by cifar24 on 2012-01-20
Thanks for help guys. I got my Xoom working with Ubuntu 10.04, following the exact instructions given in this forum. 

1. sudo apt-get install mtpfs
2. sudo gedit /etc/udev/rules.d/51-android.rules
3. Cut and paste: 
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="22b8", MODE="0777", RUN+="/bin/bash -c 'mkdir -p /media/Xoom && mtpfs /media/Xoom -o allow_other'"
ACTION=="remove", RUN+="/bin/fusermount -u /media/Xoom/", RUN+="/bin/rmdir /media/Xoom/" 
4. Reboot. 
5. Connect your xoom.

---

### Post by kev77 on 2012-07-05
[http://pkgs.org/ubuntu-11.10/ubuntu-universe-i386/gnomad2_2.9.6-1_i386.deb/download/](http://pkgs.org/ubuntu-11.10/ubuntu-universe-i386/gnomad2_2.9.6-1_i386.deb/download/)

---

