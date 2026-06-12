---
title: "Few Random Question help please"
date: 2006-04-11
forum: General Help
---

### Post by scotishhaggis on 2006-04-11
Hey guys great Linux distro but a few questions:

I have tried both copys for the pc i386 and the 64bit version. Found both ok but the 64but was hard to get stuff to work. My main question is should I stick to the 64 or reinstall the i386.

Plus how do I get the themes to work from [www.gnome-look.org](www.gnome-look.org). I see there are a few nice 1&#8217;s that seem to use a menu style like OSX with widgets??see>>>[http://www.gnome-look.org/content/pre1/37533-1.png](http://www.gnome-look.org/content/pre1/37533-1.png)

Any ideas of what software is good to install to. I.e games , general softwear for every day use. Am at uni doing computing so just generally ideas whould be great. My sys specs are below

---

### Post by earobinson on 2006-04-11
> I have tried both copys for the pc i386 and the 64bit version. Found both ok but the 64but was hard to get stuff to work. My main question is should I stick to the 64 or reinstall the i386. i386 is more stable and I find that a lot of people run that, but if you have it all working in the 64 version I dont see why you cant use that.

> Any ideas of what software is good to install to. I.e games , general softwatwrea for every day use. Am at uni doing computing so just generally ideas whould be great. My systenm specs are
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

one of my gave games is nethack to install use this command in the terminal ```
sudo apt-get install nethack-gnome
```

---

### Post by Blarion on 2006-04-11
I'd use whatever was more stable

---

### Post by yamagami on 2006-04-11
I found that my machine booted way faster and was a lot more responsive when i used the i686 kernel instead of i386 (but I'm running an intel P4 processor and not AMD). 
I also found that installing kioslaves and the Kate editor package on gnome made editing remote files much easier.

---

### Post by earobinson on 2006-04-11
i686 is more modern, one of the goals of ubuntu is to run on any computer, so they stick with the old old old kernel, 99% of computers will want to run the i686  so yes you are correct!

---

### Post by plumcreek on 2006-04-11
[quote=scotishhaggis]how do I get the themes to work from [www.gnome-look.org]("http://www.gnome-look.org"). I see there are a few nice 1’s that seem to use a menu style like OSX with widgets??[/quote]

untar/unzip the theme and place the folder in ~/.themes/

You'll have to create the folder if it doesn't exist. The .themes folder is in your home directory and it's invisible, so it's easiest to use the command line to move themes into it.

Example:
```

tar -zxf some_theme.tar.gz
mv some_theme ~/.themes/

```

Then go to System -> Preferences -> Themes and you should be able to change things around.

The Themes program does have the ability to install themes by you dragging the tar.gz files and dropping them on the window, but it doesn't always work. Manually putting themes into the ~/.themes/ directory has worked best in my experience.

I'm writing this from memory, so please correct me if there are errors.

Thanks.

---

### Post by jasay on 2006-04-11
[QUOTE=scotishhaggis]
Plus how do I get the themes to work from [www.gnome-look.org](www.gnome-look.org). I see there are a few nice 1’s that seem to use a menu style like OSX with widgets??see>>>[http://www.gnome-look.org/content/pre1/37533-1.png](http://www.gnome-look.org/content/pre1/37533-1.png)
[/QUOTE]
Download the theme you want (don't extract it).  Then open System menu > Preferences > Theme and drag the downloaded file to the new window.  That should install it, and then you can select the theme you like from the themes program.  

The second link you posted show someone running Xgl (or possible aiglx) with compiz.  This is experimental software that uses the 3-d graphics card to draw the desktop and makes a lot of fun graphical stuff possible.  Just as a warning this stuff can mess over you gui, so if you're not confortalbe fixing stuff from the command line it may not be for you yet.  It's still really new software and is getting better very quickly.  It's probably safest to wait a little.  That said, it's been working perfectly for me for 2 months now. [Old demo video.]("http://people.freedesktop.org/~davidr/xgl-demo1.xvid.avi")  [Howtos (mostly for dapper)]("http://www.ubuntuforums.org/showthread.php?t=148351").

---

