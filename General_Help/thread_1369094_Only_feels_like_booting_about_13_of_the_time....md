---
title: "Only feels like booting about 1/3 of the time..."
date: 2009-12-31
forum: General Help
---

### Post by rae_bot on 2009-12-31
I just got an Acer Aspire One (D250), and put Ubuntu Netbook Remix on it--my very first attempt at using Linux.  I kept Windows XP as a second, much smaller partition, just in case something ridiculous happens with UNR.

Well, it works fantastically when it feels like booting, but unfortunately, that isn't most of the time.  I turn on my computer, grub shows up, I choose my Ubuntu partition, and sometimes, the Ubuntu logo shows up and I log in and all of it works fine.

More commonly, though, what happens is, I choose Ubuntu, a little blinking command line cursor shows up (and won't let me type anything, so even startx isn't an option), and no matter how long I wait, it doesn't boot.  So I hold the power button to restart (or shut down and start again--it doesn't seem to change what happens either way), and see if it will boot this time.  Sometimes it does, sometimes it takes another two, three, even four tries to actually boot.  I do nothing differently.  What can I do to fix it?

Please remember, this is my first time using Linux, so I barely know the basics.  You may have to give me step-by-step instructions for your suggestions.  I know how to get to the Terminal, as well as Hardware Drivers and the Package Manager, but very little else yet.

Thank you very much for your (anticipated) assistance!

---

### Post by rae_bot on 2009-12-31
Bump...for the sake of my computer.

---

### Post by Strongman332 on 2009-12-31
have you tried a reinstall. and make sure the iso you start with has the right md5

their are several guides on how to do this one of them is linked to on the download page

---

### Post by john newbuntu on 2009-12-31
The one thing I would have always suggested is to get all the updates using the Synaptic package manager (if there is one in UNR?).

---

### Post by rae_bot on 2010-01-04
I am really, really hoping to avoid a reinstall.  I deleted the .iso (oops) because I thought I wouldn't need it, so I can't compare md5s.  I'm not sure how else I could compare them (if you have a link, I would appreciate it!).

UNR does have a Synaptic Package Manager (I think UNR is essentially the same as regular Ubuntu, at least in terms of things like that), and I did update everything available.

It seems more likely to boot when cold than from a hot reboot, but I could be wrong.  If there's any way to affect that, it could potentially help.  I want to mess with the least stuff possible.

This (relatively old) thread seems to have a similar problem: [http://ubuntuforums.org/showthread.php?t=624974](http://ubuntuforums.org/showthread.php?t=624974)  It was solved by compiling a different kernel, one that is rather older than the one I have now, but this information might help come up with a solution for my problem.

Thank you!

---

### Post by warfacegod on 2010-01-04
I ran into the same problem with a Windows machine my neighbor asked me to fix. Turned out to be a bad RAM card.

---

### Post by rae_bot on 2010-01-04
That's interesting...I don't seem to have any issue at all when booting into my XP partition, so I don't think it's the hardware...just, perhaps, the response of the UNR OS to the hardware (temperature or similar).

---

