---
title: "need to be root for everything to be done!!!!!!!!!!!"
date: 2010-05-15
forum: General Help
---

### Post by ankit singh on 2010-05-15
i have a fresh install of lucid and i have a lot of issues with it
after initial days of dealing with hardware issues, now its with software.few softwares for eg. pitivi if ran normally would not edit a single video.Instead it closes immediately. But when i run through root, it works. other software in this category are 

1)arista transcoder
2)netbeans6.8
3)play on linux
4)multiget

and there maybe many more such softwares which might not work.
as u can see frm above that it boils to enter root password for everything to work.

Pls help to sort out this.

---

### Post by camdude on 2010-05-15
well, i have to disagree with you on your comments on the new release of Ubuntu. However, I know what your problem is, so I'll help you.
First, go to System>Administration>Users and Groups
Select your account, and next to account type, click change. You'll need to type in your password, than choose administrator, and save. Next click Groups in the Users and Groups window, and find, and select root and click properties. There will be a group members radio box list, and check your user name. You will now be able to run programs without having to sudo them. I had this problem in 8.10, and 9.04... but not 10.04

---

### Post by ankit singh on 2010-05-15
i have done all that things before.

---

### Post by lavinog on 2010-05-15
How were you running the applications as root?
Some gui apps if ran from root will change the ownership of files in your home to root.

see if this command displays anything:
```

find ~ -xdev -user root

```

---

