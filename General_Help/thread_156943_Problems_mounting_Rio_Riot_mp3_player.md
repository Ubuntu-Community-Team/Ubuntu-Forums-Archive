---
title: "Problems mounting Rio Riot mp3 player"
date: 2006-04-08
forum: General Help
---

### Post by theboatashore on 2006-04-08
I've been having trouble mounting my Rio Riot mp3 player on Kubuntu Breezy.  I'm running it on a Sony Vaio that's pretty new.

**lsusb** reads:

[I]Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045a:5202 SONICblue, Inc. **(this is it)**
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 013: ID 1058:0401 Western Digital Technologies, Inc.
Bus 001 Device 011: ID 046d:c03f Logitech, Inc.
Bus 001 Device 010: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000
[/I]

So, I know it can be seen but don't know it's */dev/?* name to mount it.  I've tried *dmesg* (advice from some posts) but don't know what this means and it doesn't seem to give any useful information.

I also get messages telling me the device isn't listed in my */etc/fstab* or */etc/mtab*.  Do I need to edit these files at some point (I did to mount my iPod, which works on occasion)?

Once I get it mounted, I hope to be using jrioutils to interact with the player.

Thanks in advance.

---

### Post by tousman on 2006-05-01
I found this page on google that gives some usefull info to mount a different type of rio players, but it should be similar : 
[http://www.edwiget.name/content/view/40/26/1/1/]("http://www.edwiget.name/content/view/40/26/1/1/")

I hope it helps...

---

