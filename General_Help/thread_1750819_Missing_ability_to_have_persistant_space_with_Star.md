---
title: "Missing ability to have persistant space with Startup Disk Creator in Natty"
date: 2011-05-05
forum: General Help
---

### Post by inameiname on 2011-05-05
Ever since I installed Ubuntu Natty (from a fresh install), I have been unable to create persistant space on any of my Ubuntu Natty Remastersys backups with Startup Disk Creator. 

I have always been able to include this in every Ubuntu backup through Startup Disk Creator, but with Natty, it stays greyed out as an option. From time to time this happened in prior versions of Ubuntu, but some refreshing or whatever fixed that, but not now.

It does not matter what media I use, USB, SD, or whatever, all have a greyed-out persistant option.

Also, unlike past versions, when running Startup Disk Creator, twice it asks for me to input my password as a security measure. Not sure why, or if that matters, but I figured I would mention it.

Oh, and thinking it was my media, I did try erasing through Startup Disk Creator and having it automatically format, but that resulted in the same error. I even moved the ISO to other folders to see if that was the issue, as I know it can be for some, but to no avail.

Thanks in advance.


UPDATE:

I found this posting of a similar bug occurring in Lucid...if it is the same one, a sad sign that it probably won't get fixed anytime soon. 

[https://wiki.edubuntu.org/UbuntuBugDay/20110303](https://wiki.edubuntu.org/UbuntuBugDay/20110303)

---

### Post by inameiname on 2011-05-06
Bump...

---

### Post by inameiname on 2011-06-18
Bump... 


I cannot believe I'm the only one who doesn't have persistent space anymore using the Startup Disk Creator in Natty.

---

### Post by Matt 6:27 on 2011-08-24
You're not the only one.  I created a usb startup drive just after 11.10 Alpha 3 came out and could create the persistent space allocation (this was maybe a week ago). I just downloaded today's build (11.10 on 8/24/11) and can't create any storage space on the usb drive.

---

### Post by inameiname on 2011-08-24
> **Matt 6:27 said:**
> You're not the only one.  I created a usb startup drive just after 11.10 Alpha 3 came out and could create the persistent space allocation (this was maybe a week ago). I just downloaded today's build (11.10 on 8/24/11) and can't create any storage space on the usb drive.

So it sounds like you are saying 11.10 Alpha had fixed the issue I was having with the Startup Disk Creator in Natty, but that a new update today messed that up again? 

I really wonder what is the bug or the issue, and why don't more people notice it, as it is a fairly big one in terms of that specific package. I mean, those that 'update' it should spot it pretty easily. 

Anyway, let's just hope the solution fixes itself. That, or, perhaps file a bug on Launchpad about it, maybe that'll make it more known.

---

### Post by dcstar on 2011-08-25
> **Matt 6:27 said:**
> You're not the only one.  I created a usb startup drive just after 11.10 Alpha 3 came out and could create the persistent space allocation (this was maybe a week ago). I just downloaded today's build (11.10 on 8/24/11) and can't create any storage space on the usb drive.

Which is why **all **issues with pre-release software belong in that **specific** forum - so they can be fixed before release.

---

### Post by inameiname on 2011-08-25
> **dcstar said:**
> Which is why **all **issues with pre-release software belong in that **specific** forum - so they can be fixed before release.

True, but this issue isn't just a pre-release bug found in 11.10, but in the 11.04 Natty's 'stable' version of this package.

---

### Post by Matt 6:27 on 2011-08-25
Right, it looks like an earlier 11.10 build was ok, but not now.  I generally delete old builds, but happened to have a copy of 11.04 on a drive, so I opened Startup Disk Creator (SDC) and pointed to my 11.04 .iso file instead of my 11.10 .iso (which was still listed on the top of the SDC window) ... when I did so, the option to create persistent storage was no longer grayed out and became available not only with respect to the 11.04 iso, but also the 11.10 build.  I can't explain why or how, but this worked for me so you might want to give it a try.  Perhaps this is a SDC issue and not a Natty or Oneiric issue?


> **inameiname said:**
> So it sounds like you are saying 11.10 Alpha had fixed the issue I was having with the Startup Disk Creator in Natty, but that a new update today messed that up again? 

I really wonder what is the bug or the issue, and why don't more people notice it, as it is a fairly big one in terms of that specific package. I mean, those that 'update' it should spot it pretty easily. 

Anyway, let's just hope the solution fixes itself. That, or, perhaps file a bug on Launchpad about it, maybe that'll make it more known.

---

### Post by inameiname on 2011-08-27
> **Matt 6:27 said:**
> Right, it looks like an earlier 11.10 build was ok, but not now.  I generally delete old builds, but happened to have a copy of 11.04 on a drive, so I opened Startup Disk Creator (SDC) and pointed to my 11.04 .iso file instead of my 11.10 .iso (which was still listed on the top of the SDC window) ... when I did so, the option to create persistent storage was no longer grayed out and became available not only with respect to the 11.04 iso, but also the 11.10 build.  I can't explain why or how, but this worked for me so you might want to give it a try.  Perhaps this is a SDC issue and not a Natty or Oneiric issue?

I don't really know why the type of ISO (being 11.10.iso, or 11.04.iso, or whatever.iso) would matter, but I guess that might be a reason, IDK. Mine are Remastersys 11.04 ISOs, fyi. And I do believe its a SDC issue, not necessarily an Ubuntu version one. Perhaps trying different versions of SDC would determine whether or not its really that.

---

