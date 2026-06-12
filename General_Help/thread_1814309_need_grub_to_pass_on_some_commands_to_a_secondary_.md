---
title: "need grub to pass on some commands to a secondary OS..."
date: 2011-07-29
forum: General Help
---

### Post by ninjaaron on 2011-07-29
So, I have a netbook with a 320GB harddrive and I'm testing all kinds of fun distros out.  Right now I have 11.04, 11.10 daily, Jolicloud, Chromium OS, and MeeGo.

Meego uses it's own weirdass boot loader, which sets things up a certain way.  My computer has a touchscreen, and I had to modify some things to get it all working properly.  Anyway, I reinstalled grub on my main partition (11.04), but now the command I need doesn't go through to meego.

The command is "usbhid.quirks=0x0eef:0x725e:0x40" For my  other systems, I have it in /etc/default/grub in the "GRUB_CMDLINE_LINUX_DEFAULT=" line.

Obviously there is nothing like this in Meego, and a thread on their forum said I would have to configure it in whichever bootloader I'm using.

---

### Post by drs305 on 2011-07-29
Can you use a menu entry such as the following and allow it's own bootloader to set the value?

> menuentry "Other OS" {
set root=(hdX,Y)
chainloader +1
}

---

### Post by ninjaaron on 2011-07-29
> **drs305 said:**
> Can you use a menu entry such as the following and allow it's own bootloader to set the value?

In which file do I add the entry?

Also, the original boot scheme was weird with meego... it was like the bootloader had it's own partition.  That partition wasn't recognised by grub.

I'll give your advise a try, but I need to know exactly where to place the entry.

---

### Post by ninjaaron on 2011-07-29
Ok, I didn't do quite what you said.  I made a custom menu entry that applied the command from grub... aaaaaand...  It worked!

did it by creating menu entries from those that already existed according to the [grub documentation]("https://help.ubuntu.com/community/Grub2").

Solved. woo!

---

