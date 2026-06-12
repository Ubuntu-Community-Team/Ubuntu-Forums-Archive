---
title: "Wipe or reformat disk"
date: 2010-11-13
forum: General Help
---

### Post by John Franklin on 2010-11-13
What's the least I have to remove in order to do a clean installation of Ubuntu?

Alternatively, how do I reformat the main partition from the command line?

---

### Post by Hippytaff on 2010-11-13
Hi,

I don't quite understand what your asking. Do you already have ubuntu?

Are you dual booting? and what are you looking to do?

---

### Post by John Franklin on 2010-11-13
I have recently updated from Ubuntu 10.04 to 10.10 but there are problems including the GUI not working. I only have command line access. What I'd like to do is a clean install of Ubuntu to try to resolve these problems as quickly as possible. Just putting a CD in the drive isn't enough. So I want to remove the existing Ubuntu first. I suspect that reformatting the drive might be the easiest way to do this but how do I do this?

---

### Post by cogier on 2010-11-13
If you run through the install process there is an option to use the whole disk. This will reformat the disk for you.

---

### Post by Hippytaff on 2010-11-13
Before you do that though, you might want to try
```

startx

```

---

### Post by John Franklin on 2010-11-13
Unfortunately I can't get that far. If I boot on a 10.10 CD, it says that it can't mount the drive. If I boot on a 10.04 CD, it mounts OK, but takes me straight to a log-in screen where none of my usernames or passwords are accepted. Either way I can make no progress. I'm hoping that if I start off with a clean drive, the installation will not be confused for whatever reason with what's already on the disk.

---

### Post by John Franklin on 2010-11-13
I have already tried startx and the folks on launchpad haven't been able to suggest a solution. I need it working soon so a clean install (of 10.04 if necessary) seems my best option.

---

### Post by Hippytaff on 2010-11-13
Cool...well if your not dual booting cogier's suggestion will do it

Edit -> sorry missed a post, once you log in to the liveCD you should have an option to install or try...if your 10.10CD is playing up use 10.04, you can always upgrade or download a 10.10 CD later if you want to

---

### Post by cchhrriiss121212 on 2010-11-13
I would double check you are correctly booting from the DVD drive and not your HD. Because no live cd environment will ask you for a username or password, and whatever you have on your hard drive will have no effect on the live cd environment.
Try opening BIOS (usually f2/f11/f12) and selecting the DVD drive as first boot proirity.

---

### Post by Hippytaff on 2010-11-13
> 
no live cd environment will ask you for a username or password

good point

---

### Post by John Franklin on 2010-11-13
I checked that the computer was booting on the CD and it was. It turned out that although on most occasions it ended up with a Login dialog, on other occasions the install dialog was shown. I've now reinstalled 10.04 and am going through the setup process, trying to remember all the settings. 

I made a second 10.10 boot CD but that still wouldn't work so it may be that this version is incompatible with my graphics card.

---

### Post by Hippytaff on 2010-11-13
> 
incompatible with my graphics card.

There may be way around this, but install 10.04 first and take it from there...glad your managing to sort it :-)

---

