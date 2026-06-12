---
title: "Could I copy my exact system over with this method?.."
date: 2009-08-08
forum: General Help
---

### Post by Whiteblooded on 2009-08-08
Hey, I've been backing up my system using the technique found at: HTML]http://ubuntuforums.org/showthread.php?t=35087&page=95[/HTML] to backup and restore my system.

I was just wondering... This hard drive is kind of small, and I'd really like to switch to a larger one.

I'd like to know whether it would work if I:
-1) Installed Ubuntu on the larger hard drive (using the same computer name and user name as this one)
-2) Used the restore method, restoring this harddrive to that one (extracting a .tar.bz2 and overwriting all folders but the /sys /proc /media /lost+found and /mnt folders on the new harddrive with the old one's)   ... sorry. I've been up all night, I really don't know how I can word that better.

Would this method allow me to keep all of the codecs/drivers etc that I have on this setup? Would there be any files I'd need to change to get this to work? What, if anything would be lost?

I guess I could always try. I've got nothing to lose I suppose, I'm just kind of busy at the moment and thought I'd check here before I tried.

Thanks in advance :)
(if you hadn't noticed, i'm a bit  of a newb)

---

### Post by frt975 on 2009-08-08
I think so but why not just do a clean install?

---

### Post by frt975 on 2009-08-08
Wait untill this gets answered: [http://ubuntuforums.org/showthread.php?t=1235081](http://ubuntuforums.org/showthread.php?t=1235081)

---

### Post by Whiteblooded on 2009-08-08
Hmm. I don't really want to do a clean install. It's new enough as it is, and I can't really be bothered to set a lot of stuff up again,  and install all the codecs/drivers again >_< (as I said, I'm a noob and at the moment and it seems like a big job to do all that again xD)

I don't really see how that other thread relates to this problem. Are you suggesting I could get a similar error if I make my ubuntu think it's on a different sized harddrive than it is?

---

### Post by louieb on 2009-08-08
Heliodes guide  would work. But easier to just install both drives in the same PC or hook one with a USB enclosure. Then use the copy and paste function of Gparted (run it from a live CD) can copy and resize at the same time.  Worked great for me.  [GPARTED DOCUMENTATION - COPYING]("http://gparted.sourceforge.net/larry/move/move.htm")

Then when done copying use the same CD to put GRUB on the MBR of the new drive. [Fix Grub after Win install - catlett]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")  (same fix will work for you)

---

