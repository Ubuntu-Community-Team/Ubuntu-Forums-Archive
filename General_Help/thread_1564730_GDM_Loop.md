---
title: "GDM Loop"
date: 2010-08-30
forum: General Help
---

### Post by MetaDark on 2010-08-30
I am using a Dell Inspiron Mini 10 with poulsbo video drivers and whenever gdm tries to start it flashes purple (with noise) then black (without noise) ( I think it is looping to try to start gdm )

I was trying to remove kubuntu-netbook with the command from [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

I don't exactly remember what happened but I think it was removing kdm but my screen went weird ( that noise you see when your start gdm with poulsbo video drivers )

Starting gdm manually has the same effect, I tried reinstalling gdm, dpkg-reconfiguring gdm, reinstalling kubuntu-desktop and kdm but still I am having trouble with this, do you guys know what I can do to fix this?

---

### Post by MetaDark on 2010-08-31
Has anyone ever heard of this? Please help I would really prefer if I can get this fixed before Sept. 7 because if it is not fixed by then I will have to use *barf* windows...

---

### Post by dino99 on 2010-08-31
clean the room:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm

---

### Post by MetaDark on 2010-08-31
Sigh, sadly that did not do anything :(

---

### Post by MetaDark on 2010-08-31
I guess I will just install Ubuntu on another partition and move my files over, hopefully in recovery mode the home directory gets automatically decrypted so I don't have to re do everything I did before ( I corrupted the files in the partition I am overriding to somehow and I had to retrieve the files )

I learned my lesson, no messing around with a laptop I use for school - but I still have my desktop :D

---

### Post by MetaDark on 2010-09-01
What the! It is doing it again and I didn't even mess around that time! All I did was install Google Chrome and Compiz.

I also have those installed on my Desktop so why would it not do anything to my Desktop but make my laptop unbootable?

I am going to try re-installing the graphic drivers through recovery mode to see if that will fix anything.

Before this happened I was able to boot into Ubuntu two or three times.

---

### Post by MetaDark on 2010-09-01
Woah, very, very weird, apparently my drivers weren't even installed, all I did was

```
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config
```

and it started working again, maybe for some odd reason Compiz removed my drivers, I know they were installed in the first place because I could see the resolution change when I was last using it.

I am going to try this on the other partition that was having the same problem and I'll try to investigate this further.

---

### Post by MetaDark on 2010-09-01
Yep, that was the whole problem... Compiz did break my drivers! Maybe the pure gnome script installed compiz or something else that removed the drivers.

I hope that GMA 500 (poulsbo) users don't go through the same thing that I did, at least I know that if I see Ubuntu go through that GDM loop I know what to do

Head to recovery mode - Choose Netroot or whatever it is - run the command to install the poulsbo drivers.

( For Dell Mini 10 users, if you fall into the same problem, be sure to plug in an Ethernet cable for netroot instead of trying to get on with Wi-Fi )

---

