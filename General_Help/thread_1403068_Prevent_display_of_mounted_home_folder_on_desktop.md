---
title: "Prevent display of mounted home folder on desktop"
date: 2010-02-09
forum: General Help
---

### Post by SG2010 on 2010-02-09
Hi All,

I recently changed linux distros and switched to Karmic. In my earlier setup /home was on a separate partition. After switching to karmic I added the following line to /etc/fstab to mount my /home partition which was on /dev/sda6 (ubuntu is on /dev/sda7)

/dev/sda6 /home ext3 nodev,nosuid 0 2

After rebooting I saw that while earlier I had an empty desktop now my desktop shows the content of my home folder.

On googling I found out about how I could change the nautilus preferences.

I used gconf-editor to change

apps>nautlius>preferences>desktop_is_home_dir to false

I also changed

apps>nautlius>desktop>volumes_visible to false.

However on rebooting I still see all the contents of my home folder on the desktop.

What do I need to do to show the Desktop as blank (as in point to ~/Desktop rather than point to ~)?

Thanks for the help,
SG2010

---

### Post by quixote on 2010-02-10
I have nothing to add except that I'd really like to know the answer to this too!

---

### Post by marshcast on 2011-02-16
I would too.... a year down the line...

---

