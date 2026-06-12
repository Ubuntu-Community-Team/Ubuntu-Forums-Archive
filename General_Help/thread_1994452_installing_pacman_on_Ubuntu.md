---
title: "installing pacman on Ubuntu"
date: 2012-06-02
forum: General Help
---

### Post by inashdeen on 2012-06-02
Hi, this is a bit wacky. on Chakra Linux , I manage to get dpkg running on it and even install a .deb file on chakra. Is there a way to say install pacman, or yum on Ubuntu? when I am saying this, I don't refer to a .deb converter,like alien. I would like to get the package installer runnning on Ubuntu.
thanks in advance

---

### Post by Paddy Landau on 2012-06-03
Ubuntu is Debian-based, not RPM-based, so, to the best of my knowledge, no, they won't work without a tremendous amount of reworking. Also, I understand that pacman is specifically for Arch.

If you absolutely must have those package managers, I suggest you try a different distro (such as Arch).

Having said that, you may want to read about [PacApt for pacman]("http://lifehacker.com/5880003/pacapt-brings-arch-linuxs-amazing-pacman-package-manager-to-other-linux-distributions-well-sort-of").

---

### Post by inashdeen on 2012-06-03
Well, i don't really mind the hard work, this is not a productive desktop. I want to try the impossible. that's all

---

### Post by forrestcupp on 2012-06-03
I've heard that, technically, you can compile pacman for Ubuntu if you have all the right dependencies. I've never seen anyone actually get it done, though. I think getting all those dependencies would probably end up screwing with your system, and if you actually used the two different package manager, you would have a dependency hell, and your system would end up getting destroyed.

Having said that, the PacApt that Paddy Landau referred to is worth looking into. Also, in the last comment in [this thread](https://bbs.archlinux.org/viewtopic.php?id=98678) someone created a script that they named **pacman** that converts all the pacman commands to apt-get commands. Doing that would allow you to type in pacman commands and yet use Ubuntu's Apt repositories.

Edit: You want to do a lot of hard things, don't you? :D

---

### Post by inashdeen on 2012-06-03
I love experimenting. so far i manage to get dpkg running on my pacman. still havent get my apt-get though.
See so far what have I got.
[IMG]http://a1.sphotos.ak.fbcdn.net/hphotos-ak-snc7/s320x320/380345_2865488655472_1807440591_1601141_1564912653_n.jpg[/IMG]
will look into the thread soon.

---

