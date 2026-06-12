---
title: "Backup settings question"
date: 2006-05-29
forum: General Help
---

### Post by IndigoMontoya on 2006-05-29
Is there a guide out yet for where to find the settings to backup settings for firefox, thunderbird, gaim, etc.  for a clean dapper install

My first thought is just to copy the .mozilla .thunderbird or .gaim folders and put them in my new home folder.  Should I do something to backup my plugins as well, or is it better to install these fresh?

---

### Post by groggyboy on 2006-05-29
You got the right idea.  All you need to keep the settings for most programs is the hidden folder in your home directory.  Copy them onto a usb stick or a cd, and copy them back once your fresh install is done - replacing any new folders that may have been made.

Let me suggest something.  If you don't have a separate home partition already, make one when you do your fresh install.  The Ubuntu installer should set it up for you automatically.  Look at the size of your current one for a good idea of how large to make it.

The biggest benefit of having a seperate home partition is that any time you reinstall Ubuntu (or any other flavour of linux), all your personal settings will be saved - as long as you tell the new installation where to look for your new home directory.

groggyboy

---

### Post by IndigoMontoya on 2006-05-29
Great thanks.  I will setup the seperate home partition, great idea.  Here is a dumb question though (that has bugged me for some time).  When I ls -lh I always get 4k for any directory (I understand why, but don't know how to get the full directory contents with this command.  Is there a command line way to do this easily?

Thanka!

---

### Post by groggyboy on 2006-05-29
I'm not too sure.  I just use nautilus for such things.  Right click on your /home folder and choose properties (at the bottom of the list).

---

