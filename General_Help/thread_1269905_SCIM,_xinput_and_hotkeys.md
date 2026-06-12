---
title: "SCIM, xinput and hotkeys"
date: 2009-09-18
forum: General Help
---

### Post by renkinjutsu on 2009-09-18
I'm on an Ubuntu minimum install, and i have my own ~/.xinitrc file and ~/.xinput.d directory... and when i installed scim-bridge, it puts files into my /etc/X11/xinit/.xinput.d directory for the X input system.. but it doesn't work.. so i copy the files over to my ~/.xinput.d directory and it STILL doesn't work after logging out and and back in.. I've also tried changing the permissions and ownership of the files.. Nothing works! How do i make it work? The hotkeys don't trigger scim, instead, i have to right-click and select the input method.

any help?

---

### Post by Irihapeti on 2009-09-19
Someone else had what may be a similar issue in this thread:

[http://ubuntuforums.org/showthread.php?t=1267584](http://ubuntuforums.org/showthread.php?t=1267584)

I'm not sure how well it will work on a minimal install, but it's worth trying.

---

### Post by renkinjutsu on 2009-09-20
it doesn't work at all.. =[ even tried adding the commands into my .xinitrc

---

### Post by Irihapeti on 2009-09-20
Your system seems to be set up differently from mine. I don't have a .xinputrc file. However, those commands aren't meant to be in the .xinputrc file, so you can remove them.

Please run the following command and post its output:

```
locale | grep LANG
```

Also, please run the following command and post the output:

```
ls -l ~/.xinput.d/*_*
```

---

### Post by renkinjutsu on 2009-09-24
```
LANG=en_US.UTF-8
```
and 
```
lrwxrwxrwx 1 CENSOR CENSOR 32 2009-09-24 01:45 /home/CENSOR/.xinput.d/all_ALL -> /etc/alternatives/xinput-all_ALL
lrwxrwxrwx 1 CENSOR CENSOR 27 2009-09-24 01:45 /home/CENSOR/.xinput.d/en_US -> /home/CENSOR/.xinput.d/scim
lrwxrwxrwx 1 CENSOR CENSOR 27 2009-09-24 01:45 /home/CENSOR/.xinput.d/en_US.backup -> /home/CENSOR/.xinput.d/scim
lrwxrwxrwx 1 CENSOR CENSOR 30 2009-09-24 01:45 /home/CENSOR/.xinput.d/ja_JP -> /etc/alternatives/xinput-ja_JP
lrwxrwxrwx 1 CENSOR CENSOR 30 2009-09-24 01:45 /home/CENSOR/.xinput.d/ko_KR -> /etc/alternatives/xinput-ko_KR
lrwxrwxrwx 1 CENSOR CENSOR 30 2009-09-24 01:45 /home/CENSOR/.xinput.d/th_TH -> /etc/alternatives/xinput-th_TH
lrwxrwxrwx 1 CENSOR CENSOR 30 2009-09-24 01:45 /home/CENSOR/.xinput.d/zh_CN -> /etc/alternatives/xinput-zh_CN
lrwxrwxrwx 1 CENSOR CENSOR 30 2009-09-24 01:45 /home/CENSOR/.xinput.d/zh_HK -> /etc/alternatives/xinput-zh_HK
lrwxrwxrwx 1 CENSOR CENSOR 30 2009-09-24 01:45 /home/CENSOR/.xinput.d/zh_SG -> /etc/alternatives/xinput-zh_SG
lrwxrwxrwx 1 CENSOR CENSOR 30 2009-09-24 01:45 /home/CENSOR/.xinput.d/zh_TW -> /etc/alternatives/xinput-zh_TW
```

---

### Post by Irihapeti on 2009-09-24
It seems as though your system is linking to Scim directly, rather than Scim-bridge, which is probably why things aren't working properly.

I suggest first of all removing all scim-related files out of the .xinput.d directory. They may be causing some confusion.

Then re-create the en_US file by running the command
```
im-switch -z en_US.UTF-8 -s scim-bridge
```

This file should be a symlink to /etc/X11/xinit/xinput.d/scim-bridge

Then log out and in again and it should work.

---

### Post by renkinjutsu on 2009-09-24
no workee.. stopped X, logged out of all the consoles even and started X again.. nothing

---

### Post by Irihapeti on 2009-09-25
Scim can be horribly frustrating when things don't work like they should.

Could you run the command again:

```
ls -l ~/.xinput.d/*_*
```
and post the output. I have another idea but I want to see what's there first.

---

### Post by renkinjutsu on 2009-09-25
shows this now ```
lrwxrwxrwx 1 CENSOR CENSOR 35 2009-09-24 15:36 .xinput.d/en_US -> /etc/X11/xinit/xinput.d/scim-bridge
```

---

### Post by Irihapeti on 2009-09-25
That's what should be there. I don't understand why it isn't working.

Just to ask a possibly stupid question: you do have scim-bridge-client-gtk installed? And if you are trying to use QT applications, you have installed scim-bridge-client-qt(4)?

---

### Post by renkinjutsu on 2009-09-25
installing scim by itself installed both clients

but i thought scim would replace X input method and work on all applications?

---

### Post by Irihapeti on 2009-09-25
> **renkinjutsu said:**
> installing scim by itself installed both clients

but i thought scim would replace X input method and work on all applications?

That's what is supposed to happen. I don't know why it isn't.

Last-ditch effort before I concede defeat:

Do some hand-editing of /etc/X11/xinit/xinput.d/default
so that it reads (I'm leaving some pieces out to save space):

```
XIM=SCIM
XIM_PROGRAM=scim-bridge
XIM_ARGS=" -d"

GTK_IM_MODULE=scim-bridge
QT_IM_MODULE=scim-bridge
```

Then log out and in again.

On my system, I have made these changes and removed the .xinput directory altogether and scim works.

If it doesn't work, I can only guess that there's some other stuff somewhere in your system that's conflicting with Scim. Or else that there's a bug.

---

### Post by renkinjutsu on 2009-10-04
sorry, no idea you responded in my thread

i tried it, and it didn't work.. i'll just wait a bit until karmic

---

### Post by Irihapeti on 2009-10-04
Sounds like a good idea, especially as karmic is only a bit over three weeks away. Scim can be rather difficult to debug when it doesn't respond to the obvious things.

---

### Post by Bluebris on 2009-10-13
> **renkinjutsu said:**
> sorry, no idea you responded in my thread

i tried it, and it didn't work.. i'll just wait a bit until karmic

  Then i hope it works in the final karmic, because although mine worked fine in jaunty (don't ask how, i just followed some internet thread a long time ago) it doesn't work at all in the beta karmic...

---

