---
title: "Export KDE Colour Scheme"
date: 2006-03-26
forum: General Help
---

### Post by ace2005 on 2006-03-26
Every time i reinstall i have to try and get back to the colour scheme i was using and its very hard so how do i export the kde colour scheme, i know its possible since you can get them from kde-look but i don't see any buttons to export it, only import

Thanks

---

### Post by mips on 2006-03-26
system settings->appearance->colors->save scheme button (above import scheme)

---

### Post by GeneralZod on 2006-03-26
A better solution is to have your /home on a separate partition, so *all* your personal settings for every app are left intact across re-installs.

---

### Post by ace2005 on 2006-03-26
[QUOTE=mips]system settings->appearance->colors->save scheme button (above import scheme)[/QUOTE]

Yea i know that but where is the .kcsrc file? thats what i want so i can take it with me

[QUOTE=GeneralZod]A better solution is to have your /home on a separate partition, so *all* your personal settings for every app are left intact across re-installs.[/QUOTE]

I like it to feel clean and new when i reinstall, having old config makes it seem messed up somehow, i always want to start from scratch with a reinstall.

---

### Post by eriefisher on 2006-03-26
How often do you reinstall and why?

eriefisher

---

### Post by ace2005 on 2006-03-26
Ok i feel silly, i did a search for kcsrc by typing "locate:*.kcsrc" into the konqueror address bar and i found this in ~/.kde/share/apps/kdisplay/color-schemes/

The reason i'm reinstalling is to install Red Flag Linux since it looks sooo cool and i can't find any info on how they got that look, thought i might as well try it.

Screenshot:
[http://www.kde-look.org/content/preview.php?preview=1&id=33966&file1=33966-1.jpg&file2=33966-2.jpg&file3=33966-3.jpg&name=Zhui+Preview](http://www.kde-look.org/content/preview.php?preview=1&id=33966&file1=33966-1.jpg&file2=33966-2.jpg&file3=33966-3.jpg&name=Zhui+Preview)

The download mirrior was very slow ~5kb/s and i had to download 4CDs so i hope its worth it, i won't be keeping it since its rpm based and i don't really trust the chinese government, who knows whats installed in there.

Edit: Now trying VMPlayer :D

---

### Post by ace2005 on 2006-03-26
[QUOTE=eriefisher]How often do you reinstall and why?

eriefisher[/QUOTE]

Well i reinstall if:

 * If i have any type of virus or adware (windows)
 * Every time i find a new distro or a new version of a distro i'm using comes out, i think kubuntu 5.10 is the only distro that has lasted longer than 3 months, it was installed about a week after it came out. I used to reinstall  fedora core all the time, since i kept installing RPMs by ignoring the deps.
 * Anything with KDE goes wrong, anything whatsoever, even the smallest thing
 * If i find a nicer distro looking distro (like Redflag)
 * If just about any problem comes up, that annoys me enough, like the time i extracted a lot of .deb files into the file system instead of using  aptget, since i can't find all the deps, but it works fine for some stuff like kplayer from debian marillat, kmplayer is the only one i do it with, its the best player i've found

I reinstall windows whenever a trial i'm using runs out that i need to use, i'm trying to make a disk image with everything installed, then i just have to install the trials. But i don't see the point any more since i rarely use windows, apart from to play games

All my documents stay on a 2GB Fat32 partition. so thats ok

---

### Post by mips on 2006-03-26
[QUOTE=GeneralZod]A better solution is to have your /home on a separate partition, so *all* your personal settings for every app are left intact across re-installs.[/QUOTE]

Yes, that is probably the best idea. I fail to see why people do not have a seperate partition for /home. I've taken it a step further and put the /home partition on a seperate drive.

---

### Post by ace2005 on 2006-03-26
Wouldn't everything mess up, like if i install a new distro which does not have the themes in the config files, like i use QTcurve now but a new distro won't have it installed but my configs use it so won't that cause problems?

I installed Red Flag Linux Workstation 5.0, kind of a waste of time, looked nothing like the screenshot ](*,)  :evil:

---

### Post by mips on 2006-03-27
[QUOTE=ace2005]Wouldn't everything mess up, like if i install a new distro which does not have the themes in the config files, like i use QTcurve now but a new distro won't have it installed but my configs use it so won't that cause problems?

I installed Red Flag Linux Workstation 5.0, kind of a waste of time, looked nothing like the screenshot ](*,)  :evil:[/QUOTE]

Yes quite possible. If you change distros you could always move the affected components like KDE into a subfolder called OSbackup or something like that. This way you could always move it back later when needed.

---

