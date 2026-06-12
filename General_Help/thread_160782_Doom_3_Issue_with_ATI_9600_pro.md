---
title: "Doom 3 Issue with ATI 9600 pro"
date: 2006-04-15
forum: General Help
---

### Post by lemix on 2006-04-15
I am trying to install doom 3 on my ubuntu machine. I have the latest fglrx drivers. My fglrxinfo displays...
> lemix@lemix:~/doom3$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

Looks fine to me.!.

Here are the steps that i took to install doom...
-Copied pk files from base directory off the cds 00 thru 04 and the game.pk
-got doom3-linux-1.3.1302.x86.run from ID's website
Extracted it into my /home/doom3 folder

Running 
> lemix@lemix:~/doom3$ sh doom3

I get the following error...
> DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 192.168.1.100/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/lemix/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /home/lemix/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /home/lemix/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /home/lemix/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/lemix/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/lemix/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/lemix/.doom3/base
/home/lemix/doom3/base
/home/lemix/doom3/base/pak007.pk4 (38 files)
/home/lemix/doom3/base/pak006.pk4 (48 files)
/home/lemix/doom3/base/pak005.pk4 (63 files)
/home/lemix/doom3/base/game03.pk4 (2 files)
/home/lemix/doom3/base/game02.pk4 (2 files)
/home/lemix/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

Any Solutions??

P.S. i know that ATI Graphics Cards Suck. ](*,)

---

### Post by Ensnared on 2006-04-15
A quick google-search for the error-message shows that this might be the result of wrong permissions on directories or files. So try this:
```
sudo chown lemix.lemix /home/lemix/doom3 -R
```
This will make the directory and everything in it owned by user lemix and group lemix (which I'm assuming is your username based on the messages you posted).

---

### Post by ubernoob on 2006-04-16
> sudo chown lemix.lemix /home/lemix/doom3 -R
It sould be:
sudo chown lemix**:**lemix /home/lemix/doom3 -R

It is probably caused when you copyed the *.pk4 files, you might have used root instead of user.

---

### Post by whatever on 2006-04-16
[QUOTE=lemix]I have the latest fglrx drivers.[/QUOTE]
no, you don't.
8.16.20 is quite old

edit:
and the reason for doom3 not starting is probably that you forgot to copy game00.pk4

---

### Post by _simon_ on 2006-04-16
You need to check what you have in your base directory.

When I boot Doom 3 I get:

```

Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/simon/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)

```

---

### Post by Ensnared on 2006-04-16
[QUOTE=ubernoob]It sould be:
sudo chown lemix**:**lemix /home/lemix/doom3 -R[/QUOTE]
Apparently so, but user.group also works. I've been using that for a decade but apparently this has been changed some time during that period. Good thing they maintain backwards compatibility ;)

---

### Post by ubernoob on 2006-04-16
you are right. that worked. :) and here i was thinking it was a typo:roll:

---

### Post by lemix on 2006-06-01
My Graphics Accel was fine.

I just didnt copy the first files i copied to my hard drive into the base folder that was created.

Now if i could just fix that sound problem.
Im currently reading over LinuxForums for the answer. There are several method's discussed.

Thx everyone for help on this thread.

---

