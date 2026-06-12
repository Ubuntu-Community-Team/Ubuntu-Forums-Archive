---
title: "How do we ger rid of Grub2?"
date: 2009-11-12
forum: General Help
---

### Post by old_salt on 2009-11-12
How can one revert back to the old Grub on version 9.10? This is 
T E R R I B L E !!! :confused:

Went from a 22second boot to over 70 seconds. What a piece of trash and I can't even understand why the Devs even gave thought to putting a Beta bootloader into a final release!  :shock:

Anyone know how to revert back to the old bootloader? 

Thanks

---

### Post by undecim on 2009-11-12
just install the grub package```
sudo aptitude install grub
```

---

### Post by zeonite on 2009-11-13
I agree.  I installed Grub2 and found the same thing, takes twice as long to boot and yet doesn't provide anything new.

Go here, and scroll down to the bottom where it talks about uninstalling Grub2 and reinstalling the old Grub.

[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading) to GRUB 2

---

### Post by billgarza on 2009-11-13
I DONT KNOW BUT I REALLY WANT TO KNOW HOW TO GET RID OF GRUB?

[URL="http://www.solarpowerforyourhouse.com/solar_energy_home_systems.html"]
[/URL]   [Solar Panel]("http://www.solarpowerforyourhouse.com/solar_energy_home_systems.html")

---

### Post by old_salt on 2009-11-13
> **zeonite said:**
> I agree.  I installed Grub2 and found the same thing, takes twice as long to boot and yet doesn't provide anything new.

Go here, and scroll down to the bottom where it talks about uninstalling Grub2 and reinstalling the old Grub.

[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading) to GRUB 2

Thanks zeonite - great reference however...... I think the majority of E/K/Ubuntu users and even some fairly experienced ones would hesitate at that kind of operation for fear of toasting their systems. 

I'm confident that Grub2 in time will be fine but the fact that Canonical agreed to put a "Fledgling Beta" major system component into a final release concerns me. Last release cycle was the omission of Oo3, before that was a flaky kernel, before that was no AMD support along with USB devices. 

You see the trend here? I'm puzzled as to this behavior. The devs are missing the point and are not addressing users needs or requests such as; Desktop Publishing, Photo Printing, a comparable app to Visio, scanning support? I can keep going but these encompass a major area that MAC and Winblows excels at and is what is needed in Linux as well to keep pace. If this area was addressed, I and others could drop dual boot systems which may be part of the reasons why Grub2 takes so long to boot based on my understanding of the information in the link you provided.

Thanks again and I will mark this solved after a few hours in case someone else wants to chime in or add their 2cents worth in hopes maybe the devs will take notice?

Thanks everyone.

---

### Post by Simian Man on 2009-11-13
> **old_salt said:**
> Went from a 22second boot to over 70 seconds. What a piece of trash and I can't even understand why the Devs even gave thought to putting a Beta bootloader into a final release!  :shock:

Because Ubuntu didn't want to be stuck with the older grub in their LTS version, but also didn't want to introduce a new bootloader for the LTS.  So they got Karmic users to do a little bug testing.

---

### Post by ranch hand on 2009-11-13
You are going to run into problems reverting to grub-legacy the way proposed.

Use this guide;

