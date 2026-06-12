---
title: "Update Help!"
date: 2009-09-08
forum: General Help
---

### Post by kyle2595 on 2009-09-08
Hi, I was looking at the settings for the Update Manager, and it brought up Software Sources (which is normal).  I then clicked on the "Ubuntu Software" tab and there was a box that said "Installable from CD-ROM/DVD" and in the box there was this: I attached a picture of it. What is it? If I check the box next to it and install it, it won't let me.  Is it anything important? Thanks!

---

### Post by scragar on 2009-09-08
That is for installing software from the CDrom(which are included but not installed on most systems) or for updates(for example downloading the 9.04.1 disk to update a beta install of 9.04 which hasn't been updated for another reason). If you've got an internet connection the odds are that will be much more up to date, if not then the CDs may be your easiest method of updating software.

---

### Post by drs305 on 2009-09-08
To enable the CD option, you have to use whatever CD is listed in sources.list. Sometimes this is even the CD from your original install. If you originally installed Gutsy from CD, then did an online update to Hardy, you would still have to insert your Gutsy CD if you wanted to enable the option (which you obviously wouldn't in this case).

This is also the box, when ticked, will make Synaptic/APT ask you to insert your CD anytime you do an update. 

For those reasons, it is usually best to leave this unticked unless you have updated your sources.list to include a repository CD.

---

### Post by kyle2595 on 2009-09-08
OK, thanks! I was just curious.

---

