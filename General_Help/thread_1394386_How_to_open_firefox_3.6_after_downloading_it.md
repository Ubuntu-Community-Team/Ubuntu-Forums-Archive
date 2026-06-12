---
title: "How to open firefox 3.6 after downloading it ???"
date: 2010-01-30
forum: General Help
---

### Post by Mashvv on 2010-01-30
Hey guys i have downloaded firefox 3.6 and i dont know how to open it ?!

---

### Post by Alexandre Putt on 2010-01-30
What exactly did you download? Was it a .deb package?

You can (and should) install Firefox 3.6 from a package manager (Synaptic) or a command line. I.e.

[FONT="Courier New"]sudo apt-get install firefox[/FONT]

should do the job.

---

### Post by Silvertones on 2010-01-30
Is 3.6 available through synaptic? Doesn't appear it is.

---

### Post by wojox on 2010-01-30
```
tar xjf firefox-*.tar.bz2
```

---

### Post by Alexandre Putt on 2010-02-07
> **Silvertones said:**
> Is 3.6 available through synaptic? Doesn't appear it is.

Well, I have it as I am playing around with Lucid.

> **wojox said:**
> ```
tar xjf firefox-*.tar.bz2
```

This is not a recommended way of installing software. You can extract the files and simply run the executable (I believe firefox comes precompiled), but it is a lot better in the long run to use the package manager for Ubuntu (Synaptic), as it takes care of all updates and dependencies. If you don't want to wait till 3.6 is released in the main repositories, you may have a look at the thread [http://ubuntuforums.org/showthread.php?t=1347288](http://ubuntuforums.org/showthread.php?t=1347288)

---

### Post by malspa on 2010-02-07
> **wojox said:**
> ```
tar xjf firefox-*.tar.bz2
```

> **Alexandre Putt said:**
> This is not a recommended way of installing software.

It might not be "recommended" but it works just fine.

Obviously there's more than one approach that will work, but if you want to, you can basically follow the instructions at [http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux) in the "Installing outside of a package manager" section.  You don't necessarily have to follow the approach under "Installing Firefox on Ubuntu because the instructions for installing into your home directory will work fine unless you have multiple users.

---

### Post by Alexandre Putt on 2010-02-07
> **malspa said:**
> It might not be "recommended" but it works just fine.

Sure. The only problem is that firefox is released so frequently that it may be easier to use a manager for updating it.

---

### Post by malspa on 2010-02-07
> **Alexandre Putt said:**
> Sure. The only problem is that firefox is released so frequently that it may be easier to use a manager for updating it.

Might be.  But you can keep a more up-to-date Firefox on your system this way.  It's really no big deal because the updates come from Mozilla, Firefox lets you know there's an update available, you click to update it, Firefox restarts, you're done.

---

