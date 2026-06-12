---
title: "Lost &quot;Regular Linux&quot; in Grub, only left with &quot;Recovery Mode&quot; and other Partitions."
date: 2011-04-30
forum: General Help
---

### Post by alsmith on 2011-04-30
Hi folks,

I have a dual-boot desktop, Ubuntu and XP.

I updated to 11.04 recently, no problem. Chose to merge the old and new Grub files together. Rebooted to finalize everything, and my Grub menu had lots of doubling up of options, the old kernel, as well as two options of Windows XP (the old option that I'd put on Grub, and what I suspect was 11.04's recognition of another partition, as it was titled "Windows XP ... (on dev/sda2)")

Then I fired up Grub Customizer, re-read and double checked everything, and removed all the doubling instances. All good. Shut down for the evening.

Booted up the PC this afternoon and my Grub menu looks thus (adjusted with artistic license, just so you get the picture):

Windows XP
Ubuntu 11.04 (recovery mode)
Memtest
Memtest
Dell Utility Partition
Windows XP (on dev/sda2)

I've lost the option to choose regular Ubuntu.

I've gone into recovery mode, tried the "Update Grub" option, rebooted, but nothing changes.

Now, there's a terminal login on Recovery Mode. I am effectively an Absolute Beginner when it comes to the terminal - I know a couple of commands, am eager to learn more when I have the time, but really couldn't tell you what the hell I'm doing. The last thing I want to do is make this worse by fumbling through code. This isn't Zork.

If anybody would be kind enough to provide the terminal commands to change the Grub menu to add regular partitions, I'd be very grateful. If there's a different fix, equally good. If anybody's got any comments, diagnoses, verbal abuse, heap it on. I'm here to learn.

Cheers.

---

### Post by immaculance on 2011-04-30
My Grub is not jacked in the same manner after the upgrade, but it is Jacked... I had to go into 'previous versions' and boot from the first option from my latest kernal to even get into my Ubuntu session! I loaded into 11.04 successfully, but the upgrade definitely jacked-up my Grub, even though I told it to keep the existing version that was installed in place.

LONG STORY SHORT - THE UPDATE TO 11.04 JACKED-UP MY GRUB IN AN UNEXPECTED AND BAD WAY.  Will post more details in a sec.

And now that I'm in the session, I can't even get to my old menus to allow me get into system preferences and stuff... and I can't get this damn new docky bar on the side to go away, or to at least get me somewhere that I actually need to be!

---

### Post by hyattjon on 2011-05-08
similar problem here, Vista, 11.4 and 10.10.

I get to Vista ok, but grub only gives me recovery modes for Ubuntu 10.10.

I can boot to the Ubuntu 10.10 desktop ok by using recovery and startx, but it's a PITA.

I have no idea how to fix this, update grub does nothing and grub customiser doesn't change anything from either Ubuntu install. I have tried rewriting grub to the MBR from customiser but the same problem occurs.

I get:

2.6.38-9-Generic
2.6.38-9-Generic Recovery Mode
Previous Versions:
        __2.6.38-8-Generic
        __2.6.38-8-Generic Recovery Mode
        __2.6.35-29-Generic
        __2.6.35-29-Generic Recovery Mode
        __2.6.35-28-Generic
        __2.6.35-28-Generic Recovery Mode
Memtest 86+
Memtest 86+ Serial Console 115200
Windows Vista /Dev/sda2
2.6.35-29 Generic Recovery Mode
2.6.35-28 Generic Recovery Mode

The only ones that boot correctly are the top one and Windows. The bottom 2 in the main list are correct for recovery mode, ALL the ones in previous versions revert to 11.4 in a corrupted mode, no mouse or keyboard, locked up at the login screen.

---

