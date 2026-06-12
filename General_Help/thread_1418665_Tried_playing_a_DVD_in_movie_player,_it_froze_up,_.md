---
title: "Tried playing a DVD in movie player, it froze up, and a huge loss in free disk space"
date: 2010-02-28
forum: General Help
---

### Post by cAlpha on 2010-02-28
I tried playing a DVD several times and each time, after opening in Movie Player on Ubuntu 9.10, it froze up, I forced quit and then I noticed a huge reduction in free disk space on my root (/) directory.  Has this happened to anyone else?

I figure I Movie Player probably saved some temp files somewhere on hard disk and wasn't able to clean them up since I had to force quit.  Any thoughts about how to clean this up and take back that previously free space?

---

### Post by Primefalcon on 2010-02-28
go to the Ubuntu software center located under the applciations menu and search for VLC, and install it, it's a great dvd/media player and it has codecs for pretty much everything built in

Ubuntu itself can play dvd's but it doesn't out of the box due to copyright issues, to allow dvd playing in mplayer look here

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[hr]
basicay for dvd though just do this

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

then

```
sudo apt-get install libdvdcss2
```

There is more on that page but just go through it

---

### Post by cAlpha on 2010-02-28
Thanks, I've got VLC but it wasn't displaying video from the DVD--I'll take a look at the link you posted.  

Any idea how to get that free space back or what took the space when trying to play the DVD though?

---

### Post by Primefalcon on 2010-02-28
> **cAlpha said:**
> Thanks, I've got VLC but it wasn't displaying video from the DVD--I'll take a look at the link you posted.  

Any idea how to get that free space back or what took the space when trying to play the DVD though?
it probaly saved the data in /tmp don't bother trying to delete it yourself, just restart your system and data that programs like movieplayer save there will get wiped tmp == temporary.

-just an added hint-
flash video's from youtube get saved there while your watching them online too. so if you want to save a youtube video that you've watched, wait till the flash video is fully loaded/cached and then copy it from the /tmp folder to your desktop or whatever

---

### Post by cAlpha on 2010-02-28
Yeah, I figured some temp data would be saved in /tmp, but the directory is less than 100KB, so perhaps it's just saved elsewhere--I haven't restarted since I had the issue, so I'll give that a try later.  

Cool tip on the youtube cache.  :)  Thanks, dude...let you know if the restart fixes things.

---

### Post by cAlpha on 2010-02-28
Yeah, the restart didn't improve things.  Any other ideas for ways to check to see which directories are hogging space?

---

### Post by seventyeights on 2010-02-28
Try Applications/Accessories/Disk_Usage_Analyzer

---

### Post by cAlpha on 2010-03-01
Alright, what do you make of this:  Disk Analyzer shows my /home/{name} directory taking up 4.4GB, with Desktop and Videos folders taking up 41% and 8%, respectively, and descending percentages thereafter such that they don't seem to add up to 100%.  

Checking Properties within the File Browser window, /home/{name} is occupying only 2.4GB (not 4.4GB)--where could the missing 2GB be?  Anyone seen anything like this?

---

### Post by maestrobwh1 on 2010-03-02
> **cAlpha said:**
> Alright, what do you make of this:  Disk Analyzer shows my /home/{name} directory taking up 4.4GB, with Desktop and Videos folders taking up 41% and 8%, respectively, and descending percentages thereafter such that they don't seem to add up to 100%.  

Checking Properties within the File Browser window, /home/{name} is occupying only 2.4GB (not 4.4GB)--where could the missing 2GB be?  Anyone seen anything like this?

Check out your home again and show hidden files

There is a huge chance that the hidden file /home/user/.xsession-errors is really big.  You can just delete it.  It will be recreated on the next log in with the default size which is very small (as in kilobytes).

I experienced this once with k9copy.

---

### Post by cAlpha on 2010-03-02
Not sure how or why, but I had to reboot to use my Windows partition for a bit and upon rebooting AGAIN to get back into Ubuntu, the missing ~2G had reappeared.  Who knows.  :)

---