### Post by ankit singh on 2010-05-15
[HTML][/HTML]ankit@ankit-desktop:~$ find ~ -xdev -user root
/home/ankit/.MultiGet/single.lock
/home/ankit/.MultiGet/cmdline.pipe
/home/ankit/pitivi-0.13.4/icons/scalable/Makefile
/home/ankit/pitivi-0.13.4/icons/24x24/Makefile
/home/ankit/pitivi-0.13.4/icons/Makefile
/home/ankit/pitivi-0.13.4/icons/16x16/Makefile
/home/ankit/pitivi-0.13.4/icons/22x22/Makefile
/home/ankit/pitivi-0.13.4/icons/48x48/Makefile
/home/ankit/pitivi-0.13.4/icons/32x32/Makefile
/home/ankit/pitivi-0.13.4/config.status
/home/ankit/pitivi-0.13.4/pitivi.desktop.in
/home/ankit/pitivi-0.13.4/locale
/home/ankit/pitivi-0.13.4/locale/zh_HK
/home/ankit/pitivi-0.13.4/locale/zh_HK/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/zh_HK/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/pt_BR
/home/ankit/pitivi-0.13.4/locale/pt_BR/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/pt_BR/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/gu
/home/ankit/pitivi-0.13.4/locale/gu/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/gu/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/gl
/home/ankit/pitivi-0.13.4/locale/gl/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/gl/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/sv
/home/ankit/pitivi-0.13.4/locale/sv/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/sv/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/nb
/home/ankit/pitivi-0.13.4/locale/nb/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/nb/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/fr
/home/ankit/pitivi-0.13.4/locale/fr/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/fr/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/ast
/home/ankit/pitivi-0.13.4/locale/ast/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/ast/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/it
/home/ankit/pitivi-0.13.4/locale/it/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/it/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/pl
/home/ankit/pitivi-0.13.4/locale/pl/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/pl/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/zh_TW
/home/ankit/pitivi-0.13.4/locale/zh_TW/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/zh_TW/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/fi
/home/ankit/pitivi-0.13.4/locale/fi/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/fi/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/cs
/home/ankit/pitivi-0.13.4/locale/cs/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/cs/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/bg
/home/ankit/pitivi-0.13.4/locale/bg/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/bg/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/pt
/home/ankit/pitivi-0.13.4/locale/pt/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/pt/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/oc
/home/ankit/pitivi-0.13.4/locale/oc/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/oc/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/sl
/home/ankit/pitivi-0.13.4/locale/sl/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/sl/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/en_GB
/home/ankit/pitivi-0.13.4/locale/en_GB/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/en_GB/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/lv
/home/ankit/pitivi-0.13.4/locale/lv/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/lv/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/el
/home/ankit/pitivi-0.13.4/locale/el/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/el/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/nl
/home/ankit/pitivi-0.13.4/locale/nl/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/nl/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/dz
/home/ankit/pitivi-0.13.4/locale/dz/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/dz/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/ca
/home/ankit/pitivi-0.13.4/locale/ca/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/ca/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/zh_CN
/home/ankit/pitivi-0.13.4/locale/zh_CN/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/zh_CN/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/pa
/home/ankit/pitivi-0.13.4/locale/pa/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/pa/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/ro
/home/ankit/pitivi-0.13.4/locale/ro/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/ro/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/da
/home/ankit/pitivi-0.13.4/locale/da/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/da/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/ru
/home/ankit/pitivi-0.13.4/locale/ru/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/ru/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/ar
/home/ankit/pitivi-0.13.4/locale/ar/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/ar/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/mr
/home/ankit/pitivi-0.13.4/locale/mr/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/mr/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/hu
/home/ankit/pitivi-0.13.4/locale/hu/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/hu/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/de
/home/ankit/pitivi-0.13.4/locale/de/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/de/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/locale/es
/home/ankit/pitivi-0.13.4/locale/es/LC_MESSAGES
/home/ankit/pitivi-0.13.4/locale/es/LC_MESSAGES/pitivi.mo
/home/ankit/pitivi-0.13.4/pitivi.spec
/home/ankit/pitivi-0.13.4/common/Makefile
/home/ankit/pitivi-0.13.4/common/m4/Makefile
/home/ankit/pitivi-0.13.4/pitivi.desktop
/home/ankit/pitivi-0.13.4/tests/Makefile
/home/ankit/pitivi-0.13.4/Makefile
/home/ankit/pitivi-0.13.4/bin/Makefile
/home/ankit/pitivi-0.13.4/bin/pitivi
/home/ankit/pitivi-0.13.4/pitivi/pixmaps/Makefile
/home/ankit/pitivi-0.13.4/pitivi/timeline/Makefile
/home/ankit/pitivi-0.13.4/pitivi/configure.py
/home/ankit/pitivi-0.13.4/pitivi/log/Makefile
/home/ankit/pitivi-0.13.4/pitivi/Makefile
/home/ankit/pitivi-0.13.4/pitivi/formatters/Makefile
/home/ankit/pitivi-0.13.4/pitivi/factories/Makefile
/home/ankit/pitivi-0.13.4/pitivi/elements/Makefile
/home/ankit/pitivi-0.13.4/pitivi/ui/Makefile
/home/ankit/pitivi-0.13.4/config.log
/home/ankit/pitivi-0.13.4/po/gl.gmo
/home/ankit/pitivi-0.13.4/po/ar.gmo
/home/ankit/pitivi-0.13.4/po/el.gmo
/home/ankit/pitivi-0.13.4/po/ca.gmo
/home/ankit/pitivi-0.13.4/po/POTFILES
/home/ankit/pitivi-0.13.4/po/fi.gmo
/home/ankit/pitivi-0.13.4/po/de.gmo
/home/ankit/pitivi-0.13.4/po/zh_CN.gmo
/home/ankit/pitivi-0.13.4/po/sl.gmo
/home/ankit/pitivi-0.13.4/po/ast.gmo
/home/ankit/pitivi-0.13.4/po/pt.gmo
/home/ankit/pitivi-0.13.4/po/pl.gmo
/home/ankit/pitivi-0.13.4/po/da.gmo
/home/ankit/pitivi-0.13.4/po/bg.gmo
/home/ankit/pitivi-0.13.4/po/pt_BR.gmo
/home/ankit/pitivi-0.13.4/po/gu.gmo
/home/ankit/pitivi-0.13.4/po/zh_HK.gmo
/home/ankit/pitivi-0.13.4/po/Makefile
/home/ankit/pitivi-0.13.4/po/Makefile.in
/home/ankit/pitivi-0.13.4/po/mr.gmo
/home/ankit/pitivi-0.13.4/po/es.gmo
/home/ankit/pitivi-0.13.4/po/.intltool-merge-cache
/home/ankit/pitivi-0.13.4/po/en_GB.gmo
/home/ankit/pitivi-0.13.4/po/ru.gmo
/home/ankit/pitivi-0.13.4/po/sv.gmo
/home/ankit/pitivi-0.13.4/po/pa.gmo
/home/ankit/pitivi-0.13.4/po/stamp-it
/home/ankit/pitivi-0.13.4/po/lv.gmo
/home/ankit/pitivi-0.13.4/po/nl.gmo
/home/ankit/pitivi-0.13.4/po/dz.gmo
/home/ankit/pitivi-0.13.4/po/fr.gmo
/home/ankit/pitivi-0.13.4/po/cs.gmo
/home/ankit/pitivi-0.13.4/po/oc.gmo
/home/ankit/pitivi-0.13.4/po/ro.gmo
/home/ankit/pitivi-0.13.4/po/it.gmo
/home/ankit/pitivi-0.13.4/po/nb.gmo
/home/ankit/pitivi-0.13.4/po/hu.gmo
/home/ankit/pitivi-0.13.4/po/zh_TW.gmo
/home/ankit/Downloads/openal-soft-1.12.854/Makefile
/home/ankit/Downloads/openal-soft-1.12.854/install_manifest.txt
/home/ankit/Downloads/openal-soft-1.12.854/CMakeFiles/openal-info.dir/progress.make
/home/ankit/Downloads/openal-soft-1.12.854/CMakeFiles/openal.dir/progress.make
/home/ankit/Downloads/openal-soft-1.12.854/CMakeFiles/TargetDirectories.txt
/home/ankit/Downloads/openal-soft-1.12.854/CMakeFiles/progress.marks
/home/ankit/Downloads/openal-soft-1.12.854/CMakeFiles/Makefile.cmake
/home/ankit/Downloads/openal-soft-1.12.854/CMakeFiles/Makefile2
/home/ankit/pitivi.desktop
/home/ankit/untitled folder/pitivi-0.13.4/icons/scalable/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/icons/24x24/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/icons/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/icons/16x16/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/icons/22x22/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/icons/48x48/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/icons/32x32/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/pitivi.desktop.in
/home/ankit/untitled folder/pitivi-0.13.4/locale/zh_HK/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/pt_BR/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/gu/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/gl/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/sv/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/nb/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/fr/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/ast/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/it/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/pl/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/zh_TW/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/fi/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/cs/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/bg/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/pt/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/oc/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/sl/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/en_GB/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/lv/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/el/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/nl/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/dz/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/ca/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/zh_CN/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/pa/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/ro/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/da/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/ru/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/ar/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/mr/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/hu/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/de/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/locale/es/LC_MESSAGES/pitivi.mo
/home/ankit/untitled folder/pitivi-0.13.4/pitivi.spec
/home/ankit/untitled folder/pitivi-0.13.4/common/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/common/m4/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/tests/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/bin/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/bin/pitivi
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/pixmaps/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/timeline/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/configure.py
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/log/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/formatters/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/factories/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/elements/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/pitivi/ui/Makefile
/home/ankit/untitled folder/pitivi-0.13.4/po/POTFILES
/home/ankit/untitled folder/pitivi-0.13.4/po/Makefile.in
/home/ankit/untitled folder/pitivi-0.13.4/po/stamp-it
[HTML][/HTML]


