---
title: "missing auto, iface command"
date: 2010-09-20
forum: General Help
---

### Post by cuberotater on 2010-09-20
im using ubuntu 10.04 now, but i have problem with some terminal commands

auto eth0
iface eth0 inet static
address 192.168.2.201
netmask 255.255.255.0
gateway 192.168.2.1

i need to run these commands from terminal but it gives error,
```

sudo auto eth0
sudo: auto: command not found

iface eth0 inet static
iface: command not found
```

its fresh install but im missing these commands and i dunno how to install from terminal pls help??

---

### Post by nothingspecial on 2010-09-20
You need to be editing the  /etc/network/interfaces file and putting those lines in it rather than typing them straight into the terminal.

```
gksudo gedit  /etc/network/interfaces
```

---

### Post by cuberotater on 2010-09-20
> **nothingspecial said:**
> You need to be editing the  /etc/network/interfaces file and putting those lines in it rather than typing them straight into the terminal.

```
gksudo gedit  /etc/network/interfaces
```

in fact i dont get it exactly what to do.

can you post your interfaces file's content?

---

