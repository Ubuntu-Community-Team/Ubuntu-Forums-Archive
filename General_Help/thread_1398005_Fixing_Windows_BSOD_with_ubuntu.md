---
title: "Fixing Windows BSOD with ubuntu"
date: 2010-02-03
forum: General Help
---

### Post by residualbit on 2010-02-03
Hey guys,

I have tried everything I could possibly think of with no luck so now I am turning to you all. My mother really screwed up her computer ,which runs XP SP3, to the point where it is un-bootable even in safe mode. It BSODs right after the BIOS. The stop message it gives is "irql_not_less_or_equal". The last thing she did was install about 58 Windows updates (at once) so its hard to pin down what caused the issue.

Wiping and a reinstall is an absolute last resort because there are years worth of contacts and folders in her outlook that she never backed up (for some reason there is no PST file either.)

I have an xp cd, but the repair option isn't available, only reformat. I have tried some ninja-ing with the recovery console and manually loading restore points, but nothing gets it past the BSOD.

I have the entire drive backed up to an external USB drive.

My goal is to at least get it to boot once so I can go into her Outlook and create a PST file with all her junk. Then wipe and reinstall (and try to get her to see the light and switch to Ubuntu.)

Any ideas?

---

### Post by switch10 on 2010-02-04
I'm pretty sure that BSOD is a hardware issue.  I doubt you will get that machine to boot without switching out the CPU or RAM and getting really lucky.  I have never used outlook, but doesn't it store all of your contacts, etc. in some file?  I think your best bet would be to find that file, and restore it on a working windows system.  

You can use the live CD to check the RAM to see if that is what is causing the BSOD.  You can also use the live CD to back up any file or directory.

Good Luck

Dave

---

### Post by residualbit on 2010-02-04
From what I could find, outlook info is stored in an outlook.pst which is no existent on this pc for some reason. I checked the RAM in memtest and it passed everything.

I am going to try to put the drive on its own partition on my external drive and see if I can boot it from a different PC or something. Maybe virtualbox?

---

### Post by Kixtosh on 2010-02-04
I have had tremendous luck in similar situations with SpinRite recovery software. In fact, when one of my laptops was inadvertently thrown to the floor while running, I got multiple BSOD messages on start-up, and yet, I was still able to use this software to repair the damaged hard drive files sufficiently to boot up the O.S. completely and just copy the necessary files onto an external drive. One warning though: if the damage is severe, it can take a long time, although I don't see how that might be the case unless your mother's computer was kicked by somebody. Your problem should be a lot less severe than mine was.

Try it out. The software needs to be copied on a bootable CD or floppy disk. It's a very small download, and once the CD boots, after the BIOS, it just takes over and does as much repairs as possible. My recovery was the next best thing to a miracle, given the amount of physical damage. I've used it again to repair a damaged Thunderbird file that was causing "cyclical redundancy error" messages (if you complete an internet search for that term, you'll see that it's no joke, and basically means that the corrupted file can neither be copied or deleted without formating the drive).

I'd certainly try it if I were you, and if it doesn't succeed, you can request a refund. After my "near death" experience, I would never be without it again.

[http://www.grc.com/cs/prepurch.htm](http://www.grc.com/cs/prepurch.htm)

---

### Post by TheViLliN on 2010-02-04
Generaly a "irql_not_less_or_equal" would be a driver issue.  You might be able to boot to the recovery concole and unload the update's. 

[http://windowsxp.mvps.org/spuninst.htm](http://windowsxp.mvps.org/spuninst.htm)
 
A tedious process undoubtedly. 

You say there is no PST file.  That's odd.  Your sure she is using Outlook and not Outlook Express (Which would be .DBX folders + .WAB file for the address book).

Use your live CD or perhaps a BartPE if that's what you need.  But your live CD would be just as easy.

---

### Post by residualbit on 2010-02-04
Villin you saved the day. I didn't know express used different file types/storage methods. I called her and she told the that she thought she was using "Outlook quick or fast, something like that." Gotta love the elderly...problem solved.

Thanks everyone!

---

### Post by tgalati4 on 2010-02-04
I repaired a vista machine with a similar message.  iostor.sys was infected with a virus.  I replaced it with another copy I found on the drive.  It controls the disk drives.  Without it, no boot.  BitDefender found the infection, but couldn't repair it

---

