---
title: "Please suggest a bare-metal recovery software for ubuntu."
date: 2012-07-31
forum: General Help
---

### Post by arroy_0209 on 2012-07-31
I am a new ubuntu user and looking for a bare-metal recovery software to backup everything to avoid data loss and configuration loss in case of hard disk crash. Moreover I am not an expert in linux so some easy to use software will be more appropriate at this stage. If you know any suitable software or have experience of using such programs, please share. Thanks.

---

### Post by dino99 on 2012-07-31
Look at the ubuntu archive, all you need is already there: install and open synaptic

into a terminal:

sudo apt-get install synaptic
sudo apt-get install deja-dup

***
Déjà Dup is a simple backup tool. It hides the complexity of backing up the
Right Way (encrypted, off-site, and regular) and uses duplicity as the
backend.

Features:
 * Support for local, remote, or cloud backup locations, such as Amazon S3,
   Rackspace Cloud Files, and Ubuntu One
****

and choose hdd/ssd or usb stick for the backup hardware.
Note that the most secure is to have a dedicated /home partition for your data & settings.

here is how i do installation:
[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

):P

---

### Post by garyzw on 2012-07-31
Deja Dup will not do Bare Metal Backups

You need---

**Redo Backup and Recovery** is so simple that anyone can use it. It is the easiest, most complete disaster recovery solution available. It allows [bare-metal restore]("http://en.wikipedia.org/wiki/Bare_metal_restore"). **Bare metal restore**  means that even if your hard drive melts or gets completely erased by a  virus, you can have a completely-functional system back up and running  in as little as 10 minutes.

[http://redobackup.org/](http://redobackup.org/)

---

### Post by Cheesemill on 2012-07-31
I use Clonezilla to make a full image of my drive.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by HermanAB on 2012-07-31
Howdy,

Backup strategies on Linux and Windows are different.

Windows is expensive and remains static for many years on end, while Linux is Free and is constantly being improved.  Therefore, making a backup of Linux itself is rather pointless, since one day when your HDD fails, you would be better off to install the latest version of Linux, not a stale old, out of date, saved version.

Therefore, do as all the old hands do and only backup your data using something like DejaDup as suggested above.  This is easier, much faster and cheaper to do, than needlessly backing up the whole kit and kaboodle.

---

