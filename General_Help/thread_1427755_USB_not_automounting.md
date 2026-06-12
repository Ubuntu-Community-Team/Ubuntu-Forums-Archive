---
title: "USB not automounting"
date: 2010-03-11
forum: General Help
---

### Post by ffxigotenks on 2010-03-11
I have several flash drives that I use on a regular basis and they work fine on other systems, but on mine they won't automount all the time, I remember that there was a file that I could edit/remove to have it "forget" what drives have been connected so it will reset to the default behaviors.  I've been trying to remember what I typed in to find it before, and after two days, I'm still not able to find it I apologize for asking obvious questions, but I hate not being able to solve problems I've fixed before even more. I'm almost positive it started with "gvfs" but don't remember the rest.

---

### Post by zeroseven0183 on 2010-03-11
Hi! I was looking for ways to solve this and found a page that talks about gnome-disk-utility. Downgrade the three packages mentioned below:

> 
b) Search for **gnome-disk-ulility**, **libgdu-gtk0** and **libgdu0**  in Synaptic (search for them in this exact order), select each and then  under the *Package* menu, select "Force version" and then select  the version from Karmic (you can also remove udisks if you want: sudo  apt-get remove udisks). Then if you want to keep using the WebUpd8 PPA,  select "Lock version" (which is also under the "Package" menu) for each  of these 3 packages. If you're not interested in keep using the WebUpd8  PPA, simply remove the WebUpd8 PPA from *System > Administration  > Software Sources*.


Source: [http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html](http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html)

---

### Post by ffxigotenks on 2010-03-12
> **zeroseven0183 said:**
> Hi! I was looking for ways to solve this and found a page that talks about gnome-disk-utility. Downgrade the three packages mentioned below:



Source: [http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html](http://www.webupd8.org/2010/02/install-gnome-disk-utility-palimpsest.html)

ok, sounds good except for one thing... "downgrade" to karmic? I'm using jaunty, so do I downgrade to intrepid or upgrade to karmic? also, I'm not finding them in the jaunty repos

---

### Post by ffxigotenks on 2010-03-12
naturally, after I've started this thread it all comes back to me and I feel like an idiot, I just had to kill gvfs-gphoto2-volume-monitor and chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor and all is well, here's the bug report that I found to help me

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/363101](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/363101)

---

