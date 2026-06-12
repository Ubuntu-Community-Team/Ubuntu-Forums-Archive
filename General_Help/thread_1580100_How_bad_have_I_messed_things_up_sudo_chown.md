---
title: "How bad have I messed things up? sudo chown /*"
date: 2010-09-22
forum: General Help
---

### Post by storanta on 2010-09-22
I've done a really really bad thing. :-(

I was working on a shell script to automate the setup of websites on a server and part of the script resets the file ownerships to be that of the site account holder.

Unfortunately I had a typo in the script which reset the owner on my entire filesystem.  Effectively I did an: 
sudo chown -R storanta:storanta /*

I've managed to get things booting by going into failsafe mode and resetting the ownership to root on all of the root level folders and then resetting the ownership of the /var/lib/gdm folder to the gdm user.

How badly have I messed things up? 

Should I just backup all of my files/data and do a reinstall?

Thanks!

---

### Post by john newbuntu on 2010-09-23
Oops. Unfortunately, I do not know of a tool that can re-instate permissions on all files/dirs, although there may be one available.  One way of looking at it is "as long as it works, it works.  If something breaks we'll fix it".  Another way is to re-install and add your data.  Yet another way is to look at a second standard install and adjust file permissions accordingly(possibly via a script).

Once again for the zillionth time can't stress on creating an image of your install after you have a nicely working rig plus backups.

---

