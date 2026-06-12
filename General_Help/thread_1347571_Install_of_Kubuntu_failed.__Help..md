---
title: "Install of Kubuntu failed.  Help."
date: 2009-12-06
forum: General Help
---

### Post by kevinwmiller on 2009-12-06
I downloaded the ISO Kubuntu from the site, then used USB creator to create a book disc on the USB.

It stops at "Copy files" at about 51%, tells me it failed and that it could be because of a bad ISO, HD etc.

My question is, can you download a new ISO and store it on the HD using the USB live boot option?

Or will it just download to the USB?

---

### Post by quixote on 2009-12-10
Is it the USB that doesn't work?  Or did the install from the USB to your hard drive fail?

Do you still have a functioning Ubuntu, either on HD or USB?  

If yes, and if the functioning unit is the USB, then when you boot the HD is probably not mounted by default.  Open nautilus (eg, Places  -> Home) and double-click on the entry that is the right size to be your HD.  That will mount it.

Next you need to figure out its actual path.  Look in /media/disk-1 or the like in the /media directory and find your HD.  Then find a subdirectory on the HD where you want the download to go, eg /media/disk-1/home/you.

Enter that subdirectory in the Firefox preferences download path, and it will go to that subdir instead of your USB.  (All downloads will continue to go there until you change it back to something else.)

Then you'll at least have a new copy of the iso.  You'll probably have to burn it to a CD before you can do anything with it, though.  (?)

---

