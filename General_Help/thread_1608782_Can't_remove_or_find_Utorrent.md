---
title: "Can't remove or find Utorrent"
date: 2010-10-29
forum: General Help
---

### Post by scarface87 on 2010-10-29
Hey everybody. I was so stupid that i install Utorrent (without Wine) and now im trying to complety remove again but both Termial og synaptic but it could not find it anywhere.

Is there anyone who could help me with that problem?

PS. Thans alot :-)

---

### Post by ron999 on 2010-10-29
Hi
Which method did you use to install Utorrrent on Ubuntu?

---

### Post by scarface87 on 2010-10-29
I think i download it terminal.

NO NO, i got i from there site.

When i try to [sudo apt-get remove --purge utorrent]

```
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
E: Kunne ikke lokalisere pakken utorrent
```

---

### Post by ajgreeny on 2010-10-29
It may be worth using synaptic as it often finds apps even if they were installed in a different manner.  You have still not said how you installed it, just that you downloaded it in terminal, so having downloaded it, how did you actually install it, please?

---

### Post by MorphJet on 2010-10-29
If you run from the terminal
$  sudo apt-cache search utorrent

That will tell you what the name of the package is if it was installed via apt, if not then apt wont help you

You could also try a search to find any packages, run
$ sudo updatedb
$ locate utorrent

That might help you find it, hope it helps

---

### Post by scarface87 on 2010-10-29
[@ajgreeny]("http://ubuntuforums.org/member.php?u=27747")
I tried synaptic but it can't find it, also i tried using terminal and both of them can't find them.

I'm going insane her :-D

---

### Post by scarface87 on 2010-10-29
Hmm well.
[sudo apt-cache search utorrent]
Returns:
```
ktorrent - BitTorrent client based on the KDE platform
qbittorrent - bittorrent client based on libtorrent-rasterbar with a Qt4 GUI
qbittorrent-dbg - debug symbols for qbittorrent and qbittorrent-nox
qbittorrent-nox - bittorrent client based on libtorrent-rasterbar (without X support)
```[sudo updatedb]
[locate utorrent]
Returns nothing.

PS. I have tried to seache the system for utorrent but nothing found.

I just don't what to do :-(

---

### Post by scarface87 on 2010-10-29
Please help me guys :confused:

---

### Post by ajgreeny on 2010-10-30
Are you sure you did really install it and not simply download it?

Try the locate command again with the letter case ignored ```
locate -i utorrent
``` and see what that brings up.  It seems very strange that nothing is appearing, but then I don't know utorrent at all so maybe it's normal.

---

### Post by gandaran on 2010-10-30
utorrent is a windows program ( I believe there is no version for linux yet), it can only be installed if you have wine installed, do you have wine installed?

---

### Post by scarface87 on 2010-10-31
@ajgreeny
It returns nothing.

@gandaran
Yes there is: [http://www.utorrent.com/downloads/linux](http://www.utorrent.com/downloads/linux)

I think i just have to leave it as it is, maybe i reinstall ubuntu. Just to be sure :)
[B]
But thanks alot everybody :)[/B]

---

### Post by Chronon on 2010-10-31
Check the documentation bundled with the alpha release. 

It says that it consists of an executable named [FONT="Courier New"]utserver[/FONT] "that implements bit torrent services and is controlled through an HTTP-based application programming interface (API)."

Try locating "utserver" instead.

---

### Post by scarface87 on 2010-11-01
> **Chronon said:**
> Check the documentation bundled with the alpha release. 

It says that it consists of an executable named [FONT=Courier New]utserver[/FONT] "that implements bit torrent services and is controlled through an HTTP-based application programming interface (API)."

Try locating "utserver" instead.

Yeah, that did the trick :-) **Thanks man :)**

---

