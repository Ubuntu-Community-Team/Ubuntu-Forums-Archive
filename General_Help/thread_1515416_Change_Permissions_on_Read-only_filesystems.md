---
title: "Change Permissions on Read-only filesystems"
date: 2010-06-22
forum: General Help
---

### Post by LukeLinux on 2010-06-22
Generally, I LOVE Ubuntu 10.04...best Ubuntu yet, IMO. But there's this one thing about it that really bugs me, and that is that all executable files on CD/DVD are set with **very** restricted permissions, including the 'Allow executing file as program' checkbox being left blank. Since CD/DVD's are read-only, I can't change these permissions the normal way or even just execute the files as root!

So far I've been able to get by with just copying the disk's contents to the hard drive and then running the program with altered permissions from there, but right now I want to install Unreal Tournament 2004 (the DVD version, if that makes any difference) and its Linux installer will not function properly from a local directory, so I'm stuck on this one.

Surely there's some way to alter the permissions for a read-only filesystem! Can't I just set system-wide permissions that would even apply to CD's and DVD's?

---

### Post by jerome1232 on 2010-06-22
Perhaps remounting the cd/dvd with the exec option enabled


```
mount /dev/<cdromdevice> -o remount,exec
```

nvm I'm slightly retarded, ignore me :D

maybe with these options

```
mount /dev/<cdromdevice> -o remount,umask=000,exec
```

---

### Post by ThesaurusRex on 2010-06-22
> **LukeLinux said:**
> Since CD/DVD's are read-only, I can't change these permissions the normal way or even just execute the files as root!What is the "normal" way for you? I would: ```
cd /media/cdrom
chmod 700 setup
./setup
```Where cd-rom is the name of your dvd drive and setup is the name of the setup file (may be in deeper directory).

---

### Post by mc4man on 2010-06-22
This is the result of the new security bit policy and not having fstab entries for optical drives by default in lucid.
(or having default permissions on removable media be set to 'exec'

The policy itself has practically no value, in almost all cases people intend to execute the file, setting up a roadblock with no detour is worthless
(and 100% of the time people intend to execute an .exe from cd/dvd media

see here for wine fix and fstab suggestion (adjust if not /dev/sr0), if just in general, not wine,  then I'd go ahead and create an fstab entry and static mountpoint.

[http://ubuntuforums.org/showthread.php?t=1514122](http://ubuntuforums.org/showthread.php?t=1514122)

screen shows how with an fstab entry for your drive an .exe is executable

---

### Post by happyhamster on 2010-06-22
When Lucid auto-opens an .exe file (or if you right-click and choose "Open with Wine Windows Program Loader"), it doesn't call wine, but instead an annoying utility called "cautious-launcher" that prevents executing stuff from CD/DVD.

So, what you can do is: right-click the .exe file, and choose Open with Other Application-->Use a Custom Command". Then type: wine
When right-clicking the .exe file again, there should now be an option to open it with wine (the proper one). You can even set this in stone, by choosing Properties-->Open With and ticking the wine option. (This is the least safe way of doing things though.)

Note that it has a lot of advantages to call wine directly from a terminal instead. Good luck.

---

### Post by LukeLinux on 2010-06-30
THANK YOU, Happyhamster, that last bit did the trick! I never would have thought to open the program with the 'wine' command since it looked like that's what it's already doing...but it's all good now; I can launch EXE's from CD's no problem!

Thread solved! :cool:

---

