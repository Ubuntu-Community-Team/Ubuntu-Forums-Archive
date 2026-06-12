---
title: "Harddrive fails"
date: 2006-06-06
forum: General Help
---

### Post by Ubuntuud on 2006-06-06
Hi,
When I started my computer to day I ran into a serious problem,
It would not start. When it mounts the root filesystem it says the same line about an not repearable error on "0x51".
Help!
Any way to fix this?
If not, I'll try to copy my files to my external HDD with a live CD. But if it can be fixed differently, please tell me how.

Thanks in advance!

---

### Post by ifokkema on 2006-06-06
[QUOTE=Ubuntuud]Hi,
When I started my computer to day I ran into a serious problem,
It would not start. When it mounts the root filesystem it says the same line about an not repearable error on "0x51".
Help!
Any way to fix this?
If not, I'll try to copy my files to my external HDD with a live CD. But if it can be fixed differently, please tell me how.

Thanks in advance![/QUOTE]

Hi,

Put in the live CD and fsck your drive. Sounds like the drive (or at least the file system) is damaged.

Ivo

---

### Post by Ubuntuud on 2006-06-06
Indeed, I'll try so. I have a little update though, I let all the errors run for about 15 minutes, and now I get a thingey saying "Enter runlevel:". I'll go try your command now.

Thanks!

---

### Post by ifokkema on 2006-06-06
[QUOTE=Ubuntuud]I have a little update though, I let all the errors run for about 15 minutes, and now I get a thingey saying "Enter runlevel:".[/QUOTE]
I guess it's dropped down to a basic shell. Run level 5 is what you normally run at, but I don't think it'll just boot up nicely :)

Good luck on checking your drive. If the fsck returns something you don't know what to do with, let us know.

---

### Post by Ubuntuud on 2006-06-06
I got a bunch of errors, just entered "y" every time. Now it boots without the errors, but says it misses inittab, and again the runlevel question. I'll go and try with "5" now. Thanks again!

---

### Post by ifokkema on 2006-06-06
[QUOTE=Ubuntuud]I got a bunch of errors, just entered "y" every time. Now it boots without the errors, but says it misses inittab, and again the runlevel question. I'll go and try with "5" now. Thanks again![/QUOTE]

Did you happen to get questions about unallocated directory inodes? There may be files / directories in /lost+found that belong elsewhere on your drive. The inittab file (or maybe the whole /etc directory) may be found there.

---

### Post by Ubuntuud on 2006-06-07
OK. I'll do a little search (or large one). I got some questions about inodes indeed and some things about /etc. Thanks once more!

EDIT: I did, not my entire /etc is gone, but certainly a very large part of it. The only problem is that they are named with "#398675" (for example) in the /lost+found. I'll be glad to rename all of them as long as I know how to name them? Any hints, or is there another way? Or do I still need to reinstall because it would be a too large hassle to install? Thanks in advance!

---

### Post by ifokkema on 2006-06-07
[QUOTE=Ubuntuud]OK. I'll do a little search (or large one). I got some questions about inodes indeed and some things about /etc. Thanks once more!

EDIT: I did, not my entire /etc is gone, but certainly a very large part of it. The only problem is that they are named with "#398675" (for example) in the /lost+found. I'll be glad to rename all of them as long as I know how to name them? Any hints, or is there another way? Or do I still need to reinstall because it would be a too large hassle to install? Thanks in advance![/QUOTE]

I've had this problem before, but then it was the root inode, so all of my root directories went to lost+found. I could repair my system, which was much faster than re-install and then have the hassle of installing all packages that you need.

I would, while booted from the live CD, look at the contents of lost+found one by one. Search the Live CD's /etc folder for filenames you find in lost+found. That will allow you to track down the original location of the files you've lost.

Good luck,

Ivo

---

### Post by Ubuntuud on 2006-06-07
OK.
I haven't got the problem with the packages, since I have a recent backup of my list and exported it to my external drive. I didn't backup a lot of new files though.

I'll try it your way, although it are really many (50 I believe), and doesn't /etc contain the installed program files as well?

I wont do it this week, since there are a lot of tests coming.

Thanks, hopefully for the last time. (on this subject)

---

### Post by ifokkema on 2006-06-07
[QUOTE=Ubuntuud]I'll try it your way, although it are really many (50 I believe), and doesn't /etc contain the installed program files as well?[/QUOTE]

Wow, that is a lot. That will take some time.
/etc contains system wide preferences. Sometimes you have a config file in your home directory that overrides one in /etc, but most of these files are necessary for many packages to run properly.

Good luck figuring it out!

---

### Post by Ubuntuud on 2006-06-08
Uhm... I looked at it again, and came to the conclusion that I probably should reinstall. Why? Because it are more than 50, 213 to be exact... 

But I might have found a solution for the packages: aren't they stored somewhere in /apt? The only problem for me to check is that /apt is missing as well.

---

### Post by ifokkema on 2006-06-08
[QUOTE=Ubuntuud]Uhm... I looked at it again, and came to the conclusion that I probably should reinstall. Why? Because it are more than 50, 213 to be exact... 

But I might have found a solution for the packages: aren't they stored somewhere in /apt? The only problem for me to check is that /apt is missing as well.[/QUOTE]

213.... yeah, reinstall is going to be much faster.

For a list of packages that you currently have installed, type:
```
dpkg --get-selections
```
But I really don't know if this list is stored physically somewhere. /apt is not existent by default.

---

### Post by Ubuntuud on 2006-06-09
Well, I already reinstalled, couldn't wait, windoze is such a pain.

I know I had those packages stored somewhere, stumbled upon them once... Doesn't matter anymore, thanks for all your help!

---

### Post by ifokkema on 2006-06-09
[QUOTE=Ubuntuud]Well, I already reinstalled, couldn't wait, windoze is such a pain.[/QUOTE]
Yeah... windows zuigt.

[QUOTE=Ubuntuud]I know I had those packages stored somewhere, stumbled upon them once...[/QUOTE]

Well, I found some stuff in /var/lib/dpkg/, which can be used to deduce the installed packages, I think. But that would require some bash scripting to get a clean list...

[QUOTE=Ubuntuud]Doesn't matter anymore, thanks for all your help![/QUOTE]
Ur welcome/Graag gedaan (Just noticed you were a fellow Dutchman :))

---

### Post by Ubuntuud on 2006-06-09
Bedankt :)

---

