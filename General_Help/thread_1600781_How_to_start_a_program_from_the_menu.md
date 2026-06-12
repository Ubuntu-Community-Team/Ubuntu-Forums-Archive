---
title: "How to start a program from the menu ?"
date: 2010-10-19
forum: General Help
---

### Post by andlinux on 2010-10-19
I have downloaded the linux version of Rise of the Triad and I'm able to start this program if I double click it (Files.png) but I want an entry in the menu so that I can start it from the menu, but what's the command to start it from the menu ?

I already tried ./ and sh in front of the command but it doesn't work (menu.jpg).

See the pictures...

---

### Post by yetiman64 on 2010-10-19
> **andlinux said:**
> I have downloaded the linux version of Rise of the Triad and I'm able to start this program if I double click it (Files.png) but I want an entry in the menu so that I can start it from the menu, but what's the command to start it from the menu ?

I already tried ./ and sh in front of the command but it doesn't work (menu.jpg).

See the pictures...

As you can start the program by double clicking I suggest you add the folder it is in to your system path. Open the hidden file in your home directory called .profile and at the bottom add the line,
> export PATH=$PATH:$HOME/Games/rott-1.1.1 In the line for command just insert the command "rott"(without the quotes). Log out and login to make the change set in .profile. When you log back in you can, in a terminal, check the system path with,```
echo $PATH
```You should now be able to create and use a menu entry with just "rott" (without the quotes) in the command line.

---

### Post by andlinux on 2010-10-20
> **yetiman64 said:**
> As you can start the program by double clicking I suggest you add the folder it is in to your system path. Open the hidden file in your home directory called .profile and at the bottom add the line,
 In the line for command just insert the command "rott"(without the quotes). Log out and login to make the change set in .profile. When you log back in you can, in a terminal, check the system path with,```
echo $PATH
```You should now be able to create and use a menu entry with just "rott" (without the quotes) in the command line.
I did what you wrote but then it gives me an error.

Here's a raw translation (dutch to english) of the error:

Can't execute Rise of the Triad.
Execution of subprocess 'rott' 
failed.
(Access Denied)

---

### Post by yetiman64 on 2010-10-20
> **andlinux said:**
> I did what you wrote but then it gives me an error.

Here's a raw translation (dutch to english) of the error:

Can't execute Rise of the Triad.
Execution of subprocess 'rott' 
failed.
[COLOR=Blue](Access Denied)[/COLOR]
This sounds like a ownership/permissions problem, check the ownership and permissions of the folders in the path and the executable rott (as well as all the files in with it, in case it relies on another file to be useable). You can check this by right clicking on a file or folder and choose properties > permissions tab.

You should own all the files and folders including subfolders in your home directory and the files should be read, write and executable for yourself and at least readable to group and others (you could make them executable as well if you wish).

If any are owned by root you will not be able to change them without using the terminal and the chown and / or chmod commands.

---

### Post by andlinux on 2010-10-21
> **yetiman64 said:**
> This sounds like a ownership/permissions problem, check the ownership and permissions of the folders in the path and the executable rott (as well as all the files in with it, in case it relies on another file to be useable). You can check this by right clicking on a file or folder and choose properties > permissions tab.

You should own all the files and folders including subfolders in your home directory and the files should be read, write and executable for yourself and at least readable to group and others (you could make them executable as well if you wish).

If any are owned by root you will not be able to change them without using the terminal and the chown and / or chmod commands.

I did chmod 777 for the directory and the subdirectory and it's still not working when I want to start it in the menu...

---

### Post by yetiman64 on 2010-10-21
> **andlinux said:**
> I did chmod 777 for the directory and the subdirectory and it's still not working when I want to start it in the menu...

Ok that a bit of a puzzle then, could you post the output of the commands
```
echo $PATH
```and ```
cat ~/.profile | tail -n 5
```and ```
cd ~/Games/rott-1.1.1 && ls -l && cd
``` **and another screenshot of the properties of the launcher created** here for checking? This should cover any possible problems for you.

Note that paths as well as the terminal are case sensitive and "$PATH:$HOME/[COLOR=Blue]Games[/COLOR]/rott-1.1.1" is not the same as "$PATH:$HOME/[COLOR=Blue]games[/COLOR]/rott-1.1.1".

Note that I use this method here myself and can launch scripts or other executables in non standard path folders by this method. I have a feeling it is only something very minor & easily adjusted that is blocking it from working for you.

---

