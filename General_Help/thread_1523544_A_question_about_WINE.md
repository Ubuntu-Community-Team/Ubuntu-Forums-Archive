---
title: "A question about WINE"
date: 2010-07-03
forum: General Help
---

### Post by Bernie Gallagher on 2010-07-03
When I went to the WINE site ( [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) ) to download it, it says that it's a beta package.  I can't seem to find a version of WINE for Ubuntu that's not a beta package.  Should this be a concern?  Can I get a non-beta version of WINE for Ubuntu elsewhere?

---

### Post by Manyette on 2010-07-03
I've used the beta version without problems for quite a while, for what it's worth.

---

### Post by SmokeyThePanda on 2010-07-03
[https://help.ubuntu.com/community/Wine#Ubuntu%20versions%20of%20Wine%20%28Recommended%29](https://help.ubuntu.com/community/Wine#Ubuntu%20versions%20of%20Wine%20%28Recommended%29)

Read the part about Hardy Heron. 

[http://www.winehq.org/](http://www.winehq.org/)

Then go there.

---

### Post by Bernie Gallagher on 2010-07-03
Okay, but what is the "Ubuntu universe software channel?"  I just installed Linux for the first time a few hours ago...

---

### Post by SmokeyThePanda on 2010-07-03
It is a repository. 

Open up Synaptic. Applications --> System --> Synaptic Package Manager

Then open up Settings --> Repositories

Then check the boxes on the front page that have (Main) (Universe) (Restricted) and (Multiverse). 

The Universe is the one you want, but might as well add them all.

---

### Post by Bernie Gallagher on 2010-07-03
I did that, and several versions of WINE came up amongst the available packages.  Does it matter which one I choose?

---

### Post by SmokeyThePanda on 2010-07-03
Hmm..I believe you want WINE 1.0.1 If I recall correctly, that was the latest stable WINE on the site.

---

### Post by Bernie Gallagher on 2010-07-04
My choices are:
 
wine1.2-gecko
wine
wine1.2
wine-dev
wine-gecko
wine1.2-dev
wine1.2-dbg
winefish
 
I'm pretty sure I don't want the dev or dbg versions, but I'm a n00b who just installed Linux for the very first time yesterday and still lack many many clues :-)

---

### Post by philinux on 2010-07-04
Install wine1.2

---

### Post by Bernie Gallagher on 2010-07-04
Okay.  It's installing it.  BTW, when I selected wine1.2 it automagically sellected wine1.2-gecko also.  I assume that's as it should be?

"The marked changes are now being applied. This can take some time.  Please wait."

I'm waiting...

---

### Post by philinux on 2010-07-04
> **Bernie Gallagher said:**
> Okay.  It's installoing it.  BTW, when I selected wine1.2 it automagically sellected wine1.2-gecko also.  I assume that's as it should be?

That is what is called a dependency. wine1.2 needs the gecko app to run.

---

### Post by jingaling on 2010-07-04
I had a play around with Wine when I first started to use Ubuntu as we use certain windows applications that aren't compatible with Linux in work (mainly windows live sync). I just couldn't get it to work to save my life.

So opted for VirtualBox and a Windows XP VM running in seamless mode. So when I am at work I just bang XP on one of my workspaces and away I go all the Microsoft applications I ever need but still have the great functionality of unbuntu over the top.

Just worth thinking about that all, I find it to be much easier than Wine...sorry just though Id add my 2p worth since you mentioned you where a 'noob' and I personally found this easier than Wine :D

Jing

---

### Post by wpfaff on 2010-07-04
> **Bernie Gallagher said:**
> Okay.  It's installing it.  BTW, when I selected wine1.2 it automagically sellected wine1.2-gecko also.  I assume that's as it should be?

"The marked changes are now being applied. This can take some time.  Please wait."

I'm waiting...

wine-gecko is the fake Internet Explorer browser

---

### Post by philinux on 2010-07-04
> **wpfaff said:**
> wine-gecko is the fake Internet Explorer browser

Yes I forgot it's a recommended package and the default these days is install with recommends.

---

### Post by Bernie Gallagher on 2010-07-04
Oh yeah?  Well, that's okay I guess.  But I just want WINE to play some of my M$ games like Train Simulator.  I don't really need a fake IE.  Firefox is just fine...

---

### Post by philinux on 2010-07-04
> **Bernie Gallagher said:**
> Oh yeah?  Well, that's okay I guess.  But I just want WINE to play some of my M$ games like Train Simulator.  I don't really need a fake IE.  Firefox is just fine...

If you have specific wine related support problems please post in here.

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by RedRat on 2010-07-04
Since you are new to Linux/Ubuntu and Wine, you might also want to do a search for wine-tricks website. To run some programs, you might have to download some added free libraries from Microsoft, most the MFCs. You may not need them now, but be aware of that wine-tricks is there to help.

---

### Post by J V on 2010-07-04
Actually, skip winetricks and go for playonlinux - it will make things a lot easier to use (But for some reason it crashes ALL THE TIME for me nowadays...

---

### Post by Bernie Gallagher on 2010-07-05
Hmmm.  If it crashes all the time, why do I want it?

---

