---
title: "Help with Ubuntu"
date: 2004-10-25
forum: General Help
---

### Post by akamjballar on 2004-10-25
Hello, I am new to Ubuntu and also linux. I have installed some programs via apt-get. Most of the time the things I search for are never there, for an example apt-get install nicotine*. That wasn't found, I really need help editing, sources.list, so I can add more sites, where it will search for programs. Right now, all I have is this.

```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu warty main restricted
deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu warty universe
# deb-src http://archive.ubuntu.com/ubuntu warty universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted
```

---

### Post by shufla on 2004-10-25
Hello,

[QUOTE=akamjballar]Hello, I am new to Ubuntu and also linux. I have installed some programs via apt-get. Most of the time the things I search for are never there, for an example apt-get install nicotine*. That wasn't found, I really need help editing, sources.list, so I can add more sites, where it will search for programs. Right now, all I have is this.

```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb http://archive.ubuntu.com/ubuntu warty main restricted
deb-src http://archive.ubuntu.com/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu warty universe
# deb-src http://archive.ubuntu.com/ubuntu warty universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted
```[/QUOTE]

Huh... Well, go through [www.ubuntu.com](www.ubuntu.com) site, then you see Support link, then Documentation.

As you see, you can enable universe repository by removing # before deb with universe line. I prefer solution with Synaptic - go to Prefereces, then Repositories and enable universe. Ok, then PUSH Refresh and search again.

You may need `multiverse' repository to got other software - copy and paste two lines contating `universe', then change `universe' to `multiverse', run synaptic, ignore error and hit refresh again.

Best regards,
Lukasz Nowak

---

### Post by akamjballar on 2004-10-25
Thank you so much. It helped me out a lot.

---

