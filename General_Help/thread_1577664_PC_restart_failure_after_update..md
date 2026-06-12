---
title: "PC restart failure after update."
date: 2010-09-19
forum: General Help
---

### Post by UncleAlan on 2010-09-19
Duriing an up date pc requested a restart to complete. Then it rebooted so far and has stopped. I have the following screen:-
 
A black screen with white writing on 
 
GNU GRUB Version 1.97 beta 4.
 
And a box that lists:-
 
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
 
 
The top option is highlighted.
 
I fear my entire hard drive is gone !!! I had only swithched on to update and back it all up now my world is lost.
 
I have a disc that I installed Ubuntu with and vaguely remeber the operating system could be run from the disc. Can I put the disc in and start the pc from it and still read what I had on the Hard drive?
 
Or is everything gone and lost?
 
Prior to the calamity the pc was running Ubuntu 9.10 and nothing else.
 
 
Can any one please help?
 
Thanks Alan

---

### Post by WorMzy on 2010-09-19
When the list comes up, press Enter.

Do you get an error? What is it?

---

### Post by UncleAlan on 2010-09-19
Hello,
 
Switched on pc, it went to tha afore mentioned screen, top option highlighted. Pressed Enter, got the Ubuntu wheel for a while then this mesage:-
 
fsck from util-linux-ng 2.16
/dev/sdal: clean, 193028/4923392 files, 6734773/19661544 blocks
 
and a flashing curser? under that.
 
I hope that is of help.
 
Thanks Alan

---

### Post by WorMzy on 2010-09-19
If you leave it long enough, does it finish booting?

The screen with the kernel list is grub2, your bootloader. It gives you the option to boot into older kernels and recovery modes, as well as other operating systems if they exist on your computer. It's perfectly normal, nothing to worry about. It's strange that it's showing up when you only have one OS installed though, one of the "improvements" that the grub2 developers made over the original grub was that it's not supposed to show up unless you have multiple OS' installed.

Still, it's nothing to worry about, someone else on the forums will (hopefully) be able to show you how to hide the menu again (I have no idea, since I use the older version of grub).


If the system doesn't boot after you've left it at that fsck message for a while, then restart and boot into the recovery option (press the down arrow on the keyboard when presented with the list, to select the recovery option, then press enter), if that loads up correctly it should present you with another list, this time with recovery options in it. It should look something like this:

[[IMG]http://img299.imageshack.us/img299/8065/recovery1.th.png[/IMG]]("http://img299.imageshack.us/img299/8065/recovery1.png")

Try the fsck option first, and then the clean and dpkg options. Restart, and try booting normally again. If it fails again, hopefully it'll give us a clear message as to why it's failed.

---

### Post by mr clark25 on 2010-09-19
try doing it agian, just let it sit there a little longer.

if that still doesnt work, press the "down" arrow before you press enter. this should bring you to a comand line interface. once there, type:
```

startx

```and press enter. this *should* get you to your desktop.


EDIT: looks like WorMzy beat me to it. follow his advise first ;)

---

### Post by UncleAlan on 2010-09-19
Hi WorMzy,
 
I had the fsck on for 5 mins whilst I copied it down and it didnt change. However I have noticed there is some change in the message each time the pc is rebooted. in my first post  there are some numbers in two blocks of two lots. each time the pc is rebooted the first set in both blocks shows an increase. The numbers do not change while the message is on screen. The Hard drive light or what ever it is isnt on. The screen times out and goes blank so I have to press the reboot button and keep praying !!!!!
 
 
mr clark25
 
My understanding is your instruction follows on from WormZy screen in his picture
 
As I am still no further I havnt got to the place for your instruction yet.
 
 
Thank you so far
Alan

---

### Post by UncleAlan on 2010-09-21
Tried booting from cd but either the cd is wrong or the pc isnt having any.
 
Still not working.
 
Cntrl-Alt-del only restarts and it doesnt do anything.
 
Alan

---

