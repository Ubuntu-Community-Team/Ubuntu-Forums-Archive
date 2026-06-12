---
title: "help with some problems"
date: 2009-12-26
forum: General Help
---

### Post by geri1994 on 2009-12-26
hello i am beginner in ubuntu 

i have ubuntu 9.10 and nvidia geforce 5200 fx  and screen resolution 1024 - 768 every time i start pc i have to set this resolution .. ??

and second problem is i have pppoe connection and i use sudo pppoeconf to configure my connection but every time i start pc i have to run this comand 

can you help me with those 2 problems

sorry with my english

---

### Post by geri1994 on 2009-12-27
any answer pls

---

### Post by asqn34 on 2009-12-27
hi geri
use envy for your display configuration:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

For the second problems, i have no idea.

---

### Post by dillandriskell on 2009-12-27
For the second issue go to **system > preferences > startup applications **
Then click "add" and name it something like "pppoe connection" or something like that.
Then type the command you always have to type at the beginning.

Not a solution but a workaround.

---

### Post by smerral on 2009-12-27
f you find that you have to run pppoeconf each time you boot, you can try two things:

gksudo gedit /etc/network/interfaces and edit so that 'pppoe maintained' lines are before 'auto dsl-provider':

This is what mine looks like:

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

Failing that, gksudo gedit /etc/rc.local, and before the last line ("exit 0"), add:

ifconfig eth0 up
pon dsl-provider

---

### Post by smerral on 2009-12-27
sorry that's a bit unclear - mine works fine without the editing - so you need to edit to:

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider
auto dsl-provider
iface dsl-provider inet ppp

---

