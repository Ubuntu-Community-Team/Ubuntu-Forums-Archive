---
title: "vuze installation problem"
date: 2011-03-13
forum: General Help
---

### Post by umpat on 2011-03-13
Hello every one.....I have never used any unix before and ubuntu is my first. I am loving the idea of free and open software and the support via forums. It's been two days since I installed ubuntu notebook on my hp pavillion, everything is very good except for few glitches. I tried installing vuze from ubuntu software center and i am getting this error..


There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 179, in _process_transaction
    self.commit_packages(*self.trans.packages)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 227, in commit_packages
    self._commit_changes()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 736, in _commit_changes
    self._check_obsoleted_dependencies()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 518, in _check_obsoleted_dependencies
    for pkg in self._cache:
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 173, in __iter__
    yield self[pkgname]
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 158, in __getitem__
    pkg = self._weakref[key] = Package(self, self._cache[key])
KeyError: 'p\xecymouth-theme-glow'


complete noobie here...
thank you all

---

### Post by oboedad55 on 2011-03-13
Which version of Ubuntu are you using, 32 or 64bit? I just installed Vuze through the software center and got no errors, which of course helps you not at all. I'm running 10.04 x64. Don't know what you plan on using Vuze for, but have you tried Transmission? Also, you can try Deluge, which is available through the software center/synaptic. It has a very similar interface to uTorrent. Hope this helps some. If not, hang in there. This is a very active forum and you're almost sure to get the help you need.

---

### Post by umpat on 2011-03-13
Thank you .
I am using the 10.10 notebook. 
I can't install anything . All I get is the above error. 
Any ways to fix it ..

---

### Post by oboedad55 on 2011-03-13
Everything you try to install gives this error? If you haven't spent much time setting things up it might be easier and faster just to reinstall Ubuntu. Backup any data you want to save.

---

### Post by umpat on 2011-03-13
Well, this is the fourth time I am installing Ubuntu.  Now I just realized I cant't install anything at all. I tried running Ubuntu update manager but it never opens. 
I used the synaptic package manager to see if anything was broken but there is none. 
Is there a way I can partition my hard drive and within ubuntu ?
Thank you for your reply

---

### Post by umpat on 2011-03-13
Lol how come you are drinking skimmy soy caramel and i'm drinking the regular coffee. guess it takes a lot to get that cup, i guess.:D

---

### Post by oboedad55 on 2011-03-13
> **umpat said:**
> Well, this is the fourth time I am installing Ubuntu.  Now I just realized I cant't install anything at all. I tried running Ubuntu update manager but it never opens. 
I used the synaptic package manager to see if anything was broken but there is none. 
Is there a way I can partition my hard drive and within ubuntu ?
Thank you for your reply

You can't partition mounted drives, one of which your Ubuntu is installed on. You can boot from the  CD and use Gparted to do your partitioning. What problems have you had that have required four installs?

---

### Post by umpat on 2011-03-13
First time I installed I installed desktop instead of notebook. Second time I couldn't get the graphics and wireless to install after updating from the additional drivers from system menu. Then I get the drivers to work, then I had a unstable OS, crashed on me a lot of time. 
Now I did a fresh install yesterday and I am having this issue. 
But I am linking ubuntu. Its a good system .
So how will I get this working or i will have to reinstall.

BTW I installed all the times from a USB drive, will that make any difference ?

---

### Post by oboedad55 on 2011-03-13
> **umpat said:**
> First time I installed I installed desktop instead of notebook. Second time I couldn't get the graphics and wireless to install after updating from the additional drivers from system menu. Then I get the drivers to work, then I had a unstable OS, crashed on me a lot of time. 
Now I did a fresh install yesterday and I am having this issue. 
But I am linking ubuntu. Its a good system .
So how will I get this working or i will have to reinstall.

BTW I installed all the times from a USB drive, will that make any difference ?

What you installed from should make no difference. How is your drive partitioned?

---

### Post by umpat on 2011-03-14
I think it is Master boot Record, linux 0x83, 157 GB ext 4, extended 3.1 GB and 3.1 Swap

---

### Post by oboedad55 on 2011-03-14
> **umpat said:**
> I think it is Master boot Record, linux 0x83, 157 GB ext 4, extended 3.1 GB and 3.1 Swap

Sounds OK. I'm at a loss. Perhaps someone else will chime that has some experience with this error. I've never run across it, lots of others, but not that. BTW, I hate soy. I'd rather have all the fatty goodness of real cream.

---

### Post by umpat on 2011-03-14
Well I figured a way. I went to synaptic package manager, clicked all - mark all upgrades-and apply changes and it started working. 
Anyways thank you for your help.

---

### Post by Robins Airman on 2011-04-02
> **umpat said:**
> Well I figured a way. I went to synaptic package manager, clicked all - mark all upgrades-and apply changes and it started working. 
Anyways thank you for your help.


Dude..you're a life saver...not mine, but my pc's...i was about to throw it out the window!

This fixed all my issues!

THANK YOU!!!

---

