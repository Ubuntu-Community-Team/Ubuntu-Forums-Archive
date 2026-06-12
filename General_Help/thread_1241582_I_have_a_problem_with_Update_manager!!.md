---
title: "I have a problem with Update manager!!"
date: 2009-08-16
forum: General Help
---

### Post by air-man001 on 2009-08-16
[SIZE=5]Hi everyone..

I'm Using [COLOR=RoyalBlue]Ubuntu 9.04 Desktop version[/COLOR].

When i Try to make "[COLOR=SeaGreen]Update[/COLOR]" or "[COLOR=SeaGreen]Add/Remove...[/COLOR]" 

I show this Message:


[[IMG]http://alfaris.net/up/39/alfaris_net_1250414763.png[/IMG]]("http://alfaris.net/up/v.php?p=39/alfaris_net_1250414763.png")



This is my "sources.list" file:[/SIZE]

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb http://ubuntu.mirrors.isu.net.sa/ubuntu/ jaunty main restricted
deb-src http://ubuntu.mirrors.isu.net.sa/ubuntu/ jaunty main restricted

deb http://ubuntu.mirrors.isu.net.sa/ubuntu/ jaunty-security main restricted
deb-src http://ubuntu.mirrors.isu.net.sa/ubuntu/ jaunty-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.mirrors.isu.net.sa/ubuntu/ jaunty-updates main restricted
deb-src http://ubuntu.mirrors.isu.net.sa/ubuntu/ jaunty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu jaunty universe
# deb-src http://archive.ubuntu.com/ubuntu jaunty universe
# deb http://archive.ubuntu.com/ubuntu jaunty-updates universe
# deb-src http://archive.ubuntu.com/ubuntu jaunty-updates universe
# deb http://security.ubuntu.com/ubuntu jaunty-security universe
# deb-src http://security.ubuntu.com/ubuntu jaunty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu jaunty multiverse
# deb-src http://archive.ubuntu.com/ubuntu jaunty multiverse
# deb http://archive.ubuntu.com/ubuntu jaunty-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu jaunty-updates multiverse
# deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
# deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ubuntu.mirrors.isu.net.sa/ubuntu/ jaunty main restricted

```

[SIZE=5][COLOR=Red]
How can I resolve this problem???[/COLOR][/SIZE]

---

### Post by gimlithedwarf on 2009-08-16
it seems that you're trying to pull updates through tor, which it isn't accepting. You need to disable tor to get your updates.

---

### Post by Soul-Sing on 2009-08-16
Indeed you can handle TOR very easy via Vidalia, which is in the repos. of jauntu. (off/on etc.)

---

### Post by air-man001 on 2009-08-16
The problem has been solved :P

Mr.leoquant , Mr.gimlithedwarf

Thank you very much :)

---

### Post by Soul-Sing on 2009-08-16
glad it helped.:)

---

