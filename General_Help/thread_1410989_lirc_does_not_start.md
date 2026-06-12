---
title: "lirc does not start"
date: 2010-02-19
forum: General Help
---

### Post by levicivita on 2010-02-19
I have been attempting to follow the instructions from [http://forum.xbmc.org/showthread.php?t=50717]("http://forum.xbmc.org/showthread.php?t=50717") in order to set up and configure my PS3 remote.  However, I don't think lirc is working for me.

**WHAT HAS WORKED**
I have installed lirc using apt-get:

```
$ dpkg -l lirc | grep -i lirc
ii  lirc                                 0.8.6-0ubuntu2                             infra-red remote control support

```

I used blueman to pair with my PS3 Bluetooth remote control.

```
$ dpkg -l blueman | grep -i blueman
ii  blueman                              1.22+r699+201002191022~karmic              A Graphical bluetooth manager

```

```
$ cat /proc/bus/input/devices
I: Bus=0005 Vendor=054c Product=0306 Version=0000
N: Name="PS3 Remote Controller"
P: Phys=
S: Sysfs=/devices/virtual/input/input9
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=8000000000000000 7000001083c100 8c00ea00000000 6bc0000000000001 8000 1102c0000801 80168000000000 10000ffe

```

**WHAT HAS NOT WORKED**
irrecord and irw do not work for me.  the lirc daemon does not even seem to be up although I do start it manually:

```
$ sudo service lirc start
$ ps -e | grep -i lirc
$ ls /var/log/lirc*
ls: cannot access /var/log/lirc*: No such file or directory
$ dmesg | grep -i lirc

```

This seems like a very fundamental problem.  Any ideas?  

Thanks

---

