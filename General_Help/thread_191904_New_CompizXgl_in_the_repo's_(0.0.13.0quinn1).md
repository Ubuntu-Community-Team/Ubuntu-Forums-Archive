---
title: "New Compiz/Xgl in the repo's (0.0.13.0quinn1)"
date: 2006-06-08
forum: General Help
---

### Post by matrooswolf on 2006-06-08
There is a new compiz (0.0.13.0quinn1) in the repos (in the repos from quinnstorm), + libgl1-mesa, Xgl ...

Anybody has any experiences with it?  Mayor crashes?
(I am always a little chicken ;))

---

### Post by arendm on 2006-06-08
I have no problems with it and even got sound back with flashmovies! :-\"

---

### Post by matrooswolf on 2006-06-08
Thanks for the reply!
sound with flashmovies?  Wow!  Google Video here I come! ;)

---

### Post by CuCullin on 2006-06-08
In KDE 3.5.3, with those latest updates, XGL+compiz seems more stable.  However, I no longer have a title bar! Just the menu bar down, so I have to alt+click to move windows...

---

### Post by leohart on 2006-06-08
I didn't have any problem with it at all. Regarding sound problem in flash movies. 

I have had such problems before and it turns out that my Ubuntu box does not have sound duplex set up (or something similar to that), so if I am playing / have played music with a music player during my session, then flashmovies will lose sound.

What I did that kindda help is ```
killall artsd
```

---

### Post by zitch on 2006-06-08
I've downloaded and installed it with a few issues.  One is the new functionalities (Alt-Ctrl-Down now goes down to the bottom of the cube than pull out with the unwrap feature.  That has been changed to Alt-Ctrl-Next, or Alt-Ctrl-Pg Dn on most keyboards... ).  One bug is the bottom of the cube isn't getting pictures mapped onto it, but apparently that has already been [fixed](http://www.compiz.net/viewtopic.php?id=1189) in the CVS version, so it's a matter of time till this filters down to the Ubuntu repositories.

Other than these it has been smooth sailing, so I'm happy!

---

### Post by panurge77 on 2006-06-08
compiz (0.0.13-0quinn1) dapper; urgency=low

* new dock (6b)
* rotate/cube patches
* bugfixes, updates from CVS, perhaps icons work on x86_64 now?
* added possible fix for invisible windows becoming visible with widget
* many fixes from cvs
* reverted aiglx patch for copySubBuffer
* fixed wheeling patch
* upstream version bump
* moppsy's neg plugin
* added current release of dbus stuff
* added change to version string, quinn compiz's will now end in -quinnX
* windowshade from CVS

-- Quinn Storm <livinglatexkali@gmail.com> Thu, 8 Jun 2006 00:09:13 -0400

Let's go testing :)

---

### Post by testube_babies on 2006-06-08
I've found everything works great except the neg plugin, which is quite unpredictable.  It still has a cool effect, though.

---

### Post by matrooswolf on 2006-06-09
[QUOTE=zitch]One bug is the bottom of the cube isn't getting pictures mapped onto it, but apparently that has already been [fixed](http://www.compiz.net/viewtopic.php?id=1189) in the CVS version, so it's a matter of time till this filters down to the Ubuntu repositories.

Other than these it has been smooth sailing, so I'm happy![/QUOTE]

Yes no bottom image, and my skydome went AWOL right after updating, but it mysteriously reappeared.
> I've found everything works great except the neg plugin, which is quite unpredictable. It still has a cool effect, though. 
What is neg supposed to do?  <super>button1 doesn't do anything for me ...  BTW, does neg mean anything?  (Negative?)

Edit:
Oh I see, you get a negative of a window.  Looks nice, but doesn't work for me.

---

### Post by panurge77 on 2006-06-09
yes, it's suposed to turn your desktop into negative colors

---

### Post by grendelkhan on 2006-06-09
I've lost the ability to add wallpaper to the gnome-background-properties app.  I have to add them by hand now - major PITA.

---

### Post by matrooswolf on 2006-06-10
New compiz is out, fixes the missing bottom picture.
compiz 0.0.13.0quinn2

---

### Post by no1wantdthisname on 2006-06-10
[QUOTE=CuCullin]In KDE 3.5.3, with those latest updates, XGL+compiz seems more stable.  However, I no longer have a title bar! Just the menu bar down, so I have to alt+click to move windows...[/QUOTE]

Do you have desktop icons turned off?  I've noticed that having desktop icons turned off in kde gives me borderless windows.

---

### Post by Jeff Johnston on 2006-06-10
I had to use the gset-compiz program to change my settings. The gconf-editor did not work for me to change my settings. Every time I change one of the Compiz settings it would not stay put, including the decorator. Not sure why, but the gset-compiz is a great little tool for changing whatever you need.

---

### Post by stryderjzw on 2006-06-10
I think I lost some of my Chinese characters... :(

---

### Post by matrooswolf on 2006-06-10
[QUOTE=Jeff Johnston]I had to use the gset-compiz program to change my settings. The gconf-editor did not work for me to change my settings. Every time I change one of the Compiz settings it would not stay put, including the decorator. Not sure why, but the gset-compiz is a great little tool for changing whatever you need.[/QUOTE]
Thanks for the tip, I always use gconf-editor, and changes don't always do anything, I'll give gset-compiz a try

---

### Post by copey02 on 2006-06-12
where do i get gset-compiz and how do i install it?

---

### Post by Stroganoff on 2006-06-12
Follow the instructions to get Quinn's Repo.
[http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/)

Then just 
sudo apt-get install gset-compiz

---

### Post by matrooswolf on 2006-06-12
[QUOTE=copey02]where do i get gset-compiz and how do i install it?[/QUOTE]
It's in the repo's

---

### Post by jmrush on 2006-06-25
I've changed a lot of the gset-compiz values and now my windows seems to be messed up.Could someone please post the right values or even screenshots of different gset-compiz plugins screens?
Thanks in advance

---

### Post by matrooswolf on 2006-06-26
Just updated Xgl and compiz from quinnstorm's repositories to 0.0.13.0quinn4.

Dock and Miniwin were removed, it seems.  Which is good, I always had troubles with miniwin (in the latest compiz, I could only minimize a window once).

Miniwin as a feature is nice, but it was buggy, hope it gets back in style.

Now everything working very well and at full speed.  
(Running Xgl/Compiz with VMWare and Windows XP at the moment. with wobbly windows and transparency: Vista, eat your heart out ;))

---

### Post by joshrobinson on 2006-06-26
[QUOTE=matrooswolf] Vista, eat your heart out ;)[/QUOTE]

thats what i say to myself everytime i look at my xgl compiz desktop lol :cool:

---

