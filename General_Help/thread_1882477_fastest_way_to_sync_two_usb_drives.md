---
title: "fastest way to sync two usb drives"
date: 2011-11-17
forum: General Help
---

### Post by rmcellig on 2011-11-17
I have two external USB HD's. Hard drive one (radio1) is a 320GB USB drive. Hard drive two (radio2) in also an external 1TB USB drive. The 1TB drive is broken down into three partitions (not sure if that is a factor or not). 

I want to sync radio1 to radio2 so that radio2 is always an exact copy of radio1. What is the fastest way for me to do this? rsync, unison? I'm a bit confused as to which one will sync the fastest and is drop down simple to use.

The other thing is that if I use rsync with some of the options available, does it slow down the sync process.

Thanks as always for all the help!!

---

### Post by BillyBoa on 2011-11-17
The trough is that synchronizing works easier in Windows and especially in Win 7 with SyncToy.

I tried the SynchroRep on Ubuntu

[http://www.webupd8.org/2009/06/easy-folder-synchronization-for-linux.html](http://www.webupd8.org/2009/06/easy-folder-synchronization-for-linux.html)

but it's not the same.

---

### Post by Lars Noodén on 2011-11-17
Use rsync for that.  

```

rsync -aH /path/to/source/ /path/to/destination/

```

There is a graphical front-end, called [grsync](http://www.opbyte.it/grsync/), if you want one.

---

