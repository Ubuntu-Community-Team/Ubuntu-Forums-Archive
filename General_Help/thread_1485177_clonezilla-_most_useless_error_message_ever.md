---
title: "clonezilla- most useless error message *ever*"
date: 2010-05-16
forum: General Help
---

### Post by josephellengar on 2010-05-16
I have been using clonezilla for two years now to back up my computer about once a month.  I recently bought a netbook (Asus eee 1005ha-p) and it currently has 9.10 on it.  I set up a flash drive with the stable version of clonezilla for 32 bit processors (as my netbook doesn't have a disk drive) and tried to back up the hard drive (160 gb- about 10 gb full) to my Toshiba external hard drive (250 gb- 10 gb full).  I have run this probably 6 times now and every single time after 15/20 minutes of telling me that it is backing up it gives the error message "something went wrong."  Well, that's useful. ](*,)  I then check the external hard drive and the image size is only about 50mb or so.  I have tried many different types of compression.  I have a feeling that it has something to do with the netbook being unable to handle something that is going on, but I have never used Clonezilla with a live usb before (and don't have an external cd drive) so I can't be sure.  Does anybody have a suggestion?  Thank you.

---

### Post by WorMzy on 2010-05-16
I've never used any cloning software before, but are you running the command/gui as root? If you're not then the application may not be able to read the contents of some folders due to insufficient privileges. If you've been using this software for a while on Ubuntu, and never had any problems before, I suggest checking the developer's website to see if there's any known problems with Lucid.

---

### Post by josephellengar on 2010-05-16
> **WorMzy said:**
> I've never used any cloning software before, but are you running the command/gui as root? If you're not then the application may not be able to read the contents of some folders due to insufficient privileges. If you've been using this software for a while on Ubuntu, and never had any problems before, I suggest checking the developer's website to see if there's any known problems with Lucid.

The cloning software does not run within the operating system.  It runs as a live cd off of its own kernel.  Also, neither of my computers are on lucid.  Both are still on karmic and the desktop replacement works but the netbook doesn't.  Thanks for the suggestions though.

---

