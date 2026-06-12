---
title: "Helping deleting a disk drive."
date: 2011-02-16
forum: General Help
---

### Post by Coldboltage on 2011-02-16
Hello,

I have a big issue which has forced me for the first time to use ubuntu and to be honest, best problem i've had in terms of being introduced to linux. 

The Main Problem:

Ok so basically this isn't my harddrive but hear me out. It's a known issue but it only happened after him downloading stuff off priate bay. The harddrive is not detected on BIOS, so you can't boot through it, just the CD Drive is now detected. You can't use SAFE mode as it reverts to another issue, a black screen with a white cursor, no keyboard commands work.

No restoring disks will fix it nor master disks, it's literally a bad *** issue. Thou I can still load things via CD Drive so I used the Acronis Bootable Media and surely enough, it could anaylse data on the harddrives. I thought maybe i'll try PE Bart but once again, loads up to Black screen with White Cursor. So I put in Ubuntu and yes, I can get on the GUI, but I can't install the operating system.

There would always been an issue. something about in/out whilst installing but as long a I can use the tools, then we go onto Disk Utility. When I try to format, the Error Message apprears stating : Eroor creating File System: helped exited with error code 1: Error calling fsync(2) on /dev/sda2: Input/Output error. This would be the same error i would get via installing and I would have to ignore and eventually whilst installing, from being complete on the right hand side, it would say ERROR or ABORTED after 70,000.

Hopefully you can help me out

---

### Post by DanneStrat on 2011-02-16
> **Coldboltage said:**
> Hello,

I have a big issue which has forced me for the first time to use ubuntu and to be honest, best problem i've had in terms of being introduced to linux. 

The Main Problem:

Ok so basically this isn't my harddrive but hear me out. It's a known issue but it only happened after him downloading stuff off priate bay. The harddrive is not detected on BIOS, so you can't boot through it, just the CD Drive is now detected. You can't use SAFE mode as it reverts to another issue, a black screen with a white cursor, no keyboard commands work.

No restoring disks will fix it nor master disks, it's literally a bad *** issue. Thou I can still load things via CD Drive so I used the Acronis Bootable Media and surely enough, it could anaylse data on the harddrives. I thought maybe i'll try PE Bart but once again, loads up to Black screen with White Cursor. So I put in Ubuntu and yes, I can get on the GUI, but I can't install the operating system.

There would always been an issue. something about in/out whilst installing but as long a I can use the tools, then we go onto Disk Utility. When I try to format, the Error Message apprears stating : Eroor creating File System: helped exited with error code 1: Error calling fsync(2) on /dev/sda2: Input/Output error. This would be the same error i would get via installing and I would have to ignore and eventually whilst installing, from being complete on the right hand side, it would say ERROR or ABORTED after 70,000.

Hopefully you can help me out

Is it a "smart" enabled drive? If so, what does the "disk 

utility" smart status say about the drive when

you boot from the live cd?

If you have tried everything and think it would

help to erase the disk(write zeroes on it), 

then you can try "killdisk"

Just burn the .iso to a cd and boot from it.

The process will take a long time so I

would recommend you run it over night.

Info on usage:

