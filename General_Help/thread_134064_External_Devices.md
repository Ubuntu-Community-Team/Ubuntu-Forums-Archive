---
title: "External Devices"
date: 2006-02-21
forum: General Help
---

### Post by noeluylee on 2006-02-21
Hi! I am having problem with my external hard disk and external dvd writer. I was using these devices for months with no problem. but suddenly, my external dvd writer (HP dvd640) stop working, when I plug it in to firewire and/or usb, the icon does not show up. as far as my external hard drive, sometimes it shows up, sometimes dont. 

hope anybody could give me suggestion on how to go with this problem.

Thanks a lot.

---

### Post by GoldBuggie on 2006-02-21
do a ```
sudo adduser hal disk
```(reboot afterwards) then everything will show in media:/ and you can configure what to show on the desktop via *right-click on desktop->behavior->device icons*

---

### Post by testube_babies on 2006-04-04
I have that same dvd-burner, with similar problems (although my external hard drives work fine).  It seems Ubuntu kills that drive.  I am being totally serious.  My dvd640 stopped turning on a few months ago, so I sent it back to HP and got new one.  When I turned on my computer (and booted into Ubuntu), the new drive died.  It was fine in Windows.  So, I'm getting rid of the drive and buying a new one.  Any recommendations?

PS (Shameless plug): If you want to buy an HP dvd640e (one that works), check out [this eBay listing]("http://cgi.ebay.com/HP-DVD640-External-DVD-CD-Burner-Lightscribe-Discs_W0QQitemZ8791457740QQcategoryZ116244QQssPageNameZWDVWQQrdZ1QQcmdZViewItem").

---

