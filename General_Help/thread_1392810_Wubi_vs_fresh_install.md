---
title: "Wubi vs fresh install"
date: 2010-01-28
forum: General Help
---

### Post by imns81 on 2010-01-28
This is my first post here, so hello everyone!

I have wubi installed on one of my laptops that has Windows XP on it and everything seems to be working fine.  

I want to do a fresh install of ubuntu 9.10 and get rid of Windows but I was wondering if wubi and a fresh install are the same and if everything will still work with a fresh install?  I just wasn't sure if Wubi was specifically designed to work on windows machines and if I will have to do more work with a fresh install to get everything working correctly?

As you can probably tell, I am linux noob, but very excited about it and enthusiastic to learn more.

Thanks for the help.

---

### Post by lisati on 2010-01-28
One of the main differences between "Wubi" and a regular installation is where Ubuntu gets stored. Wubi sets aside a folder on your Windows partition, while a regular installation usually requires one or more partitions of its own. 

Another difference is that with Wubi, you can use the Windows add/remove programs option to remove Ubuntu.

Wubi is good if you want to try Ubuntu for a while before committing yourself to a regular installation.

---

### Post by audiomick on 2010-01-28
Hi.
I haven't tried a wubi install, but as far as I know, if everything works there, it will also work on a normal install.

---

### Post by Leppie on 2010-01-28
if your fear is that you have to set up a lot of things after installation, you could check out linux mint helena (is karmic with a lot of options already installed).

---

### Post by sailthesea on 2010-01-28
> **Leppie said:**
> if your fear is that you have to set up a lot of things after installation, you could check out linux mint helena (is karmic with a lot of options already installed).

I second that
It should go straight into action It looks a little different from Ubuntu but it's only the surface

If you want rid of Windows don't bother with Wubi just download,burn the disc and install on whole drive
Job done!:)

Edit: Try viewing this thread. I wanted to reinstate my setup from a backup disc or USB Was a big help!

[http://ubuntuforums.org/showthread.php?t=1240550](http://ubuntuforums.org/showthread.php?t=1240550)

Good Luck

And Welcome!

---

### Post by imns81 on 2010-01-28
That's the first I've heard about mint helena.  So, they basically take ubuntu and make it more user friendly?  Why doesn't everyone use that then?

---

### Post by Leppie on 2010-01-28
linux mint is aimed at users transitioning to linux from windows.
when you get more used to the linux way, you may appreciate the native styles and ways more (or just continue using linux mint ;))

---

### Post by ovroniil on 2010-02-08
Can anyone please discuss what are the pros and cons of a "Wubi Installation" and a "Fresh Installation"?

---

### Post by Leppie on 2010-02-08
> **ovroniil said:**
> Can anyone please discuss what are the pros and cons of a "Wubi Installation" and a "Fresh Installation"?
wubi:
pro: no partitioning involved, can be removed from the windows add/remove applciations applet
cons: won't boot if windows didn't shut down properly, more likely to be subject to data corruption as the linux filesystem is build on top of the windows filesystem

side by side install:
pro: possibility to troubleshoot your windows install and recover files from within ubuntu, less subject to data corruption
cons: you have to look into partitioning a little bit as doing it the wrong way could mean erasing the drive

---

### Post by howefield on 2010-02-08
> **ovroniil said:**
> Can anyone please discuss what are the pros and cons of a "Wubi Installation" and a "Fresh Installation"?

An older post but still valid as far as I can see.

[http://ubuntuforums.org/showthread.php?t=481219&highlight=catch](http://ubuntuforums.org/showthread.php?t=481219&highlight=catch)

---