[http://www.killdisk.com/screenshots.htm](http://www.killdisk.com/screenshots.htm)

Download link:
[http://software.lsoft.net/boot-cd-iso.zip](http://software.lsoft.net/boot-cd-iso.zip)

---

### Post by Coldboltage on 2011-02-16
Hello,

Regarding the Smart Disk, it says it's healthy so wondering what the hell there.

When on killdisk, it was not able to detect the 2 drivers but using the NFTS viewer, it could see 2 partitions. Any Linux based programs I could use

---

### Post by DanneStrat on 2011-02-16
> The harddrive is not detected on BIOS

I missed that part.

This is the first thing you need to fix.

The fact that the disk is not listed in bios and

thus not usable could be because of a faulty power cable.

Could you give me some more info about the drive? Interface?(pata, 

sata, usb etc.) Is the drive inserted properly?

---

### Post by Coldboltage on 2011-02-16
It is unfortuantely a Laptop with a SATA connection. What is werid is when I use a restore disk it says "Windows is restoring files" or something with a white loading meter and then goes to "sigh" vista and then goes to a black screen with a white cursor

I think I know where you are going, Hitachi made the harddrive so i'm looking here : [http://www.hitachigst.com/support/downloads/](http://www.hitachigst.com/support/downloads/)

---

### Post by Mark Phelps on 2011-02-16
Don't know if you know how to tell a PATA drive from a SATA drive, so I'm passing along some advice ...

A PATA drive has a bunch of little pins on the back and is connected to a controller on the PC using a wide ribbon cable.  It also has a smaller set of pins that use a "jumper" to determine whether a particular drive is viewed as the Master or as the Slave.

A SATA drive has a set of contacts on the back on two plastic tabs.  The larger tab is for the power cable, the smaller tab is for the data cable. There are no jumper pins as SATA drives don't need you to set Master or Slave.

IF the drive is PATA, and you already have another PATA drive in your system, it's likely that your drive is NOT jumpered as master or slave (the default in single drive systems).  That confuses the controller such that it won't see the second drive.  So, if they are both PATA drives, you will need to jumper one as Master and the other as Slave.  Jumper settings are normally printed on the drive case on the label.

---

### Post by Coldboltage on 2011-02-16
Hello,

Now heres the mega problem, I can't open it or else it voids the warranty but i'm near sure it's SATA but I can check via the Linux CD, I think it's a BIOS Driver issue so i'll just need to use linux to find out which driver and such it is.

Any assistance further on would be mega appericated

Just to let you know, Linux can see the 2 drives, one labeled windows and the other data

---

### Post by Coldboltage on 2011-02-16
Just trolled everyone, the harddrive is as follows


[LIST]
[*]ATA FUJITSU MJA2500BH-G2
[*]Port 2 of SATA Host adapter
[*]500GB
[/LIST]
Persume it's SATA now

---

### Post by DanneStrat on 2011-02-16
> **Coldboltage said:**
> Just trolled everyone, the harddrive is as follows


[LIST]
[*]ATA FUJITSU MJA2500BH-G2
[*]Port 2 of SATA Host adapter
[*]500GB
[/LIST]
Persume it's SATA now

I would suspect that the bios is

misconfigured or that there

is some problem with the sata

connector.

Here is some general info on

SATA troubleshooting from seagate:

[http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=212667&NewLang=en](http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=212667&NewLang=en)

---

### Post by PaulReaver on 2011-02-16
i had a similar problem... the hard disk was good but for some unknown reason just couldn't detect it in the bios. it worked 100% fine in other pc's???

I solved it by installing grub to a usb stick.... a pain in the backside but it saved me from having to buy another pc for a whole year :)


also I just use an ubuntu live cd to wipe a hard disk clean

dd if=/dev/zero of=/dev/sda bs=1M

will wipe a drive clean

---

### Post by Coldboltage on 2011-02-16
Hello,

Well I just opened hte back of the laptop and there was the harddrive. I took it out and in and you could hear it start so i'm now suspecting it's BIOS. Like I said, the BIOS doesn't detect it so I need a way for it to detect it again, anyway I could do that

---

### Post by PaulReaver on 2011-02-16
oh right.... a laptop...

i had this problem on a desktop.... so having a usb stick poking out the back wasn't a big deal for me, but I needed to recompile the kernel with the mmc stuff in the kernel not as modules :(  not really worth the hassle.



do you have another hard disk??? or an external hard disk???

---

### Post by Coldboltage on 2011-02-16
I have a USB External. Seagate Seatools just came back Failed

---

### Post by Coldboltage on 2011-02-16
Hello,

Got the issue, it's bad sectors on the harddrive according to Seatools. Can anyone assist me onto how to fix the issue or how to go around it. I have access to the Live CD without error and can still use the CD Drive "Duh"

---

### Post by Nixarter on 2011-02-16
I would wipe the drive and then do a full format.  If you format with a full/complete format I've been told that the formatting programs generally search bad sectors and remap them to good sectors, so that the OS sees only good sectors (so your data doesn't get corrupted by the OS writing to bad sectors).  Quick formats don't check this, they just do a very basic re-write on some low-level data.  Unfortunately, I don't know whether this sector remapping by using a complete format is true or not... it is just hear-say, as I have never had the issue myself.

I suggest DBAN to wipe the drive, as it is stable/reliable, runs independently from a disk, and is easy to use (and very difficult to screw up).  Just make sure you only have the hard drive you want to wipe installed, as it might wipe your usb sticks too.  It takes a while... a good while.  By the time you're all done, you will have filled every byte on the drive at least twice... which will take hours.

Good luck

EDIT: PS:  Do you want any data from the drive?  The above assumes that you don't.  If you do, however, there are options.  ddrescue (dd command) is one I've used before.  There are lots of tutorials about, but what you'll basically do is skip bad sectors (depending on your settings) and make a byte-by-byte image of every readable byte on the drive into file on another drive.  Then you take other tools to examine that image.  A word of warning, though.  DD is a powerful, low-level program.  If you mix up parameters you can end up overwriting your good drive with corrupted data from your bad one (which would suck).  But if you choose to write to an image file (instead of to a drive) and you accidentally reverse the parameters, it will error out saying that the source image doesn't exist (and it won't damage your good data).  But still be careful...

---

