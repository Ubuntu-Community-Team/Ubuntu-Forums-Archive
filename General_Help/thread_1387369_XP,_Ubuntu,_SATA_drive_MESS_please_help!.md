---
title: "XP, Ubuntu, SATA drive MESS please help!"
date: 2010-01-21
forum: General Help
---

### Post by carlson79523 on 2010-01-21
So here's my problem. I had an old laptop that i bought a brand new SATA hard drive for and figured that I wanted to install Ubuntu Linux as the main OS but I'd dual boot XP for my gaming addiction. I didn't know that XP wouldn't recognize my SATA drive, and went ahead and installed Ubuntu 9.10 smoothly and hit a road block with XP. Can someone please tell me how to intall the proper drivers to my SATA drive and use them to dual boot XP so I can get back to my PC gaming

---

### Post by jamesisin on 2010-01-21
So, when you run the Windows installer you find no hard drives onto which it might install?

Did you leave an empty (unpartition/unformated) space to install Windows?  If you installed Ubuntu on the entire drive you'll have to first resize your partition (using GParted).

If the Windows installer is simply not able to see the drive/controller, then you can presumably download the driver from the manufacturer's site and use that when you build the system (this is rare today and will require a floppy drive).

---

### Post by carlson79523 on 2010-01-21
I partitioned the hard drive, I get that classic XP installation error "Setup Could Not Find any Hard Disk Drivers". I didn't custom build this laptop, its an HP from about a year and a half ago that I just put a new HD into. The PC doesn't have a floppy disk drive, so how can I install those same drivers using Linux? (I've tried nLite it freezes in Linux)

---

### Post by flabdablet on 2010-01-21
The problem is that the XP setup program is a bit long in the tooth (remember that XP was released in 2002!) and it doesn't understand what to do with SATA controllers.

Sometimes you can persuade it to work by changing SATA-related settings in your BIOS; if it offers you options to use your SATA controller in "legacy" or "emulation" or "IDE" mode, try that. If that doesn't work for you, you will need a FAT-formatted floppy disk (a real one, I'm afraid - XP Setup doesn't understand USB sticks either) with "F6 drivers" or "text-mode drivers" for your SATA controller on it. Then, when XP Setup tells you to press F6 to install additional drivers, do so.

If your computer doesn't have an inbuilt floppy drive, really your only option is to use nLite on a working Windows machine to prepare a custom setup CD that includes the requisite F6 driver.

Yes, this is all a royal pain in the ****.

Yes, setting up Ubuntu is much easier.

Also, in general, when you're setting up dual-boot Ubuntu+XP systems, the path of least resistance is to install XP first and Ubuntu second. This is because the last system you install will be the one whose boot loader ends up being used, and the Ubuntu boot loader has no trouble booting XP, but the XP boot loader doesn't know how to boot Ubuntu.

---

### Post by flabdablet on 2010-01-21
If you don't have access to a working Windows machine, but your laptop does have a decent amount of RAM, you can install VirtualBox on it, set XP up inside VirtualBox, then run nLite inside that virtual XP environment to build you the XP setup disc you need for the non-virtual install. Definitely the long way round, but will definitely work.

---

### Post by jamesisin on 2010-01-21
I bought a USB floppy drive at a garage sale for $1 for just such occasions.

---

### Post by carlson79523 on 2010-01-21
I actually tried the virtualbox route but got frustrated half way through because I have no idea what drivers to install or where to get them. do you have any suggestions as to where to find those?/which ones to use

---

### Post by jamesisin on 2010-01-21
> **carlson79523 said:**
> I have no idea what drivers to install or where to get them. do you have any suggestions as to where to find those?/which ones to use

The device manufacturer's Web site.

---

### Post by flabdablet on 2010-01-21
The SATA controllers built into HP laptops are usually from Intel, if I recall correctly. You can verify this from an Ubuntu terminal with the lspci command - look for the word SATA or IDE in the resulting spew, and that will tell you the model number of the controller you have.

You can get [F6 drivers for Intel controllers]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17883&ProdId=2300&lang=eng") from the Intel support website. If your controller is non-Intel, you should still be able to get F6 drivers for it by poking around on the manufacturer's website. Typical F6 driver downloads will be small and may be tucked away in an obscure corner of the site. The typical massive multi-megabyte [driver pack]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17412&ProdId=2101&lang=eng") downloads will generally be drivers for Windows proper rather than its setup program (although you probably will need those as well, come to think of it, so Windows works correctly once installed).

