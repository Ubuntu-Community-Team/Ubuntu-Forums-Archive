---
title: "Newby install problem with PikLab"
date: 2011-08-27
forum: General Help
---

### Post by g0mgx on 2011-08-27
Hi Guys

New to the forum and to Linux in general! I've installed Ubuntu 11.4 and have been trying to get the PIC microcontroller development environment PikLab installed. 

I followed these instructions to the letter:

[http://ubuntuforums.org/showthread.php?t=123481](http://ubuntuforums.org/showthread.php?t=123481)

but have found that when I issue the "PikLab" command as the last instruction I get:

piklab: error while loading shared libraries: libpcreposix.so.0: cannot open shared object file: No such file or directory

the installation instructions includes a reply from someone with the same issue and the solution is this:

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libktexteditor&searchmode=searchword&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libktexteditor&searchmode=searchword&case=insensitive&version=breezy&arch=i386)

but that link is returning no results for me.

Can anyone help as I don't confess to understand symbolic links or the error I am seeing.

Very grateful for any assistance...

Thanks.

Mark.

---

### Post by fouadatmeh on 2011-11-05
Hello,

I think this answer comes too late, but it might still help someone out there :)
I have successfully installed it in 11.04 & 11.10 according to the following tutorials:
- 11.04:
[http://sourceforge.net/projects/piklab/forums/forum/633023/topic/4020117?message=9053167](http://sourceforge.net/projects/piklab/forums/forum/633023/topic/4020117?message=9053167)

- 11.10:
[https://thebitbangtheory.wordpress.com/2011/10/27/how-to-setup-a-pic-microcontroller-development-environment-in-ubuntu-11-10-oneiric-ocelot-with-piklab-sdcc/](https://thebitbangtheory.wordpress.com/2011/10/27/how-to-setup-a-pic-microcontroller-development-environment-in-ubuntu-11-10-oneiric-ocelot-with-piklab-sdcc/)

---

