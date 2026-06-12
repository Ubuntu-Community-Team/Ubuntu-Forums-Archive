---
title: "help needed please&gt;flash&gt;mozilla"
date: 2010-01-05
forum: General Help
---

### Post by jayze on 2010-01-05
I cannot watch vid on most sites eg utube...sites say I havent the latest flash player or java is not enabled.  Not so! when i try to redownload flash player a little brown box with apturl in it  pops up and asks me do I want ubuntu equivalents. if I tick yes it chucks 40 or so updates at me...and nothing resolved. If I tick no then the box simply will not go away and i still cant add flash to mozilla. What am I doing wrong please..thanks

---

### Post by pmlxuser on 2010-01-05
download the one from adobe and see if the problem get solved.. 
just go adobe website flash player linux /ubuntu... get the deb version and install it..

---

### Post by jayze on 2010-01-05
Thanks....but thats exactly what I am doing when I get into difficulty and can't download it

---

### Post by philinux on 2010-01-05
> **jayze said:**
> I cannot watch vid on most sites eg utube...sites say I havent the latest flash player or java is not enabled.  Not so! when i try to redownload flash player a little brown box with apturl in it  pops up and asks me do I want ubuntu equivalents. if I tick yes it chucks 40 or so updates at me...and nothing resolved. If I tick no then the box simply will not go away and i still cant add flash to mozilla. What am I doing wrong please..thanks

Click the restricted formats link below my signature and follow the instructions to install ubuntu-restricted-extras.

---

### Post by audiomick on 2010-01-05
Hi Jayze.
I think we have already been through the restricted extras thing haven't we?

So for pmlxuser's suggestion, go to adobe
[http://www.adobe.com/](http://www.adobe.com/)
and choose the link for "get adobe flash player"

When you're there, you have to choose the version with the drop down menu that is on the page.

Choose .deb for Ubuntu 8.04+

The APT one for ubuntu would also work, but I am not sure how to install that...

Then click on "agree and download". You should be offered the choice between "store" and "open with gdebi". If you choose the latter, it should just install. If you choose the former, you will have to then go to where the file is stored, right click, and choose "open with gdebi" or something similar to that from the list that opens.

There is a lot of information about optimizing firefox here:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by pricetech on 2010-01-05
What version of Ubuntu are you running and is it 32 bit or 64 bit ??

It makes a difference.

---

### Post by jayze on 2010-01-05
Hello people and thanx to you all for replying.> Philinus I do already have restricted extras. Hello again Mick (blushing with shame) Yes ditto I did and I do and I am going to Adobe.com. Theres a "Karmic Partner Channel" that seems to be causing me probs. And hello there you in Tenessee but (um ) (more shame) how do I tell if its 64 or 32. I'm a bit fed up really because after a few lovely weeks on ubuntu now the laptops behaving just like the when using microsoft so it has to be something I'm doing wrong!:(...anyway I'm going to follow Micks instructions to the letter and check out the 64/32  thing...will be back!

---

### Post by pricetech on 2010-01-05
> **jayze said:**
> how do I tell if its 64 or 32

You would know based upon which one you downloaded / installed.  Since you don't know that offhand, you're probably running 32bit.

I'm assuming also that you are running Karmic based upon your reference to a Karmic Partner Channel.

I'm afraid I won't be much help beyond suggesting that you try removing what you downloaded and install again via Synaptic to see if perhaps that makes it work.  It may not be the latest, but if it works .......

---

### Post by plucky on 2010-01-05
> how do I tell if its 64 or 32.


From a terminal ```
uname -a
```

x86, i686, i386 = 32 bit
x86_64 = 64 bit


Good Luck

---

### Post by bluestar14 on 2010-01-05
javascript probably isn't enabled, go to options and look for the javascript on thing

---

### Post by jayze on 2010-01-06
solved...quite simple really...settings on "noscript" not configured correctly:)

---

