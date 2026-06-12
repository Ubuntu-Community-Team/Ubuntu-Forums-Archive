---
title: "Floppy/Network install help"
date: 2006-02-10
forum: General Help
---

### Post by n0manarmy on 2006-02-10
I've grabbed the floppy's off this thread for a network floppy install of ubuntu (since i have no cdrom option for my laptop)

[http://www.ubuntuforums.org/showthread.php?t=29555](http://www.ubuntuforums.org/showthread.php?t=29555)

I want to give kubuntu a shot but i'm not having much luck telling the software what mirror to go to for download (if it's even possible with kubuntu.)

Every directory I point the floppy install to says that it can't find a valid Release file on it, try a different mirror. Does anyone know the URL i should try?

I've tried
us.releases.ubuntu.com and the directory is /releases/kubuntu/breezy/


Am i going to the wrong places or is it not even possible to do a network floppy install of kubuntu?


EDIT:

Nevermind, I found a bass-ackwards way of doing it.

Install from the floppys and depending on what flavor you get (5.04 or 5.10) do an apt-get install kubuntu-desktop to get the KDE flavor on there. Once this is done, replace hoary with breezy in your /etc/apt/sources.list file and then do

(which i recommend to do OUTSIDE of the GUI)

apt-get clean
apt-get update
apt-get dist-update

after a lengthy download and a reboot. You should be up to date with kubuntu instead of 5.04 hoary ubuntu...

all in all...a little convoluted but it worked.



You can close the thread if you want

---

