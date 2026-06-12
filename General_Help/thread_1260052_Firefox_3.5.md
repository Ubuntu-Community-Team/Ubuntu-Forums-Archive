---
title: "Firefox 3.5"
date: 2009-09-07
forum: General Help
---

### Post by Anybloodyid on 2009-09-07
Hi

Using Ubuntu, Firefox is version 3.0.13, yet the latest version is 3.5.2
How do I upgrade to he latest Firefox?

Thanks

---

### Post by wojox on 2009-09-07
You can use Synaptic or go here:

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Anybloodyid on 2009-09-07
Thanks
It nearly worked I downloaded Firefox 3.5 and went to add remove looked for Abrowser 3.5 and clicked to add program
but I got a message to say there was a conflict and I need to go to Synaptic this would be a good idea if it had told me what the conflict was!
Never mind, it's another nail in the coffin for Ubuntu.

---

### Post by Vakman on 2009-09-07
[http://ubuntuforums.org/showthread.php?t=1235196](http://ubuntuforums.org/showthread.php?t=1235196)
This is a script that works great for me. Will do all the work for you.

---

### Post by FunkyRes on 2009-09-07
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main

is what I used - and then I installed it via synatptic.

No dependency problems or conflicts, so if you have some, my guess it is from a conflicting repository.

That's a development repo (I'm using 3.5.4pre) but if a development version is nicely packaged than 3.5.2 should be.

I agree though that 3.5 should be in the main repo. It's a major improvement. My guess is there are conflicts with ubuntu specific extensions/addons that haven't been updated/tested yet and it will come soon.

html 5 media support rocks.

---

### Post by lovinglinux on 2009-09-07
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by bettlebrox on 2009-09-07
Add (or comment in) the backports repository to you /etc/apt/sources.list:

```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
```

Then from the command line:
```
sudo apt-get install firefox-3.5 firefox-3.5-gnome-support 
```

---

### Post by Anybloodyid on 2009-09-07
Thisislaw thanks

Followed your link and all worked fine.

---

### Post by Vakman on 2009-09-08
> **Anybloodyid said:**
> Thisislaw thanks

Followed your link and all worked fine.

No problem, he did make quite a useful script.

---

