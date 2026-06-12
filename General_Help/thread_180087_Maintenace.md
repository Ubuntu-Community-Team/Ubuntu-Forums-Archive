---
title: "Maintenace"
date: 2006-05-21
forum: General Help
---

### Post by bobby19 on 2006-05-21
What maintence is necessary to keep Ubuntu Linux 5.10 running fast, smooth, error free, and free of viruses or pests? Since I am new to Linux, I really don't know. Any help would be greatly appreciated. Thank you.

---

### Post by Fass on 2006-05-21
What do you mean by maintenance? There are only a few viruses for linux, and they're extremely rare, and the filesystem doesn't need to be defragmented... and there isn't a registry that gets bloated.... so, umm, I don't do anything particular myself. I just make sure to run all package removals with --purge.

---

### Post by glotz on 2006-05-21
I think this is a very good question and certainly it's all different to windows world. This is a really good FAQ question. This should be answered in offline version of Ubuntu users manual!

I'm rather new to Linux myself and i'm under the illusion that there really is *nothing* to do, besides maybe emptying synaptic pm cache every now and then if you experiment with lot of packages and if you need disk space and got a fast internet connection...

Looking forward to see some gurus answer this.

---

### Post by rich.bradshaw on 2006-05-21
I wrote a script that cleans up the apt caches a bit, it basically boils down to running these commands.

```

apt-get autoclean

apt-get clean

remove-orphans

apt-get remove --purge $(deborphan)

```

run the last one a couple of times, until there is nothing left to remove - it removes packages that nothing depends on; i.e. orphaned packages.

I never use synaptic or anything, but I think that there are commands in there that do the same things.

It is interesting to run ```
df -h
``` before and after doing this to see how much disk space you have freed up.

---

### Post by adamkane on 2006-05-21
If you are a new user, you want to install the correct kernel packages for your hardware (something that Ubuntu doesn't do automatically, but should).

Intel Pentium:
```

sudo apt-get install linux-686 linux-headers-686

``` 
AMD K Series (Duron, Athlon, Sempron):
```

sudo apt-get install linux-k7 linux-headers-k7

``` 
Reboot.

This is really all you need to do to keep your system responsive. Ubuntu doesn't seem to suffer from adware or cache overload.

---

### Post by bobby19 on 2006-05-21
so Linux Ubuntu doesn't need any defragmentaton? What about a linux version of scandisk to check and correct filesystem errors?

---

### Post by Koori23 on 2006-05-21
All of your program Temp files are located in /tmp. These should not be erased while logged in as they may be used by a program you have currently running. When you reboot, that /tmp folder is cleaned up anyway.

ext3 (The default format for Ubuntu) is a journaling filesystem, meaning, everything is written to the disk in continuous blocks, so defrag is unnecessary because data isn't reshuffled just because you installed something or erased something.

Over time though, if you've installed a bunch of packages from the Package Manager, these can take up a fair amount of space. To get rid of those old packages, type:

sudo rm -f /var/cache/apt/archives/*.deb

Be aware though, you must replicate that command exactly as I've written it, you don't want to add extra spaces or anything.

Firefox Cache can be cleared by choosing Edit->Preferences->Privacy and the  last option is to clear the cache. You can modify this setting as well.

Remember to empty the Waste basket regularly, just right click the icon and then "Empty Trash"

As far as harddisk errors and such, hdparm is probably what you would be looking for, it's a benchmark tool as well as an optimizer. **This however shouldn't be messed with for a while, as this is a super user tool and requires exclusive access to the disk, so the GUI can't be running.** The changes are permanent and can cause crashes due to it's exclusive access to the disk. So I'm just mentioning it for informational purposes.

By in large though, anything that would bog down your system is taken care of automatically by Linux on a regular basis.

---

