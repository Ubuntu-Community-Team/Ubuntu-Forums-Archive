---
title: "Moving files to a pendrive renders 0 bytes files and files gets deleted"
date: 2011-06-10
forum: General Help
---

### Post by GTMoraes on 2011-06-10
That's the second time this crap comes to happen with me. Damnit.

I get a SD card. Put in the SD reader. It's empty. I go to my super-important-pictures-to-a-monthly-relatory folder and select all files. Select them for MOVE. Paste them on the SD card. When the move/paste process is finished, i click on the "Eject" button on top of the SD card name. Card's ejected. I can't access the card anymore. I take out the card and put on my other computer. From 300 pictures, there are only 10 available, the remaining ones are there, but with 0bytes and unrecoveable. I panic. I go back to my main computer, my pictures are not there anymore. The pictures were on the Home folder. I panic again. I reset the computer and boot on the LiveCD. I install foremost, scalpel, photorec and about everything till my USB drive complains about being filled up. I run everything and I can't recover my files. I'm in the danger of getting fired.

Things like that makes Windows sounds more appealing. When you securely remove a pendrive, things get REALLY pasted there before screwing everything up with a removal.

---

### Post by GTMoraes on 2011-06-11
Just an quick update - I've got an warning and got to work this weekend to recover the pictures by taking them all again. I've took pictures across 4 states.

I'm setting up my things and checking up my car for a long, long trip.
Wish the Ubuntu dev's the best.
Also an way to ONLY eject a removeable drive when EVERYTHING were copied.

See ya

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **GTMoraes said:**
> Just an quick update - I've got an warning and got to work this weekend to recover the pictures by taking them all again. I've took pictures across 4 states.

I'm setting up my things and checking up my car for a long, long trip.
Wish the Ubuntu dev's the best.
Also an way to ONLY eject a removeable drive when EVERYTHING were copied.

See ya

What I would do if there isn't a fix in Ubuntu is install Windows in VMWare like this, and use an USB reader device for that SD in VMware..
after you have transfered your photos into your emulated win on VMWare, you can set up a shared folder between VMware, and Ubuntu to 
migrate that data around.

Here is how you can get VMWare installed:

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

Make sure you have the additional package from VMWare for Windows USB installed. 

Then you will need to find a USB reader for your SDCard.  Like a 6-in-1 USB reader or whatever from the electronics store. Plug it in
when you have your VMware all installed with win and booted.

If it is really that important, this should work.

---

### Post by GTMoraes on 2011-06-11
> **linuxinstalledfromhdd said:**
> What I would do if there isn't a fix in Ubuntu is install Windows in VMWare like this, and use an USB reader device for that SD in VMware..
after you have transfered your photos into your emulated win on VMWare, you can set up a shared folder between VMware, and Ubuntu to 
migrate that data around.

Here is how you can get VMWare installed:

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

Make sure you have the additional package from VMWare for Windows USB installed. 

Then you will need to find a USB reader for your SDCard.  Like a 6-in-1 USB reader or whatever from the electronics store. Plug it in
when you have your VMware all installed with win and booted.

If it is really that important, this should work.
Yup. I did it, but with VirtualBox.
Nonetheless, I wish to be windoze free. sigh.

---

### Post by linuxinstalledfromhdd on 2011-06-11
users have reported issues with the USB in virtualbox with what you are doing.

try VMware, windows, and good 6-in-1 usb reader device hooked to the VMWare booted win.

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

you will never know unless you try  :)

VMware may look like Virtuabox but they are not the same. :)

---

### Post by GTMoraes on 2011-06-11
> **linuxinstalledfromhdd said:**
> users have reported issues with the USB in virtualbox with what you are doing.

try VMware, windows, and good 6-in-1 usb reader device hooked to the VMWare booted win.

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

you will never know unless you try  :)

VMware may look like Virtuabox but they are not the same. :)
Believe me, I'm trying. I've replaced every micro n' soft things for OpenSource derivatives, and they perform very well.
But the loss of the pictures... Twice...
Luckly I don't have any children, yet. Can't imagine if I had lost my children' first moments pictures.

Can I use my already-created virtual HDD on VMWare?
I think there is a limitation regarding on how many computers you can install windoze to..

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **GTMoraes said:**
> Believe me, I'm trying. I've replaced every micro n' soft things for OpenSource derivatives, and they perform very well.
But the loss of the pictures... Twice...
Luckly I don't have any children, yet. Can't imagine if I had lost my children' first moments pictures.

Can I use my already-created virtual HDD on VMWare?
I think there is a limitation regarding on how many computers you can install windoze to..

Don't cut corners by doing that. That's one of the major reasons why new users have so many issues and problems with their systems.. They imagine a way of doing something, that doesn't exist in reality... :)   Just follow the guide I posted and you will be OK:

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

There is no short cut if you want to stop losing data. I hear everything else you are saying though. And virtualbox sucks for professional use - imo..  But you got to try all the alternatives first, if sadly there simply is no workaround..  and AFAIK there is none. Maybe someone knows?

I used to tell my auto mechanic the same thing, and he would stand there like I was nuts.  I imagine a way of doing something, and he just laughs at me.

---

### Post by GTMoraes on 2011-06-11
> **linuxinstalledfromhdd said:**
> Don't cut corners by doing that. That's one of the major reasons why new users have so many issues and problems with their systems.. They imagine a way of doing something, that doesn't exist in reality... :)   Just follow the guide I posted and you will be OK:

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

There is no short cut if you want to stop losing data. I hear everything else you are saying though.  But you got to try all the alternatives first, if sadly there simply is no workaround..  and AFAIK there is none. Maybe someone knows?
Will do when I come back from the picture trip.
At least I'm not paying for the fuel.

The solution ubuntu-wise sounds simple, but I don't know how to do:
Only eject the device when transfer is complete.

Something like when you select "Securely remove the device", on the ubuntu side too. But I can't choose this option, otherwise it'll disable my built-in 6-in-1 (i already have one =]) card reader till next restart.

Got to go now. Maybe tuesday I'll be back and I'll check this post to see any solution.
See ya

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **GTMoraes said:**
> Will do when I come back from the picture trip.
At least I'm not paying for the fuel.

The solution ubuntu-wise sounds simple, but I don't know how to do:
Only eject the device when transfer is complete.

Something like when you select "Securely remove the device", on the ubuntu side too. But I can't choose this option, otherwise it'll disable my built-in 6-in-1 (i already have one =]) card reader till next restart.

Got to go now. Maybe tuesday I'll be back and I'll check this post to see any solution.
See ya

And my professional suggestion is to not use the internal (virtualbox isn't using that internal correctly) and use an external 6-and-1 or 12-in-1 (that you aquire from a store) or whatever with VMWare USB enabled WinXp. That might work. The USB support is better with VMWare too. You'll see that rightaway.

---

