---
title: "Jaundiced Jackass killed by falling Koala! Can't mount anything post grub."
date: 2009-10-30
forum: General Help
---

### Post by euphemus on 2009-10-30
I should have known better... JJ was working OK - OH WHY OH WHY DID I UPGRADE? It will be another few months of ironing out bugs...

Upgraded from JJ to KK after enduring (edit: should be "ensuring" - Freudian typo) JJ was fully up to date.

Restarted fine. That was the first time...

Then after getting past grub, it wanted to do a full system check, I ESC to cancel (busy), then...

**It can't mount, something to do with fdisk: "/dev/disk/by-uuid/20f373f8-77c7425d-8093-7d7d430b27a7" - whatever that means.**

Help! That's a word I understand after years of Ubuntu.

I have a 1 Gig disk; 30 Meg for XP. When I have the time I will remove KK completely and turn the whole disk over to the Empire. At least they don't stuff me around like this, I seem to avoid their viruses, and its free (if you know what to do!) just like Ubuntu.

Did I say HELP!

---

### Post by alphaniner on 2009-10-30
First, post an exact copy of the error.

UUID is one of the ways partitions are identified.  Boot into a live cd and post the output of **sudo fdisk -l** and **blkid**.  See if you can mount the system partition.  If you can, post the output of the /etc/fstab file that is on it.

---

### Post by euphemus on 2009-10-30
First, I can't get into MY computer!

Forget it - I give up - keep your ridiculous OS. This happens every time.

---

### Post by SadaraX on 2009-10-30
> **euphemus said:**
> First, I can't get into MY computer!

Forget it - I give up - keep your ridiculous OS. This happens every time.

Haha. I have been using Linux as my desktop OS for 7 years and this is certainly the first time this has ever happened to me. It's no simple problem.

Still, calling it ridiculous is just wrong. Anyway, best of luck. If I find a solution, I will post it.

---

### Post by SirBismuth on 2009-10-30
> **euphemus said:**
> First, I can't get into MY computer!

Forget it - I give up - keep your ridiculous OS. This happens every time.

Ok.

:-({|=

B

---

### Post by roccivic on 2009-10-30
You have only yourself to blame. Upgrading an already running OS is asking for trouble. Don't know why the ubuntu guys even offer this option....

I always keep a spare empty partition for a fresh install, this preserves whatever other OS I'm running from being effed in the behind.

---

### Post by tempus on 2009-10-30
> **euphemus said:**
> First, I can't get into MY computer!

Forget it - I give up - keep your ridiculous OS. This happens every time.

euphemus,

the same thing happened to me...no boot up but a slightly different error was shown. I needed to do a clean install to have KK work properly. somehow things get messed up during an upgrade that cannot be undone easily...at least less experienced people. I would say to give it another chance becuase the bugs will be worked out as soon as is humanly possible.

---

### Post by euphemus on 2009-10-30
I am a little more calm today and what I say is completely honest and thoughtful. I have been using Ubuntu for many years. I have nearly finished my backup and will shortly convert my machine wholly to xp.

An ancillary problem, that becomes a primary frustration, with being an Ubuntu user is that when things go wrong and you are frustrated, other Ubuntu users take great offense at your honest (if angry) feedback: its as if I should be grateful for this annoyance, for the privilege of it. Fiddling around in the code seems to be an assumed prerequisite for the user - I shouldn't complain.

Its frustrating: I CAN do it! I  have been working with computers since I was 11 (way back last century sometime), all my life, but I have other things I NEED to do now and can't do them because my OS NEEDS my attention first. My math teacher's maxim "get your basics right and everything else falls into place" has served me well - on this occasion however I have the expectation that the OS (my basics) will work without my assistance, because it doesn't other things are not resolved.

Fair's fair: Ubu is free and when it works it works ok, it does stuff windows won't or can't do, and in doing so has forced microsoft's hand, they have had to improve, and not having the virus vulnerabilities is fantastic; but it does come at a cost.

Why replace an already working install?: its not really working - its a compromise installation. When I install a release there is always somethings not working right: I research it (sometimes for weeks); fiddle with it (sometimes for months); sometimes its fixed and sometimes not. In the latter case I disable or ignore OS options or programmes because I simply can't get a solution (and I do try very hard to find one).

So when I get updates (everyday) I install them hoping that the problem causing that little glitch I have ignored, or the ap that is not working, to be remedied. I trust the Ubu's have checked it out. Sometimes the update causes more problems. Most times it doesn't fix the already existing ones. 

In a similar vein, when there is a new release I install it: the hope that there will be a remedy therein drives me on. But there isn't - not one install has gone smoothly. I started using Ubu because I wanted to beleive, I genuinely supported its aims and the vision of the community; but the result is I still am fixing things years on, sometimes the same things. I have put in the effort and am tired, and frustrated with the results.

I've received posts (as I do often) saying "it always works for me"" well good for YOU - but take a look at the forum. Every time a new release is issued the posts for assistance increase. YOU **are** Robinson Crusoe there!

If you want to use it, do; if it works for you - great; but I am tired of it - its too hard and I have other things to do. I just want to switch on my machine and have it work; Xp actually does that as a minimum. I am not an OS developer and I don't want to be!

---

