---
title: "Do you like challenges? Ubuntu system after upgrade"
date: 2009-09-27
forum: General Help
---

### Post by _godbout_ on 2009-09-27
Hi guys!

I'm gonna start the thread very slowly... 
I've used Ubuntu for 2 years without much trouble but some days ago I made a basic update, as usual. I got a message of broken dependencies, click 2 or 3 boxes and reboot. I'm stuck to the command line since.

I've tried to gather information here and there, rebooted many times and have tried many options, it never worked. 

So, I've got 2 solutions here:
-format and install again from scratch
-try to play and learn stuff by making this install work again

The good news: i can connect to the internet in command line, so I get check stuff from the repositories. 

If I'm alone on the journey, i'm gonna give up. If some people want to join, we can play together! :D

So, to start slowly, here's what I've done lately:
-sudo apt-get clean
-sudo apt-get -f install (can't write file anywhere, lots of dependencies errors)
-sudo dpkg --configure -a (finishes with a list of packages with problems and a sentence saying that it stopped coz too many errors, hehe)
-sudo apt-get update (dependencies errors installing)
-sudo apt-get upgrade (same same)

then i've checked with
- sudo apt-get -f remove (dep. errors)
- sudo apt-get remove -f 'package_name' (some removed, some got errors while removing)
-sudo apt-get -f install (dep. errors)

That's about it.
If you want to join the journey, let me know, and i'll start giving logs and stuff needed.

Thanks in advance!

---

### Post by _godbout_ on 2009-09-27
I've updated all the packages tonight, I can't even install one. Got a message saying that the configuration of libattr1 is impossible. By investigating, I got that it's because libc6 is not installed. If I try to install libc6, I've got other problems, and it going in cycle. A needs B, B needs A.

---

### Post by 3rdalbum on 2009-09-27
Try downloading libc6 and libattr1 straight from [http://packages.ubuntu.com](http://packages.ubuntu.com) and instaling them manually using sudo dpkg -i.

Also, you might be able to get some clues from running:

```

sudo dpkg --audit
```

---

### Post by darkstaar on 2009-09-28
> **_godbout_ said:**
> I'm gonna start the thread very slowly...

Right...

Well, since you've been plagued with this problem for "some days" and no one seems to want to take up your "challenge", I'll suggest that it's far easier and faster to just simply reinstall. It takes less than 30 minutes.

Of course, you do have a separate /home partition, Right?

Reinstalling all of your installed apps with just a few clicks is fast and easy too since you surely remembered to "Save Markings" often in the Synaptic Package Manager. You did remember to do this. Right?

So, start your reinstall now and you'll be back on here in 60 minutes or less with a fully working system in the same (or better) condition it was in before your problems.

Trust me. You'll be pleasantly surprised at how easy and effective this solution really is.

---

### Post by _godbout_ on 2009-09-28
I've downloaded them from the ubuntu packages and tried with dpkg - i already but it didn't work. I'll copied the error messages tonight. I'll check the -audit option also, never tried that one. Thanks!

darkstaar -> well, maybe I was not clear enough that this is a "challenge" (yah, I put the double-quotes also like you for the style). I'm not interested by a new half an hour install, I want to learn more about the system. And no need to be so arrogant.

---

### Post by 3rdalbum on 2009-09-28
> **darkstaar said:**
> Right...Well, since you've been plagued with this problem for "some days" and no one seems to want to take up your "challenge", I'll suggest that it's far easier and faster to just simply reinstall. It takes less than 30 minutes.

If you know how to fix dpkg problems, then it can take less than 10 minutes to fix one, and you learn a lot.

---

### Post by _godbout_ on 2009-09-28
> sudo dpkg -i/var/cache/apt/archives/libc6_2.7-6_i386.deb 

gives

> A non-dpkg owned copy of the libc6-i686 package was found.
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library and try again.
dpkg: error processing /var/cache/apt/archives/libc6_2.7-6_i386.deb (--unpack):
subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
/var/cache/apt/archives/libc6_2.7-6_i386.deb

> sudo dpkg --audit  returns nothing.

I'm gonna investigate more on the first behavior.

---

### Post by _godbout_ on 2009-09-28
End of the story.
I've followed some stuff from the web about people having the same problem, didn't work. I removed a bit too much, now I can't login or launch anything, plus kernel panic.

I'm gonna do a fresh install when I have time.
Thanks for the help anyway! :)

---

### Post by darkstaar on 2009-09-30
> **3rdalbum said:**
> If you know how to fix dpkg problems, then it can take less than 10 minutes to fix one, and you learn a lot.

True. But as the OP has already pointed out, he/she has already had a non-functioning system for several days. That said, an easy solution was apparently not what the OP was looking for anyway.

> **_godbout_ said:**
> darkstaar -> well, maybe I was not clear enough that this is a "challenge" (yah, I put the double-quotes also like you for the style).

Sorry. I guess I just (wrongly) assumed that you wanted a functioning system.

> **_godbout_ said:**
> And no need to be so arrogant.

Again, my mistake. Good luck with whatever you're attempting to achieve.

---

