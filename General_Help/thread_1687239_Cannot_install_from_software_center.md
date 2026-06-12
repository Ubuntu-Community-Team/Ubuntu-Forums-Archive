---
title: "Cannot install from software center"
date: 2011-02-13
forum: General Help
---

### Post by Cloudkookoo on 2011-02-13
So apparently I've got a broken dependency and Ubuntu can't handle it itself. This is the error message I get when it fails to repair.

Unpacking dockmanager (from .../dockmanager_0.1.0~bzr83-0ubuntu1~10.10~dockers1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/dockmanager_0.1.0~bzr83-0ubuntu1~10.10~dockers1_i386.deb (--unpack):
 trying to overwrite '/usr/share/dockmanager/data/skype_dnd.svg', which is also in package faenza-icon-theme 0.8
Errors were encountered while processing:
 /var/cache/apt/archives/dockmanager_0.1.0~bzr83-0ubuntu1~10.10~dockers1_i386.deb
dpkg: dependency problems prevent configuration of dockmanager-daemon:
 dockmanager-daemon depends on dockmanager (= 0.1.0~bzr83-0ubuntu1~10.10~dockers1); however:
  Package dockmanager is not installed.
dpkg: error processing dockmanager-daemon (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dockmanager-daemon

How can I go about fixing this? I can't use the software center until the error is cleared.... :[

---

### Post by Cloudkookoo on 2011-02-13
Bump, because it's kind of important.

---

### Post by sikander3786 on 2011-02-13
> **Cloudkookoo said:**
> Bump, because it's kind of important.
From Applications > Accesssories > Terminal, please run and post the output of these commands.

```
sudo apt-get update
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags for readability purposes.

---

### Post by uRock on 2011-02-13
> **Cloudkookoo said:**
> Bump, because it's kind of important.

Everyone's problems are important. Please do not bump for at least 24 hours.

Thanks,
uRock

---

### Post by corncob on 2011-02-13
If you can (I know its just the other side of the Software Center Coin) go to System > Administration > Synaptic Package Manager.  Open the Edit menu and click "Fix Broken Packages".  With any luck at all,  "Successfully fixed dependency problems" will appear on the information bar at the bottom of the window.

---

### Post by jonbwilson on 2011-05-06
I'm actually having this exact same error.  I can't install or remove anything.

I've tried fixing broken packages from synaptic package manager and I get the same error.  I've tried manually deleting all of the Faenza icon folders.  I've tried apt-get -f install.  Nothing works.

Any ideas?  I'm kind of stuck until I can figure this out.

---

### Post by jonbwilson on 2011-05-06
> **jonbwilson said:**
> I'm actually having this exact same error.  I can't install or remove anything.

I've tried fixing broken packages from synaptic package manager and I get the same error.  I've tried manually deleting all of the Faenza icon folders.  I've tried apt-get -f install.  Nothing works.

Any ideas?  I'm kind of stuck until I can figure this out.

Nevermind, I fixed it.

Anybody else out there having this problem, check out this article from WebUpd8.  Works like a charm.

[http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html](http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html)

---

