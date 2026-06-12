---
title: "how to readd all instaled packages to the /var/cache/apt/archives"
date: 2010-01-26
forum: General Help
---

### Post by vinnywright on 2010-01-26
hay all :D 

I have a wanderfulley working Kubuntu Karmic 9.10 box and love it.

now I just did another install of 9.10 on a old box that dosent have eney network card.
the old thing is runing prity well but I want it set up like this one that I'm on now......... SO I thought I'd try aptoncd .................. the trouble is that I have done apt-get clean a few times sence seting this box up so wat's left in /var/cache/apt/archives is a varey incomplete set of packages.

I'm trying to find a way to reload the /var/cache/apt/archives with all insaled packages.

I'v managed to make a list of them with 

> sudo dpkg --get-selections > installed-software
and tryed

> sudo dpkg --set-selections < installed-software
folowd by

> sudo apt-get install --download-onlyand when that dident work

> sudo aptitude install -d
to no avale ??         so IS thare a way to do this or a better way to add ALL the packages on the system back to/var/cache/apt/archives so aptoncd will find them?

VINNY

---

### Post by vinnywright on 2010-01-26
Hummm is this realey that difacult?

VINNY

---

### Post by Barriehie on 2010-01-28
Found it, now I'll try it...

[http://ubuntuforums.org/showthread.php?t=1367832&highlight=dpkg+--get-selections](http://ubuntuforums.org/showthread.php?t=1367832&highlight=dpkg+--get-selections)

---

### Post by linuxguy2009 on 2010-01-28
Here is the way I would do this...

Boot your working fully configured machine.
"dpkg --get-selections > ~/Desktop/PackageList.txt"
Copy this text file to an external drive like a flashdrive.

Boot this same machine with the live CD.
Copy the text file back to the desktop in the live session.
"sudo dpkg --set-selections < ~/Desktop/PackageList.txt"
"sudo apt-get dselect-upgrade"
Sit back while it downloads and installs everything.

Copy all of the packages from "/var/cache/apt/archives/" to an external drive.

Go over to the offline machine.
cd to the package folder on the flashdrive.
"sudo dpkg -i *.deb"

Its up to you if you want to use aptoncd to create a CD/DVD repository disk.

As long as you have enough system ram this can all be done in one shot.
If your low on ram then you'll have to split the PackageList.txt file into a few peices and do it in chunks.

Not sure if theres an easier way, but this ain't bad at all.

Edit: Make sure you have all needed repositories added first on the live CD session.

---

### Post by Barriehie on 2010-01-29
Mine blew up because each line from **dpkg --get-selections** has installed at the end of each line.  I did this:
```

[color="green"]dpkg --get-selections | gawk '{ print $1 }' > ~/InstalledPackages.txt[/color]

```
to generate my install list.

Barrie

---

### Post by Leppie on 2010-01-29
> **Barriehie said:**
> Mine blew up because each line from **dpkg --get-selections** has installed at the end of each line.  I did this:
```

[COLOR=green]dpkg --get-selections | gawk '{ print $1 }' > ~/InstalledPackages.txt[/COLOR]

```to generate my install list.

Barrie
very handy, thanks very much :)

---

### Post by Barriehie on 2010-01-29
Anytime!  gawk is 8)

---

### Post by Barriehie on 2010-01-30
So is this solved? 8)

---

### Post by Leppie on 2010-01-30
well, for me it works... ;)
just don't know bout the OP...:P

---

### Post by Barriehie on 2010-01-30
Yeah, I'm unsubscribing, time to clean up the links...

---

### Post by Leppie on 2010-01-30
> **Barriehie said:**
> Yeah, I'm unsubscribing, time to clean up the links...
yes, i've stopped subscribing to threads i post in as people very often do not get back to you.
and if they do, you should be able to see the reply in the first couple of pages ;)

but apart from that, i'm very thankful for that oneliner :D

---

