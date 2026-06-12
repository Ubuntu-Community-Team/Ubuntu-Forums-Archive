---
title: "Question about AMD / ATI Drivers"
date: 2012-04-07
forum: General Help
---

### Post by ToxicBurn on 2012-04-07
hi guys and gals i have a question i just downloaded the 11.10 and install was fine 

It then told me there was Additional Drivers for my AMD HD6870 in order to get full 3D support so just like i would do in the older versions of Ubuntu for the last 3 years i clicked on download and install thinking it would install the ATI drivers for my video card 

after no error or warning it was done i rebooted and no new driver was being used.

This is on a 100% clean install AMD/ATI drivers do not work.

my question is will this be fixed by the time 12.04 is Final ?
i miss playing with Linux but when i do I like to have Real Drivers for my Video card because i like to play with Wine and some 3D games.

this is the first time i have had this much trouble with ubuntu and getting my drivers. it seems to me the Linux community is more focused on these hacked / open source drivers then the real official drivers is this the case ?

anyway thanks for any input you may have 

hopefully i will be in 12.04 with 3D support soon :)

---

### Post by cortman on 2012-04-07
I have a netbook that uses ATI Radeon HD graphics, and frankly, the open source driver outperforms the stuffing out of the proprietary ATI driver. Are you sure the open source driver does not have 3D support?
To see if you have correctly installed and are running the proprietary ATI driver, type

```
fglrxinfo
```

which will tell you whether or not the driver is used. ATI graphics in Linux are temperamental at best; if you have a functioning driver it's usually best to stick with what's safe.

---

### Post by Redblade20XX on 2012-04-07
In addition, take a look at this to see if it helps with your problem:
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) ;)

- Red

---

### Post by ToxicBurn on 2012-04-10
Ouch I think it's just to much trouble just to get video drivers working best bet for me us just to stick with wIth windows . It's such a shame as far as Linux has come over the years we still can't get video card drivers without a PHD in unix . 

So much for this hobby for me :(

---

### Post by jadtech on 2012-04-10
PHD ? 

go to your terminal window 

past this in it  fgl_glxgears press enter if a window with a rotating cube with gear turning shows up the driver is working.

no matter if you still have to boot in Ubuntu 2d the video driver is installed and working  and supporting 3d

---

### Post by ToxicBurn on 2012-04-10
Ubuntu does not install that by default if i am correct it uses some other type of hacked open source driver with really basic 3d support just enough for unity to work and the additional driver option for jockey I have used for years does not work in 11.10 driver does not install and gives error there are pages and pages of people that have reported this in launchpad .

---

### Post by FatFrog on 2012-04-10
the ATI drivers caused me some heartburn when I first loaded up 11.10 on a brand new machine. After an update was released I downloaded the drivers from the AMD site and they seemed to resolve my issue...

have you tried installing the latest update from AMD/ATI

---

### Post by jadtech on 2012-04-10
nope its not installed by default how ever if you click system setting  in the folder for other drivers you will find the ATI driver there..
the only drivers installed  by default are drivers Linux has some input with development  many company s wont share source code or coporate in making a version that works with the linux development .. 

I have the same video card the driver installed works fine Ubuntu 11.10..

---

