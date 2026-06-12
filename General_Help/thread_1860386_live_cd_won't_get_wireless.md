---
title: "live cd won't get wireless"
date: 2011-10-14
forum: General Help
---

### Post by garyed on 2011-10-14
I just bought a new cheap laptop mainly for Ubuntu but still plan on dual booting since Win 7 is pre-installed.  Its a Compaq:
[http://www.walmart.com/ip/Compaq-15.6-250GB-CQ57-229WM/16662274](http://www.walmart.com/ip/Compaq-15.6-250GB-CQ57-229WM/16662274)
I know the specs are weak but they're practically giving it away.
I've got three different laptops & none have had any problems connecting from the 10.04 live CD but this one won't. I assume its a driver problem so my question is assuming I can find a driver for the wireless & download it from another computer how can I use it with the live CD to get the wireless working? I have 15 days to return the laptop so I don't want to install anything or change any partitions until I'm sure Ubuntu will work.
Any ideas?

---

### Post by speedwlk on 2011-10-14
Hi!
I am not sure how much of help it will be, but have a look: [assuming you need a STA driver]

step 3 under "STA -INTERNET ACCESS" at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_Internet_access)

Download the proper driver and transfer it using a usb.

Good luck.

---

### Post by mixmastamyk on 2011-10-14
Nothin' to sneeze at kid.  Ten years ago you couldn't buy a PC that powerful no matter how much money you had.  ;)

What's it got in it?
  
```

lspci | grep -i net
iwconfig

```

---

### Post by garyed on 2011-10-14
Sorry I didn't get back sooner but I've been downloading 11.10 in hopes it would solve the problem & it did. I finally got it burned to a CD & booted from it on my new laptop & it picked up the wireless with no problem.
I got on line & tried to run the terminal commands & I couldn't even figure out how to get to a terminal. Wow have things changed from 10.04. 11.10 looks more like the Macs that I've seen. After using alt-f2 I got to a terminal but the I lost the page I minimized from & couldn't figure out how to get it back. 11.10 obviously has whatever drivers needed for my laptop so things are solved but I don't want to mark this thread solved. I would still like to know how I could have resolved things from a live CD that wouldn't recognize my wireless.

---

### Post by grahammechanical on 2011-10-14
This is just a guess based upon my understanding that the Live CD stores settings and things in RAM unlike an actual install which stores things on the hard disk. In other words, the Live CD Ubuntu will not try to store the changes on the CD ROM but in RAM memory.

I would say, make a connection to the router by ethernet cable. Run Additional Drivers and install the wireless adapter driver. And go from there. If that works then you would know that an actual install would work on that machine.

When installing we are asked to install with an existing Internet connection. The latest updates are then done in the process of installing.

Regards.

---

