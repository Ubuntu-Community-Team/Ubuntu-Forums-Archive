---
title: "HP Compaq unable to support 4gb ram but should"
date: 2012-06-06
forum: General Help
---

### Post by abduljones on 2012-06-06
I have a second hand HP Compaq 6720s which is supposed to take 4096mb of RAM. But it doesn't. I have tried installing the max and it tries to boot and dies. I have tried individual sticks and in different slots and there appears to be no problem with either the RAM or the RAM slots. Research on google suggests this is not an unknown problem and the finger has been poited at Windows 32bit. However, the laptop is wholly Ubuntu, but it is the 32 bit 12.04 version that I am using. Would this affect the machine's ability to recognise the RAM? I read a suggestion in another post (I think it was a similar problem with a Dell) the there was a "PAE enabled in the repository" that could support more. However I had no idea what this meant (only with Ubuntu since Easter) or whether it was relevant to 12.04.
  I am okay about using xterm, so any help will be appreciated. It's just annoying me that I can't work it out

---

### Post by cek on 2012-06-06
I had a similar issue on a Dell M4500.  I upgraded the RAM and it wouldn't boot.  This problem went away when I upgraded to the latest BIOS version.

---

### Post by d4m1r on 2012-06-06
32 bit OS can only address something like 3.2GB of RAM. Now, if you have more than that (ie 4GB), with PAE, it should be at least recognized and the same is true for Windows.

How do you know the RAM and all the slots are O.K? How do you know the laptop can support 4GB of RAM? My hunch is that it cannot as laptops that you put more RAM in than they can support will simply not boot into any OS at all....

---

### Post by Kr0nZ on 2012-06-06
32-bit operating systems will only be able to access 4GB of memory, and of that most applications will only be able to use 2GB. Remeber some of that will be used for on-board graphics and such.

But even if you were using ram that your OS couldnt use, it would just use up as much as it could.

If you are certain your ram is OK and the slots are fine, then its likely an BIOS issue.

BTW im using 32 bit 12.04 with 6 gigs of ram, but it only uses 3.6 gigs for the OS, I've had too many problems with 64 bit.

---

### Post by abduljones on 2012-06-11
Thank you for your help. It occurred to me while reading your posts with the discussion as to whether it was a bios or OS problem, that I had tried the 4gb ram on the previous  version of ubuntu. So I tried again, with 12.04. The laptop started booting up and then asked me if I wanted to confirm the change in memory or check the ram first. So thinking it might force the system into recognising the ram, I chose test memory and went off to do something else. Came back and the test screen was gobbeldygook. Doh! So I rebooted and, to my surprise, it booted properly and here I sit with 4GB of ram, no problem. Rebooted a few times and no problem. The benchmark utility is showing all the ram.
  REVISION: though it seemed okay yesterday, the lappy is now freezing. I have run a mem test on each of the units in each of the slots, and the report says they are both okay. Run them together, and i get a message after 20% saying there's an error at 3F7E8144, reading AAOOAAA instead of AAAAAAA. Whether there are further errors, i can't find out as the mem test throws a hissy fit and i have to reboot.
  The search continues....

---

