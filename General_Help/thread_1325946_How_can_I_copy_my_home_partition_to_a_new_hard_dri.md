---
title: "How can I copy my /home partition to a new hard drive?"
date: 2009-11-13
forum: General Help
---

### Post by 3pinner on 2009-11-13
I am going to do a fresh install on a new hard drive.
I would like to copy my /home partition to the new drive to keep all my current settings and accounts.
So what is the best way to do this?

Also,
Is there any value in creating a new /home partition and starting over?
Cleaner system that way??
Thanks!

---

### Post by fluffman86 on 2009-11-13
First, boot from a live CD.

Press Alt + F2, then type "gksu nautilus"

Use the left panel to select the hard drive with Ubuntu installed on it, and navigate to your home directory.

Press CTRL + H to view all of your hidden files.  I like getting all of the nice new settings with the new distro, so I usually only select (ctrl + click) Documents, Music, etc, and .gnupg, .ssh, and .mozilla.  You may have other stuff to grab as well.  Or, you can just get everything with CTRL + A, and copy with CTRL + C.

Now, in the same window, navigate to your external HDD or wherever you want to save stuff, and ctrl + V to paste.

Wait til the copying is finished, and make sure you have everything, then you can go on with your install.

---

### Post by 3pinner on 2009-11-14
Thank you.
Next question:
What files do I need to copy to retain my desktop and other settings?

I've tweaked my appearance to exactly what I want, and would like to keep those settings as well.
I assume I will also need to copy over any third party applications I have installed - such as Opera, a photo editing program etc??

thanks again!

---

### Post by 3pinner on 2009-11-14
any ideas?

---

### Post by Zoot7 on 2009-11-14
It's best to copy the whole partition to the new drive using Gparted. Or if you want to set it up afterwards (I rather this myself) with a separate home partition, it's just a case of copying everything to the new partition and specifying where to mount it in fstab. Here is a good guide:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

