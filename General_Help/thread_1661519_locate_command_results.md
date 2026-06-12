---
title: "locate command results"
date: 2011-01-06
forum: General Help
---

### Post by HotForLinux on 2011-01-06
I am using the locate command and I have just realized that it gives me many very different results depending on the working directory from where I issue the same command.

This happens, at least, with:

*$ locate *\.*\.* *

S[FONT="Fixedsys"][/FONT]houldn't the results of every search be independent on the working directory?

---

### Post by micael3000 on 2011-01-06
--removed--

---

### Post by MaxIBoy on 2011-01-06
Locate does not care about the current directory:
```
maxtothemax@maxtothemax-mint ~/Desktop $ ls
maxtothemax@maxtothemax-mint ~/Desktop $ locate Makefile
/debian-boot/usr/share/doc/netcat-traditional/examples/data/Makefile
/debian-boot/usr/share/groff/1.20.1/font/devps/generate/Makefile
/etc/dkms/template-dkms-mkdeb/Makefile
/home/maxtothemax/.fr-QDOQrz/remove-duplicates-plugin-0.0.4/src/Makefile.am
/home/maxtothemax/.fr-QDOQrz/remove-duplicates-plugin-0.0.4/src/Makefile.in
/home/maxtothemax/.gegl-0.0/plug-ins/Makefile
/home/maxtothemax/alienarena/Makefile
/home/maxtothemax/alienarena/Makefile.am
/home/maxtothemax/alienarena/Makefile.in
/home/maxtothemax/alienarena/.svn/text-base/Makefile.am.svn-base
/home/maxtothemax/alienarena/.svn/text-base/Makefile.in.svn-base
/home/maxtothemax/alienarena/Tools/FUSE/Makefile
/home/maxtothemax/alienarena/Tools/FUSE/.svn/text-base/Makefile.svn-base
/home/maxtothemax/alienarena/Tools/utils3/Makefile
/home/maxtothemax/alienarena/Tools/utils3/.svn/text-base/Makefile.svn-base
<many many more lines follow but you get the idea...>
```

However, the command line glob match (i.e. the * wildcard) doesn't work the way you think it does. For example: ```
maxtothemax@maxtothemax-mint ~/Videos $ echo *.flv
169_cheaperbythedozen_freegames_vf_111708_700.flv 1 v 5 Warsow Clutch.flv cows _amp; cows _amp; cows.flv Eddie Izzard - Wikipedia and Terms and Conditions.flv First Contact - Warsow Frag Movie.flv Pure Motion.flv SOUND EFFECT DERANGED WOMAN SCREAM.flv The Website Is Down - Sales Guy vs. Web Dude.flv Video explains the world_s most important 6-sec drum loop.flv Warsow Movement School #0 with mote.flv Warsow Movement School #1 with mote.flv
maxtothemax@maxtothemax-mint ~/Videos $ 

```

To fix this, put your search term in quotes and it will behave the way you want it to.

---

### Post by HotForLinux on 2011-01-06
> **MaxIBoy said:**
>  ......
To fix this, put your search term in quotes and it will behave the way you want it to.

Sorry, You are right. I have just realized that if I issue the command with the search pattern in quotes, like:

[FONT="Fixedsys"]locate '*\.*\.*'[/FONT]

then all the results are correct, regardless on the working directory. Without the quotes, for x reason, I was receiving (correct but) partial and very different results from each other. Thanks.

IMHO you should receive a syntax error before an incorrect and misleading result.

---

