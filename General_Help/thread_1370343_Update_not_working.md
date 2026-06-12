---
title: "Update not working?"
date: 2010-01-02
forum: General Help
---

### Post by warfacegod on 2010-01-02
I'm not entirely sure if this belongs here or not but it seems related to me anyway. My update manager hasn't shown me any new updates in around a week. I'm thinking either something is broken in my system or ubuntu hasn't released any in a while. Ubuntu not releasing updates for this amount of time seems a bit far fetched to me, I don't think I've gone more than 2 days before this, without seeing at least one update. Thanks in advance.

---

### Post by Linuxforall on 2010-01-02
Same case here, haven't seen updates for a week, never been like this. Have tried changing update server from local to mail and still no results.

---

### Post by warfacegod on 2010-01-02
Perhaps there really aren't any. Still, I find that difficult to believe.

---

### Post by macstr1k3r on 2010-01-02
Hmm what is your kernel version?? I'm having trouble updating to the latest..

---

### Post by warfacegod on 2010-01-02
Linux 2.6.31-16

I installed them a few weeks ago.


GNOME 2.28.1

---

### Post by ratcheer on 2010-01-02
I, also, have received no updates of anything for about the past week. It seems like they have stopped releasing updates during the holidays, but that is hard to believe.

Is anyone getting any updates?

Tim

---

### Post by Svens on 2010-01-02
Heh, I wanted to start a thread with the same "problem", but it seems like developers really are getting their rest in holidays. :)
Ubuntu 9.10, 2.6.31-16 Kernel.

---

### Post by warfacegod on 2010-01-02
I just tried updating in Terminal. No luck.

---

### Post by Cheesemill on 2010-01-02
Looking at [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/) it seems there have been no updates since the 23rd Dec.

---

### Post by JackRock on 2010-01-02
I just had a partial upgrade a day or two ago.  Not sure how to look up the kernel (I'm still new to Linux), but I'm on 9.10 ubuntu, and on Gnome 2.28.1 (is that the kernel in this case?).

It might be that the upgrade was for a program, instead of the OS.

---

### Post by warfacegod on 2010-01-02
> **JackRock said:**
> I just had a partial upgrade a day or two ago.  Not sure how to look up the kernel (I'm still new to Linux), but I'm on 9.10 ubuntu, and on Gnome 2.28.1 (is that the kernel in this case?).

It might be that the upgrade was for a program, instead of the OS.

Not sure what a partial *upgrade* is. There is a terminal command to show you what kernel you have but I don't recall what it is. I just use Ubuntu Tweak to find it. No, Gnome 2.28.1, is not the kernel, it is your desktop environment. Your kernel should be something like: 2.6.31-16

---

### Post by cariboo on 2010-01-02
This really has nothing to do with security. Moved to General help.

---

### Post by warfacegod on 2010-01-02
> This really has nothing to do with security. Moved to General help.

Do you mean to say that there are no updates that make our computers safer to use or put another way: security updates? I seem to recall seeing the word security often in Update Manager.

I don't mean to be rude or second guess you by any means. However, I would qualify our computers inability to update themselves as a *_huge_* security issue. I, of course, could be misunderstanding the purpose of the security category. 

Frankly, I don't care where this thread is posted, as long as this problem gets resolved to our satisfaction or at least a reasonable explanation is offered. So far, all this thread has been is several users find that they all have the same or similar problems and you telling us we are in the wrong spot.

---

### Post by Leppie on 2010-01-02
> **JackRock said:**
> I just had a partial upgrade a day or two ago.  Not sure how to look up the kernel (I'm still new to Linux), but I'm on 9.10 ubuntu, and on Gnome 2.28.1 (is that the kernel in this case?).

It might be that the upgrade was for a program, instead of the OS.
you can find the kernel version with this command:
```
$uname -r
```

---

### Post by warfacegod on 2010-01-02
> **Leppie said:**
> you can find the kernel version with this command:
```
$uname -r
```

$uname -r = command not found

uname -r     is correct

Users new to the terminal may not realize that $ would already be there. Heck, I been using Linux for almost three years and I'm none too familiar with the terminal myself.

---

### Post by JackRock on 2010-01-02
Thanks, Warfacegod.  Yeah, I'm just now starting to realize the $ is part of the prompt, not the command.

My kernel output was "2.6.31-17-generic"

As for the "partial upgrade", that's simply what the system called it.  The exact words.  I had a similar situation when upgrading to Karmic.  Not all the programs were fully updated, so I had to wind up doing a CD install from the boot.  Not so this time.

---

### Post by Leppie on 2010-01-02
> **JackRock said:**
> My kernel output was "2.6.31-17-generic"
i believe that kernel is from the "proposed" (testing) repo.

---

### Post by warfacegod on 2010-01-02
> Thanks, Warfacegod. Yeah, I'm just now starting to realize the $ is part of the prompt, not the command.

Certainly. Your partial upgrade thing sounds like either you had internet issues during your upgrade or software/package conflicts. Just a guess.


I'm starting to lean more towards the idea that there may simply be no updates, in light of Cheesemills' post but not much.

[http://archive.ubuntu.com/ubuntu/dists/karmic-updates/]("http://archive.ubuntu.com/ubuntu/dists/karmic-updates/")

This does not explain macstr1k3r's inability to update to the newest kernel.

Some advice from someone allot more experienced would be nice.

---

### Post by john newbuntu on 2010-01-02
Just had one a few minutes back for gcalctool, libasound and screensaver.  Yes had nothing prior to that for almost a week.
Thanks Cheesemill for pointing out the update locations.

---

### Post by Svens on 2010-01-03
> **john newbuntu said:**
> Just had one a few minutes back for gcalctool, libasound and screensaver.  Yes had nothing prior to that for almost a week.

Yes, I got my updates too few minute ago for calculator, screensaver and libsound. :)

---

### Post by Linuxforall on 2010-01-03
Same here that means all is well.

---

### Post by warfacegod on 2010-01-03
I just did as well. However, I am loath to mark this as solved because nothing actually was. It just seems to be working again. I'm going to mark it solved at the end of the day or until an explanation is posted whichever is first.

---

### Post by Leppie on 2010-01-03
i think the developers took a break as well and there were no really urgent issues presented during the festivities.

---

### Post by warfacegod on 2010-01-03
Some kind of warning would have been nice. Although, I didn't look at the ubuntu main site so maybe we're all just twits for not going there.

---

### Post by warfacegod on 2010-01-03
Okay, christmas break it is. It's either that or all of Cannonical forgot to show up for work for a week. Marking as solved.

---

### Post by warfacegod on 2010-01-04
```
sudo apt-get update
```

```
sudo apt-get install
```


I *think* that's it. The top one will find them anyway.

---

