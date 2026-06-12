---
title: "Qink not in repositories"
date: 2009-10-27
forum: General Help
---

### Post by arnab_das on 2009-10-27
Qink (ink level monitor) a program which i loved when i had jaunty, is no longer available in the repositories of karmic. is it still possible to install it? plz help.

---

### Post by bruno9779 on 2009-10-27
> **arnab_das said:**
> Qink (ink level monitor) a program which i loved when i had jaunty, is no longer available in the repositories of karmic. is it still possible to install it? plz help.

I have found this:

[https://launchpad.net/ubuntu/karmic/i386/qink](https://launchpad.net/ubuntu/karmic/i386/qink)

It was the first result when i googled : Qink koala

---

### Post by bruno9779 on 2009-10-27
I saw your signature a tad too late.

[https://launchpad.net/ubuntu/karmic/amd64/qink/0.3.5-1](https://launchpad.net/ubuntu/karmic/amd64/qink/0.3.5-1)

this is the AMD64 version of the .deb

---

### Post by arnab_das on 2009-10-27
thanks. but it says i require libinklevel4 when i try installing it via the .deb file. and the status is "Deleted". :( [https://launchpad.net/ubuntu/karmic/amd64/qink/0.3.5-1](https://launchpad.net/ubuntu/karmic/amd64/qink/0.3.5-1)

---

### Post by bruno9779 on 2009-10-27
see if this deb solves your dependencies

[https://launchpad.net/ubuntu/intrepid/amd64/libinklevel4/0.7.3-1](https://launchpad.net/ubuntu/intrepid/amd64/libinklevel4/0.7.3-1)

---

### Post by arnab_das on 2009-10-27
i cant thank u enough. however a slight problem. it works perfectly only when i run it as root. say when i run it as "sudo qink" from the terminal. else it shows couldnt detect printer.

---

### Post by arnab_das on 2009-10-27
okay i solved it by downloading hp-toolbox gui pack. it fortunately doesnt have root access hassles and has loads of options. thanks for the help once again :)

---

### Post by bruno9779 on 2009-10-27
You are welcome!!!
:p

just mark the thread as solved plz

---

### Post by akakingess on 2009-10-27
I am just curious, as I am running Karmic 64-bit as well, and I just went to Add/Remove programs (not the usual way I install things, but just wanted to check) and a quick search for qink brought it right up? Were not all of your repositories enabled perhaps?

---

### Post by arnab_das on 2009-10-27
> **akakingess said:**
> I am just curious, as I am running Karmic 64-bit as well, and I just went to Add/Remove programs (not the usual way I install things, but just wanted to check) and a quick search for qink brought it right up? Were not all of your repositories enabled perhaps?
multiverse is enabled for me. but qink i using an older version of libinklevel. thats not included in karmic. i think qink uses libinklevel4 and karmic has libinklevel5 in its repos. have u upgraded from jaunty or gone for a fresh install?

---

### Post by akakingess on 2009-10-28
> **arnab_das said:**
> multiverse is enabled for me. but qink i using an older version of libinklevel. thats not included in karmic. i think qink uses libinklevel4 and karmic has libinklevel5 in its repos. have u upgraded from jaunty or gone for a fresh install?

Mine is a fresh install, I always do a fresh install when changing and/or upgrading, just prefer it that way and have all my home directories on their own partition so they aren't affected.

---

### Post by arnab_das on 2009-10-28
well i had qink in repos when i had jaunty. but ever since i got karmic i didnt have it. apparently the 64 bit version of qink with libinklevel5 isnt available (although the 32 bit version is), according to google code.

btw when jaunty stable releases today, will u again do a fresh install? just asking. am in a dilemma.

---

### Post by akakingess on 2009-10-28
> **arnab_das said:**
> well i had qink in repos when i had jaunty. but ever since i got karmic i didnt have it. apparently the 64 bit version of qink with libinklevel5 isnt available (although the 32 bit version is), according to google code.

btw when jaunty stable releases today, will u again do a fresh install? just asking. am in a dilemma.

Honestly, I have 4 machines running Jaunty and the one I would do the first (test) install on is my laptop with a downed power supply. So, I am not sure whether I will be doing it on my second choice or not, since it is my server/best desktop. I will decide by the time I get off of work in the morning, and will get back to you tomorrow, probably in the morning for me (U.S. Central Standard Time).

---

