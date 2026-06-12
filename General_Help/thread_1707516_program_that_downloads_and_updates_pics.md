---
title: "program that downloads and updates pics?"
date: 2011-03-15
forum: General Help
---

### Post by Arminius on 2011-03-15
is there a program that will download an image from the web.
specifically from

[http://www.timeanddate.com/worldclock/showsunmap.php?iso=20110315T174800](http://www.timeanddate.com/worldclock/showsunmap.php?iso=20110315T174800)

and can be set to update the pic every 60 mins?
replacing the old one with a new version?

---

### Post by wojox on 2011-03-15
Look at the script here [http://ubuntuforums.org/showthread.php?t=1514926](http://ubuntuforums.org/showthread.php?t=1514926)

It uses wget and sleep.

---

### Post by Arminius on 2011-03-15
nah I'm not wanting to change the wallpaper sorry.
just wanting to have a conky image, which get's updated every 30 or 60 mins.

all I need is to be able to auto update the image

---

### Post by wojox on 2011-03-15
Look at the code in the script. It will teach you to use wget to downland the file then sleep for an hour and download it again.

Or you can write a bash script to download the image to your directory of choice and set up a cron job for it. :P

---

### Post by Arminius on 2011-03-15
a cron job?
so there's no thread that explains in detail what that is?
I've googled around and so far come up with nothing.

---

### Post by wojox on 2011-03-15
> **Arminius said:**
> a cron job?
so there's no thread that explains in detail what that is?
I've googled around and so far come up with nothing.

Really? [CronHowto]("https://help.ubuntu.com/community/CronHowto")

---

