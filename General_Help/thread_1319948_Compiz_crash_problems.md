---
title: "Compiz crash problems"
date: 2009-11-08
forum: General Help
---

### Post by Redsoxfanatic on 2009-11-08
hi guys, im new at this so try and stick with me.
 I have been trying to run compiz for a few weeks now and am encountering a problem over and over. When I run compiz in the terminal my background image covers the screen and the computer freezes. from here i am force to do a cold boot. This also happens when i turn on Animation, that is, if  it doesn't just say animations could not be enabled. i would post the output when i run compiz and compiz --replace, but i cannot since the computer freezes to fast.(all the windows and and panels dissapear too.) 
 Oh yeah and just another little piece of info... i skipped the check for blacklisted video cards using compiz-check.(by the way that is a great program, thanks furlong.) I run the intel 8 something(if the exact video card is important tell me and i will find out. It still crashes. Please help!!!:mad:

---

### Post by QIII on 2009-11-08
The details of the card probably are important.

Which version of Ubuntu are you using?  If it is Jaunty, then you may be running into some known regressions in Jaunty with regard to Intel video chipsets.

---

### Post by Redsoxfanatic on 2009-11-08
i am apparently running the Intel Corporation 82845G/GL says Compiz check. I am running Gnome(ubuntu 9.10) Thanks for getting back to me so quick

---

### Post by QIII on 2009-11-08
A bug was reported on Launchpad, and it appeared that it had been fixed at one point.

However, two more recent posts indicate it may still be a problem:

[https://bugs.launchpad.net/ubuntu/karmic/+source/compiz/+bug/385398](https://bugs.launchpad.net/ubuntu/karmic/+source/compiz/+bug/385398)

Similar comment on this guy's blog

[http://kagashe.blogspot.com/2009/11/running-ubuntu-karmic-on-intel.html](http://kagashe.blogspot.com/2009/11/running-ubuntu-karmic-on-intel.html)

I found a few more threads in the forums, and this seems to be an open issue for several people.

Sorry.  That's not very helpful!

When was the last time you went to the terminal and did

```
sudo apt-get update
```
```
sudo apt-get uprade
```
```
sudo apt-get dist-upgrade
```

---

### Post by Redsoxfanatic on 2009-11-09
Thanks ill try that

---

### Post by Redsoxfanatic on 2009-11-09
thanks ill try that

---

### Post by Redsoxfanatic on 2009-11-09
When i try the first line of code i get this:
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5

The others install fine and compiz still doesn't work...are there any other programs i could use to use desktop animations?

---

### Post by Redsoxfanatic on 2009-11-10
Bump

---

