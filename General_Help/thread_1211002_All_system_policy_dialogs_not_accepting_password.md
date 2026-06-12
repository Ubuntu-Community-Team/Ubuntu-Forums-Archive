---
title: "All system policy dialogs not accepting password"
date: 2009-07-12
forum: General Help
---

### Post by ThatBum on 2009-07-12
Wazzup. I will forgo an introduction because I'm somewhat antisocial and not good at making them on these types of forums anyway. I have an urgent and befuddling problem too, so here goes...

All the "System policy prevents..." or "Authentication is required to..." or any dialog with the option to switch users to authenticate or authorise something is not accepting my known-correct password. Thus I can't mount my Windows drive (this is a dual-boot machine with XP), can't change user authorisations, can't logout or shut down if I left a root terminal open in another desk, etc. This is frustrating, because I don't seem to have many changes...I think all I did was install compiz fusion. What's strange is that sudo, gksudo, gksu, su, etc, those all work in the terminal and through Alt-F2. I can't imagine what is wrong, but to me is just FEELS like a problem a lot of people are having, but a quick search here and through Google didn't turn up anything.

I would like to know how to fix these prompts so they will recognise my password

Again, the prompts that just have the password field and grey out what's behind it (which, I understand, are related to sudo & friends) work fine...so it's GUI related somehow.

As a parting note, let me say that I installed Ubuntu for the first time about a month ago on a spare 160 gigger that I had kicking around. It's sitting in a USB enclosure now (because the drive is ATA and the mobo is SATA), if that means anything. This is my first experience to Linux, so I'm somewhat of a noob, but I'm fairly knowledgeable because I've had a long time Linux user Elmer me into it a little. I'm fairly well versed in the command line and all that, I know of RTFM, etc.

Finally, I hope I'll be around here more and help other people solve their problems as you are helping me solve mine someday. My personality will show if I stick around here long enough. ;)

I have to go now, It's approaching 2:00 in the morning here in GMT -8, as in Pacific Time. Yes, I have been trying to solve this since around noon.

ThatBum

P.S. Can't wait for Karmic!

---

### Post by ThatBum on 2009-07-12
BUMP!

Still looking for an answer for this...I suspect it's some kind of permissions problem.

---

### Post by ThatBum on 2009-07-12
Another bump. Bumpity-bump-bump-bumptastic!

Seems there's a lot of problems coming in today.

EDIT: I have ext4, maybe that's it, some kind of filesystem bug. Also, my screen lock works fine.

EDIT2: Submitted a bug report [https://bugs.launchpad.net/ubuntu/+bug/398638](https://bugs.launchpad.net/ubuntu/+bug/398638)

---

### Post by EonFromTeton on 2009-07-13
Bump
this guy really needs some help! i dont know how to help him, but someone should have the know how.

---

### Post by ThatBum on 2009-07-14
Forget it. I got tired of waiting and reinstalled Ubuntu. It works now.

---

