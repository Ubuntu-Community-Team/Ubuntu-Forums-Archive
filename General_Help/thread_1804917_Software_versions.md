---
title: "Software versions"
date: 2011-07-15
forum: General Help
---

### Post by Spitted on 2011-07-15
Hi

I noticed a lot of applications in the Software Center are really outdated. Also I think it's that it's not that great that if I want to continue using Ubuntu 10.10 other software is even more outdated (OpenOffice for example).

What can I do if I want to have the cutting edge software? Do other distributions provide that?

---

### Post by flipper T on 2011-07-15
google search for the apps ppa

eg for the latest GIMP, search for "gimp ppa"


i assume that you have already ticked the boxes for proposed updates in software sources



ps if you are not used to adding ppas, a real easy way to do it is by install ubuntu tweak and using its software centre. this contains a large selection of the most commonly used ppas

---

### Post by snowpine on 2011-07-15
10.10 = October 2010.

Use 11.04 if you want software from April 2011. 

Or get newer versions of the apps you want from another source, like the app's developer or a PPA.

---

### Post by Spitted on 2011-07-15
You describe it as if software from Software Center does not get updated at all! But I do get regular updates from the Update Manager, so why isn't it updating Tomboy to 1.6.0 (again just an example)?
If I would rely on PPAs, I would have to maintain a PPA for EVERY software I have individually, which is a mess. And moving to 11.04 just for the latest Tomboy is really not an option.
I ask again, is this a flaw in every distribution, or some has figured it out?

---

### Post by flipper T on 2011-07-15
have you tried open office ppa or tomboy ppa ?

"maintaining" ppas is not an arduous task

---

### Post by Steeperton on 2011-07-15
Ubuntu does not update to newer versions of software (mainly - there are some exceptions), but it does issue security updates. The Ubuntu team have decided that stability is a priority over "latest and greatest".

If you want the latest version of software, then either use (official, where possible) PPAs, or switch to a "rolling" distro.

---

### Post by snowpine on 2011-07-15
> **Spitted said:**
> You describe it as if software from Software Center does not get updated at all! But I do get regular updates from the Update Manager, so why isn't it updating Tomboy to 1.6.0 (again just an example)?
If I would rely on PPAs, I would have to maintain a PPA for EVERY software I have individually, which is a mess. And moving to 11.04 just for the latest Tomboy is really not an option.
I ask again, is this a flaw in every distribution, or some has figured it out?

It is not a "flaw" but a design goal to create a stable product. Update Manager gives you bug fixes and security patches for the application version you have installed. You don't automatically get major upgrades (for example from version 1.1 to 1.2 of a software). Major upgrades happen every 6 months in the form of a new release.

You are of course free to install whatever version you want of any application you like. :)

---

### Post by dFlyer on 2011-07-15
Linux is about choice. If you want the latest and greatest and possible beta programs install the ppa's for the program you want. If you want stable, bug fixed programs use the repos.

---

### Post by idoitprone on 2011-07-15
> **Spitted said:**
> Hi

I noticed a lot of applications in the Software Center are really outdated. Also I think it's that it's not that great that if I want to continue using Ubuntu 10.10 other software is even more outdated (OpenOffice for example).

What can I do if I want to have the cutting edge software? Do other distributions provide that?

when you are updating software, you have to understand Gates or Wirth; 
More you update software the slower it gets. [http://en.wikipedia.org/wiki/Wirth%27s_law]("http://en.wikipedia.org/wiki/Wirth%27s_law")

Even though phoronix does not make the best benchmarks, it is somewhat valid.
[http://www.phoronix.com/scan.php?page=article&item=linux_2612_2637&num=6](http://www.phoronix.com/scan.php?page=article&item=linux_2612_2637&num=6)

Updating software is not always good 

Of course sometimes you want the newest snapshot such as the wine project. The latest version is usually more stable then the stable version.

---

### Post by mikewhatever on 2011-07-15
> **Spitted said:**
> You describe it as if software from Software Center does not get updated at all! But I do get regular updates from the Update Manager, so why isn't it updating Tomboy to 1.6.0 (again just an example)?
If I would rely on PPAs, I would have to maintain a PPA for EVERY software I have individually, which is a mess. And moving to 11.04 just for the latest Tomboy is really not an option.
I ask again, is this a flaw in every distribution, or some has figured it out?

No, it's not a flaw, that's how most of the Linux distros work, including Debian, Ubuntu, Fedora, Opensuse, Mandriva, etc. The name of the game is stability. 
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
If you want to use the newest software, consider switching to a rolling release distro - PCLinux, Arch.

---

### Post by Spitted on 2011-07-15
Thanks, I get it now. I didn't think that not giving out the latest software is by design, but it makes sense. 
I still don't think that having numerous PPAs is the solution. Maybe I'll try a rolling distribution some time, even though stability does worries me.

---

### Post by snowpine on 2011-07-15
> **Spitted said:**
> Thanks, I get it now. I didn't think that not giving out the latest software is by design, but it makes sense. 
I still don't think that having numerous PPAs is the solution. Maybe I'll try a rolling distribution some time, even though stability does worries me.

Ubuntu's designers assume that people using older releases want stable, well-tested software, and people wanting current software will use the current release. 

Your software is outdated because you're using 10.10, last year's release. Upgrade to the current 11.04 release if you want the latest (or 11.10 Alpha if you really want to live on the edge).

---

### Post by Spitted on 2011-07-15
But I don't want to completely reinstall my OS and configuring everything again. I have my custom Gnome 2 desktop and I certainly don't want to upgrade it somehow (let alone replace it with Unity). This has nothing to do with me wanting all my other software to be up-to-date.

---

### Post by snowpine on 2011-07-15
> **Spitted said:**
> But I don't want to completely reinstall my OS and configuring everything again. I have my custom Gnome 2 desktop and I certainly don't want to upgrade it somehow (let alone replace it with Unity). This has nothing to do with me wanting all my other software to be up-to-date.

Ubuntu 10.10 with Gnome 2 will be supported through April 2012. No reason to upgrade to the latest at this point if you prefer using stable, well-tested software like Gnome 2. :)

---

