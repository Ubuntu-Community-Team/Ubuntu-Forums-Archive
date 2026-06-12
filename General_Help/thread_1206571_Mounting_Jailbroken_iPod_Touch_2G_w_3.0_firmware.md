---
title: "Mounting Jailbroken iPod Touch 2G w/ 3.0 firmware"
date: 2009-07-07
forum: General Help
---

### Post by egernant on 2009-07-07
is this possible? I have been reading ways to make gtkpod work similarly to itunes, but either I am a complete noob (which is true) or my ipod doesn't seem to work with the apps I'm using.  I Jailbroke the ipod with the 3.0 upgrade in Windows and it is working great.  I have no experience with using the jailbreak features and very little knowledge of Linux.  This is the tutorial I am using now:

[http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/07/how-to-use-gtkpod-to-manage-your-ipod-in-ubuntu/)

I get the program installed and open it, then hit Load iPod(s) and nothing happens.  Can anyone tell me how to make my iPod Touch work with Linux (Ubuntu 9.04)?

---

### Post by milesje on 2009-08-07
Apple changed the database & hash with the 3.0 firmware and it has not be cracked yet. so as of right now you can not use gtkpod to sync with an iPhone or iPod Touch with out iTunes, if you are using the built in media player. 
Now if you want to use dTunes (downloadable from cydia) you can ssh into your iPod Touch (user:root password:alpine)and then place your music into the correct folder (not sure what folder that is) and then use dTunes to view your music and movies.

---

### Post by dsm iv tr on 2009-08-18
Because nobody has figured out the 3.0 database hash yet, there are still only two options to sync the iPod Touch in Ubuntu.

1: Downgrade your device to firmware 2.2.1, jailbreak it + install SSH, then sync with gtkpod mounted with SSHfs over wifi. You may also sync without jailbreaking (after downgrading!) using iFuse and your USB cable.

2: Keep firmware 3.0, run iTunes inside of a Windows install in VirtualBox, and share your media with the VirtualBox install by way of a "Shared Folder".

Personally, I am running 2.2.1 and syncing with GTKpod over wifi. I will likely upgrade to firmware 3.1 when it's release later this month (or possibly September?) to fix the issues with wifi signal I had when I upgraded to 3.0, then use iTunes + VirtualBox.

Good luck!

---

