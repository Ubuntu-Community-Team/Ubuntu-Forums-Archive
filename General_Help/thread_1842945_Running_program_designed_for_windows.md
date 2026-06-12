---
title: "Running program designed for windows"
date: 2011-09-12
forum: General Help
---

### Post by legbe on 2011-09-12
Hello to everyone,

I have recently installed ubuntu in my computer and I am facing a problem.

I want to install a program from a CD that is designed for windows. The program contains GRE tests. I tried to search for some solutions but without success. Could you please help me because I am giving this exam in a few days?

Thank you!

---

### Post by haqking on 2011-09-12
> **legbe said:**
> Hello to everyone,

I have recently installed ubuntu in my computer and I am facing a problem.

I want to install a program from a CD that is designed for windows. The program contains GRE tests. I tried to search for some solutions but without success. Could you please help me because I am giving this exam in a few days?

Thank you!


using [Wine]("https://help.ubuntu.com/community/Wine") or [playonlinux]("http://www.playonlinux.com/en/") or [crossover]("http://www.codeweavers.com/products/crossover/")

or with virtualisation using somethng like [www.virtualbox.org]("http://www.virtualbox.org") but this presumes you have a legal copy of Windows you can install ;-)

---

### Post by legbe on 2011-09-13
I have already downloaded wine but when I select to **[COLOR=Blue]"Open with Wine Windows Program Loader"[/COLOR]**

I receive this message: **Blocked: wine start/unix**
**The file '/media/ETS GRE/POWERPREPIIV1_0.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.**

I tried to change the permissions by making right click to the icon but this was not allowed either.:confused:

---

### Post by seawolf167 on 2011-09-13
To make something executable, do the following

```
sudo chmod +x /path/to/file_name.extension
```This will work if you copy the files off the cd, else you need to make the mounted cd executable

```
mount -o /dev/cdrom
```

(or manually edit /etc/fstab and add the *exec* option to the cdrom line)

---

### Post by legbe on 2011-09-13
Please excuse my ignorance, but where do I enter these codes?

---

### Post by haqking on 2011-09-13
> **legbe said:**
> Please excuse my ignorance, but where do I enter these codes?

in terminal.

press ctrl+alt+t and terminal window will appear.

use CD to make sure you are where files are located or specify the path in the command

---

### Post by oldos2er on 2011-09-13
If this is the program you're wanting to run, it doesn't look as though it will work.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8755](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8755)

Always check Wine's app database before trying to install any Win* app; you'll save yourself some grief.

---

### Post by haqking on 2011-09-13
> **oldos2er said:**
> If this is the program you're wanting to run, it doesn't look as though it will work.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8755](http://appdb.winehq.org/objectManager.php?sClass=application&iId=8755)

Always check Wine's app database before trying to install any Win* app; you'll save yourself some grief.

+1

ah yeah good point.

Your next best bet is my original post referring you to virtualisation with [www.virtualbox.org]("http://www.virtualbox.org")

---

### Post by donaldsmith on 2011-09-13
If the file or program you are trying to drive is missing or damaged, Windows will be able to execute the file properly and sometimes generate this error message.

---

