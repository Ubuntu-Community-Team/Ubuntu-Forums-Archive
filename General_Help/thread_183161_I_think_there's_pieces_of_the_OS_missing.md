---
title: "I think there's pieces of the OS missing"
date: 2006-05-27
forum: General Help
---

### Post by Ray100 on 2006-05-27
I installed 5.10 from a CD some time ago, mainly to get the PC up and folding. I had some problems at the time with the install, some files or other that gave problems, I don't remember now, it was all mumbo jumbo to me at the time, still is :) 

Now that I have time, I'm trying to get more involved with it but I have this feeling that some parts of the install are missing, Is this possible?

I'm trying to set up networking with my two Windows machines, I can see them, but they can't see this one. When I go to System/Administration/Networking I get the password box, I enter my password and I get the little clock type icon running, it says "Networking starting" at the bottom, and that's all that happens.

There's a couple of other items that do the same thing, just can't remember what they were at the moment.

Just found one, shared folders does not seem to work

I did run an update from the terminal a couple of days ago and that worked fine. But it didn't help with the networking thing.

Any help would be greatly appreciated.

Ray

---

### Post by kingmonkey on 2006-05-27
try running the following to see if it installs more apps.

```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by PriceChild on 2006-05-27
You have installed samba to share folders with windows right?

---

### Post by Ray100 on 2006-05-27
Kingmonkey:

I tried the two commands, one asked me for my password, but nothing happened with either.

PriceChild:

No I haven't installed samba, I've just downloaded it, 3.0.22
How do I install it, I extracted it to a folder on the desktop and tried to read some of the files, but. . . :confused: 

Ray

---

### Post by catlett on 2006-05-27
samba should be in synaptic. go to System<Administration<Synaptic Package Manager. Hit on the search button and enter samba in the search box. Right-click on samba and it will give you a menu with the option "mark for installation". Choose that option. Go to the top of synaptics window and hit on "apply" Synaptic will install it.

---

### Post by jvictor on 2006-05-28
U **NEED* samba for windows sharing.. It works pretty fine too

---

### Post by Ray100 on 2006-05-28
[QUOTE=catlett]samba should be in synaptic. go to System<Administration<Synaptic Package Manager. Hit on the search button and enter samba in the search box. Right-click on samba and it will give you a menu with the option "mark for installation". Choose that option. Go to the top of synaptics window and hit on "apply" Synaptic will install it.[/QUOTE]

I did that, it asked me for my password, filled that in, then nothing happened. 

As I mentioned before, there are several other "routines" that do the same thing, that's why I'm thinking that they're missing from the install.

Ray

---

### Post by kingmonkey on 2006-05-28
ok do

```

sudo apt-get install ubuntu-base ubuntu-desktop

```

This will install any missing packages.

---

### Post by Ray100 on 2006-05-28
Ok, that gave me;

E: Could not open lock file /var/lib/. . . . . . ..  (13 Permission denied)
E: Unable to lock the list directory

I tried using sudo, that asked me for my password but did nothing else at all.

---

### Post by kingmonkey on 2006-05-28
Sorry yes you have to use sudo.

Can you post what your console says after typing the above please?

Also can you post your /etc/apt/sources.list?

---

### Post by Ray100 on 2006-05-28
ray@ubuntu:~$ sudo apt-get install ubuntu-base ubuntu-desktop
ray@ubuntu:~$

That's it

ray@ubuntu:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

ray@ubuntu:~$ sudo /etc/apt/sources.list
ray@ubuntu:~$

And that's the other

---

### Post by kingmonkey on 2006-05-28
could you paste the contents of /etc/apt/sources.list here please? Try 
```

sudo gedit /etc/apt/sources.list

```

---

### Post by Ray100 on 2006-05-28
Nothing happened.

---

### Post by kingmonkey on 2006-05-28
type 

```
 whereis gedit 
```

and paste the output here.

---

### Post by Ray100 on 2006-05-28
ray@ubuntu:~$ whereis gedit
gedit: /usr/bin/gedit /usr/bin/X11/gedit /usr/share/man/man1/gedit.1.gz
ray@ubuntu:~$

---

### Post by kingmonkey on 2006-05-28
ok

do
```
sudo gedit /etc/apt/sources.list 
or
sudo nano /etc/apt/sources.list
```

paste the following into it:

```
## Uncomment the following two lines to fetch updated software from the network
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://gb.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted

```

then type

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-base ubuntu-desktop

```

---

### Post by Ray100 on 2006-05-28
ray@ubuntu:~$ ## Uncomment the following two lines to fetch updated software from the network
ray@ubuntu:~$  deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
bash: deb-src: command not found
ray@ubuntu:~$
ray@ubuntu:~$ ## Uncomment the following two lines to fetch major bug fix updates produced
ray@ubuntu:~$ ## after the final release of the distribution.
ray@ubuntu:~$ deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
bash: deb: command not found
ray@ubuntu:~$  deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
bash: deb-src: command not found
ray@ubuntu:~$
ray@ubuntu:~$ ## Uncomment the following two lines to add software from the 'universe'
ray@ubuntu:~$ ## repository.
ray@ubuntu:~$ ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
ray@ubuntu:~$ ## team, and may not be under a free licence. Please satisfy yourself as to
ray@ubuntu:~$ ## your rights to use the software. Also, please note that software in
ray@ubuntu:~$ ## universe WILL NOT receive any review or updates from the Ubuntu security
ray@ubuntu:~$ ## team.
ray@ubuntu:~$ deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
bash: deb: command not found
ray@ubuntu:~$  deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
bash: deb-src: command not found
ray@ubuntu:~$
ray@ubuntu:~$ ## Uncomment the following two lines to add software from the 'backports'
ray@ubuntu:~$ ## repository.
ray@ubuntu:~$ ## N.B. software from this repository may not have been tested as
ray@ubuntu:~$ ## extensively as that contained in the main release, although it includes
ray@ubuntu:~$ ## newer versions of some applications which may provide useful features.
ray@ubuntu:~$ ## Also, please note that software in backports WILL NOT receive any review
ray@ubuntu:~$ ## or updates from the Ubuntu security team.
ray@ubuntu:~$ deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
bash: deb: command not found
ray@ubuntu:~$  deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
bash: deb-src: command not found
ray@ubuntu:~$
ray@ubuntu:~$  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
bash: deb-src: command not found
ray@ubuntu:~$
ray@ubuntu:~$ deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
bash: deb: command not found
ray@ubuntu:~$  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
bash: deb-src: command not found
ray@ubuntu:~$ deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

---

### Post by kingmonkey on 2006-05-28
```

sudo apt-get -f install
sudo dpkg --configure -a

```

---

### Post by Ray100 on 2006-05-29
Thanks Kingmonkey, I couldn't get that to work either. I was talking to my son tonight and he walked me through a few things and found out that there's something dicy with the sudo. I can run these commands from the root level but not from the user using sudo.

I decided to upgrade to 6.06 anyway so that's happening right now. I'm off to bed so I'll see what's what in the morning and report back. Thanks again.

Ray

---

