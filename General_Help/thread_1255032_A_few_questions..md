---
title: "A few questions."
date: 2009-09-01
forum: General Help
---

### Post by mohanish666 on 2009-09-01
I am a novice to the (recently discovered) world of linux. I also happen to be a sound recording enthusiast. I decided to go with Ubuntu Studio.

I first installed Ubuntu 8.10 onto my laptop and then upgraded it to Ubuntu Studio using:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```I then applied the Studio theme and Studio log-in screen

Lets call this state 'A'.

Then after a few days I upgraded Ubuntu to 9.04 (from System>Administration>Update Manager)

Lets call this state 'B'


What I used to think is that at state A I had Ubuntu Studio 9.04.

But as I transitioned to state B my themes and stuff changed which is confusing me (I expected only the non studio stuff to change)

My question is:
What distribution did i have at state A and B?

---

### Post by anujpathania on 2009-09-01
Ideally -

State A >> Ubuntu Studio 8.10

State B >> Ubuntu 9.04

Practically -

State  A >> Mess

State B >> Bigger Mess

Well you confused not only yourself but perhaps also your computer. Problems will crop up sooner or later which will be hard to diagnose and rectify.

Better option is to perform a clean installation of Ubuntu or its flavor, but do some web research to see what you want and make up your mind before hand this time.

---

### Post by mohanish666 on 2009-09-01
Well i couldn't install a clean version of Ubuntu Studio as my netbook doesn't have a cd-rom and when  installing through usb, it kept asking for cd-rom drivers (being an alternate disk). I know there is a way to do this, but it was beyond my scope. So I let that go and proceeded with the mentioned method.


What wouold you suggest is the best method for me to get Ubuntu Studio 9.04 on my machine with as less a "mess" as possible?

---

### Post by earthpigg on 2009-09-01
> What wouold you suggest is the best method for me to get Ubuntu Studio 9.04 on my machine with as less a "mess" as possible?


system -> administration -> usb startup disk creator -> point the ubuntu studio 9.04 .iso file to a thumb drive -> use the thumb drive just like you would a LiveCD.

---

### Post by mohanish666 on 2009-09-01
But would this method get over the problem that I was having from flash disk installation earlier?

(I have installed Ubuntu once and Kubuntu twice from flash disks. Its just Ubuntu Studio that gives the following error. (Something to do with it being an alternated cd I guess))

During installation, after setting keyboard preference and before it can load information it gives an error that the CD-ROM is not mounted (but my netbook has no CD-ROM, anyway). I can't go any further than this step.

---

### Post by lisati on 2009-09-01
Probably not a good idea to mix two different versions of Ubuntu (8.10 & 9.04) unless you find some way of keeping them separate or upgrading the older to match the newer first.

---

### Post by jmfal on 2009-09-01
You dont have to download ubuntu studio onto a usb stick.
Put whatever flavor ubuntu on your stick, install it in your pc, and you can convert to studio in synaptics= system>administration>synaptics.
 If you cant find it go to system>adminisration>software sources and put a check in all the boxes except source and uncheck cdrom.
Next -third party, put a check in all those, close it. A window willcome up saying, man I forgot what it says, but anyway agree and it will add those repositories.
 You might need medibuntu for codecs and such, go to medibuntu website, it will show you how to add repository and keyring.
  Hope this helps, its the easyist way to get studio, if you dont have a dvd burner

---

### Post by mohanish666 on 2009-09-01
> **jmfal said:**
> You dont have to download ubuntu studio onto a usb stick.
Put whatever flavor ubuntu on your stick, install it in your pc, and you can convert to studio in synaptics= system>administration>synaptics.
 If you cant find it go to system>adminisration>software sources and put a check in all the boxes except source and uncheck cdrom.
Next -third party, put a check in all those, close it. A window willcome up saying, man I forgot what it says, but anyway agree and it will add those repositories.
 You might need medibuntu for codecs and such, go to medibuntu website, it will show you how to add repository and keyring.
  Hope this helps, its the easyist way to get studio, if you dont have a dvd burner


Ok cool. Will try that. Thanks.

Anyway another question I had was:
Will Studio be stable if I first do a clean install of Kubuntu 9.04 and then convert to Studio.
Also will the product be any different than Ubuntu 9.04 (clean install) and then convert to Studio.

Sorry if this sounds stupid, but am just trying to understand how this whole thing works.

---

### Post by snowpine on 2009-09-01
Hi Mohanish, you didn't do anything wrong, and you don't have a "mess." If I understand your post correctly, the only "problem" is that your themes and artwork got switched to the 9.04 defaults... however, you should be able to easily switch back to the Studio themes if you want (System-Preferences-Appearance).

Either way, your audio applications should still work okay (now upgraded to the 9.04 versions), is this correct?

---

### Post by mohanish666 on 2009-09-03
> **snowpine said:**
> Hi Mohanish, you didn't do anything wrong, and you don't have a "mess." If I understand your post correctly, the only "problem" is that your themes and artwork got switched to the 9.04 defaults... however, you should be able to easily switch back to the Studio themes if you want (System-Preferences-Appearance).

Either way, your audio applications should still work okay (now upgraded to the 9.04 versions), is this correct?


Yes yes, I never mentioned I had witnessed any problem,  i was just confused about the version of ubuntu in my system.

Thanks for your help anyway.

---

