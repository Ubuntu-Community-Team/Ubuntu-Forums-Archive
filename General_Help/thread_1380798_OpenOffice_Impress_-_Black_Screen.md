---
title: "OpenOffice Impress - Black Screen"
date: 2010-01-14
forum: General Help
---

### Post by TDK740 on 2010-01-14
I'm encountering a strange problem running presentations in Impress.

I can open a presentation, and run it just fine using F5, or the Slide Show menu.  The problem occurs when trying to start a show automatically from the command line.  When running Impress with the "-show" argument, e.g.

```
/usr/bin/soffice -impress -show /home/whoever/path_to_file
```The presentation opens, and the show starts, but nothing but a black screen shows.  If I click the mouse, press a key or even roll the scroll wheel, then the slides will actually start to appear.  

Additionally, right-clicking and using the context menu to jump to slides also gets things running; however the screen doesn't seem to re-draw properly, as I can right-click many times to create "ghosts" of the context menu. (See attached for an example, rather than my poor explanation)

Oddly, prefixing the command with "sudo" solves the problem, but that's not something I really want to do.

I can replicate this on multiple machines running 9.10 and OO.o 3.1.  I've read through another thread (which I'm unable to find again) that suggested disabling hardware acceleration, but that had no effect.

I don't know if it matters, but all of the machines are running on the ION platform using version 185.18.36 of the NVIDIA drivers.

Any suggestions would be very much appreciated.

EDIT: As far as I can remember, this worked without any problems on 9.04.

---

### Post by TDK740 on 2010-01-18
Bump for assistance.  I can also replicate this behaviour on a clean install of kubuntu running in a VM.

---

### Post by Caduvet on 2010-01-27
Same problem here...

Since Karmic update, my Impress slideshows (started by a script with -show option) begin with a black screen that goes away only with a keypress or mouse wheel action. Since my Ubuntu box is meant to display different presentations round the clock, it is completely useless now that a user input is requested at each slideshow launch.

Disabling hardware acceleration changes nothing, nor adding any -display option I thought of.

I also run the nvidia drivers 185.18.36 on a GeForce 7100, and OOo 3.1.1 (OOO310m19 build 9420)

Running soffice with sudo does make the trick too, but seems a bit unsecure to me...

However, I don't have the "ghosts" issue ;). right-clicking works just fine to launch the slideshow.

Thanks !

---

### Post by Hagar Delest on 2010-01-30
Rather strange. It may be a problem of rights on your profile. Try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by TDK740 on 2010-02-03
> **Caduvet said:**
> Same problem here...

Ah, so it isn't just me then.  I'm in the exact same boat; the machine is intended solely as an info display, but it's now useless to me.

> **Hagar de l'Est said:**
> Try to [reset your OOo user profile]("http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403")

That was one of the things I've tried since I made this topic, but to no avail.

However, I have discovered 2 things:

1 - The "black screen" is actually the beginning of my fist transition.  I have the slides set to fade smoothly into each other after a delay of 5 seconds, which works fine when running the show manually.  If I remove the transitions, the first slide does appear, but will not advance until it detects user input.

2 - The same thing happens on a completely fresh user account I created to test this with.

---

### Post by Hagar Delest on 2010-02-03
Usually, I would advise to install the Sun version ([[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)). But as running OOo as root works fine, I don't think it would change anything.

If running as root works, I guess it's a problem with rights on some files...

---

### Post by TDK740 on 2010-02-26
Well after 3 weeks with no joy, I eventually came back to this issue the other day.  Seeing as I hadn't used the machine for a while, I checked for updates and found some OOo core updates (1:3.1.1-5ubuntu1.1 Feb 19 23:52:09).

Installing these seems to have cured the problem.  Thanks to everyone who gave me suggestions.

---