as u can see i even compiled pitivi from source and then installed it,but still then it refuses to work.

---

### Post by ALIENDUDE5300 on 2010-05-15
> **ankit singh said:**
> [HTML][/HTML]ankit@ankit-desktop:~$ find ~ -xdev -user root
/snip/

as u can see i even compiled pitivi from source and then installed it,but still then it refuses to work.

The problem is that all those files belong to root, so you can't modify them. Use chown to change the file permissions, and it will work properly.

---

### Post by jerome1232 on 2010-05-15
aka

```
sudo chown -R $USER:$USER ~/*
```

---

### Post by ALIENDUDE5300 on 2010-05-15
> **jerome1232 said:**
> aka

```
sudo chown -R $USER:$USER ~/*
```

Thanks! I should've probably clarified that, but I see you did it for me. :)

---

### Post by srs5694 on 2010-05-15
> **jerome1232 said:**
> aka

```
sudo chown -R $USER:$USER ~/*
```

Just be *very very sure* to include that tilde ("~") before the slash ("/"), and do *not* include a space between them. If you omit the tilde, that command will give ownership of everything on the system to your normal user, which will break at least some things, maybe a lot of things. (I'm not crazy enough to try it to find out how bad it would be.)

---

### Post by jerome1232 on 2010-05-15
I didn't even think about that, just copy and paste the command so your sure not to make an error.

---

### Post by ankit singh on 2010-05-15
no,nothing happened.its still closing

---

### Post by lavinog on 2010-05-15
run it from a terminal and post the message it gives.

---

### Post by ankit singh on 2010-05-16
> 
ankit@ankit-desktop:~$ sudo chown -R $USER:$USER ~/*
ankit@ankit-desktop:~$ 


i don know whether to replace  USER with my user name .i just copied it .

---

### Post by Oasu4g on 2010-05-16
No, I don't believe you should replace anything. Just copy and paste it like jerome1232 said. 

Run pitivi from the terminal, by typing:

```
pitivi
```

And hitting enter. Give us the output from the terminal after the program crashes.

---

### Post by ankit singh on 2010-05-16
> 
ankit@ankit-desktop:~$ pitivi

progname=pitivi; RGBA=on


program  runs but when a video is played the entire window collapses (shuts down)

and then in the terminal the following message is displayed

> 
The program 'pitivi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 58 error_code 8 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
however why this same thing don appear when run as root?
also this is the same error i get while running other programs.

---

### Post by 3rdalbum on 2010-05-16
When I started reading this thread, I thought "I'll ask him if he's got RGBA turned on".

You do.

Pitivi doesn't work with RGBA - you'll need to add it to your RGBA blacklist in ~/.profile.  You can tell when a program has crashed because of RGBA incompatibility, because the terminal prints a message similar to what you've seen.

RGBA works on a user-by-user basis, so running a program as root will mean that RGBA doesn't get applied to it, and therefore it won't crash.

Hey, there's a reason why official RGBA in Ubuntu has been delayed until 10.10. Some programs just don't work with it.

---

### Post by ankit singh on 2010-05-16
(slaps forehead)
Thanks i didnt thought of that
i removed the rgba-module (i thought removing it is better because every new program crashed)

thanks again :guitar:

---

