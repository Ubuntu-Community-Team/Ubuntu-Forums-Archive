---
title: "Installing into 10.10 using WINE"
date: 2011-09-13
forum: General Help
---

### Post by Yamipirogoeth on 2011-09-13
First, I wasn't sure where to put this thread, so sorry in advance if its in the wrong place.

Secondly, the reason for this thread is that I'm trying to install Perfectworld Genesis into Ubuntu 10.10 using WINE 1.2.2

I have tried to follow the 2 following webpages to no avail

[http://pwi-forum.perfectworld.com/showthread.php?t=579982&page=15](http://pwi-forum.perfectworld.com/showthread.php?t=579982&page=15)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923&iTestingId=64304](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923&iTestingId=64304)

Now, if I try to run it I get the following message from the archive manager

```
Archive:  /media/PWI Genesis Installer/PWI_Genesis_Installer/install.exe
[/media/PWI Genesis Installer/PWI_Genesis_Installer/install.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/PWI Genesis Installer/PWI_Genesis_Installer/install.exe or
          /media/PWI Genesis Installer/PWI_Genesis_Installer/install.exe.zip, and cannot find /media/PWI Genesis Installer/PWI_Genesis_Installer/install.exe.ZIP, period.
```I tried to just click on the .exe file located in the PWI install files.

As far as anything that I've needed to type into the command line, it just comes back saying that it's an unknown command for anything involving wine.

So at this point I'm a little lost on what I need to do to get this program installed and am looking for help in either pointing in the right direction or maybe something I'm missing in getting the program installed.

---

### Post by jacksaff on 2011-09-13
Try 
wine "/media/PWI Genesis Installer/PWI_Genesis_Installer/install.exe"

---

### Post by seawolf167 on 2011-09-13
Try right-clicking the exe and selecting "Open with Wine ..." and see if that works. Also, see the [how-to ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9923")posted on this page.

---

### Post by Yamipirogoeth on 2011-09-14
Thanks guys,

Unfortunately, command line wouldn't load it that way, but right clicking and telling it to work in wine seems to be just fine that way.

However, this brought up a new...thought I guess.

Is it normal to have to install the same program between 2 accounts on each account? Cause I installed it into my account which has full access but the user with restricted access its not even showing as installed in wine...is that normal?

---

### Post by decrepit on 2011-09-14
In my system wine resides in my home folder,
/home/me/.wine

So I guess if there's no access to your account there's no wine either.

Maybe you can install wine to a common folder, but I'd be wary about what permissions you give it. After all wine can execute all the windows nasties.

---

### Post by seawolf167 on 2011-09-14
The WINE program directory is stored under each users' names' home directory. i.e., here:

/home/*username*/.wine/

So yes, it is normal

---

### Post by Yamipirogoeth on 2011-09-15
Ah, thanks again guys.

I think I'll keep them separate...already had issues before where they somehow managed to kill ubuntu...don't want that again

---

