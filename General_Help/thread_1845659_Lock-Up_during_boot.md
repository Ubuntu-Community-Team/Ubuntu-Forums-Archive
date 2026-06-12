---
title: "Lock-Up during boot"
date: 2011-09-17
forum: General Help
---

### Post by 4thVariety on 2011-09-17
I need an expert on what Ubuntu excatly does when booting up.

Board: MSI Z68A-G45
CPU: i7-2600k
8 GB Ram

No drives, everything is disconnected, Ubuntu is on a USB stick which works fine on any other machine.

But no matter if it is different Versions of Ubuntu, Win7 or Win8, the whole rig locks up some time during boot. The screenshot is from 11.04 which is the only piece of software breaking  down and giving some sort of feedback.

[[IMG]http://img88.imageshack.us/img88/930/bugxc.th.jpg[/IMG]](http://imageshack.us/photo/my-images/88/bugxc.jpg/)

Does anybody have some insights on which part of the hardware Ubuntu is trying to talk to?

---

### Post by TeoBigusGeekus on 2011-09-17
I'd try connecting all the devices and see if the pc boots up.
If it does, I'd then try disconnecting them one by one to see who the culprit is.

---

### Post by 4thVariety on 2011-09-17
This message was generated with only the board, the processor, the cpu, ram,  and an USB stick. No other devices. Ok, a PSU, obviously.

I can put in a GTX260, which does not change a thing.
I can put in a HDD with a working operating system, which does not change a thing (i.e. same crash, boot-up logos freezing, Linux versions dropping dead to black screens, etc.).
I can connect a DVD Rom and a blank HDD, bott all sorts of Linux and Windows DVDs which does not change a thing.

The system already is as barebone as it gets. I only got CPU or mobo to blame. Since Ubuntu at least freezes with displaying text, I was hoping somebody can assign the blame.

---

### Post by joolzg on 2011-09-19
I have the exact same problem, machine has NO extra cards in, but wont boot.

I have also tried to run Memtest from the boot cd but it just hangs

Any help ANYONE

---

### Post by trevelyon on 2011-12-16
Having same issue here.  Loads up until usb drive is detected (or after usbhid is loaded when booting from cdrom) then hangs.  Tried ubuntu 11.04 from usb and cd and xubuntu 11.10 from usb.  All hang at the same place.  Any ideas on what gets loaded after the usbhid in the ubuntu early boot sequence?

I should mention that memtest seems to run fine from xubuntu 11.10 from usb.

---

### Post by gordintoronto on 2011-12-16
If there is more than one stick of RAM, try with just one - then the other(s).

Is the RAM specifically supported by the MSI Z68A-G45? Have you made any "tweaks" to the BIOS settings? Oops, it's a UEFI board. Ubuntu version?

Also see: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

I also suggest you have a look at the feedback for this board at newegg.com. They are no longer selling it.

---

### Post by trevelyon on 2011-12-16
Thanks for the reply but the memory seems fine (no errors running on memtest86+ for 6+ hours).  It seems to be a problem with the ubuntu boot.  I booted Debian 6.0.3a live usb and it comes right up.

Ubuntu installations tried:

11.04 usb - ubuntu
11.10 usb - xubuntu
11.04 cdrom - ubuntu

All hang at the same place early on in the boot, just after detecting usb pen drive or usb hid (when booting from CD).

I should also point out I just bought this board from newegg 3 days ago on a special they had so it just might be sold out from that.

Is there a way to install ubuntu from a working debian installation seeing as the installer is failing for me right now?

---

### Post by trevelyon on 2011-12-16
Got it to boot at least.  I used the nomodeset noacpi options and it comes up.  Seems it's EFI problems with the ubuntu boot process (it works on Debian 6.0.3).  This page gave me the idea:
[http://dustin.li/2011/05/how-to-install-ubuntu-11-04-on-a-mac-mini/](http://dustin.li/2011/05/how-to-install-ubuntu-11-04-on-a-mac-mini/)

It's installed now on the SSD but grub is not booting so on to the next issue to solve.  Hope this helps someone else.

---

### Post by trevelyon on 2011-12-17
Well, got it up and running.  Just need to add the nomodeset and noacpi to /etc/default/grub and run update-grub.  All is working great and wow natty FLIES when installed on an SSD. :D

---

### Post by gordintoronto on 2011-12-17
I would be interested in knowing how it works with the 3.0.0-14 kernel and no boot parameters.

---

