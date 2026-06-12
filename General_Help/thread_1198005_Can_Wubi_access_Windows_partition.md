---
title: "Can Wubi access Windows partition?"
date: 2009-06-26
forum: General Help
---

### Post by Ryupower on 2009-06-26
heya all,
I installed Wubi, since I didn't want to get into all the partitioning mess again, and the potential problems I could have with booting windows, etc...

So far I like it, but I'd like to know if there's some way to mount the windows partition it runs on so I can access my files on it. Is it possible?

kthx
-R

---

### Post by Steelmourne on 2009-06-26
Usually you open up your home folder and on the left should be an icon for your windows partition, assuming NTFS tools are already installed. It should also be listed under the places menu. Identify it by its hard disk size.Hopefully, you defragmented the disc before installing WUBI otherwise the performance may lessen.

---

### Post by nmaster on 2009-06-27
in root, you can go to the host directory.

---

### Post by Ryupower on 2009-06-27
There is no icon on the left for windows, the root home dir doesn't have anything but 'desktop'. I looked if there was anything under /mnt, there was nothing. Under /media I have the two CDrom drives, the floppy, just not the windows partition. HELP!

---

### Post by bodhi.zazen on 2009-06-27
According to this :

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

your windows drive is under /host

---

### Post by nmaster on 2009-06-27
> **bodhi.zazen said:**
> According to this :

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

your windows drive is under /host

this is what i had posted earler, so obviously i agree.  open the terminal and enter "cd /host". enter "ls" to list all the files.

if you prefer gui: Places->Computer->Filesystem->host

when in doubt, read about it!  this is definitely on the wubi faq page ([http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php))

---

### Post by nmaster on 2009-06-27
> **Ryupower said:**
> There is no icon on the left for windows, the root home dir doesn't have anything but 'desktop'. I looked if there was anything under /mnt, there was nothing. Under /media I have the two CDrom drives, the floppy, just not the windows partition. HELP!

why don't you read the replies?  i told you exactly where to look more that half an hour before you posted this.  you really need to take some initiative to help yourself.  we already told you the answer that you could have found for yourself online with 30 seconds of google searching.  the rest is up to you.

ADDITION:
okay, sorry if that sounded harsh, this is meant to be a friendly place for all.  this is a place for people to learn.  wubi doesn't actually make a new parition.  it makes a virtual drive on in your C: drive. there is plenty of info on this forum and else where.  just use google and go for it.  reading will be your best friend if you've never used ubuntu before.

---

### Post by bodhi.zazen on 2009-06-27
> **neal.m.master said:**
> why don't you read the replies?  i told you exactly where to look more that half an hour before you posted this.  you really need to take some initiative to help yourself.  we already told you the answer that you could have found for yourself online with 30 seconds of google searching.  the rest is up to you.

:lolflag:

Perhaps your first post was not clear enough ? Your second post, while it contains the same information, is better presented.

---

### Post by nmaster on 2009-06-27
> **bodhi.zazen said:**
> :lolflag:

Perhaps your first post was not clear enough ? Your second post, while it contains the same information, is better presented.

ill keep that in mind.  but still, this info was clearly available from wubi-installer.org.

---

### Post by Ryupower on 2009-06-27
Oh I see!
You meant a host directory like /mnt and all. Not a host directory INSIDE the root folder. I never realized that directory is there, must be Wubi-only.
So yes, I found it. Thank you very much, and sorry for being an idiot. :)

---

### Post by #11u-max on 2009-08-02
wait...... if wubi doesn't make an additional partition, why do i have 3 partitions?

---

### Post by benditoelqueviene on 2009-10-16
Thanks a lot!  I was trying to create a new partition, install new aplications...  And it was so simple: Windows was in /host.  Now i created a link to My Documents very easily.

---

### Post by andor1970 on 2009-10-16
I have also installed (K)Ubuntu by means of Wubi. I use the KDE desktop.  It is installed on partition D. I can see my windows folders of parition D in /host but I am not able to see the windows folders of partition C. In the link posted here it said that they could be found in /places/removable media, but I can't find such folder.

---

