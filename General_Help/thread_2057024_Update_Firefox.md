---
title: "Update Firefox"
date: 2012-09-12
forum: General Help
---

### Post by mayagrafix on 2012-09-12
I just installed Ubuntu 12.04 to a laptop and it came with Firefox 11. Will this version update by itself to FF v15 or do I have to manually initiate the upgrade?

Thanks for any and all help:KS

---

### Post by cg40k on 2012-09-12
I believe (I could be wrong) that Firefox is getting updated in Ubuntu 12.10 to FFv15

---

### Post by newb85 on 2012-09-12
Typically, Ubuntu doesn't automatically do version upgrades like this.  For the most part, the automatic updates that come through the main repos are bug fixes and security updates.

---

### Post by Frogs Hair on 2012-09-12
If you just installed run the update manager and it should be updated along with a lot of other packages.

---

### Post by snowpine on 2012-09-12
Currently 15.0.1 according to: [http://packages.ubuntu.com/precise/firefox](http://packages.ubuntu.com/precise/firefox)

---

### Post by mayagrafix on 2012-09-12
I left the laptop running 5 hours and still FF v11, no auto update

---

### Post by newb85 on 2012-09-13
> **mayagrafix said:**
> I left the laptop running 5 hours and still FF v11, no auto update

These updates aren't instantaneous.  If you open Update Manager (open the dash, start typing *Update Manager*...), hit *Settings* and go to the *Updates* tab, you can see how often your system is set to automatically check for updates, and what it's set to do when they're available.  If you don't want to wait for the automatic settings to kick in, you can make it happen now.

In Update Manager, hit *Check* to have it check for updates, and once it's done, hit *Install Updates* to have it install the updates.

If you want, you could also do this from the terminal.

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

(The first line is like hitting *Check*, and the second is like hitting *Install Updates*.)

---

### Post by snowpine on 2012-09-13
Alternately if you are primarily interested only in Firefox:

```
sudo apt-get update
apt-cache policy firefox
sudo apt-get install firefox
```

"installing" an already installed application will actually update it to the newest version.

---

### Post by Frogs Hair on 2012-09-13
I left the laptop running 5 hours and still FF v11, no auto update. With a new installation this far away from the release date you should have well over 100 updates easily. To set update preferences open the update manager and select settings.

---

