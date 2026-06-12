---
title: "Configuring Ubuntu to work like Windows for my boss"
date: 2010-07-13
forum: General Help
---

### Post by Mendel314 on 2010-07-13
My boss's computer got so riddled with malware that it became unusable, so I asked my friend to install Ubuntu on it. The internet was down, so he couldn't finish configuring it.  Now the internet is back, but I don't know how to configure it for her so that it works like Windows. Does anyone know where to start?  I just want it to run intuitively for her.

---

### Post by mike555 on 2010-07-13
Depends what kind of Internet , dsl, dialup, wireless?
more info will let use help better . I'm assuming your trying to get Internet working .....

---

### Post by Braik on 2010-07-13
First of all, HELLO (even if you are hurry),
 
If you want a real complete answer, you should ask a complete question
 
> **Mendel314 said:**
> My boss's computer got so riddled with malware that it became unusable, so I asked my friend to install Ubuntu on it. The internet was down, so he couldn't finish configuring it.
 
I don't understand what was needed on internet since it is normaly installed with a CD.
 
>  Now the internet is back, but I don't know how to configure it for her so that it works like Windows.  
 
What do you mean "work like Windows"? You want to have the blue screen or what?, maybe the two previous questions are related and you can explain us for a little help?
 
>  Does anyone know where to start? I just want it to run intuitively for her.
 
I will tell you where to start, give us more information, we are not in front of your boss's computer, and we do not have a crystal ball to guess...

---

### Post by uRock on 2010-07-13
Installing ubuntu-restricted-extras will install flash that will make most web pages work. To install it you can either search for it in Synaptic Package Manager via the System> Administration menu or opening a terminal under the Applications> Accessories menu and copying and pasting this command;```
sudo apt-get install ubuntu-restricted-extras
```
You will first want to run updates by going to System> Administration> Update Manager or opening a terminal and running this command;```
sudo apt-get update && sudo apt-get dist-upgrade
``` The reason I am directing to run dist-upgrade instead of the normal upgrade command is because there is going to be a kernel update that will not install with the plain upgrade command.
Let us know if you need to know more.

Cheers,
uRock

---

### Post by kennedyvelez on 2010-07-13
you need internet for your update manager and your software center... and don't try making your desktop looks like a pc (aka windows), try configuring it like a mac... ask google how... you're gonna be needing an internet connection...

---

### Post by uRock on 2010-07-13
> **kennedyvelez said:**
> you need internet for your update manager and your software center... and don't try making your desktop looks like a pc (aka windows), try configuring it like a mac... ask google how... you're gonna be needing an internet connection...

The OP already said the INTERNET connection was up.

If your computer isn't connecting even after the network being up, then please let us know so we can walk you though getting it working.

---

### Post by bodhi.zazen on 2010-07-13
IMO the closest to Windows is KDE, so I would install kubuntu-desktop.

With that said, looks are skin deep and Linux is not windows. Are you sure your boss is willing to run Linux ?

The old adage applies , Linux (Ubuntu) is not a drop in replacement for Windows and unless the boss is willing to change I foresee problems no matter how much or little it looks like windows.

Personally I would change or install a "better" theme, see gnomelook

---

### Post by prodigy_ on 2010-07-13
If malware is the **only** problem, the immediate answer is probably just a good anti-virus (I'd recommend NOD32) with forced auto-cleaning in settings. For extra protection you can slap a free version of Ad-Aware on top of that.

In many respects Linux isn't like Windows. You can make it **look** almost exactly like Windows with a transform pack but I'd advise against that. Because you don't want to encourage "it's almost Windows" way of thinking - it leads to groundless expectations and painful disappointments.

---

### Post by uRock on 2010-07-13
Here is a great link explaining how to install themes. [http://www.youtube.com/watch?v=gl-tmGfQrzs](http://www.youtube.com/watch?v=gl-tmGfQrzs)

---

### Post by gadolinio on 2010-07-13
Mmm the thing is, Ubuntu doesn't work like Windows.
It has many similarities, but many differences too. Generally speaking it's not very different: a mouse pointer, icons to double click, files inside folders, etc. But going deeper you find many differences that would require the user to get used to them. I personally find it far more intuitive than windows, but if your boss wants it to be the same as windows, well, that's not going to happen. :S  If your boss is willing to learn how to use ubuntu, it would be a good choice. And you can change the way ubuntu looks, to make it nearly the same as windows. IMO, it's not difficult to learn how to use ubuntu, but some people just don't want ANY change in the way the use their computer.
So the first thing is asking her whether she's interested in using ubuntu. In that case, download it and burn a liveCD for her to test it first.

---

### Post by Gordonbp531 on 2010-07-13
> **uRock said:**
>  The reason I am directing to run dist-upgrade instead of the normal upgrade command is because there is going to be a kernel update that will not install with the plain upgrade command.




And the Kernel upgrade (if you are talking about going from 32-21 to 32-23) very probably messes up the Shutdown Menus. That's the last thing you want to do to the boss's computer!
See here for the bug in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576204](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576204)

---

### Post by uRock on 2010-07-13
> **gendibal said:**
> And the Kernel upgrade (if you are talking about going from 32-21 to 32-23) very probably messes up the Shutdown Menus. That's the last thing you want to do to the boss's computer!
See here for the bug in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576204](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576204)
If it only effects 16 people, then I wouldn't worry about it. It has not effected any of my machines.

