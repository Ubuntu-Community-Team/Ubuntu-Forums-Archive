---
title: "Update of programs not used"
date: 2012-07-26
forum: General Help
---

### Post by alarmguy on 2012-07-26
I just received an update for Mono, which, as i understand, is a MS Visual Basic look alike for .NET.  I do not use this program.  Nor do I use Unity.  I accidentally installed the Unity updates because it put them back in the que after I had deleted them and updated the balance.  This time with Mono, I unchecked the Mono updates (12MB), but they came back with a later update.  Am I going to have to keep unchecking the Mono updates until I die?
Is Mono used by Ubuntu that I do not know about?

Tia, John

---

### Post by d4m1r on 2012-07-26
Yes you will keep having to uncheck updates you don't want...unfortunately, there is NO way to ignore updates permanently from Update Manager....

---

### Post by ajgreeny on 2012-07-26
> **d4m1r said:**
> Yes you will keep having to uncheck updates you don't want...unfortunately, there is NO way to ignore updates permanently from Update Manager....
Actually there is a way; you can pin the packages that you do not wish to update to their current version by editing  /etc/apt/preferences with root permissions, and adding these lines to it:
```
Package: *name*
Pin: version *(current number from repos)*
Pin-Priority: 1001
```However, you could end up with a number of dependency problems if you do that, with some of the other applications that depend on mono not being able to update.  I would therefore forget about pinning versions and just go ahead and update everything.  It is much better for all sorts or reasons, not least system security.

---

### Post by d4m1r on 2012-07-26
That's not very user friendly...Wouldn't it be so much better if we could just right click on an update we don't want and permanently ignore it? This is probably my only complaint about Ubuntu not having a feature that most versions of Windows (if not all) do...

---

### Post by ajgreeny on 2012-07-26
> **d4m1r said:**
> That's not very user friendly...Wouldn't it be so much better if we could just right click on an update we don't want and permanently ignore it? This is probably my only complaint about Ubuntu not having a feature that most versions of Windows (if not all) do...
But this is not windows, is it?  The filesystem of Linux works in a completely different manner.  In windows if a new version of a program appears it will contain all the dependencies that are needed to update the system, ie all the dll files etc etc.  Linux does not do this or work that way and hence the problem I mentioned earlier about the potential for dependency problems.

What actually is the difficulty you have with keeping everything up-to-date?  The example you gave of mono required downloads of only 6MB as far as I remember, so surely it is not a bandwidth problem you are worrying about.

---

### Post by restorator on 2012-07-26
You may want to think about this as you really might want to do all updates anyway. Even if you do not use these programs they are apparently installed on your machine. If you do not need them at all, you would be better served to remove the programs entirely than to simply not update them. The updates may include security fixes and even if you, yourself do not use the program, malware or some other rouge item may use the security issue to compromise your machine. This is actually a reason (not the only one) Windows has more of a bad reputation for viruses spreading. Many users simply do not update, or as you said in a previous post, you "turn off" Windows warnings to update. This inevitably leads to security issues being exploited.

---

### Post by directhex on 2012-07-26
> **alarmguy said:**
> I just received an update for Mono, which, as i understand, is a MS Visual Basic look alike for .NET.  I do not use this program.

It's a programming framework. Some of the software you have installed may require it to operate - e.g. Banshee, Tomboy, gBrainy, Pinta, Gnome Do.

> Am I going to have to keep unchecking the Mono updates until I die?

You could just uninstall software you don't want, you know.

> Is Mono used by Ubuntu that I do not know about?

See above

---

### Post by alarmguy on 2012-07-26
Thank you all for the insight.  I think I will go ahead and accept all of the updates.  Re: the bandwidth issue, this computer is at a location that uses the Exede satellite  for its internet connection.  They limit the throughput to 7.5Gb per month.  Sounds like a lot, but I see the data led flashing when we are not using any of the computers connected to the router.

Thanks again, John

---

### Post by Cheesehead on 2012-07-26
Then you should definitely uninstall packages you are not using. "Uninstall" does not erase the cached version of the deb package in your /var/cache/apt/archives, so if you later reinstall you won't need to re-download...until you update.

There are a lot of little tips to reduce your bandwidth overhead quite painlessly and tailor Ubuntu to the way you use it.

---

### Post by d4m1r on 2012-07-27
> **ajgreeny said:**
> But this is not windows, is it?  The filesystem of Linux works in a completely different manner.  In windows if a new version of a program appears it will contain all the dependencies that are needed to update the system, ie all the dll files etc etc.  Linux does not do this or work that way and hence the problem I mentioned earlier about the potential for dependency problems.

What actually is the difficulty you have with keeping everything up-to-date?  The example you gave of mono required downloads of only 6MB as far as I remember, so surely it is not a bandwidth problem you are worrying about.

No, some Windows updates are also sequential meaning other updates are dependencies...Anyway, in my case bandwidth nor diskspace is the problem but I do have a problem downloading packages I'll never use nor do I need...A recent example of this is some Chinese language files. I will never use any program in Chinese as I don't know it and I want to keep the number of packages as low as possible on my system to keep it lean and optimized.

---

