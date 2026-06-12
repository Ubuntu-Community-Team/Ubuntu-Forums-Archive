---
title: "Shotwell won't open"
date: 2012-04-02
forum: General Help
---

### Post by Hungry Man on 2012-04-02
Right click an image, open shotwell, nada.

I'm on Ubuntu 12.04. Up to date.

I've tried:

sudo apt-get remove shotwell

sudo apt-get install shotwell

sudo apt-get dist-upgrade shotwell

Nothing works. Won't open.

> shotwell: error while loading shared libraries: libgexiv2.so.0: cannot open shared object file: No such file or directory


---

### Post by RJARRRPCGP on 2012-04-02
Clearly a broken package installation routine.

I can't see why you would get dependency-hell when installed from a repository. The facepalm of April 2, 2012. 

You shall never get an error about being unable to load a shared library when installed from a repository.

---

### Post by jmaryinchina on 2012-04-02
Same here :

shotwell: error while loading shared libraries: libgexiv2.so.0: cannot open shared object file: No such file or directory

Trying to recompile :

First doing : 

root@ju-U36SD:/home/ju# apt-get build-dep shotwell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-Depends dependency for shotwell cannot be satisfied because candidate version of package libgexiv2-dev can't satisfy version requirements.

So the problem belong to libgexiv2 and I guess the problem might solve by itself when libgexiv2 will be upgraded.

by the way, it seems to be under investigation : [http://askubuntu.com/questions/116662/shotwell-0-12-shared-library-error](http://askubuntu.com/questions/116662/shotwell-0-12-shared-library-error)

---

### Post by lemonbar on 2012-04-03
This happened to me as well, but I didn't get any kind of message.  It just ignored me completely - I was taking it personally until I saw this thread.  I'm running Ubuntu Studio 12.04.

---

### Post by Hakunka-Matata on 2012-04-04
me too.  12.04 amd64 
Two Identical machines, both stopped opening Shotwell, I've had several similar glitches with different apps, it gets fixed fast usually, I just live with it for a few days now.  12.04 is working very well for me.

of interest:  digikam is quite good too for me

---

### Post by eric-yorba on 2012-04-04
> **RJARRRPCGP said:**
> Clearly a broken package installation routine.

I can't see why you would get dependency-hell when installed from a repository. The facepalm of April 2, 2012. 

You shall never get an error about being unable to load a shared library when installed from a repository.

True, you shouldn't get an error when you install something from a repo.  But that's the risk you run with a beta version of an OS -- the guinea pig is you!

That said, we know about this issue and so does Canonical.  Expect a fix in the repo soon (if it's not there already.)

---

### Post by lemonbar on 2012-04-06
Thanks eric-yorba!

---

### Post by Hakunka-Matata on 2012-04-08
SOLVED, repository and updates fixed shotwell.  12.04 looking good

---

