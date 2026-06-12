---
title: "wine/dreamweaver/ubuntu problems"
date: 2010-10-07
forum: General Help
---

### Post by tech7 on 2010-10-07
I've been running a dual-boot system (ubuntu lucid and windows 7) for some time now for the sole purpose of being able to use my dreamweaver cs4 and rosetta stone software on windows, and for everything else, booting into my favorite OS; Ubuntu.
I've also been trying to install Dreamweaver on my Ubuntu via wine w/o success.  
I've tried so many things and followed so many threads in various forums trying to get my fave piece of software to work on my fave OS so I can finally stop messing around with booting into one operating system then another and back again, what a pain!!!
I've come to an issue in my current attempt where, while trying to uninstall wine, I get this error message:

"Previous installation hasn't been completed"
"The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

And I cannot do anything with wine anymore.  I was going to uninstall it once again, to try to just do a completely clean install and start over.  But, now I cannot even do that..  

Does anybody know a way to remedy this situation?

---

### Post by ivarn on 2010-10-08
I had the same problem when I first installed ubuntu and I figured out why it wouldn't work.
The Wine version from Synaptic is old and unupdated.
I figured this out because I visit the Wine website [http://www.winehq.org/](http://www.winehq.org/)
There's a software database where you can see if your windows software are compatible and stable with your installed wine version.
So I suggest you uninstall the wine packages from synaptic and instead install the one from [http://www.winehq.org](http://www.winehq.org).

---

### Post by Merthod on 2010-10-08
You can just delete CS4 from program files within wine directory and from your home folder in the .wine (hidden) directory.

Be sure to update your software sources regularly with
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
``` .

Then run your system update manager.

Look up in [http://appdb.winehq.org]("http://appdb.winehq.org") for DreamWeaver CS4 and check its status. You may find it works but not smoothly (it's rather rare so install something that works smoothly without some tweaking), and need some tweaking to get it working.

Hope this helps: [http://aminesoft.wordpress.com/2009/08/18/install-dreamweaver-cs4-in-ubuntu-and-debian/]("http://aminesoft.wordpress.com/2009/08/18/install-dreamweaver-cs4-in-ubuntu-and-debian/")

---

### Post by tech7 on 2010-10-09
thanks guys..
I followed your advice ivarn and got one of the programs that I wanted to use on wine to work now..  It wasn't dreamweaver, but it's just as valuable to me.  
Merthod, I'm going to save those commands and use them quite a bit i think..  
Thanks..

---

