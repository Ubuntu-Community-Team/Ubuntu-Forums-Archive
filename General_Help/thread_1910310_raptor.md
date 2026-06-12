---
title: "raptor"
date: 2012-01-16
forum: General Help
---

### Post by d2redneck on 2012-01-16
Hey all first off, thanks for all the help that you have all given me on getting used to Ubuntu. I am really close to either making windows my backup operating system on my laptop or get rid of windows all together.  I do have yet another question though. I am currently in college and I have to use raptor for programming class.  I was wondering if there was a substitute for raptor or if there was a way that I could get raptor to run on Ubuntu.  I haven't been able to find anything on the web about using raptor with linux at all.  Any help would be greatly appreciated.

---

### Post by epic.mint on 2012-01-16
have you tried **wine** it's an application for running windows programs in linux.
if you haven't tried it do this. copy the install directory for raptor to your linux partition and simply run the .exe with wine. it also runs warcraft 3 flawlessly.

it's in the repositories so simply.
```
sudo apt-get install wine
```

hope it helped and have an awesome linux experience.

---

### Post by xyzzyman on 2012-01-16
Admit you. You didn't actually look on the internet... They talk about on right on the homepage for Raptor... It's also been answered here on the forums: [http://ubuntuforums.org/showthread.php?t=1581691](http://ubuntuforums.org/showthread.php?t=1581691)

---

### Post by d2redneck on 2012-01-17
sorry i did must not have put in the right search terms lol but, thanks for the info

---

### Post by xyzzyman on 2012-01-17
Well let this be your lesson. :P

But yeah, it apparently works almost fully under Wine. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=24239](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24239)

I would recommend installing Wine from the WineHQ PPA (Is more up to date):

```

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
```

And it's probably safe to assume that Windows came with your laptop so it's a valid license. Because of this if you have a working dual-boot then why not keep Windows? At the very least make sure you've created your recovery DVD's, but keep it on there even if you wind up giving it alot less space 'cuz at some point in the future you'll thank yourself. There's a few people on the forums that will preach you should get anything 'Winbloze' off your system but you'll find most people who use Linux use Windows also. 

EDIT: Another thought is if you are in college, your school may participate with Microsoft and you can get free copies of MS OS's and software. If so then take advantage of it and you can always use VirtualBox and run Windows inside of a VM (VirtualMachine). Not a 100% replacement for running natively as you're not going to play most games in it, etc... But a program like Raptor would run fine.

Also remember to report back to this thread and mark SOLVED if Wine does work for you (especially if you have to take any steps that aren't the basic defaults), and update the raptor entry at WineHQ.com.

---

### Post by xyzzyman on 2012-01-17
I don't see raptor in the repositories...

---

### Post by d2redneck on 2012-01-17
is wine kind of like VMware player?

---

### Post by xyzzyman on 2012-01-17
It's sort of like a universal-translator for programs. They think they're running in Windows while they actually are in Linux. Wine captures any system calls from Windows programs and handles it. Doesn't work for everything, and the more proprietary the code the less likely it will work.

---

### Post by oldos2er on 2012-01-17
> **xyzzyman said:**
> I don't see raptor in the repositories...

I show raptor-utils and raptor2-utils and various libraptor* packages in the repositories.

---

### Post by xyzzyman on 2012-01-17
> **oldos2er said:**
> I show raptor-utils and raptor2-utils and various libraptor* packages in the repositories.

raptor-utils and it's associated packages are for an RDF processor... He uses RAPTOR a program used by educators for beginning programmers.

Also, there was a post by someone saying raptor was in the repositories... Not sure where it went??? Unless I completely imagined it.... haha

---

### Post by oldos2er on 2012-01-17
> **xyzzyman said:**
>  Unless I completely imagined it.... haha

No, it was spam, so it's gone.

Sorry, guess I got the wrong raptor.

---

### Post by d2redneck on 2012-01-17
I was looking in the synaptic package manager and I saw those same raptor files.  I think that those where the ones that the first saw.  I don't think that those are the same programs that I need but, I need to figure out how to use WINE and then I will have that going.

---

### Post by xyzzyman on 2012-01-17
Have you read the Wine page for raptor? Depending on your usage the known issues may/may not be able to be lived with.

---

### Post by d2redneck on 2012-01-18
I have been looking at it and I am having some trouble figuring it out.

---