### Post by andlinux on 2010-10-23
> **yetiman64 said:**
> Ok that a bit of a puzzle then, could you post the output of the commands
```
echo $PATH
```and ```
cat ~/.profile | tail -n 5
```and ```
cd ~/Games/rott-1.1.1 && ls -l && cd
``` **and another screenshot of the properties of the launcher created** here for checking? This should cover any possible problems for you.

Note that paths as well as the terminal are case sensitive and "$PATH:$HOME/[COLOR=Blue]Games[/COLOR]/rott-1.1.1" is not the same as "$PATH:$HOME/[COLOR=Blue]games[/COLOR]/rott-1.1.1".

Note that I use this method here myself and can launch scripts or other executables in non standard path folders by this method. I have a feeling it is only something very minor & easily adjusted that is blocking it from working for you.

```
andy@ubuntu-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/andy/Games/rott-1.1.1
```

```
cat ~/.profile | tail -n 5
    PATH="$HOME/bin:$PATH"
fi


export PATH=$PATH:$HOME/Games/rott-1.1.1 
```

```
cd ~/Games/rott-1.1.1 && ls -l && cd
totaal 52
-rw-r--r-- 1 andy andy 18011 2008-06-18 20:24 COPYING
drwxr-xr-x 2 andy andy  4096 2009-06-26 14:34 doc
drwxr-xr-x 4 andy andy  4096 2009-06-26 14:34 mac
drwxr-xr-x 2 andy andy  4096 2009-06-26 14:34 misc
-rw-r--r-- 1 andy andy  3662 2009-06-26 14:28 README
drwxrwxrwx 3 andy andy 12288 2010-01-23 13:07 rott
drwxr-xr-x 2 andy andy  4096 2009-06-26 14:34 vs.net

```

:)

---

### Post by yetiman64 on 2010-10-23
Does "Toepassing", mean "Application" or "Application in Terminal" or "Location"? 

You should have it set as the equivalent of "Application".

[s]The rest of that looks perfectly OK[/s]. [COLOR=Blue](see post 10 it's not OK)[/COLOR]

Edit: just "Google translated" it [s]and now I'm stumped as to why it won't work for you[/s].

---

### Post by matt_symes on 2010-10-23
Hi

> 
drwxrwxrwx 3 andy andy 12288 2010-01-23 13:07 rott


Drwxrwxrwx <- D

rott is a directory and not a file.

Kind regards

---

### Post by yetiman64 on 2010-10-23
> **matt_symes said:**
> Hi



Drwxrwxrwx <- D

rott is a directory and not a file.

Kind regards

Good pick up on that, thank you, was seeing that as the executable because of the pics. Cheers.

@ OP can you post back the output of,
```
cd ~/Games/rott-1.1.1/rott && ls -la && cd 
```You will have to alter the .profile file in your home directory to,
> export PATH=$PATH:$HOME/Games/rott-1.1.1/rott _*then logout and log back in*_. May need to do some more alterations but need to see the output of the command 1st

Thanks matt_symes :)

---

### Post by andlinux on 2010-10-23
> **yetiman64 said:**
> Good pick up on that, thank you, was seeing that as the executable because of the pics. Cheers.

@ OP can you post back the output of,
```
cd ~/Games/rott-1.1.1/rott && ls -la && cd 
```You will have to alter the .profile file in your home directory to,
_*then logout and log back in*_. May need to do some more alterations but need to see the output of the command 1st

Thanks matt_symes :)

Here is the output:

