---
title: "Make bootable usb from iso"
date: 2011-04-09
forum: General Help
---

### Post by ntesla123 on 2011-04-09
I need to boot the [ultimate boot cd]("http://www.ultimatebootcd.com/download.html") from an usb stick. Do I just copy the iso image to the usb key?

How do I make the usb stick bootable?

---

### Post by KegHead on 2011-04-09
Hi!

Make sure you have at least a 1gb stick.

Goto:

system...administration...start up disk creator.

your iso will show up as source 

 &

your stick as disk to use.

hit erase disk and then make start up disk.

Enjoy!

KegHead

---

### Post by linuxuser12345 on 2011-04-09
What version are you trying to put onto a USB? 10.10 and up will work fine the way KegHead showed you, but 10.04 LTS and under you will have to use UNetbootin to install the Live Disk to a USB drive.

Go to:
*Applications... Ubuntu Software Center... (type)UNetbootin... Install*

Then go to:
[I]Applications... System Tools... UNetbootin

[/I]May I mention that 10.10+ will *also* work with UNetbootin?

---

### Post by Dave_L on 2011-04-09
Startup Disk Creator, when run on 10.04, can make a 10.04 Live USB.

---

### Post by C.S.Cameron on 2011-04-09
> **ntesla123 said:**
> I need to boot the [ultimate boot cd]("http://www.ultimatebootcd.com/download.html") from an usb stick. Do I just copy the iso image to the usb key?

How do I make the usb stick bootable?

If you actually meant to ask how to boot the **iso** from USB stick, check out MultiBootUSB.
It works from grub 2 so you will need to install it while booting a grub 2 system, (Live CD works.

UNetbootin should also work but does not offer persistence out of the box.

Persistent partitions can be added for both of the above.

Not sure if usb-creator works with the Ultimate edition.

---