[http://ubuntuforums.org/showthread.php?t=1298932&highlight=kansasnoob](http://ubuntuforums.org/showthread.php?t=1298932&highlight=kansasnoob)

Read all the way trough before doing anything and you should miss a ll the pitfalls.

---

### Post by old_salt on 2009-11-13
> **Simian Man said:**
> Because Ubuntu didn't want to be stuck with the older grub in their LTS version, but also didn't want to introduce a new bootloader for the LTS.  So they got Karmic users to do a little bug testing.

Wouldn't it have made sense to provide users an option during install with a brief explanation so users can make a choice? That is what Linux is about right? 

I understand what your saying and it makes sense but also doesn't. Basically the Devs were on the fence on this one and tossed a coin or something? A regular update down the line from Grub to Grub2 could have been very easily accommodated without issue. 

Your mention of LTS in their dilemma also tells me they are more concerned about perception now more so than in the past which is affecting their decision making process. This is not what got Ubuntu where it is today.

---

### Post by Simian Man on 2009-11-13
I think it's a very bad decision as well.  I was just explaining what I think their motives were for shipping a bootloader that isn't even considered stable enough for Fedora yet.

---

### Post by old_salt on 2009-11-13
Not blasting you, I think your right and I think the Devs need to not forget what got them here. Ubuntu is #1 but it wasn't this or the last release that did it. It was the project as a whole which seems to be souring a little.

---

### Post by old_salt on 2009-11-13
> **ranch hand said:**
> You are going to run into problems reverting to grub-legacy the way proposed.

Use this guide;

[http://ubuntuforums.org/showthread.php?t=1298932&highlight=kansasnoob](http://ubuntuforums.org/showthread.php?t=1298932&highlight=kansasnoob)

Read all the way trough before doing anything and you should miss a ll the pitfalls.

Thanks!!!!!!

I think it might be best to wait it out to see if fixes develop or give those instructions a try. As a last resort, pick another Distro until the community as a whole decides the fate of Grub2.

Based on the article you referenced, seems there was very little to no testing done on dual or multi-boot systems and for those that did, there were very few. 

I think wrong priorities were introduced and once again a major release with no progress made on a huge void Linux has compared to MAC or Winblows.

Maybe next year? or within 5 years?

---

### Post by lykwydchykyn on 2009-11-13
> **old_salt said:**
> Last release cycle was the omission of Oo3, before that was a flaky kernel, before that was no AMD support along with USB devices. 

You see the trend here? I'm puzzled as to this behavior. The devs are missing the point and are not addressing users needs or requests such as; Desktop Publishing, Photo Printing, a comparable app to Visio, scanning support? 


Understand that "the devs" are not some group of guys who sit around a table every morning and debate whether or not to install a new bootloader or write a replacement for Visio.

Ubuntu repackages software projects from other sources and brings them together into something usable as an OS.  If there is no free, open-source "replacement for $COMMERCIAL_SOFTWARE" out there, they can't include it.  

What's more, if the upstream source releases a flaky version of their software, Ubuntu has to decide whether to include the flaky version or stick with the current version (which may lack features).  Not always an easy choice, and not always popular either way (note that you mention both that OOo was not the latest and greatest, and that grub is not the old stable version -- clearly, either choice frustrates users).

If you stop and consider the way Ubuntu is put together and what the team actually does, it makes more sense.

> **old_salt said:**
> Wouldn't it have made sense to provide users an option during install with a brief explanation so users can make a choice? That is what Linux is about right? 


The first time I installed Debian six years ago, it was the hardest OS install I'd ever done.  It took 3 hours, most of which was dpkg asking me incomprehensible questions along the lines of "libfoo-2.1.2a has experimental support for M72 file data, but only if buffer_extents = 24 in foobaz.conf.  Do you want to enable this option?"

The driving ethos behind Ubiquity is to ask the bare minimum of questions from the user, and I think it's worked out great.  How many technical questions do you want to bombard the user with during install?

> 
I understand what your saying and it makes sense but also doesn't. Basically the Devs were on the fence on this one and tossed a coin or something? A regular update down the line from Grub to Grub2 could have been very easily accommodated without issue. 

From all accounts, the original GRUB is an unmaintainable mess of spaghetti code and hacks.  GRUB2 has been years in development and promises a world of improvements.  

But at some point, someone has to start using it or the last round of bugs won't get found and worked out.  Its inclusion in Karmic should help get it stable enough to put the old GRUB out to pasture.

See [http://www.gnu.org/software/grub/grub-2-faq.en.html](http://www.gnu.org/software/grub/grub-2-faq.en.html)


I think the point about LTS is that LTS is maintained for 5 years, and nobody is quite sure they want to be maintaining GRUB 1 in 2015.

---

### Post by old_salt on 2009-11-13
lykwydchykyn, we both seem to understand each other yet the problem is in front of us all. There is a disconnect between users and Devs. Without the Devs, users have nothing, without the users, the devs might as well be MS Coders. There has to be some measure of communication or else resentment is going to set in which does nobody or anything any good.

---

### Post by ranch hand on 2009-11-13
One thing to consider is that grub-legacy (0.97) is no longer supported.

If you hunt the archives, you will find that grub-legacy, that we have come to love, was about as popular as a turd in a punch bowl when it came out.

I got into 9.10 testing with alpha1.  Grub2 was introduced with Alpha2.  There were some problems with it and multi boot on multi drives.

The main problem that still exists is not part of the grub project.  It is os-prober and it has come a very long ways too.

---

### Post by egalvan on 2009-11-13
> **old_salt said:**
> Wouldn't it have made sense to provide users an option during install with a brief explanation so users can make a choice? That is what Linux is about right? 

This is very sensible, but the implementation may have been difficult.
I have no clue, so no opinion.

> I understand what your saying and it makes sense but also doesn't. Basically the Devs were on the fence on this one and tossed a coin or something? A regular update down the line from Grub to Grub2 could have been **very easily accommodated without issue.** 


again, no way to tell how **easy** this would be.

> Your mention of LTS in their dilemma also tells me they are more concerned about perception now more so than in the past which is affecting their decision making process. This is not what got Ubuntu where it is today.

Long Term Support (LTS) versions are all about STABILITY and SECURITY, not PERCEPTION.
Almost nothing in an LTS is upgraded past a major-point number, and even some minor-point upgrades are not allowed.
LTS have five years of support (on the Server), so trying to keep grub v 0.97 out of them is something the devs probably have in mind.

And as for GRUB LEGACY being "mature", yes it was, but it is version 0.97

GRUB2 is (last time I checked) version 1.97
and has been around quite some time now.

And as for the  longer boot times being caused by GRUB2,
this would have to be proved with two identical installs,
differing only in GRUB vs GRUB2.

9.10 has many more changes, not just GRUB2.


P.S.
and it's curious that you state that OOo was too old, and GRUB was too new.

Which should it be? :)

---

### Post by ranch hand on 2009-11-13
Actually what we are using is 1.97beta4.  1.97 has been released but I do not know when we will be seeing it.

What has been around for some time is 1.96.

I hope to see an update of os-prober myself,  the bugger is pretty good with Debian based systems and MS but breaks down after that (as it did in grub 0.97).

There is some info in the link in my sig and the first three links in it are great.

---

### Post by AndiB on 2009-11-13
I'm all in favour of progress when it comes to GRUB v2, but I'm really dissappointed by the the beta version. So slowww. Sure the developers need to test it but there are other ways. Combine this with the frankly pathetic 9.10's start up screen and you wonder why on earth I upgraded so quickly to this version.

---

### Post by old_salt on 2009-11-13
egalvan,

Ooo was released a month or 6 weeks prior to the Ubuntu release and was included in almost every other Distro's fall release. Fedora, Suse, Mandriva all included Ver 3 upon release. 

I can live with an app issue here and there compared to a system issue that causes crashes or instability. In fact, until you perform the first update after a fresh install, Grub2 doesn't recognize or even list your other installed systems. How could this pass testing to support a final release?

---

### Post by old_salt on 2009-11-13
Actually, I think a 6 mo release cycle is a little too aggressive to be honest. I would like to see and have always made known my support for annual releases which I believe Mr. Shuttleworth is advocating as well albeit not constrained to Ubuntu but to Linux as a whole which I think is ambitious.

---

### Post by ranch hand on 2009-11-13
I think more people testing would help.  You do not see posts from people that were testing complaining, for instance, about speed.

To build an OS to work on all kinds of hardware, you need all kinds of hardware involved in testing.

---

