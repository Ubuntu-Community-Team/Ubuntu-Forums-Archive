---
title: "gnome desktop losing its tiny mind.  please help!"
date: 2009-09-06
forum: General Help
---

### Post by quixote on 2009-09-06
Audacity gave me a few error messages about not opening a file because it couldn't get a lock on some /var file it needed, and the next thing I knew, my desktop was all screwy.  Desktop icons have large type instead of small, and refuse to change when reset to small in nautilus.  Network-manager isn't remembering keyrings, and sometimes isn't finding networks.  Sometimes it is, and then it wants the password re-entered.  I had a to-do list on the Desktop in a "Sticky Note" applet, but even though the panel itself is normal, Sticky Note says it has zero notes.  I do still have my usual wallpaper.

I don't get any error messages on bootup, but I do have all these very annoying glitches.  My home directory is backed up daily, so I would think that if I could just figure out where gnome keeps all the desktop info, I could just restore from backup.  

Searching the forums, it seemed like I should be looking for .gdm, but there's no such directory or file on my 9.04 system.  Where should I look for the gdm settings?  Or whatever I need?

I hope somebody can help.  It's been a while since I backed up my system files (of course) and I really don't want to have to reinstall just to get a functioning desktop again. :-?

---

### Post by Efwis on 2009-09-06
to show the .gdm file you need to have hidden files shown. open nautilus and then hit ctrl+H or you can click on view and check the box next to show hidden files.

as for restoring your install from a backup I don't have that info. I dont' back up my system, nor do I do anything that would break it, at least not yet.

---

### Post by quixote on 2009-09-06
I did show hidden files.  I couldn't find it.  Can you tell me the path I should follow?  Eg ~/.gnome2/and/then/no/doubt/a/zillion/subdirectories? :)

---

### Post by Efwis on 2009-09-06
> **quixote said:**
> I did show hidden files.  I couldn't find it.  Can you tell me the path I should follow?  Eg ~/.gnome2/and/then/no/doubt/a/zillion/subdirectories? :)

only place I'm finding GDM is in /etc/gdm

---

### Post by quixote on 2009-09-06
In that case, if gdm is what I really need, I'm screwed because I haven't backed up system files in months.

I guess my question now is: what is the best thing to do to try to resuscitate an iffy desktop?

---

### Post by Efwis on 2009-09-06
well there is always the re-installation route. i can't think of anything else to fix it.

---

### Post by quixote on 2009-09-06
Aaaack.  No!  Don't say that!  There has **got** to be some way to fix config or settings files!  Some sort of dpkg --configure -a for gnome.  Right?  Right?

---

### Post by Efwis on 2009-09-06
> **quixote said:**
> Aaaack.  No!  Don't say that!  There has **got** to be some way to fix config or settings files!  Some sort of dpkg --configure -a for gnome.  Right?  Right?

i'll do some more research on it, who knows maybe someone will respond with the answer while I'm looking around.

---

### Post by utnubuuser on 2009-09-06
you can restore the desktop to its original state with:> cd /home/username
rm -rf .gnome2 .gconf .gconfd .metacity 

-- all your desktop configuration files will be deleted, and the desktop will be like a new install.  - bit of a pain if you've got your DT all tricked out,  but considerably less work than a fresh install.

Here's the related thead:[http://ubuntuforums.org/showthread.php?t=10604]("http://ubuntuforums.org/showthread.php?t=10604")

PS I use 8.04 and have used this to restore a desktop, - not a 100% sure, but the commands should work equally well in 9.04

---

### Post by quixote on 2009-09-06
Thanks for your replies, Efwis and utnubuuser.  Since the directories you mentioned are in my ~home, the first thing I'll try is just copying those back over from backup.  If that brings me no joy, then I'll try the removing.  Hopefully, I'll have good news to report when I come back.

---

### Post by quixote on 2009-09-07
Yes!  That worked.  The directories listed by utnubuuser were the ones I needed.  

I booted into recovery mode, just in case it was a bad idea to change desktop settings files while the desktop was actually "on."  

Connected to my backup drive, switched directory to the backup of my home, copied over the three directories using ```
cp -a .gnome2 /home/quix/.gnome2
``` and so on.  In my case, .metacity is a subdirectory of one of those, so I didn't need to do it separately.

In the process of doing all that, I noticed that my home dir was 100% used!  No wonder I was having trouble.  Turned out that .thumbnails/ had gotten huge, even though I'd told Nautilus NOT to cache the damn things.  (I'd run into that problem once before.)  So it was nothing to do with Audacity.  The original problem was that the partition had filled up and I hadn't noticed.

Thanks for all your help folks!  I couldn't have done it without you and I really appreciate it.

---

