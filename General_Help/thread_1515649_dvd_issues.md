---
title: "dvd issues"
date: 2010-06-22
forum: General Help
---

### Post by archeryrob on 2010-06-22
I just did a build for an HTPC and trying to figure this thing out. New to Linux. 

I got a DVD/Blue ray and I am not sure if it setup properly. I installed WINE and tried to figure out how to install CIV4 game and got an error reading the autorun from wine. Gave that up for a while and got the Avatar DVD and was going to try and rip it with DVD rip and it will not read it, VLC, Movie player and other programs will not read it either. I installed a few more DVD codecs from software center but nothing seems to work, yet.

I figured it's a newbie skip, any ideas?

---

### Post by Smart Viking on 2010-06-22
Hey, to play dvd's, you need to do this:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

It is pretty easy. :)

And i am not sure, but i think the wine thingy have something with security to do, the autorun wont execute, i saw a thread yesterday i think, and he was advised with copying the files to the pc and mark the exutable and install it that way. But i don't know if thats true. I hope this helps. :)

---

### Post by bobcollard on 2010-06-22
> **archeryrob said:**
> I just did a build for an HTPC and trying to figure this thing out. New to Linux. 

I got a DVD/Blue ray and I am not sure if it setup properly. I installed WINE and tried to figure out how to install CIV4 game and got an error reading the autorun from wine. Gave that up for a while and got the Avatar DVD and was going to try and rip it with DVD rip and it will not read it, VLC, Movie player and other programs will not read it either. I installed a few more DVD codecs from software center but nothing seems to work, yet.

I figured it's a newbie skip, any ideas?
Run the following in Terminal:
```
sudo apt-get install libdvdcss2
```

---

### Post by cbrunhaver on 2010-06-22
you'll want to install the ubuntu-resitricted-extras in the Ubuntu Software Center.

Also, I would add the medibuntu repository to get other codecs etc.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by cbrunhaver on 2010-06-22
you'll want to install the ubuntu-resitricted-extras in the Ubuntu Software Center.

Also, I would add the medibuntu repository to get other codecs etc.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by archeryrob on 2010-06-25
Bob, went into terminal and typed this
 ```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```Didn't work

---

### Post by archeryrob on 2010-06-25
cbrunhaver, I added the stuff on the link into terminal for AMD 64 and it's playing the DVD, Thanks. :p

I'll still have to try the ripper.

---

### Post by archeryrob on 2010-06-25
OK, (Rant coming)

 I am all for Linux over windows, I am an anti-establishment kind of guy. Libertarian, you know, free to be stupid on my own terms. :p

BUT, the wife come home and I go to have beer with her and pause Avatar, Ubuntu goes to screen saver and will not come back. Took a cold start to get the computer back. (power plug) 

fargin' crap is driving me nuts. :mad:

---

### Post by bobcollard on 2010-06-25
> **archeryrob said:**
> OK, (Rant coming)

 I am all for Linux over windows, I am an anti-establishment kind of guy. Libertarian, you know, free to be stupid on my own terms. :p

BUT, the wife come home and I go to have beer with her and pause Avatar, Ubuntu goes to screen saver and will not come back. Took a cold start to get the computer back. (power plug) 

fargin' crap is driving me nuts. :mad:
Check your settings in screensaver and Power Manager, it may have gone beyond screensaver into suspend or hibernate.  There are bugs in both of these in Ubuntu 10.04.

---

### Post by archeryrob on 2010-06-26
Screen saver had something in there checked about locking it. So I unchecked it. Why would you want screen saver to lock while in used? Or does that mean you have to log back in?

Yea, 10.04 bugs. I am ready for 9.04 again. shutdown does not work for me yet. I have the restart and pull power when I see the bois screen

---

### Post by bobcollard on 2010-06-26
> **archeryrob said:**
> Screen saver had something in there checked about locking it. So I unchecked it. Why would you want screen saver to lock while in used? Or does that mean you have to log back in?

Yea, 10.04 bugs. I am ready for 9.04 again. shutdown does not work for me yet. I have the restart and pull power when I see the bois screen
Screensaver lock is for people who don't trust their neighbors while they are away for very long.  Like in accounting offices.

---

