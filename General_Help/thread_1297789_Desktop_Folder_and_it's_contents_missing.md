---
title: "Desktop Folder and it's contents missing"
date: 2009-10-22
forum: General Help
---

### Post by brunoscunha on 2009-10-22
Last night I shutdown the laptop. Later I connect it again, but the Desktop directory has disapeared and all of it's contents. I'm pretty sure I did not do any strange command.
Is it possible to recover what has disapeared from the Desktop folder and the folder itself?
I'm running jaunty 32 bits

Thank you

---

### Post by vinutux on 2009-10-22
```
ls /home/[COLOR="Red"]YOURUSERNAME[/COLOR]/Desktop
```

---

### Post by brunoscunha on 2009-10-22
Thanks for answering so fast. I did what you suggested but I'm still with the same problem. What I have as desktop now are the contents of Documents. Under my username I did ls -la and in fact the Desktop dir is missing (all I did last night was to disconnect the laptop).
Ok I can make a new Desktop dir and make it default, but all the files that were in that dir are missing, and that's a big pain.
Is there, like on xp, a restore point?

---

### Post by P4man on 2009-10-22
an XP restore point doesnt restore deleted files either. And no, there isnt.
But try this. Open a terminal and type

gconf-editor

then browse to 

apps > nautilus >  preferences

make sure "desktop_is_home_dir" is deslected.

---

### Post by wojox on 2009-10-22
Try this also 

Open ~/.config/user-dirs.dirs

Look for this entry: XDG_DESKTOP_DIR. Make it like this: 

XDG_DESKTOP_DIR="$HOME/Desktop"

Log off and log in again.

---

### Post by brunoscunha on 2009-10-22
Already did that. No luck recovering the files that were in the Desktop
:(

---

### Post by mechro on 2009-10-22
Is it in Trash?

or root Trash?

---

### Post by brunoscunha on 2009-10-22
> **mechro said:**
> Is it in Trash?

or root Trash?
Neither. Damn I lost pretty important documents

---

### Post by mechro on 2009-10-22
If there's no other ideas you could try Testdisk. It will list and copy deleted and lost files if they haven't been overwritten.

---

### Post by mechro on 2009-10-22
> **mechro said:**
> If there's no other ideas you could try Testdisk. It will list and copy deleted and lost files if they haven't been overwritten.

Oops, sorry, I'm wrong. I don't think it copies deleted files... it'll find a record of them but that's not much use. There's Photorec...

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Edit: Photorec available via installing Testdisk from Synaptic... rolls eyes at self!

---

### Post by vinutux on 2009-10-22
> **brunoscunha said:**
> Already did that. No luck recovering the files that were in the Desktop
:(

That two thing is not for restoring..... make your desktop dir to home... 

For restoring deleted files try foremost or scapel

[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html]("http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html")

---

### Post by brunoscunha on 2009-10-22
> **mechro said:**
> Oops, sorry, I'm wrong. I don't think it copies deleted files... it'll find a record of them but that's not much use. There's Photorec...

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Edit: Photorec available via installing Testdisk from Synaptic... rolls eyes at self!
Thank you. I'll try photorec

---

### Post by mechro on 2009-10-22
> **brunoscunha said:**
> Thank you. I'll try photorec

Just done a quick test with Photorec on my system. It's pretty awesome!

There's an option to check for certain filetypes so you can narrow it down. And try and get it to copy the recovered stuff to another partition; in my case I navigated to /media/Data and it saved the stuff there in a bunch of folders owned by root.

---

### Post by alexwyu on 2009-11-08
My situation is even worse.  After I installed Ubuntu from scratch (wiped out everything in the harddrive), all I have is a pitch black background with the top tool bar and bottom status bar.  No matter what background I choose, it keeps staying pitch black.  Rebooting the system or updating the OS does not change the situation. But the strangest thing is that I install the same Ubuntu 9.10 in the other PC with Win XP in it, and specified to import win stuffs, the background appears, in win's background photos.  What could be wrong?

[IMG]file:///home/alexwyu/Screenshot.png[/IMG]

---

### Post by mechro on 2009-11-08
> **alexwyu said:**
> My situation is even worse...


In **System > Preferences > Appearance: Background** what colour is showing in the Colours box? Can you change it?

---

### Post by P4man on 2009-11-08
are you runnign desktop effects? If so, did you try disabling them ?
system > preferences > appearace > desktop effects

What videocard do you have?

---

### Post by alexwyu on 2009-11-09
Just for further information:

I had tried changing backgrouds and themes; and the only thing changed was the top and bottom bars color, the desktop area stayed black.  Then I shutdown the system; and somehow the background picture I chose flashed by briefly before it was shut down.

Now, there is another thing: I tried booting the Ubuntu 9.10 info my system to see the situation.  And strangely enough, the same pitch black desktop also appeared!  This has nothing to do with any special settings, as it situation appeared right after I booted the livecd.  But booting the Ubuntu 9.04 livecd gives no such problem.

I am starting to doubt if it is the iso file having problem.  I have wiped out the installation on my harddrive already and will try other methods later.

Anyway, here is some hardware info of my PC:

CPU: Pentium D 2.66GHz
RAM: 512M
Video: ATI Radeon 9200SE

---

### Post by mechro on 2009-11-09
Did you try P4man's suggestion about Desktop Effects/Compiz?

There has been a bug reported mentioning ATI drivers...

[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/421334](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/421334)

---

### Post by alexwyu on 2009-11-12
Thank you Mechro.  Your suggestion get my desktop back.  I believe the problem is with the bug you mentioned.

I did not know compiz was activated as I only used Normal instead of None for the desktop effect, which is set as default upon installation.  But anyway, the problem is solved for the moment. I hope the bug would be fixed in the near future.

Once again, thank for all the support.

---

### Post by Claus7 on 2009-11-12
Hello,

for the starter of the thread, what I could advice for a quick thing to try, is the find command. That way you will be sure that you had not moved accidentally the Desktop folder to some other location. If you remember also some names of your files you might be able to find them. That, only in case they are not erased. Other than that you can follow the suggestions of this thread.

Regards!

---

