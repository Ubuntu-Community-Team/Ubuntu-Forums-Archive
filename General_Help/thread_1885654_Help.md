---
title: "Help"
date: 2011-11-23
forum: General Help
---

### Post by Lab72 on 2011-11-23
Hi all just downloaded 64 bit version of Ubuntu and was hopping it would get rid of Windows xp but its still there ?? I have seen Ubunto setup and and takes over and gets rid of windows , can any one help please :D

---

### Post by hwttdz on 2011-11-23
So what you are trying to do it to remove windows from your computer and install windows?  Do you want to keep your data?  I'd recommend as a first step first backing everything up to external media (cd/dvd/external disk formatted as fat32/ntfs).

---

### Post by Lab72 on 2011-11-23
Data all backed up and yes want to remove windows completely :D

---

### Post by hwttdz on 2011-11-23
First a recommendation which will hopefully make your life easier in the long run, use a separate partition for "/" and "/home", so at some point during install you should see at least 3 partitions:
1) "/"
2) "swap"
3) "/home"

So, just put the cd in, make sure your bios is set to boot from the cd and then restart.  You'll be greeted by the installation process which should walk you through it (I haven't used the standard install in years, so I'm not actually terribly familiar with it).  You'll be reformatting your entire drive(s) (again this will erase all your data, nothing that you have on there now will be recoverable).  When you're done with the install it will tell you to remove the cd and restart.  When the computer turns back on you'll be greeted by a ubuntu desktop.  

There is lots of info about installing: [https://help.ubuntu.com/community/Installation#Standard_installation](https://help.ubuntu.com/community/Installation#Standard_installation)
And booting from a live cd: [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
And probably reformatting and whatnot floating around in the ubuntu wikis.

---

