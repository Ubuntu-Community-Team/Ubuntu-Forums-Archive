---
title: "Create USB that runs a program on boot"
date: 2011-07-19
forum: General Help
---

### Post by Norcalli on 2011-07-19
I thought using linux was the best way to do it. I want to create a specialized USB that does a simple thing like run a program or automated script I put on it when you boot into it. I don't want a GUI or anything like that, I just want to have it run in tty and restart. One example would be like a recovery tool that runs and does fsck and stuff like that, or one that recovers the password automatically. As if I were running autorun on windows on boot.

How would I go about making something like that? I'm a programmer in C/C++, so I can handle complicated solutions. I thought I might have to make a custom linux distro.

Thank you,
Norcalli

---

### Post by An Sanct on 2011-07-19
The complex way would be something like memtest86 does ([source included]("http://www.memtest.org/#downcode"))

There are other ways to manipulate a Live USB too (check out [this documentation]("http://oldfield.wattle.id.au/luv/boot.html"), note, that it might be old/outdated)

But mostly you will a kind of "[init.d]("http://www.linuxforums.org/forum/red-hat-fedora-linux/24951-start-script-boot.html")" solution if you google for it.

---

