---
title: "PAE and 6GB RAM = no compiz, why?"
date: 2011-03-19
forum: General Help
---

### Post by karrank% on 2011-03-19
Apologies if this has been asked/answered already, my searches haven't turned up anything useful. 

Running Lucid 32bit with 2GB RAM & bought 4GB on sale , installed PAE kernel, and now having sluggish display probs, find compiz disabled, 

here's the h/w if it helps.

Asus M4A785-M board, ATI RadeonHD4200 IGP (ati prop driver installed & in use)

6GB (3 X2GB ddr2 800MHz) corsair xms2 

Where do I need to start looking to solve this?

Do i need to enable a repository or something?

Thanks for looking, will provide other info if missing.

---

### Post by karrank% on 2011-03-19
ok, I removed the frglx proprietary driver and that seemed to have got compiz more or less stable, but now the dual-screen goodness I was depending on evaporated. 

Not exactly solved, but manageable for the time being.

If I switched to 64-bit Lucid, could  I do it alongside my 32-bit install or is that an asinine q? As in a dual-boot scenario? 

What about compatibility of some of my older equipt and browsers, etc? Canon N650U scanner, HP 812C printer, Logitech kb, mouse & webcam? ff 3.6.15? flash 10.2?

Anyway, thanks for looking.

---

### Post by idoitprone on 2011-03-19
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

oouch graphic cards. linux does not exactly have the greatest history to graphic card support. that is prob wat went wrong

---

### Post by karrank% on 2011-03-19
> **idoitprone said:**
> [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

oouch graphic cards. linux does not exactly have the greatest history to graphic card support. that is prob wat went wrong

Thanx I checked out the link & had already confirmed my cpu mobo & mem are fine, just concerned about the older peripherals listed.

and flash.

and yeah, a little surprised at the driver incompatibility thingy, as all my previous exp implementing ati drivers in linux worked fine.

oh well.

---

### Post by idoitprone on 2011-03-19
Ur pretty lucky with ur video cards, if you had not hit a problem. I heard ati make pretty bad driver in comparison to nivida. Linux does not have a good history of good video drivers. It so bad that even Linus himself gives advice.

[http://www.realworldtech.com/beta/forums/index.cfm?action=detail&id=115488&threadid=115450&roomid=2](http://www.realworldtech.com/beta/forums/index.cfm?action=detail&id=115488&threadid=115450&roomid=2)

You might hit a regression with new kernel, dawm if i know.
[https://bugzilla.redhat.com/show_bug.cgi?id=629427](https://bugzilla.redhat.com/show_bug.cgi?id=629427)
here other people have problem with that particular video card
 [http://ubuntuforums.org/showthread.php?t=1358746](http://ubuntuforums.org/showthread.php?t=1358746)

---

### Post by karrank% on 2011-03-19
Luck o' the Irish, I guess.

---

### Post by karrank% on 2011-03-19
The question for me now becomes how and/or whether to migrate to 64bit lucid.

---

### Post by idoitprone on 2011-03-19
> **karrank% said:**
> The question for me now becomes how and/or whether to migrate to 64bit lucid.

back up then clean install

[http://www.linuxquestions.org/questions/linux-desktop-74/switching-from-ubuntu-32-to-kubuntu-64-bit-508769/](http://www.linuxquestions.org/questions/linux-desktop-74/switching-from-ubuntu-32-to-kubuntu-64-bit-508769/)

changing from 32 to 64 or vise-versa not supported

You can try to migrate from 32 bit to 64 manually, but its tricky and not worth it. Btw, if you actually do it, then tell me, because I always wondered how.

---

### Post by dcstar on 2011-03-19
> **karrank% said:**
> The question for me now becomes how and/or whether to migrate to 64bit lucid.

Create a separate /home (many detailed instructions available) and then just install 64-bit.

---

### Post by dcstar on 2011-03-19
> **karrank% said:**
> Apologies if this has been asked/answered already, my searches haven't turned up anything useful. 

Running Lucid 32bit with 2GB RAM & bought 4GB on sale , installed PAE kernel, and now having sluggish display probs, find compiz disabled, 
.........

32 bit systems **only** directly address data space below 4GB. PAE is basically a kludge that allows RAM to be accessed in 4GB chunks in 32-bit systems but it comes with performance issues.

In 32-bit systems video cards (and other motherboard resources) must be mapped in the <4GB range so all processes can access them, sometimes if you install RAM >4GB and still use a 32-bit OS then you can have issues.

Look in the BIOS settings for options on mapping things differently, or use a 64-bit OS that will take care of it.

---

### Post by karrank% on 2011-03-19
> **dcstar said:**
> 

Look in the BIOS settings for options on mapping things differently


Thanks, already enabled memory hole remapping (think we're talking about the same thing)

And a clean install is the only way to get 64 bit, correct? No such animal as a 32/64 dual boot? (excuse the ignorant q)

---

### Post by idoitprone on 2011-03-20
> **karrank% said:**
> 

And a clean install is the only way to get 64 bit, correct? No such animal as a 32/64 dual boot? (excuse the ignorant q)

yep, think about it 32 bit is backward compatitable with 64bit. To be honest, your just wasting space that could of been used for the faster 64 bit os. Of course you can dual boot. People dual boot all the time to test other os. lol this netbook have 3 oses lol

---

### Post by karrank% on 2011-03-21
Thanks for your help David and idoitprone, gonna stick with 32 bit as everything else works effortlessly-- sporadically chipping away at the frglx driver issue as I have time, Meanwhile, I'll mark this solved but if you have any epiphanies about this feel free to alert me.

--K

---

### Post by 5149.5 on 2011-03-21
I was having trouble with compwiz and had tried quite a few things. I had about given up and then today I did an update of a lot of X11 sources, rebooted and the visual effects came to life.

---

### Post by karrank% on 2011-03-22
> **5149.5 said:**
> I was having trouble with compwiz and had tried quite a few things. I had about given up and then today I did an update of a lot of X11 sources, rebooted and the visual effects came to life.

Actually compiz works fine without the frglx driver since I went with the PAE kernel. My only issue now is getting the dual screen (specifically cloning or mirroring, whatever it's called) working.

---

