---
title: "Mozilla 3.6.8"
date: 2010-07-24
forum: General Help
---

### Post by lotusalive on 2010-07-24
Hi Experts :))  

Can't seem to install an Archive Mgr extracted tar.bz2 ?  Will someone kindly direct me on this ?

> root@lightening-desktop:/home/lightening# apt-get install firefox-3.6.8.tar.bz2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firefox-3.6.8.tar.bz2
root@lightening-desktop:/home/lightening# 

---

### Post by ubunterooster on 2010-07-24
<snip>see post number 6

V
V
V
V
V
V

---

### Post by wojox on 2010-07-24
> **lotusalive said:**
> Hi Experts :))  

Can't seem to install an Archive Mgr extracted tar.bz2 ?  Will someone kindly direct me on this ?

What archive manager did you get this from? The Mozilla site?

---

### Post by ubunterooster on 2010-07-24
> **wojox said:**
> What archive manager did you get this from? The Mozilla site?
I think he means he is trying to install firefox and already used archive manager to unpack it

---

### Post by wojox on 2010-07-24
> **ubunterooster said:**
> I think he means he is trying to install firefox and already used archive manager to unpack it

Ahh, got it. If you extracted Firefox and it made a firefox folder in your user directory, try opening a terminal and running

```
~/firefox/firefox
```

---

### Post by lovinglinux on 2010-07-24
> **lotusalive said:**
> Hi Experts :))  

Can't seem to install an Archive Mgr extracted tar.bz2 ?  Will someone kindly direct me on this ?

You cannot install a downloaded tar.gz file with the package manager, like you are trying to do. When you use the command **apt-get install something**, you are actually looking for the package **something** in the online repositories. So putting the name of file that you have downloaded from a web site won't work. Besides, a tar.gz file is not even a format recognized by the package manager, which uses .deb files.

What you have downloaded is an archive of a Firefox release. All you need to do is to extract it and then run the file **firefox** located inside the extracted folder. See Method #1 of my Firefox tutorial [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html).

If you have a 32bit system, perhaps would be easier for you to use Ubuntuzilla (Method #2).

There is also an extension for Firefox that I develop, called [FoxTester]("http://foxtester-extension.blogspot.com"), that allows you to easily install and test different versions of Firefox, without running any commands or disrupting your current Firefox installation.

---

### Post by lotusalive on 2010-07-25
Yep:  I need a new Browser, if I want to keep using Jaunty 9.04, i guess.  I got the firefox-3.6.8 tar.bz2, From Mozilla's Shiretoko page, abandoned by Ubuntu, completely I guess...  ms's $ probably... certainly is mine too, as we all know !  lol...  But Shiretoko SURE WAS The Nicest INTERFACE WITH W's...  (and I could get my 'work' done with it)...   I lost ALL my past six-months of Bookmarks today too with the www 3.6 Moz Upgrades... [har :()]

I wasn't a big security freak, but I did utilize FoxyProxy: Patterns, still got ripped off in a FB 'Game' Sim.  Nothing will stay installed today with Either Shiretoko (defunct in Linux Ubuntu ?  Site offered the d/l, but said it was 'abandoned'... (in Linux ? )  Couldn't EVEN Bring Adobe Flash or the Game or auto install From Adobe with G-debi. I did the Medibuntu instead, last week.  But today, the Game Sim I've been working on for 6 mos, would not even come up in Regular Firefox, or KDE Konquoror,(because I don't use it and don't think there's anything on me that I don't already know, not if I can help it, which is also KNOWn !)  None of Adobe was installing automatically today, nor was it STAYING installed upon restarting, logging out, etc...  O' well.  All suggestions welcome, and All of the above is Greatly Appreciated !  ty

---

### Post by lovinglinux on 2010-07-25
> **lotusalive said:**
> Yep:  I need a new Browser, if I want to keep using Jaunty 9.04, i guess.  I got the firefox-3.6.8 tar.bz2, From Mozilla's Shiretoko page, abandoned by Ubuntu, completely I guess...  ms's $ probably... certainly is mine too, as we all know !  lol...  But Shiretoko SURE WAS The Nicest INTERFACE WITH W's...  (and I could get my 'work' done with it)...   I lost ALL my past six-months of Bookmarks today too with the www 3.6 Moz Upgrades... [har :()]

I wasn't a big security freak, but I did utilize FoxyProxy: Patterns, still got ripped off in a FB 'Game' Sim.  Nothing will stay installed today with Either Shiretoko (defunct in Linux Ubuntu ?  Site offered the d/l, but said it was 'abandoned'... (in Linux ? )  Couldn't EVEN Bring Adobe Flash or the Game or auto install From Adobe with G-debi. I did the Medibuntu instead, last week.  But today, the Game Sim I've been working on for 6 mos, would not even come up in Regular Firefox, or KDE Konquoror,(because I don't use it and don't think there's anything on me that I don't already know, not if I can help it, which is also KNOWn !)  None of Adobe was installing automatically today, nor was it STAYING installed upon restarting, logging out, etc...  O' well.  All suggestions welcome, and All of the above is Greatly Appreciated !  ty

Well, Shiretoko wasn't abandoned. It was the development codename of Firefox 3.5, just like Namoroka is the codename of Firefox 3.6. What happened is that Mozilla changed it's update policy and started to push new features into minor-updates, like for example from 3.6.3 to 3.6.4, when plugin isolation was introduced, instead or waiting for Firefox 3.7 (aka Firefox 4). Additionally Mozilla stopped supporting Firefox 3.0 series recently, so Canonical decided to make Firefox 3.6 series available to all supported Ubuntu versions, which is very uncommon. Usually Ubuntu only provides security updates, until a new Ubuntu version is released, which then gets the latest versions of most applications.

You can download any version of Firefox, including Firefox 3.5.x (Shiretoko) from [Mozilla FTP site]("ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/") and install following method #1 of my tutorial. Nevertheless, I recommend to use 3.6.8, which was released just two days after 3.6.7, to fix instability issues. It isn't in the official repositories yet, but will be soon.

I don't know why you lost your bookmarks. Installing a new version or upgrading Firefox shouldn't mess with personal settings and files. They are all kept, no matter which version you have. Perhaps the profile folder has changed. Sometimes they do that with development versions like Shiretoko and Namoroka. So check your ~/.mozilla folder to see if there is more than one firefox folder there. Your bookmarks might still be there.

For future reference, [backup your profile]("http://firefox-tutorials.blogspot.com/2010/05/backups.html") or at least sync your bookmarks with an online service. Profiles can get corrupted, so if the data is important, you should backup regularly.

For your flash issues, get my extension [FLASH-AID]("http://flash-aid-extension.blogspot.com").

---

### Post by lotusalive on 2010-07-26
I haven't had a moments peace yet, to utilize your instructions here.  But I did lose my Bookmarks, and installed Persona Skin from Firefox, with their upgrade 2 days ago.  Thanks for the explanation, lovinglinux, is much appreciated.  'Shiretoko' is STILL not saving my Bookmarks, lol ;/, maybe I'll just go back to Firefox Standard Browser until I have time to work on this. :)

---

### Post by lotusalive on 2010-10-12
You guys are all just the best :) :guitar:  I sure wish I had the time to get good at this, b/c I absolutely love the feeling of getting around w/bg...  Thanks so much all-:KS's

---

