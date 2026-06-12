---
title: "update-manager does not install updates"
date: 2009-11-24
forum: General Help
---

### Post by kaurman on 2009-11-24
Hi,

I have been using ubuntu 8.04 for a long time without any remarkable problems. Now it seems that I have managed to mess something up.

Namely, some time ago I was thinking of upgrading to 8.10. I did not do so eventually as I thought I'm happy enough with hardy. To tell the truth, I didn't even start to download the new packages. Still, although I canceled the upgrade before anything was really upgraded, I missed an important point... In other words, my sources file had already been altered. I did not consider this an issue though, as I was able to restore hardy's sources.lst from the live cd.

Well, there I was, happy with my good old hardy. Yet, I was jumping the gun with celebrations. It turns out that gnome-update manager has somehow broken down. It notifies me, it even seems to download the updates, but it does not install them. Every time I want it to do so, all I get is the 'building dependency tree' window which disappears after the building process is complete, leaving me with a gnome-update window which is still full of possible updates.

**To put it in a nutshell, no installation is attempted.**

Some facts worth mentioning are:

1) I can upgrade from the terminal without any problems or complaints.
2) Upgrading through synaptic isn't possible. **Synaptic seems to think that there are no packages that can be upgraded.** 

Any suggestions?

Thanks in Advance,

K

---

### Post by Julita on 2009-11-24
Try cleaning package cache:
sudo apt-get clean
sudo apt-get autoclean

---

### Post by kaurman on 2009-11-24
> **Julita said:**
> Try cleaning package cache:
sudo apt-get clean
sudo apt-get autoclean

Hi,

thanks for your reply. The commands didn't help though. After all, all they do, is delete the files downloaded by the update-manager. 

PS AFAIK, if one has already ran sudo apt-get clean, there is no point in running apt-get autoclean as apt-get clean deletes everything autoclean could possibly delete. 

The difference between those two commands should be, that autoclean only deletes older files.

Still, thanks for your help, as it uncovered some new aspects. After deleting the packages the updates must be downloaded again as we know. Well, it turns out that now update-manager is not able to do so. All I get is the dependency tree thing which I mentioned in my previous post.

In other words: it seems that update-manager is able to download the updates automatically but refuses to download them when I want it to do so.

It seems odd though... I'm not 100% sure that it really downloaded the updates when it acted on its own but I'm still fairly sure it did since before I cleaned the cache it said that the size of updates which had to be downloaded was 0. 


K

---

