---
title: "Midnight Commander 4.7 theming (skinning) is broken on lucid? No white color etc"
date: 2010-07-14
forum: General Help
---

### Post by aneganov on 2010-07-14
After upgrading to Lucid, MC looks ugly -  like some colors are missed. Its very difficult to work in MC now - directories and files have same color for example.

[ATTACH]163373[/ATTACH]

Also, applying different themes (skins) changes bottom bar (with menu: F1 F2 etc) button colors only, not affecting colors of panels.

Any ideas?

SOLUTION: Install 4.7.3 build of MC from here: [https://launchpad.net/~webupd8team/+archive/unstable](https://launchpad.net/~webupd8team/+archive/unstable)

---

### Post by aneganov on 2010-07-15
Bump

---

### Post by aneganov on 2010-07-17
Bump

---

### Post by aneganov on 2010-07-18
No colors, no highlighting. Am I the only user affected?
Bump

---

### Post by Nortie on 2010-07-20
Hello aneganov,

I copy your problems. I did a fresh lucid install yesterday (don't even kept my home/), 
and there it is: no file colors, no bold directories. 
I did not install anything afterwards, so I am pretty sure this behaviour ships with the
initial CD.
I tried an "apt-get upgrade" and replaced the whole /usr/share/mc with the files from
a different system -- no change yet.

Also, fiddling with the files in /etc/mc and ~/.mc/ did not result any good.

Sorry for not having any solution for you.

---

### Post by mcframe on 2010-07-22
Hi,
same prob here. Would be very thankful if someone could post a solution, it's hard to work with this fu****up mc config.

---

### Post by aneganov on 2010-07-22
Good news, fellows :)

It is 4.7.0 - the stable (and outdated) version of MC which is nobody cares about anymore (found some ooold reports about colors on official track). So I decided to find fresh 4.7.3 build for Lucid and got it, thanks to this article:

[http://www.webupd8.org/2010/07/install-midnight-commander-mc-473-in.html](http://www.webupd8.org/2010/07/install-midnight-commander-mc-473-in.html)

Launchpad.net project page:
[https://launchpad.net/~webupd8team/+archive/unstable](https://launchpad.net/~webupd8team/+archive/unstable)

Short instructions for command line are:

This goes to /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu lucid main 
```

and this adds a key:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C2518248EEA14886
```

then finally 

```
apt-get update 
apt-get install mc
```

Tada! Colors are back! 
[ATTACH]164253[/ATTACH]


[dancing]

---

### Post by aneganov on 2010-07-22
[Also discovered]("http://www.webupd8.org/2010/07/install-midnight-commander-mc-473-in.html") an elegant way to add repo from ppa:

```
sudo add-apt-repository ppa:webupd8team/unstable && sudo apt-get update
sudo apt-get install mc
```

Also, changes in 4.7.3 look exciting:

[LIST]
[*]Mult-screen feature: support of many opened editors and viewers
[*]Reorganization of menu and configuration dialogs. More options are available in UI
[*]Mark of text in input fields is available now, DEL removes selected/unchanged text
[*]Now copy/move dialog shows the full path with file name in the field "to:"
[*]Added new capability to create relative symlinks: menu item and "C-x v" default shortcut
[*]Now we can use external utility to copy/paste text to X clipboard
[*]A built-in tool to visual compare and merge two files
[*]Added new skins: nice and dark
[*]Autodetect codepages of edited/viewed files with enca program
[*]Added ability to show progressbars (when copy files) from right to left
[*]Added indication of total BPS and ETA for file operations
[*]Viewer is now very fast
[/LIST]

---

