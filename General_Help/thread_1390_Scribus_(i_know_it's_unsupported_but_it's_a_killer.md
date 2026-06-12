---
title: "Scribus (i know it's unsupported but it's a killer app)"
date: 2004-10-20
forum: General Help
---

### Post by calvinpriest on 2004-10-20
Hi All,

Thanks for the exceptional distro.  My highest compliments to everyone involved.

So I know that Scribus is currently unsupported, and may continue to be because it's qt based, but it is completely broken in universe.  It will install and it will start, but it can't open Scribus files ("Scribus crashes due to Signal #11").  The version in universe is from cvs, probably because the current version in Debian unstable is dependent on a very slightly newer library.

I have been able to install the latest deb file (1.2.0-1_i386) from Scribus with "dpkg -i --force-depends".  It installs and has worked perfectly thus far.  However, that breaks apt, and i have to remove Scribus before i a can install/uninstall packages again.  I imagine there is a better work around?  Maybe slightly different dpkg command?

In the long run, I believe Scribus should be supported, as should K3B.  IMHO, Scribus is one of Linux's killer apps and there is no equivalent, same as K3B.  But at least K3B works -- which keeps the peace.   Scribus may not be as high a priority, but at some point relatively soon it would be good to fix it.

Thanks all,
Calvin Priest

---

### Post by flygmaskin on 2004-10-20
Have you tried compiling from source, or building your own debs? That might (possibly, not sure) solve your problems.

I'm basicly just guessing, so don't blame me if it fucks up your computer :)

---

### Post by calvinpriest on 2004-10-20
Yes, I've attempted a source install, and that has even more dependency problems (libart2-config, freetype-config, and then it errors out).

I imagine with some sweat and determination, I can get the source to install.  But I would view that as a sort of hack, because a less technical user would probably be lost at this point.  And my interpretation of this distribution is that it wants to be user friendly.  And, in fact, I have found it extremely user friendly thus far.

I fully appreciate Ubuntu's focus on Gnome/GTK.  I think it's a wise idea.  But I also think exceptions need to be made for killer apps.  I believe those apps need to work, whether or not they are ultimately fully supported.  Otherwise we are going to turn away otherwise happy community members.

It seems like a good project for a little while after Warty's official release and associated patching.

Thanks,
Calvin

---

### Post by josel on 2004-10-25
You could download qt3 (a good idea wouls also be qt3-devel debs if you need to compile other kde/qt packages) from  [http://geeksoc.org/~jr/ubuntu/](http://geeksoc.org/~jr/ubuntu/)  unstable and go get  1.2.0final  from the debian website (search for it on sarge). I did that and it works fine.

Cheers
José Lobato

---

### Post by goozer on 2005-01-31
Well, I for one was disappointed to look at the list of apps in Ubuntu and not find Scribus. Then to go to this forum and find this thread indicating that it won't really work.

Please don't read this as putting down Ubuntu. I'm just interested in publishing a newspaper with open source and Scribus is probably the only option for detailed publishing.

If you know of something other than Scribus that would work for producing a real newspaper please post the program.

I'm new to Linux so I don't even feel comfortable using special commands to force an install of Scribus.

I read that SuSe includes Scribus, and I did buy the latest version of SuSe so I guess I'll install that.

I don't know if Scribus is a killer app but if it reasonably replaces Quark or InDesign then it most certainly is.

John in Medford Oregon

---

### Post by JNewman on 2005-02-20
[QUOTE=goozer]Well, I for one was disappointed to look at the list of apps in Ubuntu and not find Scribus. Then to go to this forum and find this thread indicating that it won't really work.

Please don't read this as putting down Ubuntu. I'm just interested in publishing a newspaper with open source and Scribus is probably the only option for detailed publishing.

If you know of something other than Scribus that would work for producing a real newspaper please post the program.

I'm new to Linux so I don't even feel comfortable using special commands to force an install of Scribus.

I read that SuSe includes Scribus, and I did buy the latest version of SuSe so I guess I'll install that.

I don't know if Scribus is a killer app but if it reasonably replaces Quark or InDesign then it most certainly is.

John in Medford Oregon[/QUOTE]
 I've had Scribus working on Warty for a couple of months and like it very much. As far as I remember, there weren't any problems getting it to work. (If there had been, I probably wouldn't have been able to solve them; I'm far from being Linux-savvy.)

I remember Synaptic needed access to unstable, and I needed to get Scribus from scribus.org.uk -- that was basically all there was to it.

---

### Post by WW on 2005-02-20
JNewman: It is possible to install scribus from warty's universe repository.  I just tried it, and I was able to create, save and load a small file.  However, when I tried to load a large file (80 pages, according the site where I found the file), I got the error that calvinpriest described: "Scribus crashes due to Signal #11".  So, to quote the linux kernel, "...it is broken and must be fixed."

---

### Post by kassetra on 2005-02-20
goozer: here are a couple more applications:
 
 [PageStream]("http://www.grasshopperllc.com/") - a commercial desktop publishing application for linux (they have a "free" version, and a "pro" version) - [screenshot]("http://www.gnomefiles.org/shots/pagestream.png")
 
 [Passepartout]("http://www.stacken.kth.se/project/pptout/") - a newer desktop publishing application with some nice features - [screenshot]("http://www.stacken.kth.se/project/pptout/screenshots.html")
 
 So you're not limited to just scribus.  Also, if you didn't want to force scribus, you could always build and install the source code, which I can help you with.  :)

---

### Post by kh4nh on 2005-02-21
I got Scribus running fine under Hoary, [Install Scribus Now](http://ahnews.music.salford.ac.uk/scribus/documentation/dpkg.html)

---

### Post by jdong on 2005-02-21
A Warty-compatible Scribus 1.2.0 is in Warty's Backports. Please let me know if it's not new enough. [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

