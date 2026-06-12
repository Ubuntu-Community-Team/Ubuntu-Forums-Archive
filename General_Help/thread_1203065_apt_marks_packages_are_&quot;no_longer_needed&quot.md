---
title: "apt marks packages are &quot;no longer needed&quot; when they are!!"
date: 2009-07-02
forum: General Help
---

### Post by gamblor01 on 2009-07-02
I keep getting this message whenever I install something with apt-get:

```

The following packages were automatically installed and are no longer required:
  sametime-connect ibm-lotus-cae ibm-lotus-activities ibm-lotus-notes
  ibm-lotus-notes-fixes libeel2-data ttf-xfree86-nonfree ibm-lotus-notes-8.5
  t1-xfree86-nonfree libeel2-2 ibm-lotus-notes-compat

```The problem is, this message is nonsense.  I absolutely need Lotus Notes and Sametime.  In fact, I had this problem yesterday when I quickly installed Apache and then removed it.  Unfortunately, I didn't read things very carefully when I typed "sudo apt-get autoremove apache2" and just typed 'Y' and pressed enter.  It uninstalled everything related to IBM on my laptop, which is a problem since this is my work laptop and Notes and Sametime are how I communicate with everyone at work.

I wanted to upgrade from Hardy anyway, so instead of just reinstalling the .deb packages from /var/cache/apt/archives,    I spent all day today at work reinstalling everything.  Now that I am running Jaunty and have everything reinstalled and configured the way I want it to, apt is again telling me these packages are not necessary (probably because I removed Lotus Symphony?).

Is there a way I can override what apt is telling me here?  I would like to mark the packages above as necessary so that apt doesn't remove them if I happen to remove another package with autoremove.

---

### Post by linuxmagick on 2009-07-02
You could try doing ```
sudo aptitude keep-all
```
You can read more about it by looking at the man page for aptitude ```
man aptitude
```.

Those packages apt wants to remove were probably dependencies of another app that you removed.  If it were me, I would ```
sudo apt-get autoremove
``` to remove them and then try installing only the applications that I want again.  However, the first command I gave, should tell apt to un-mark those packages for removal.  Haven't used it myself, though, so no promises.

---

### Post by CatKiller on 2009-07-02
> **gamblor01 said:**
> Is there a way I can override what apt is telling me here?  I would like to mark the packages above as necessary so that apt doesn't remove them if I happen to remove another package with autoremove.

Go into Synaptic. Find the packages that you want to keep. Deselect the Package -> Automatically installed option.

---

### Post by gamblor01 on 2009-07-03
sudo aptitude keep-all works perfectly.  Thanks!

---

