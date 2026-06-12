---
title: "Can not Print from Wine"
date: 2006-03-07
forum: General Help
---

### Post by SteveF on 2006-03-07
I'm hoping someone could point me in the right direction to solve this issue.  When I print from my Wine apps, nothing happens.  I get the print dialog, click print, it goes away, but nothing prints nor does anything show in the print queue.

I checked the cups log file and it showed an error an recommended turning debug  on.  I did this and got the following in te log file:

E [07/Mar/2006:10:34:12 -0500] [Job 83] No pages found!
E [07/Mar/2006:10:34:12 -0500] PID 15960 stopped with status 1!

There are a lot more lines prior to these related to Job 83, but nothing else showing an error.

Thanks for any pointers,

Steve

---

### Post by erimar77 on 2006-03-07
i guess the first question would be.. do you have printing working in ubuntu?

---

### Post by SteveF on 2006-03-07
[QUOTE=erimar77]i guess the first question would be.. do you have printing working in ubuntu?[/QUOTE]

Yes, printing works fine for all of my Linux-based apps.  I have 2 printers installed.  An Epson 820 on USB.  The other is the gnome pdf printer.  Both work from Linux apps.  Under Wine, both appear as selections, but neither print.

Steve

---

### Post by SteveF on 2006-03-20
More information.  I installed a new Hp Photosmart printer (I've been using an Epson).  I can print fine to the HP from Wine, but still can not print to the Epson.  SO at least I can print now.  Must be something with the Epson driver.

Steve

---

### Post by kerry165 on 2006-04-28
Also curious about this. Started learning about Linux properly two days ago.
Picked an old decommissioned "server". 2 x P III processors, 393Mb RAM, AHA 2904 card running 2 x 8Gb disks, DAT drive, CD-ROM, Whatever ethernet controller was in it, on-board VGA, sound & usb.

Wed evening I installed Ubuntu from CD, letting it use whatever defaults it wanted. Went in like a dream. Have not tested it all yet. But step one was to see how easy it was to install.

Thursday morning. Find out and learn how to set the network card to access my network. Interface seemed easy to use (I worked on Unix internals when it first went commercial and not since. So graphic interfaces on IX products is still a WOW! for me) I need to set the MTU as certain sites cause me grief if I don't. A bit dissapointed that I had to manually set this number in the **interfaces**file. But no big deal.

Now the printers. Searched and worked out how to connect to shared printers on a Win2k and a Win2003 box. From Linux could see and print to both.

Next WINE. From winehq I got the download and installed. Bit of grief seeing this work (ish). Still having issues but with using "sudo" running of WINE the printers worked fine.

Installed VNC for remote desktop access and worked out how to run my win app in WINE without sudo.

_Printers no longer print from my win app in WINE. Printers are fine under Linux_.

It is now Friday morning and about to go back to office.

Today I am looking at VNCServer without rdp (i.e. no existing login session required).
When this is done I will check if the printers work unde WINE using a "sudo" execution. If not I need to know what differences were made to the system since I actually saw the printers working.


Kerry

---