```
andy@ubuntu-laptop:~$ cd ~/Games/rott-1.1.1/rott && ls -la && cd 
totaal 24612
drwxrwxrwx 3 andy andy    12288 2010-01-23 13:07 .
drwxr-xr-x 7 andy andy     4096 2009-06-26 14:34 ..
drwxr-xr-x 2 andy andy     4096 2010-01-23 13:04 audiolib
-rw-rw-rw- 1 andy andy     2239 2008-05-24 08:34 byteordr.c
-rw-rw-rw- 1 andy andy     1357 2008-05-24 08:34 byteordr.h
-rw-rw-rw- 1 andy andy    12096 2010-01-23 13:04 byteordr.o
-rw-rw-rw- 1 andy andy     6007 2002-12-20 21:15 cin_actr.c
-rw-rw-rw- 1 andy andy     1268 2002-12-20 21:15 cin_actr.h
-rw-rw-rw- 1 andy andy    11784 2010-01-23 13:04 cin_actr.o
-rw-rw-rw- 1 andy andy     2116 2002-12-20 21:15 cin_def.h
-rw-rw-rw- 1 andy andy    19137 2008-05-24 08:34 cin_efct.c
-rw-rw-rw- 1 andy andy     2807 2002-12-20 21:15 cin_efct.h
-rw-rw-rw- 1 andy andy    31680 2010-01-23 13:04 cin_efct.o
-rw-rw-rw- 1 andy andy     9637 2002-12-24 05:44 cin_evnt.c
-rw-rw-rw- 1 andy andy     1216 2002-12-20 21:15 cin_evnt.h
-rw-rw-rw- 1 andy andy    21240 2010-01-23 13:04 cin_evnt.o
-rw-rw-rw- 1 andy andy     1054 2002-12-22 06:17 cin_glob.c
-rw-rw-rw- 1 andy andy     1030 2003-02-14 06:51 cin_glob.h
-rw-rw-rw- 1 andy andy     4920 2010-01-23 13:04 cin_glob.o
-rw-rw-rw- 1 andy andy     4777 2008-05-24 08:29 cin_main.c
-rw-rw-rw- 1 andy andy     1164 2002-12-20 21:15 cin_main.h
-rw-rw-rw- 1 andy andy    14176 2010-01-23 13:04 cin_main.o
-rw-rw-rw- 1 andy andy     1364 2002-12-21 02:57 cin_util.c
-rw-rw-rw- 1 andy andy      869 2002-12-20 21:15 cin_util.h
-rw-rw-rw- 1 andy andy     4000 2010-01-23 13:04 cin_util.o
-rwxrwxrwx 1 andy andy   162646 1995-02-15 12:20 DARKWAR.RTC
-rwxrwxrwx 1 andy andy   408100 1995-02-15 12:20 DARKWAR.RTL
-rwxrwxrwx 1 andy andy 14610173 1995-02-15 12:20 DARKWAR.WAD
-rw-rw-rw- 1 andy andy     1840 2010-01-23 13:01 develop.h
-rw-rw-rw- 1 andy andy     1840 2008-05-24 08:29 develop.h~
-rw-rw-rw- 1 andy andy     6072 2009-03-30 10:25 dosutil.c
-rw-rw-rw- 1 andy andy    18544 2010-01-23 13:04 dosutil.o
-rw-rw-rw- 1 andy andy    11909 2003-07-11 03:11 dukemusc.c
-rw-rw-rw- 1 andy andy    30928 2010-01-23 13:04 dukemusc.o
-rw-rw-rw- 1 andy andy    10843 2008-05-24 08:29 engine.c
-rw-rw-rw- 1 andy andy      993 2002-12-20 21:15 _engine.h
-rw-rw-rw- 1 andy andy     1435 2008-05-24 08:29 engine.h
-rw-rw-rw- 1 andy andy    22432 2010-01-23 13:04 engine.o
-rw-rw-rw- 1 andy andy     3621 2002-12-20 22:12 fli_def.h
-rw-rw-rw- 1 andy andy      811 2002-12-20 21:15 fli_glob.h
-rw-rw-rw- 1 andy andy    13552 2002-12-20 21:15 fli_main.c
-rw-rw-rw- 1 andy andy     2998 2002-12-20 21:15 fli_main.h
-rw-rw-rw- 1 andy andy     1851 2008-05-24 08:26 fli_type.h
-rw-rw-rw- 1 andy andy    10216 2002-12-20 21:15 fli_util.c
-rw-rw-rw- 1 andy andy     4556 2002-12-20 21:15 fli_util.h
-rw-rw-rw- 1 andy andy     1220 2002-12-24 04:51 f_scale.h
-rw-rw-rw- 1 andy andy    33447 2008-05-24 08:34 fx_man.c
-rw-rw-rw- 1 andy andy     4423 2008-05-24 08:34 fx_man.h
-rw-rw-rw- 1 andy andy      787 2002-12-20 21:15 gmove.h
-rw-rw-rw- 1 andy andy    16415 2008-05-24 08:29 isr.c
-rw-rw-rw- 1 andy andy     1040 2002-12-20 21:15 _isr.h
-rw-rw-rw- 1 andy andy     2682 2002-12-29 23:29 isr.h
-rw-rw-rw- 1 andy andy    12200 2010-01-23 13:04 isr.o
-rw-rw-rw- 1 andy andy     2590 2002-12-20 21:15 keyb.h
-rw-rw-rw- 1 andy andy     4890 2008-05-24 08:29 lookups.c
-rw-rw-rw- 1 andy andy     4642 2002-12-24 11:18 lumpy.h
-rw-rw-rw- 1 andy andy     2617 2009-03-30 10:35 Makefile
-rw-rw-rw- 1 andy andy       25 2002-12-20 22:12 memcheck.h
-rw-rw-rw- 1 andy andy    15035 2008-05-24 08:29 modexlib.c
-rw-rw-rw- 1 andy andy     5268 2008-05-24 08:29 modexlib.h
-rw-rw-rw- 1 andy andy    26072 2010-01-23 13:04 modexlib.o
-rw-rw-rw- 1 andy andy     2946 2002-12-31 01:19 music.h
-rw-rw-rw- 1 andy andy     1521 2008-05-24 08:34 myprint.h
-rw-rw-rw- 1 andy andy      815 2002-12-20 21:15 profile.h
-rwxrwxrwx 1 andy andy   110484 1995-02-15 12:20 REMOTE1.RTS
-rwxrwxrwx 1 andy andy  2185447 2010-01-23 13:04 rott
-rw-rw-rw- 1 andy andy     2566 2003-02-14 06:51 rottnet.h
-rw-rw-rw- 1 andy andy    11075 2002-12-20 23:56 _rt_acto.h
-rw-rw-rw- 1 andy andy   319215 2008-05-24 08:29 rt_actor.c
-rw-rw-rw- 1 andy andy    11983 2008-05-24 08:26 rt_actor.h
-rw-rw-rw- 1 andy andy   453752 2010-01-23 13:04 rt_actor.o
-rw-rw-rw- 1 andy andy    29769 2002-12-24 04:51 rt_battl.c
-rw-rw-rw- 1 andy andy     4652 2002-12-20 22:18 rt_battl.h
-rw-rw-rw- 1 andy andy    55640 2010-01-23 13:04 rt_battl.o
-rw-rw-rw- 1 andy andy    37311 2008-05-24 08:29 rt_build.c
-rw-rw-rw- 1 andy andy     2354 2002-12-25 05:14 rt_build.h
-rw-rw-rw- 1 andy andy    74432 2010-01-23 13:04 rt_build.o
-rw-rw-rw- 1 andy andy     1333 2002-12-20 21:15 _rt_buil.h
-rw-rw-rw- 1 andy andy    66750 2008-05-24 08:34 rt_cfg.c
-rw-rw-rw- 1 andy andy     3348 2008-05-24 08:34 rt_cfg.h
-rw-rw-rw- 1 andy andy    99536 2010-01-23 13:04 rt_cfg.o
-rw-rw-rw- 1 andy andy    17436 2008-05-24 08:34 rt_com.c
-rw-rw-rw- 1 andy andy     1239 2002-12-20 21:15 _rt_com.h
-rw-rw-rw- 1 andy andy     1348 2002-12-24 05:44 rt_com.h
-rw-rw-rw- 1 andy andy    25520 2010-01-23 13:04 rt_com.o
-rw-rw-rw- 1 andy andy     4097 2002-12-23 11:50 rt_crc.c
-rw-rw-rw- 1 andy andy      827 2002-12-20 21:15 rt_crc.h
-rw-rw-rw- 1 andy andy     5240 2010-01-23 13:04 rt_crc.o
-rw-rw-rw- 1 andy andy    34374 2008-05-24 08:29 rt_debug.c
-rw-rw-rw- 1 andy andy     1067 2002-12-20 21:15 rt_debug.h
-rw-rw-rw- 1 andy andy    66304 2010-01-23 13:04 rt_debug.o
-rw-rw-rw- 1 andy andy    13909 2008-05-24 09:19 rt_def.h
-rw-rw-rw- 1 andy andy     9918 2002-12-21 02:57 rt_dmand.c
-rw-rw-rw- 1 andy andy     3762 2002-12-20 21:15 rt_dmand.h
-rw-rw-rw- 1 andy andy    17776 2010-01-23 13:04 rt_dmand.o
-rw-rw-rw- 1 andy andy      925 2002-12-20 21:15 _rt_dman.h
-rw-rw-rw- 1 andy andy    91896 2008-05-24 08:34 rt_door.c
-rw-rw-rw- 1 andy andy     1209 2002-12-20 21:15 _rt_door.h
-rw-rw-rw- 1 andy andy     7441 2008-05-24 08:26 rt_door.h
-rw-rw-rw- 1 andy andy   160488 2010-01-23 13:04 rt_door.o
-rw-rw-rw- 1 andy andy     1813 2002-12-24 04:51 rt_dr_a.h
-rw-rw-rw- 1 andy andy   150116 2008-05-24 08:34 rt_draw.c
-rw-rw-rw- 1 andy andy     1794 2002-12-20 21:15 _rt_draw.h
-rw-rw-rw- 1 andy andy     3289 2002-12-25 02:28 rt_draw.h
-rw-rw-rw- 1 andy andy   356304 2010-01-23 13:04 rt_draw.o
-rw-rw-rw- 1 andy andy    24709 2002-12-28 02:01 rt_err.c
-rw-rw-rw- 1 andy andy     6304 2010-01-23 13:04 rt_err.o
-rw-rw-rw- 1 andy andy     9285 2008-05-24 08:34 rt_error.c
-rw-rw-rw- 1 andy andy      885 2002-12-20 21:15 rt_error.h
-rw-rw-rw- 1 andy andy     1603 2002-12-24 04:51 rt_fc_a.h
-rw-rw-rw- 1 andy andy      938 2008-05-24 08:29 _rt_floo.h
-rw-rw-rw- 1 andy andy    14943 2008-05-24 08:34 rt_floor.c
-rw-rw-rw- 1 andy andy     1285 2002-12-20 21:15 rt_floor.h
-rw-rw-rw- 1 andy andy    39448 2010-01-23 13:04 rt_floor.o
-rw-rw-rw- 1 andy andy   132070 2008-08-08 18:29 rt_game.c
-rw-rw-rw- 1 andy andy     3986 2008-05-24 08:29 _rt_game.h
-rw-rw-rw- 1 andy andy     4411 2008-05-24 08:29 rt_game.h
-rw-rw-rw- 1 andy andy   203840 2010-01-23 13:04 rt_game.o
-rw-rw-rw- 1 andy andy    51712 2009-06-12 14:30 rt_in.c
-rw-rw-rw- 1 andy andy     1723 2002-12-24 04:51 _rt_in.h
-rw-rw-rw- 1 andy andy     4916 2008-05-24 08:23 rt_in.h
-rw-rw-rw- 1 andy andy    81136 2010-01-23 13:04 rt_in.o
-rw-rw-rw- 1 andy andy    85539 2008-05-24 09:19 rt_main.c
-rw-rw-rw- 1 andy andy     1921 2002-12-20 21:15 _rt_main.h
-rw-rw-rw- 1 andy andy     3856 2008-05-24 08:34 rt_main.h
-rw-rw-rw- 1 andy andy   145792 2010-01-23 13:04 rt_main.o
-rw-rw-rw- 1 andy andy    22557 2008-05-24 08:34 rt_map.c
-rw-rw-rw- 1 andy andy     1239 2002-12-24 04:51 _rt_map.h
-rw-rw-rw- 1 andy andy     1011 2002-12-20 21:15 rt_map.h
-rw-rw-rw- 1 andy andy    54504 2010-01-23 13:04 rt_map.o
-rw-rw-rw- 1 andy andy   234870 2009-03-28 16:12 rt_menu.c
-rw-rw-rw- 1 andy andy     9500 2008-05-24 08:29 _rt_menu.h
-rw-rw-rw- 1 andy andy     5191 2008-05-24 08:34 rt_menu.h
-rw-rw-rw- 1 andy andy   307776 2010-01-23 13:04 rt_menu.o
-rw-rw-rw- 1 andy andy    14881 2008-05-24 08:29 rt_msg.c
-rw-rw-rw- 1 andy andy      816 2002-12-20 21:15 _rt_msg.h
-rw-rw-rw- 1 andy andy     2113 2002-12-20 21:15 rt_msg.h
-rw-rw-rw- 1 andy andy    40888 2010-01-23 13:04 rt_msg.o
-rw-rw-rw- 1 andy andy    83710 2008-05-24 08:34 rt_net.c
-rw-rw-rw- 1 andy andy     3502 2002-12-24 04:51 _rt_net.h
-rw-rw-rw- 1 andy andy     6972 2008-05-24 08:29 rt_net.h
-rw-rw-rw- 1 andy andy   135960 2010-01-23 13:04 rt_net.o
-rw-rw-rw- 1 andy andy     4016 2008-05-24 08:29 _rt_play.h
-rw-rw-rw- 1 andy andy   152106 2008-05-24 08:34 rt_playr.c
-rw-rw-rw- 1 andy andy     7692 2002-12-20 22:46 rt_playr.h
-rw-rw-rw- 1 andy andy   353840 2010-01-23 13:04 rt_playr.o
-rw-rw-rw- 1 andy andy     3760 2008-05-24 08:34 rt_rand.c
-rw-rw-rw- 1 andy andy    13900 2002-12-25 02:28 _rt_rand.h
-rw-rw-rw- 1 andy andy     1292 2002-12-20 21:15 rt_rand.h
-rw-rw-rw- 1 andy andy     8352 2010-01-23 13:04 rt_rand.o
-rw-rw-rw- 1 andy andy     1494 2002-12-24 04:51 rt_sc_a.h
-rw-rw-rw- 1 andy andy    32573 2008-05-24 08:34 rt_scale.c
-rw-rw-rw- 1 andy andy     1847 2002-12-20 21:15 rt_scale.h
-rw-rw-rw- 1 andy andy    52784 2010-01-23 13:04 rt_scale.o
-rw-rw-rw- 1 andy andy      836 2002-12-20 21:15 _rt_scal.h
-rw-rw-rw- 1 andy andy    34779 2008-05-24 08:34 rt_sound.c
-rw-rw-rw- 1 andy andy    17026 2002-12-20 21:15 rt_sound.h
-rw-rw-rw- 1 andy andy    89472 2010-01-23 13:04 rt_sound.o
-rw-rw-rw- 1 andy andy     2585 2002-12-21 01:57 _rt_soun.h
-rw-rw-rw- 1 andy andy      868 2002-12-20 21:15 _rt_spba.h
-rw-rw-rw- 1 andy andy    13727 2002-12-24 07:43 rt_spbal.c
-rw-rw-rw- 1 andy andy     1107 2002-12-20 21:15 rt_spbal.h
-rw-rw-rw- 1 andy andy     8032 2010-01-23 13:04 rt_spbal.o
-rw-rw-rw- 1 andy andy     1358 2002-12-24 09:03 rt_sqrt.c
-rw-rw-rw- 1 andy andy     3658 2002-12-21 06:38 rt_sqrt.h
-rw-rw-rw- 1 andy andy     7440 2010-01-23 13:04 rt_sqrt.o
-rw-rw-rw- 1 andy andy    46977 2008-05-24 08:34 rt_stat.c
-rw-rw-rw- 1 andy andy   105446 2002-12-24 14:26 rt_state.c
-rw-rw-rw- 1 andy andy   435208 2010-01-23 13:04 rt_state.o
-rw-rw-rw- 1 andy andy     1600 2002-12-20 21:15 _rt_stat.h
-rw-rw-rw- 1 andy andy     5806 2008-05-24 08:26 rt_stat.h
-rw-rw-rw- 1 andy andy   240224 2010-01-23 13:04 rt_stat.o
-rw-rw-rw- 1 andy andy    44457 2008-05-24 08:34 rt_str.c
-rw-rw-rw- 1 andy andy     1641 2002-12-25 05:14 _rt_str.h
-rw-rw-rw- 1 andy andy     3427 2008-05-24 08:34 rt_str.h
-rw-rw-rw- 1 andy andy    79384 2010-01-23 13:04 rt_str.o
-rw-rw-rw- 1 andy andy     2990 2002-12-21 08:05 _rt_swft.h
-rw-rw-rw- 1 andy andy    10656 2002-12-21 08:05 rt_swift.c
-rw-rw-rw- 1 andy andy     2402 2002-12-20 21:15 rt_swift.h
-rw-rw-rw- 1 andy andy     9608 2010-01-23 13:04 rt_swift.o
-rw-rw-rw- 1 andy andy    22663 2002-12-20 21:15 rt_table.h
-rw-rw-rw- 1 andy andy   158141 2008-05-24 08:34 rt_ted.c
-rw-rw-rw- 1 andy andy     2760 2008-05-24 09:19 _rt_ted.h
-rw-rw-rw- 1 andy andy     4251 2008-05-24 08:34 rt_ted.h
-rw-rw-rw- 1 andy andy   284336 2010-01-23 13:04 rt_ted.o
-rw-rw-rw- 1 andy andy    35708 2008-05-24 08:34 rt_util.c
-rw-rw-rw- 1 andy andy     1318 2003-02-14 06:51 _rt_util.h
-rw-rw-rw- 1 andy andy     5698 2008-05-24 08:34 rt_util.h
-rw-rw-rw- 1 andy andy    75728 2010-01-23 13:04 rt_util.o
-rw-rw-rw- 1 andy andy     1134 2002-12-21 01:19 rt_vh_a.h
-rw-rw-rw- 1 andy andy    26974 2008-08-08 18:28 rt_vid.c
-rw-rw-rw- 1 andy andy     1422 2002-12-20 21:15 _rt_vid.h
-rw-rw-rw- 1 andy andy     3384 2008-05-24 08:29 rt_vid.h
-rw-rw-rw- 1 andy andy    36744 2010-01-23 13:04 rt_vid.o
-rw-rw-rw- 1 andy andy    20759 2008-05-24 08:34 rt_view.c
-rw-rw-rw- 1 andy andy     3745 2008-05-24 08:29 rt_view.h
-rw-rw-rw- 1 andy andy    54512 2010-01-23 13:04 rt_view.o
-rw-rw-rw- 1 andy andy    10637 2002-12-25 06:01 sbconfig.c
-rw-rw-rw- 1 andy andy     3798 2002-12-20 21:15 sbconfig.h
-rw-rw-rw- 1 andy andy     5759 2008-05-24 08:34 scriplib.c
-rw-rw-rw- 1 andy andy     1234 2002-12-20 21:15 scriplib.h
-rw-rw-rw- 1 andy andy    11728 2010-01-23 13:04 scriplib.o
-rw-rw-rw- 1 andy andy     1491 2008-05-24 08:34 sndcards.h
-rw-rw-rw- 1 andy andy    68680 2002-12-25 04:10 snd_reg.h
-rw-rw-rw- 1 andy andy    65088 2002-12-24 04:51 snd_shar.h
-rw-rw-rw- 1 andy andy     5912 2002-12-25 06:01 splib.h
-rw-rw-rw- 1 andy andy    49114 2002-12-22 03:12 sprites.h
-rw-rw-rw- 1 andy andy    17545 2008-05-24 08:29 states.h
-rw-rw-rw- 1 andy andy     2014 2002-12-20 21:15 task_man.h
-rw-rw-rw- 1 andy andy      895 2003-02-14 06:51 version.h
-rw-rw-rw- 1 andy andy      767 2008-05-24 08:26 watcom.c
-rw-rw-rw- 1 andy andy     1956 2002-12-20 21:15 watcom.h
-rw-rw-rw- 1 andy andy     5256 2010-01-23 13:04 watcom.o
-rw-rw-rw- 1 andy andy     4857 2008-05-31 09:23 winrott.c
-rw-rw-rw- 1 andy andy     1398 2008-05-31 09:23 WinRott.h
-rw-rw-rw- 1 andy andy    11896 2010-01-23 13:04 winrott.o
-rw-rw-rw- 1 andy andy    13504 2008-05-24 08:34 w_wad.c
-rw-rw-rw- 1 andy andy     1596 2002-12-24 05:44 _w_wad.h
-rw-rw-rw- 1 andy andy     2173 2002-12-24 05:44 w_wad.h
-rw-rw-rw- 1 andy andy    19256 2010-01-23 13:04 w_wad.o
-rw-rw-rw- 1 andy andy    22004 2008-05-24 08:34 z_zone.c
-rw-rw-rw- 1 andy andy     1599 2002-12-20 21:15 _z_zone.h
-rw-rw-rw- 1 andy andy     3448 2002-12-20 21:15 z_zone.h
-rw-rw-rw- 1 andy andy    23480 2010-01-23 13:04 z_zone.o

```

