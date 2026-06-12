---
title: "Ubuntu 8.04 not booting after hard reboot"
date: 2011-05-30
forum: General Help
---

### Post by kalle_mod on 2011-05-30
Hi there!

Well I'm having a bit of trouble with my fit-pc2 with  ubuntu 8.04. It all started one day a few weeks ago when I couldn't ssh  into my box, it said access denied which meant that my password was  wrong. I'm kinda sure it isn't/wasn't since I have used it many times  before to login through ssh (and I tried several times, both over the  Internet and over LAN).

I realized that my box might have been compromised so I turned it off by hitting the on/off button for a while. Then I found [http://ubuntuforums.org/archive/index.php/t-3609.html](http://ubuntuforums.org/archive/index.php/t-3609.html)  stating how to recover/change a password. Only problem was: My keyboard  didn't respond when it dropped to the root shell (pressing Num Lock i  few times didn't turn on/off the light, it was off all the time meaning  no power for the keyboard :/).

Then I had to turn the box off  using the button again (I tried a few times, also with the "single"  argument at the end as one comment says in the link). Then I tried to  boot from my external USB drive containing the recovery image from the  fit-pc2 wiki. No matter whether I try booting from the USB drive or the  internal drive it says "Operating System not found" as the first thing  on the screen (even before GRUB). I just tried booting my laptop from  the USB drive and it worked fine?

Can anyone help me out here,  how can I boot from the USB drive and change the password on the ubuntu  installed on the internal drive, or how can I get my keyboard to respond  when dropping to a root shell (if I can get the box to boot from the  internal drive again)?

Wiping the internal drive is not really an  option, I have a few config files that I would love to keep, as well as  some website-stuff that I don't have backups for :S (after backing up these files a wipe can be done)

Kind regards
Kalle_mod

---

### Post by RHTopics on 2011-05-30
You may be having hardware problems with your fit-PC2.

Can you get into the BIOS when the computer starts to boot up?  I believe by looking at the fit-PC2 website, you should be able to get into the BIOS by pressing the F2 key.

If you can get into the BIOS, see if it is properly identifying your hard drive and your USB ports.  Also see if the boot order of devices looks okay.  By that I mean it should show USB device should boot before the hard drive if present.

---

### Post by kalle_mod on 2011-05-30
I tried all that yesterday and this morning :) Bios works fine, It labels the internal drive as primary master and I have played around with the bootsequence to see if that was the problem. I tried USB drive first, internal drive second, USB alone and internal drive alone - nothing worked as supposed :( (Just saying Operating System Not Found" or something)

---

### Post by kalle_mod on 2011-05-31
Okay in the meantime I managed to crash the install so I have to start all over now :(

This thread can be closed...

---