---

### Post by h3llb0y~ on 2010-07-13
I dont think you can configure it to "work like windows". Ubuntu is ubuntu and Windows is....well Windows.
If malware is the only problem, I suggest you get a good antivirus (Kaspersky and BitDefender were rated highly)

---

### Post by uRock on 2010-07-13
I don't think that telling the OP to go back to Windows is the best advice. Apparently Ubuntu is already installed, so the OP only needs to know how to get the system up to date, make it look pretty and get the full functionality of Firefox and maybe MP3 and DVD support. If the boss was a power user, then the boss wouldn't have a malware loaded system, nor would he/she have let someone change the OS because of malware.

---

### Post by bigsmitty64 on 2010-07-13
> **uRock said:**
>  If the boss was a power user, then the boss wouldn't have a malware loaded system, nor would he/she have let someone change the OS because of malware.

That to me is a great reason to reload windows for the boss. If the boss can't understand how to run, or simply doesn't know about ad-aware, or antivirus,  she will no doubt be confused for some time in Linux. If this is a work environment, then the boss needs a usable (to her) pc.
MY advice would be load windows back (if possible), show her ad-aware, and AVG Free Antivirus, and how to use it.
Then, throw a live cd to her and let her play around with it at her convenience. 

One thing we don't know from the OP is, is the boss aware and willing to try Ubuntu? If so then well.....never mind :P

---

### Post by scrooge_74 on 2010-07-13
Where is the OP by the way?

---

### Post by uRock on 2010-07-13
> **bigsmitty64 said:**
> That to me is a great reason to reload windows for the boss. If the boss can't understand how to run, or simply doesn't know about ad-aware, or antivirus, he or she will no doubt be confused for some time in Linux. If this is a work environment, then the boss needs a usable (to him or her) pc.
MY advice would be load windows back (if possible), show the boss ad-aware, and AVG Free Antivirus, and how to use it.
Then, throw a live cd to him or her and let them play around with it at their convenience.
How can they be confused about double clicking the Firefox shortcut to go online or opening OO.org to create a document? Most non-IT managers don't care how a PC runs. It is not their job. They have a small set of functions that they need to do and as long as the IT guy makes those functions easy to find the boss will be happy.

---

### Post by gadolinio on 2010-07-13
> **uRock said:**
> Apparently Ubuntu is already installed, so the OP only needs to know how to get the system up to date, make it look pretty and get the full functionality of Firefox and maybe MP3 and DVD support. If the boss was a power user, then the boss wouldn't have a malware loaded system, nor would he/she have let someone change the OS because of malware.
Good deduction.

> **bigsmitty64 said:**
> 
One thing we don't know from the OP is, is the boss aware and willing to try Ubuntu?
In practice, this is the main question, i guess.

> **scrooge_74 said:**
> Where is the OP by the way?
hahahhahahahahahah

> **uRock said:**
> How can they be confused about double clicking the Firefox shortcut to go online or opening OO.org to create a document? Most non-IT managers don't care how a PC runs. It is not their job. They have a small set of functions that they need to do and as long as the IT guy makes those functions easy to find the boss will be happy.
+1.

If the boss just doesn't want to use linux, even without any valid reason, the topic is over. I know people who just don't want to even give it a look. "It's difficult, and it's difficult, and also difficult". And, after all, they don't >need< a reason. But if she wants to do what's best, I think ubuntu is far better than windows, the main things will be done in the same way, and the ones that are different are worth the try.

---

