---
title: "How to install mplayer?"
date: 2006-03-31
forum: General Help
---

### Post by Roxxor on 2006-03-31
I have followed the instructions in [http://www.ubuntuforums.org/showthread.php?t=76559&highlight=mplayer](http://www.ubuntuforums.org/showthread.php?t=76559&highlight=mplayer)
(except line 3, "2) add a line similar to universe see the example; [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse
(note I am in Canada, I sugest you get a miiror closer to you)"
I don't understand, what line am I supposed to use?

When i try to insall it with apt-get, I get this error (translated):
```

root@laptop:~# apt-get install mplayer-586
Reading packages... Done
Building dependency tree... Done
W: Could not get status of source code file http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 The file or folder does not exist)
W: You can correct this problem by running "apt-get update"
E: Could not find the package mplayer-586
```

EDIT:
I changed /etc/apt/sources.list so it now seems like this:
```
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse

deb http://archive.ubuntu.com/ubuntu/ breezy main

```

Then I run **sudo apt-get update** and then
```

roxxor@laptop:~/ sudo apt-get install mplayer-586
.......
Following packages have dependencies that are not installable:
  mplayer-586: Dependency libdirectfb-0.9-20 but it is not installable
               Dependency libsvga1 but it is not installable or
                      svgalib-dummyg1 but it is not installable
               Dependency slang1 (> 1.4.9dbs-4) but it is not installable
```


What's wrong?

---

### Post by Sutekh on 2006-04-01
[QUOTE=Roxxor]
EDIT:
I changed /etc/apt/sources.list so it now seems like this:
```
deb http://security.ubuntu.com/ubuntu **breezy**-security universe
deb-src http://security.ubuntu.com/ubuntu **breezy**-security universe

deb-src http://archive.ubuntu.com/ubuntu/ **hoary** multiverse

deb http://archive.ubuntu.com/ubuntu/ **hoary** multiverse

deb http://archive.ubuntu.com/ubuntu/ **breezy** main

```

What's wrong?[/QUOTE]
You're all over the place.  Are you using Ubuntu 5.04 - Hoary or Ubuntu 5.10 - Breezy?  

You have some repositories that are for **breezy** and some for **hoary**, which is not a good idea.  It's most likely the cause of your troubles. 


Mplayer-586 is in the **multiverse** section of the **security** repositories.

To get mplayer-586 in **Hoary** you need these lines in your /etc/apt/sources.list
```
deb http://security.ubuntu.com/ubuntu **hoary-security** universe **multiverse**
deb-src http://security.ubuntu.com/ubuntu **[B]hoary**-security[/B] universe **multiverse**
```
To get mplayer-586 in **Breezy** you need these lines in your /etc/apt/sources.list
```
deb http://security.ubuntu.com/ubuntu **[B]breezy**-security [/B]universe **multiverse**
deb-src http://security.ubuntu.com/ubuntu **[B]breezy**-security[/B] universe **multiverse**
```
Then you can refresh the repositories list and install mplayer
```
sudo apt-get update
sudo apt-get install mplayer-586
```

Also you might want to consider cleaning up the sources.list too.

Here is a link I'd recommend

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

