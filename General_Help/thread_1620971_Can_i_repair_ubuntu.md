---
title: "Can i repair ubuntu?"
date: 2010-11-13
forum: General Help
---

### Post by chasigor on 2010-11-13
Hi. I have a little problem here. I tried to copy include directory from g++ to a place where it suppose to be and when i couldn't because of the rights i wrote something like this in the bash:
```
sudo su
password
```and then 

```
chmod 770 / -R 
```
cause i hate when I can't do what I want without tiping command

After few minutes all daemons crashed   and now I can't boot normally

in console i've tried    ```
 chmod 771 and 777 
``` and that stopped on /prc/756 directory

Well now i can boot normally but most of programs are not working, i can't get to the internet? and it looks like there is no way to become a root cause there is no sudo/

Can i reinstall ubuntu and keep all packages and files on its places?


And yeah it's funny:roll:

---

### Post by Monotoko on 2010-11-13
After doing that, I would advise reinstalling. It is the only way to make yourself secure again.

May I ask why you didn't just copy the library as root? Once you have run "gksudo su" you are root and can do anything. You can also run "sudo nautilus" to get the file manager up as root, you can simply use the cp command.

Take this as a lesson learnt, never do anything to your root /.

Daniel

---

### Post by chasigor on 2010-11-13
Well actually i always worked on windows and it was my task to compile something in g++. After i triedto compile source and saw non declared problems i've tried to use g++ -I path. It doesn't work.  I saw include directory in etc/include  not in /etc/local/include. Because i couldn't copyitfrom file manager and had some problems copying it recursively by cp i decided that I hate those rights stuff and decided to give all the rights cause i'm in root group.

---

### Post by WorMzy on 2010-11-13
Reinstall. You've messed up permissions so badly that trying to manually fix this would take hours of work, and there's no guarantee that you'll fix everything.

Never chmod/chown/chgrp "/". Ever.

```
sudo cp /path/to/library /path/to/destination
``` is all you ever needed to do. If that. Chances are, that library is installed by one of the -dev/lib- packages available in the repos.

Oh, and ignore this:
> **Monotoko said:**
> sudo nautilus

_NEVER_ use sudo for graphical applications. Use gksu or gksudo instead.

---

### Post by nothingspecial on 2010-11-13
> **chasigor said:**
> Can i reinstall ubuntu and keep all packages and files on its places?


I`m going to third the above opinions....... you`ve stuffed it.

If dpkg still works you can create a list of installed apps with

```
dpkg --get-selections
```

But I wouldn`t trust it after that.

Welcome to the "I hosed my linux system in one line" club...........

......... I am a member :)

---

### Post by chasigor on 2010-11-13
It was directory not library.

---

### Post by nothingspecial on 2010-11-13
> **chasigor said:**
> It was directory not library.


It makes no difference except you need the -r flag

> **WorMzy said:**
> 

```
sudo cp /path/to/library /path/to/destination
``` is all you ever needed to do.

```
sudo cp -r
```

for directories.

Don`t mess with / is the lesson.

If you need to execute a lot of sudo commands for a sustained period

```
sudo -i
```

---

### Post by Monotoko on 2010-11-13
> **WorMzy said:**
> 

Oh, and ignore this:

_NEVER_ use sudo for graphical applications. Use gksu or gksudo instead.

Indeed, I do apologize I wasn't thinking when I typed it ^.^ changed it now.

---

### Post by liddlem on 2010-11-13
I'm struggling with a similar problem. The question is . . . . "How can I re-install my OS without destroying my data (ie. I want to keep/save the /HOME/UserName folder(s))

---

### Post by zaphod777 on 2010-11-13
> **liddlem said:**
> I'm struggling with a similar problem. The question is . . . . "How can I re-install my OS without destroying my data (ie. I want to keep/save the /HOME/UserName folder(s))

Easiest thing to do is back everything up to a USB drive. When you are re-installing create a separate partition for /home then when you reinstall you will not need to backup your data first.

---

### Post by liddlem on 2010-11-14
thanks zaphod777 - 
I have tried viewing my data by booting a virtual image and mounting/browsing my HDD, but I am having issues.
sorry Chasigor - i dont mean to Hijack your post so if don't mind zaphod77 - please see [http://ubuntuforums.org/showthread.php?t=1621075](http://ubuntuforums.org/showthread.php?t=1621075)
Thanks

---

