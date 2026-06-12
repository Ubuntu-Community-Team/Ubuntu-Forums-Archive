---
title: "Help on installing Adobe Flash Player"
date: 2010-06-29
forum: General Help
---

### Post by minichambre on 2010-06-29
I've just installed Ubuntu and loving it so far. 

I've just tried to access YouTube and have been prompted to install Adobe Flash Player - which Im finding impossible, do I download the APT or .Deb file, I've tried both and I just dont understand how it works.

All help appreciated thanks.

---

### Post by howefield on 2010-06-29
Open System > Administration > Synaptic Package Manager and search for flashplugin-installer, right click and select Mark for Installation, then hit the apply button and apply again..

---

### Post by Frogs Hair on 2010-06-29
Install Adobe flash plugin from the Ubuntu software center.

---

### Post by QIII on 2010-06-29
Install it from Synaptic.  You'll find it as something like "flashplugin-nonfree", I believe.  (Sorry, not at my machine right now.)

Just a note:  Support for the 64 bit Beta has been pulled by Adobe for the time being.  A security flaw in the 32 bit version was also present in the 64 bit version.  Adobe quickly put out a new update of the 32 bit version, but has not done so with the 64 bit version.  

What you will get with flashplugin-nonfree is the 32 bit version.

---

### Post by minichambre on 2010-06-29
Ahh ok, I have the 32 bit version anyway.

One more question for now guys, Adobe is installed and working now but Im unable to use the pause/play and fullscreen buttons on the video. Nor can I minimise the annoying adds that pop up.

Why is this?

---

### Post by garvinrick4 on 2010-06-29
> **minichambre said:**
> Ahh ok, I have the 32 bit version anyway.

One more question for now guys, Adobe is installed and working now but Im unable to use the pause/play and fullscreen buttons on the video. Nor can I minimise the annoying adds that pop up.

Why is this?
Next time you do a ubuntu GUI set-up use:
```
sudo apt-get install ubuntu-restricted-extras
```It will give you all your codecs, java, true type fonts, flash, and much more.
You have to go to software sources and check the partners repostory first.
Make it the first thing you install, it is a package that will save time and bother.
Matter of fact you can run it and it will install anything that you have not in the package.

---

### Post by howefield on 2010-06-29
> **garvinrick4 said:**
> You have to go to software sources and check the partners repostory first.

Why would you do that to install ubuntu-restricted-extras ?

It isn't in the partner repository.

---

### Post by minichambre on 2010-06-29
> **garvinrick4 said:**
> Next time you do a ubuntu GUI set-up use:
```
sudo apt-get install ubuntu-restricted-extras
```It will give you all your codecs, java, true type fonts, flash, and much more.
You have to go to software sources and check the partners repostory first.
Make it the first thing you install, it is a package that will save time and bother.
Matter of fact you can run it and it will install anything that you have not in the package.

Sorry to sound stupid, but I understand very little of that.. what's a Ubuntu GUI set up? And should I do that now, and where, and how? lol

As you may have noticed... I'm incredibly new to Ubuntu

---

### Post by garvinrick4 on 2010-06-29
> **howefield said:**
> Why would you do that to install ubuntu-restricted-extras ?

It isn't in the partner repository. I am now on 10.10 but is not 10.04 still have java in partners? Still no reason not to have partners in sources.list.
I see from 9.04 to 9.10 to 10.04 to 10.10 partners has changed quite a bit.

---

### Post by garvinrick4 on 2010-06-29
> **minichambre said:**
> Sorry to sound stupid, but I understand very little of that.. what's a Ubuntu GUI set up? And should I do that now, and where, and how? lol

As you may have noticed... I'm incredibly new to Ubuntu GUI = Graphic user interface. Just a fancy way to say Desktop. There are no stupid questions ask all you want.

Open a terminal Ctrl/Alt/t and insert:  (or Applications to Accessories to terminal)
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by howefield on 2010-06-29
> **garvinrick4 said:**
> but is not 10.04 still have java in partners?

Sun Java is in partner, but that has nothing to do with ubuntu-restricted-extras. Install that package in 10.04 and you get java based on openjdk.


> Still no reason not to have partners in sources.list.

Sure, just not for the reason you gave.

---

### Post by garvinrick4 on 2010-06-29
By the way there are a lot of ways to get things done in Linux so you will get a variety of
answers and mostly they are all just different ways to get same thing done. I just mentioned ubuntu-restricted-extras in case you wanted to play videos and music and such.
It is just a package to install that has a lot of packages enclosed.

---

### Post by garvinrick4 on 2010-06-29
> **howefield said:**
> Sun Java is in partner, but that has nothing to do with ubuntu-restricted-extras. Install that package in 10.04 and you get java based on openjdk.




Sure, just not for the reason you gave. I will make sure I look into all the different changes in partners over the last 4 or so versions. Thanks, I do not want to give
any misguided info.

I just looked in 10.10 and java was in main now also, partners has just about nothing left.

---

