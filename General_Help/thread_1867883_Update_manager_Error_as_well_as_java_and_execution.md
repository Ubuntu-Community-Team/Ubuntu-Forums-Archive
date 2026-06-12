---
title: "Update manager Error as well as java and execution through Sun Java."
date: 2011-10-23
forum: General Help
---

### Post by Asad3ainJalout on 2011-10-23
Hello,
Please bear with me, I have only recently gotten into Ubuntu LInux. I was wondering if you could please help me with my dilemma. If possible use layman's terms and explaining what things do (i.e. dont jsut put sudo apt-get please add that means sudo go to root etc... i want to learn as well :D)

Ok here is the problem. I got a game called minecraft to work by downloading Sun-Java and turning the minecraft.jar folder to an executable. This worked fine. My first contact with the error was double clicking on the jar and ... nothing happening. I ignored it. It was just a game and it didn't really bother me. Later on i tried to access some things that required Sun Java. They did not work. I went to the Ubuntu Software Manager via the gui  and i tried reinstalling sun java i got this... hmm well cross that i cant even open up the Software manager any more.

Ok when i try to run ubuntu update manager i get this. 

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 55 in source list /etc/apt/sources.list (dist parse)'

And i get a little red circle with a horizontal line through it on the top of my gui saying

> A problem occurred when checking for the updates.

Anyway, I am pretty sure i have not given enough info. Please tell me how to provide the Tech info you need.

---

### Post by Asad3ainJalout on 2011-10-23
Shameless Bump

---

### Post by linuxinstalledfromhdd on 2011-10-23
Clean it out.. 

Do it this way...

[http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/](http://debianhelp.wordpress.com/2011/10/16/how-to-install-minecraft-in-ubuntu/)

Works perfectly on my system mate.

---

### Post by Asad3ainJalout on 2011-10-23
Thank you.
How do i do that i mean i got open the Ubuntu software manager at all.

---

### Post by Asad3ainJalout on 2011-10-23
I got this error  When performing step 1 of the tutorial.

**Step One: Video Drivers**
 **Open your Terminal, cut and paste:**
 sudo jockey-gtk

> SystemError: E:Malformed line 55 in source list /etc/apt/sources.list (dist parse)


---

### Post by coffeecat on 2011-10-23
Before you try to install Minecraft and/or follow that tutorial, you need to deal with this:

```
SystemError: E:Malformed line 55 in source list /etc/apt/sources.list (dist parse) 
```

The sources.list file is the main configuration file for your repository sources. All the package managers use it, including Update Manager, and you won't be able to update or install things in your system until that problem is solved.

Open a Nautilus file browser window, and click on "File System". Open the /etc folder, and now the /apt folder. Right-click on the sources.list file and choose "open with text editor". It will open read-only. Copy and paste the contents of the file into your post and we'll take it from there.

---

### Post by Asad3ainJalout on 2011-10-23
Thank you. (btw if there is a way to add a spoiler tell me and i will hide this wall of text.

**The Source.List text.**
> # deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric main restricted
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-updates main restricted
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric universe
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric universe
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-updates universe
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric multiverse
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric multiverse
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-updates multiverse
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-security main restricted
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-security main restricted
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-security universe
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-security universe
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main #Third party developers repository
deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) oneiric-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

---

### Post by coffeecat on 2011-10-23
> **Asad3ainJalout said:**
> Thank you. (btw if there is a way to add a spoiler tell me and i will hide this wall of text.

Don't worry. It's better if you use code tags rather than quote tags for terminal outputs and the contents of config files - it preserves formatting - but it's OK for now.

The reason you are getting the malformed line error is that both of the last two lines are indeed malformed:

```
deb http://archive.canonical.com/lucid partner
deb-src http://archive.canonical.com/lucid partner
```

There should be a space between ".com/" and "lucid". But you don't need these lines anyway - they're for Lucid and you are running Oneiric. You have a line for the partner binary packages for Oneiric earlier in the file here:

```
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu lucid partner
```

Edit the sources.list file with:

```
gksu gedit /etc/apt/sources.list
```

Be very careful now - you have that file open with root privileges. Remove the two Lucid lines at the end of the file, save and close. Now try to update your system.

---

### Post by Asad3ainJalout on 2011-10-23
That fixed everything perfectly. Thanks a million. BTW, did that happen when i updated cause i sort of upgraded straight from 10.04 up to 11.10

---

### Post by coffeecat on 2011-10-24
You upgraded directly from 10.04 to 11.10? That's not a recommended/supported upgrade pathway so I can't be sure, but it's possible I suppose. To go from 10.04 to 11.10, you should have gone 10.04 -> 10.10 -> 11.04 -> 11.10. The only time "skipping" releases is supported is LTS -> LTS, so when 12.04 comes out next year it will be possible to go directly 10.04 -> 12.04.

Anyway, if that's the only problem you've encountered, you've done well!

There is still a Lucid line in your sources.list. It's commented (starts with #) so it's non-functional at the moment, but if you want to edit that to show oneiric instead of lucid, that would be a good idea.

---

### Post by Asad3ainJalout on 2011-10-24
I did go by the path your wrote out. I.E. 10.04--> 10.10--> 11.04-->11.10

---

