---
title: "unity crashed in ubuntu 11.10"
date: 2011-11-03
forum: General Help
---

### Post by vat with tux on 2011-11-03
Hi all...
I installed compiz customization manager and try to change some settings. Because of that my unity crashed down.. 

Now I have already tried "unity --reset" but it gives following output and then do nothing ...

> vatsal@ubuntu:~$ sudo unity --reset
[sudo] password for vatsal: 
WARNING: no current gconf profile set, assuming unity
WARNING: Unity currently default profile, so switching to metacity while resetting the values

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x36000db
 

Myunity 2D is working fine ....
Please help me out.....
Thanking in advanced....

---

### Post by jjer on 2011-11-03
Hi, 

I have had this problem twice:
- First time I re-installed Ubunty 11.10. 
- After this I have carefully backed up all hidden folders files in my user home folder (/home/<user>/) before using compiz.
- At the next crash of unity desktop, I opened my home folder and copied in my backed up hidden files. After logging out and in everything was working again.
- I suspect the problem is corrupt files in the ~/.config/compiz-1/ folder structure.
- Before you eventually get desperate and delete everything in order to reinstall try deleting the files here first.

I hope this may help you.

---

### Post by bbrg548 on 2011-11-03
> **jjer said:**
> Hi, 

I have had this problem twice:
- First time I re-installed Ubunty 11.10. 
- After this I have carefully backed up all hidden folders files in my user home folder (/home/<user>/) before using compiz.
- At the next crash of unity desktop, I opened my home folder and copied in my backed up hidden files. After logging out and in everything was working again.
- I suspect the problem is corrupt files in the ~/.config/compiz-1/ folder structure.
- Before you eventually get desperate and delete everything in order to reinstall try deleting the files here first.

I hope this may help you.

Thanks! That helped me with the same issue. Fortunately, I keep regular backups on an external hard drive (and had backed up my system just last night), and I was able to restore those files from there.

---

### Post by vat with tux on 2011-11-04
> **jjer said:**
> Hi, 

I have had this problem twice:
- First time I re-installed Ubunty 11.10. 
- After this I have carefully backed up all hidden folders files in my user home folder (/home/<user>/) before using compiz.
- At the next crash of unity desktop, I opened my home folder and copied in my backed up hidden files. After logging out and in everything was working again.
- I suspect the problem is corrupt files in the ~/.config/compiz-1/ folder structure.
- Before you eventually get desperate and delete everything in order to reinstall try deleting the files here first.

I hope this may help you.

That worked for me too.. thanks buddy...:) 
Anyway I was not going to reinstall ubuntu because my gnome , KDE and unity 2D were working fine......:D

---

### Post by washington luiz on 2011-11-06
Dude deleting that folder just kind of saved a really bunch of time and work!!!

I screwed it up so much that it came to a point where I could do on my user account was open a folder on nautilus and from there open an .html file to open a browser and find your reply. Even terminals wouldnt appear anymore with Ctrl Alt T.

People should really be careful when using compiz manager .. That thing is can so **** your desktop environment.

Thanks for your reply!!!

---

### Post by recezone on 2011-11-06
yeah,  I had a lot of issues messing with compiz as well.  i was having to restart all the time.  Like "hard restarts"  pressing the power button.  Anyway,  I did notice that when logged into unity 3d i had no desktop menus or launcher.  If this is happening, After logging into unity 2d and opening up compiz manager I noticed that the "ubuntu unity plugin" was turned off,  although i didn't turn it off myself.  i think sometimes it will happen messing with desktop cube and stuff like (not sure how). So just selecting it again in 2d did the trick. This was a big relief for me. I really hate reinstalling.

---

### Post by madnag4u on 2012-01-06
> **jjer said:**
> Hi, 

I have had this problem twice:
- First time I re-installed Ubunty 11.10. 
- After this I have carefully backed up all hidden folders files in my user home folder (/home/<user>/) before using compiz.
- At the next crash of unity desktop, I opened my home folder and copied in my backed up hidden files. After logging out and in everything was working again.
- I suspect the problem is corrupt files in the ~/.config/compiz-1/ folder structure.
- Before you eventually get desperate and delete everything in order to reinstall try deleting the files here first.

I hope this may help you.

This morning my unity crashed with no apparent reason. I had not installed ccsm or messed with any config file of compiz. Suprisingly, the solution you posted worked! :) 
There does seem to be a problem in that folder structure... 
+1 to you jjer !!

---

