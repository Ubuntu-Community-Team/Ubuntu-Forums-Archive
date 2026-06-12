---
title: "Need Grub 2 help"
date: 2009-10-31
forum: General Help
---

### Post by resination on 2009-10-31
I'm trying to set up the grub menu to look like I used to have it.  I've found:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=login+screen](http://ubuntuforums.org/showthread.php?t=1195275&highlight=login+screen)

[LEFT]but I still can't figure out what I need to do.  It was so simple before to edit the menu.lst file.  I could rearrange/rename/remove entries easily.   Now it seems to be 10 times more complicated to do the very same thing.  Anyone know of an easier way to rearrange/rename/remove grub entries?
[/LEFT]

---

### Post by QIII on 2009-10-31
It is just as simple, it is just different.   But  you may be a bit more limited in how easily it is to "rearrange" things.

Your primary config file, /boot/grub/grub.cfg, is not meant to be edited by hand.  I'm not sure you even could with sudo.

Getting Windows or other Linux OSs to run is as simple as

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```For some other OSs, it's still fairly simple. You need to modify /etc/grub.d/40_custom as needed.

For instance, to add my OpenSolaris, I added (after the "exec tail" entry and the commented lines around it)

```
menuentry "OpenSolaris" {
        set root=(hd1,2)
        chainloader +1
}
```Then ran

```
sudo update-grub2
```

---

### Post by ikacer on 2009-10-31
I found this thread which might be helpful:

[http://ubuntuforums.org/showthread.php?t=1278577]("http://ubuntuforums.org/showthread.php?t=1278577")

---

### Post by resination on 2009-10-31
[LEFT]Thanks for the links.  I'm giving up on rearranging the order.  I can live with the default, and isn't worth much effort to fix.  I was able to remove the memtest entry, but not the recovery mode entry.  I'll keep working on that.

But I still haven't figured out how to rename the entries. Grub found everything, but I don't like the names.  For example, the recovery partition for my laptop is titled "Windows NT/2000/XP" in grub.  I'd simply like to rename it "Recovery Partition."   The Windows 7 partition is titled "Windows 7 (loader)" and I'd like to get rid of the "(loader)"

Is this even possible without directly editing the grub.cfg file?  The only way I can see to do it is to remove the 30_os-prober file, and add the 2 "windows" entries into the 40_custom file.

It seems overly complicated compared to how it used to work.


[/LEFT]

---

### Post by QIII on 2009-10-31
You get to "recovery" by selecting the "single user" mode, as I recall.

---

### Post by resination on 2009-10-31
[LEFT]Aha!  I found the right thread.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[/LEFT]

---

