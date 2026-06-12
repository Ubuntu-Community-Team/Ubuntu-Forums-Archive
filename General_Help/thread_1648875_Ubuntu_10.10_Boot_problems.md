---
title: "Ubuntu 10.10 Boot problems"
date: 2010-12-19
forum: General Help
---

### Post by Lethedethius on 2010-12-19
Ok guys, I just wiped my TB drive from a really horrible build of Ubuntu *it was having sound problems and kernel issues with the video*.  I downloaded 10.10 last night and did an upgrade this morning, it installs perfectly no issues, but when I go to reboot I get nothing, I just get a black screen with the _ that blinks constantly as if it's waiting for me to do something.

I'm working from Live CD right now, same disc.

I have Phenom II 3.1-5Ghz :)
6GB DDR3
ATi Radeon HD 4670 *I think*
1.3TB drive with Windows 7 *which has failed recently*
1.0TB drive with Ubuntu 10.10 which has been partitioned by the prior install to have a 17GB swap.

What the frack is going on!?  I'm not a total moron am I? Maybe I should type Open Says Me!  Oh also I went thru boot/grub/ and I did not see a menu.lst...  Could I have a fouled up grub folder?  If you have a solution post on here but also e-mail me at [EMAIL="lethedethius@gmail.com"]lethedethius@gmail.com[/EMAIL] as I check it often! :)

---

### Post by dFlyer on 2010-12-19
The file your now looking for with 10.10 is grub.cfg. As far as knowing what your problem is, sorry I can't help you there. I would look into the above file, but not make any changes without knowing what your doing.

---

### Post by marin123 on 2010-12-19
i also get a blinking cursor, but after a few seconds it boots normally. how long did you wait? what happens if you press ctrl+c?

---

### Post by Lethedethius on 2010-12-19
I let the cursor sit for about an hour before I gave up... I haven't pressed  Ctrl+C.  I'm downloading Fedora 14 right now, so if Ubuntu fails me I'll switch to Fedora 14 *I hate being a betrayer to Ubuntu, as I switched to it because Fedora failed me 2 years ago, but... it's what works right?* Once I burn Fedora 14 I'll be sure to try Ctrl+R and let all of ya'll know the results.  This is a problem that may be plaguing other users, and if so it should be fixed because it may turn several people off of a free Open Source OS and force their hand in just paying for Small-Limp(Micro-Soft) Windows 7.

---

### Post by Lethedethius on 2010-12-19
ok I tried CTRL+C and nothing.  Really irritating!  I'm about to install an Older Ubuntu Disc and move to Fedora from there.  This is killing me :(, I got homework to submit for college...  Any ideas people?

---

### Post by marin123 on 2010-12-19
i can only tell you to try installing ubuntu again, maybe stable version (10.04).
did you remember what were the updates?
maybe you got some grub upgrade or kernel upgrade that messed up grub. i really cant help you since i've never had any issues like this. i must say that i have a home desktop that my mom uses and i have installed 9.10 and have been upgrading since and never had any problem. i must be lucky bastard, never had upgrade problem haha :D

---

### Post by Lethedethius on 2010-12-19
well it's working now, there was one of two things that fixed it, I did live CD and installed via live cd after I loaded the desktop.

The other possible solution was I switched out the boot order. <-- I think this is the one that matters however.

---

### Post by techunit on 2010-12-19
What build of Ubuntu were you using before the upgrade? I would recommend you try a fresh install it really is your best bet. You can use your Live CD to back up data to a external drive. Good Luck, and best regards.

---