---

### Post by jamesisin on 2010-01-21
Probably easier to find the drivers through the laptop manufacturer's site (assembler?) than the SATA controller manufacturer's site.

---

### Post by carlson79523 on 2010-01-21
Well I looked on the Seagate website and no dice. I cannot find a driver for this hard drive

Seagate Momentus 250 SATA Hard drive

if anyone knows where i could find one please let me know

---

### Post by jamesisin on 2010-01-21
Did XP recognize the old drive?  It's usually NOT the drive.  It's the controller.

---

### Post by carlson79523 on 2010-01-21
Xp doesn't recognize the hard disk driver thats what it says anyway. Virtualbox XP finds and can use the C:/ just fine but the installation process for my dualbooting efforts just refuses.

---

### Post by jamesisin on 2010-01-21
Let's see the output from:

sudo fdisk -l

---

### Post by carlson79523 on 2010-01-21
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e325

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2253    18097191   83  Linux
/dev/sda2           29651       30401     6032407+   5  Extended
/dev/sda5           29651       30401     6032376   82  Linux swap / Solaris


copied and pasted

---

### Post by jamesisin on 2010-01-21
And what about:

df -h

---

### Post by carlson79523 on 2010-01-21
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              17G   11G  5.7G  65% /
udev                 1007M  284K 1006M   1% /dev
none                 1007M  524K 1006M   1% /dev/shm
none                 1007M  192K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
none                   17G   11G  5.7G  65% /var/lib/ureadahead/debugfs
/dev/sr0              550M  550M     0 100% /media/cdrom0

---

### Post by jamesisin on 2010-01-21
So it looks like your Ubuntu installation is using about 20 GB of a 250 GB drive (approximately).  Can you go into Partition Editor (Disk Utility in 9.10) and see how the unpartitioned space is being reported?  Perhaps we can create an NTFS partition here which the Windows installer will like.

---

### Post by carlson79523 on 2010-01-21
I restarted and booted with the live CD to get to gParted. this is a screenshot. the huge partition that i put in before installing XP is there.
[IMG]http://[URL=http://img190.imageshack.us/[/IMG]
http://img190.imageshack.us/img190/834/screenshotka.png

---

### Post by Jackzor on 2010-01-21
Well. Try creating a ntfs partition try the setup again? (my first guess)

---

### Post by carlson79523 on 2010-01-21
how exactly does one create an ntfs partition as opposed to a normal partition?

---

### Post by carlson79523 on 2010-01-21
nevermind on that last post. i figured it out, ill try the windows install with the ntfs partition and post back

---

### Post by carlson79523 on 2010-01-21
okay so i created the ntfs partition with no luck, the xp install disc still can't find it

---

### Post by flabdablet on 2010-01-23
As I said before, Windows XP Setup doesn't understand SATA, not even a little bit. Wouldn't matter if the drive was a Seagate or a Samsung or a Maxtor or whatever, if it's connected to your computer via SATA and you can't persuade your BIOS to make the SATA controller look like a standard IDE one, you're going to need to make an F6 driver for your SATA **controller** available to Windows Setup if you're going to have any hope of installing XP.

Repeat: the driver you need is the F6 (text mode) driver for your computer's SATA **controller.** The brand of disk drive you're attaching to the controller is irrelevant.

If you post the output of the **lspci** command, I'll find you a website where you can download the F6 driver you need.

---

