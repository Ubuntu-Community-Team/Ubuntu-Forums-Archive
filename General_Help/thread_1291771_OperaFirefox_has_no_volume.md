---
title: "Opera/Firefox has no volume"
date: 2009-10-15
forum: General Help
---

### Post by oohbuntoo on 2009-10-15
For the last two days I have not had volume in Opera or Firefox when watching YouTube, Dailymotion, etc.  I've received advice to upgrade Opera to the latest release.  Unfortunately I still do not have volume.  My music plays in Rhythmbox and all the button effects, opening music plays fine.  Just no volume for the internet.  I have no idea where to go from here.  Any suggestions would be the business.

Jaunty 9.04
Toshiba Satellite
3GB Memory
250GB HD

---

### Post by P4man on 2009-10-15
Im guessing you only have no sound when playing flash? Try reinstalling flash:
[http://newtoubuntu.wordpress.com/2009/04/25/ubuntu-904-no-sound-with-flash-videos/](http://newtoubuntu.wordpress.com/2009/04/25/ubuntu-904-no-sound-with-flash-videos/)

---

### Post by oohbuntoo on 2009-10-15
> **P4man said:**
> Im guessing you only have no sound when playing flash? Try reinstalling flash:
[http://newtoubuntu.wordpress.com/2009/04/25/ubuntu-904-no-sound-with-flash-videos/](http://newtoubuntu.wordpress.com/2009/04/25/ubuntu-904-no-sound-with-flash-videos/)
Thanks.  I didn't think of that.  I just don't want to boot Vista...again...EVER!  Luckily I have Mint installed on an old laptop.  I'll get right on it.

---

### Post by oohbuntoo on 2009-10-15
> **oohbuntoo said:**
> Thanks.  I didn't think of that.  I just don't want to boot Vista...again...EVER!  Luckily I have Mint installed on an old laptop.  I'll get right on it.
Well, I followed the instructions to reinstall flash.  Only problem is when I searched for flash in Add/Remove, it found nothing.  I went to synaptic and reinstalled it there, but, got nothing after a restarting the session.  Also, I have a more updated version installed already than the link provides.  Where do I go from here?

---

### Post by P4man on 2009-10-15
it should be in add/remove. Make sure you selected the "show all available program" in the drop down though.

Now you say you installed it through synaptic. Which package did you install, and what does it mean when you say "you got nothing"? Did it not install, dont have you any flash at all anymore, or what?

---

### Post by oohbuntoo on 2009-10-15
> **P4man said:**
> it should be in add/remove. Make sure you selected the "show all available program" in the drop down though.

Now you say you installed it through synaptic. Which package did you install, and what does it mean when you say "you got nothing"? Did it not install, dont have you any flash at all anymore, or what?
My bad.  When I reinstalled the flash items that are already installed in Synaptic, it didn't fix anything.  I still do not have sound when watching Youtube, Dailymotion, etc, in Opera or Firefox.  It feels like it's something so simple I'm just overlooking it.  But, I've check every volume setting available and nothing is on mute.  I'm super lost now.

---

### Post by oohbuntoo on 2009-10-15
> **P4man said:**
> it should be in add/remove. Make sure you selected the "show all available program" in the drop down though.

Now you say you installed it through synaptic. Which package did you install, and what does it mean when you say "you got nothing"? Did it not install, dont have you any flash at all anymore, or what?
Also, I went to Add/Remove again, and searched "flash" with "All" in the list to the left selected.  This is what I get:

Movie Player
DNGConverter
Parley
KWordQuiz

The search doesn't return anything flash related.

---

### Post by oohbuntoo on 2009-10-15
> **P4man said:**
> it should be in add/remove. Make sure you selected the "show all available program" in the drop down though.

Now you say you installed it through synaptic. Which package did you install, and what does it mean when you say "you got nothing"? Did it not install, dont have you any flash at all anymore, or what?
O.k., now I have zero sound in Ubuntu.  No Rhythmbox, Banshee, Songbird, Stored movies, Opera, Firefox, Chromium.  I am completely lost as to what happened.  To quote a favorite song of mine, "it was all good just a week ago".  I've read a couple of other post where folks are complaining of the same issue.  I have executed everything I've found so far with no dice.  Yikes, I hope I don't have to bust a fresh install of Juanty.  I just got this thing runnin' the way I want.  Any ideas???

---

### Post by P4man on 2009-10-16
run alsamixer from a command line and see if none of the channels (like PCM) got muted by an update?

---

### Post by abhishek.malhotra35 on 2009-10-16
flash is removed from ubuntu repository. You can get flash from the non-free plugins or there are alternatives of adobe flash in repository that you can use.

---

### Post by oohbuntoo on 2009-10-20
Well after not being able to fix the problem I did a fresh install of Jaunty and installed Chromium.  Hopefully it won't die in a few months again!

---

