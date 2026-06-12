---
title: "any reason to upgrade from meerkat?"
date: 2011-05-18
forum: General Help
---

### Post by qwertyjjj on 2011-05-18
I keep getting notified about the update to 11.04.
Is there any point in doing this if Meerkat works fine?
Will the upgrade delete my existing programs and or settings in things like i8kmon, etc.?

---

### Post by VanR on 2011-05-18
Well I'll just say that I'm back to 10.10 now after using 11.04 for a month or so.  Much more stable for me and I hated Unity and found 11.04 clunky and slow.

---

### Post by fluffman86 on 2011-05-18
Go ahead and update. Maverick will only get security updates from this point on, while Natty has new versions of programs like firefox, etc. 

Also, you can't upgrade directly from 10.10 to 11.10, you will have to go through 11.04 Natty first. Otherwise, you could just wait for 12.04, the long term support release, and do a fresh install then, but you would have to reinstall all of your programs and settings.

Doing an upgrade now lets you keep your settings and programs.

---

### Post by fluffman86 on 2011-05-18
> **VanR said:**
> Well I'll just say that I'm back to 10.10 now after using 11.04 for a month or so.  Much more stable for me and I hated Unity and found 11.04 clunky and slow.

Then why not just use Ubuntu Classic? Unity 3D was really slow for me, too, so I now use Unity 2D or Classic with no problems. Why go through the trouble of a complete reinstall?

---

### Post by qwertyjjj on 2011-05-18
> **fluffman86 said:**
> Go ahead and update. Maverick will only get security updates from this point on, while Natty has new versions of programs like firefox, etc. 

Also, you can't upgrade directly from 10.10 to 11.10, you will have to go through 11.04 Natty first. Otherwise, you could just wait for 12.04, the long term support release, and do a fresh install then, but you would have to reinstall all of your programs and settings.

Doing an upgrade now lets you keep your settings and programs.

Does it automatically install firefox 4?
...because many of my add ons don't work with FF4 yet.

---

### Post by VanR on 2011-05-18
> **fluffman86 said:**
> Then why not just use Ubuntu Classic? Unity 3D was really slow for me, too, so I now use Unity 2D or Classic with no problems. Why go through the trouble of a complete reinstall?

Well I did use classic for almost the whole time I used 11.04. Hated Unity from the start and never hardly used it. But 11.04 is slow and buggy period (unless they have really improved it in the last 2 weeks)  and I have a brand new machine so it's not my hardware. 11/04 was not ready for primetime and I'll go with what works for now. I'm actually running Zorin OS 4 (10.10) which is a fantasic distro.

---

### Post by VanR on 2011-05-18
> **fluffman86 said:**
> Go ahead and update. Maverick will only get security updates from this point on, while Natty has new versions of programs like firefox, etc. 

Also, you can't upgrade directly from 10.10 to 11.10, you will have to go through 11.04 Natty first. Otherwise, you could just wait for 12.04, the long term support release, and do a fresh install then, but you would have to reinstall all of your programs and settings.

Doing an upgrade now lets you keep your settings and programs.

I don't know about any future Maverick updates, but I'm running Firefox 4 and linux kernel 2.6.39 with Nividia 270.41.06 driver so you can keep Maverick up to speed if you stay on top of it. I haven't found any NEW program versions for say Natty or even Oneiric that don't run on Maverick too, at least so far. Maybe they are not supposed to run, but I don't know any better.  LOL

---

### Post by jerome1232 on 2011-05-18
You mean shiny new interface wasn't enough to get you hammering on the update button?

If you very used to gnome classic and are not open to new ways of doing things you won't like Unity right away. It doesn't have all of it's features implemented yet, but I'm loving it so far. Give it a try in a virtual machine before deciding to do a full install (remember to enable 3d in the vm to try unity) Natty's core components are stable in my experience.

---

### Post by timgood on 2011-05-18
I've also reverted to 10.10 and it was the slowing down of the system (there are bad memory leaks in Natty) plus other problems getting classic mode to work that made me revert. I'm glad I did. 10.10 to me is the nearly perfect desktop.

YMMV.

---

### Post by qwertyjjj on 2011-05-18
Seems best to keep Maverick then.
Why don't they just make 1 distro and update it?!?!?!

---

### Post by doas777 on 2011-05-18
> **qwertyjjj said:**
> Seems best to keep Maverick then.
Why don't they just make 1 distro and update it?!?!?!
that is called a rolling release, and it has been a matter of some contraversy over the years. 
the benifet of ubuntus approach is it keeps them driving forward to the next goal. Ubuntu changes far more frequently than it's competitors, and allows them to take more risks with less danger. Ubuntu has made huge progress over the last few years in terms of overall desktop usability. my first hardcore linux experience was hand configuring an xorg.conf in Feisty for TVOuts; today is an entirely  different story because of changes they made, that other distros were afraid to make. 
the release cycle also (debatebly) pushed the other linux vendors to move forward rather than sitting still. there is a benifet to having a (reasonably set) deadline.


if you don;t want to have your distro change every 6 months, just do what i do, and what Cannonical intends for you to do: install the LTS ever 2 years, and maintain it in the interim.

---

### Post by perspectoff on 2011-05-18
Any individual program can be updated in any OS.

For me, Skype works far better in Natty than in Maverick.

The reason is PulseAudio. PulseAudio in Natty has been improved head and shoulders above Maverick. It is easier to configure, less choppy, and more reliable.

My Skype in Natty just works, whereas in both Lucid and Maverick I spent days tweaking both Skype and PulseAudio until it worked.

I agree with the other reply -- if you don't like Unity, just install Gnome 3. Big deal.

It's the background stuff (like PulseAudio) that is hard to change so easily. I won't go back to Maverick (or Lucid, for that matter) on any computer on which I need PulseAudio/Skype.

(Yeah, and don't flame me just because Skype was bought by Microsoft. I have Ekiga, too, and OpenSIPS servers, but many of my contacts don't).

As to having just one distro and updating it, that doesn't work. Ubuntu is not a self-contained system. It is an amalgam of independent projects that do not have co-ordinated update schedules. 

PHP and MySQL and PostgreSQL all update on different schedules, and the applications that rely on them also update independently. To try and put together any distro version and guarantee compatibility of the versions of so many independent efforts is very difficult. 

Trying to do this yourself (by having an old distro version and "updating" each package manually) is even harder. I had a Karmic system that was allowed to do updates and it became unusable in late 2010 because of incompatibilites between the updated packages.

I was forced to convert to Lucid whether I wanted to or not. Karmic did not successfully upgrade to Lucid, so i was forced to install a fresh Lucid and then recreate my Karmic system anew, migrating databases, etc.

It took me 3 weeks of intensive work. Upgrades are not the answer. Scripted re-installations are the only solution I have ever found able to work. Then the hardest part that remains is to migrate databases to the current database version (which can also be scripted).

(This problem is not unique to Linux. I have never been able to move to Windows Vista/7 because many of my business-oriented applications are still not compatible with them. We still use XP Pro for any Windows use. Apple products are merely toys. Anyone in the company who got a Mac was forced to also get a PC (running both Windows and Linux) for real business use.)

---