What do I need to change in .profile ?

---

### Post by yetiman64 on 2010-10-23
> **andlinux said:**
> ....What do I need to change in .profile ?

Change the line,> export PATH=$PATH:$HOME/Games/rott-1.1.1to read,
> export PATH=$PATH:$HOME/Games/rott-1.1.1/rott                       that is add the extra directory "rott" to the path. Dont' forget to log out and log back in to make the change take effect.

The path was incorrect by one folder depth.

The file "rott" in this folder is executable and owned by you so the above should fix your problem. Let us know how you go, hoping it works for you :).

Edit: FYI as an extra, if this works for you, you will be able to launch rott from the terminal as well, just by typing "rott" (without the quotes) then press the enter key.

---

### Post by andlinux on 2010-10-23
Well, this is strange.

I added rott in .profile and logged out and back in.

Now I see 2 lines of "Rise of the Triad" in the menu and if I click on one it doesn't work.

If I open a console and give the command "rott" (without the quotes" then it gives this as output:

 ```
andy@ubuntu-laptop:~$ rott
Rise of the Triad Startup  Version 1.4
 CD Version 
Z_INIT: 8950000 bytes
IN_Startup: Mouse Present
Error, Could not find User file 'DARKWAR.WAD', ignoring fileError, Could not find User file 'REMOTE1.RTS', ignoring fileW_InitFiles: no files found Episode      = 0
Area         = 1

```

I have to add that I had installed rott with synaptic (you can find it there) in the past but I removed that completly because that was the shareware version. It has maybe something to do with that ?

If I go to /home/andy/Games/rott-1.1.1/rott and double click on rott then the game still starts without a problem.

---

### Post by yetiman64 on 2010-10-23
> **andlinux said:**
> Well, this is strange.

I added rott in .profile and logged out and back in.

Now I see 2 lines of "Rise of the Triad" in the menu and if I click on one it doesn't work.

If I open a console and give the command "rott" (without the quotes" then it gives this as output:

 ```
andy@ubuntu-laptop:~$ rott
Rise of the Triad Startup  Version 1.4
 **CD Version **
Z_INIT: 8950000 bytes
IN_Startup: Mouse Present
Error, **Could not find User file 'DARKWAR.WAD**', ignoring fileError, Could not find User file 'REMOTE1.RTS', ignoring fileW_InitFiles: no files found Episode      = 0
Area         = 1

```I have to add that I had installed rott with synaptic (you can find it there) in the past but I removed that completly because that was the shareware version. It has maybe something to do with that ?

If I go to /home/andy/Games/rott-1.1.1/rott and double click on rott then the game still starts without a problem.

The bolded file is actually in the rott folder you listed the contents for in an earlier post :confused:
> -rwxrwxrwx 1 andy andy 14610173 1995-02-15 12:20 DARKWAR.WADThis is beyond my scope as to why the failure unfortunately, however another possibility now I understand the path correctly is to remove the entry in .profile completely.

**This will totally undo my suggestion re the system path** after *_another log out and login_*.

Delete any launchers for rott in the menu (not just detick them), then create a new one with

Type: Application

Name: Rise of the Triads

Command: /home/andy/Games/rott-1.1.1/rott                      /rott

Set an icon. 

This is pretty much back to where you started but just fixing the command.

I think this would be worth a try. If this fails again I could also suggest (though not for the menu unfortunately) a direct link to the rott executable put on your desktop (a rather inelegant workaround :()

I have a feeling what you're running up against may have to do with "**CD Version** ", though can't confirm that at all. Interesting.

---

### Post by andlinux on 2010-10-23
> **yetiman64 said:**
> 
I have a feeling what you're running up against may have to do with "**CD Version** ", though can't confirm that at all. Interesting.

I did what you wrote but without any luck. 
But when I was going true the hidden files in my home directory I saw a directory called .rott, if I open that dir then I see that this is from the rott install that I did remove in the past with synaptic. So when I checked rott in synaptic to remove all the files it didn't do that. I'm sure this is what is bugging me because there is a config file "config.rott" and in the first lines you see this:

```
Rise of the Triad Configuration File
;                  (c) 1995

Version            14

```
Version 1.4 ...

Then I did a search in the complete filesystem and found more parts of the old rott install. I found a file rott.desktop with this in:

```
[Desktop Entry]
X-AppInstall-Package=rott
X-AppInstall-Popcon=96
X-AppInstall-Section=multiverse

Type=Application
Name=Rise of the Triad
Comment=A high quality, fast scrolling first-person perspective 3D action game
Icon=rott
TryExec=rott
Exec=rott -fullscreen -resolution 800x600
Categories=Game;ActionGame;
X-Ubuntu-Gettext-Domain=app-install-data
```

So again stuff from the old installation... and I said that there was a new line in the menu with "Rise of the Triad" and if you take a look at the comment of that link then you see stuff like 800x600 etc.

So I think this old installation that I "removed" with synaptic is bugging me.

---

### Post by yetiman64 on 2010-10-23
> So I think this old installation that I "removed" with synaptic is bugging me. Yes , that makes more sense. The situation was baffling me, I expected at least one of the methods, full path in launcher or exec in the system path to work.

I think (now you know the full path to the new install) that with a **total** manual clean out of the old install you stand a better chance of getting either one to work on the new install. Old config files can cause some real headaches (I remember having seen that a few times here in the past now - this has been a good memory booster for me :smile:).

Either method of launching (noted in my first sentence above) would probably be worth another shot now you have found that out. I prefer the system path means myself because of the ability to launch from terminal by the apps name alone. This is handy for troubleshooting (like in this situation). Good luck.

---

