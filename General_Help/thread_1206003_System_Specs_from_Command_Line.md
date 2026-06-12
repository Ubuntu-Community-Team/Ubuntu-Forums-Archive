---
title: "System Specs from Command Line"
date: 2009-07-06
forum: General Help
---

### Post by DnDer on 2009-07-06
I have a server with unknown specs, but I can tell it's running Linux (I saw something with "/hda001" or something similar whiz by during boot). But it's old, and I need to know exactly what's on it, so I can determine what distro will run on the thing.

Is there a command for this? All I REALLY need is HD capacity, Processor speed and RAM.

---

### Post by LowSky on 2009-07-06
type

```
uname -a
```

otherwise look at this
[http://linux.about.com/library/cmd/blcmdl1_uname.htm](http://linux.about.com/library/cmd/blcmdl1_uname.htm)

---

### Post by JC Cheloven on 2009-07-06
If I understand, you want to find out your hardware specs. 

For HD capacity:```
df -h
``` and/or ```
sudo fdisk -l
```

For RAM memory:```
free -m
```

For the linux version rou're on: ```
uname -a
```

For cpu's info ```
sudo lshw -class cpu
```
EDIT: look at "size" of your cpu0 to find out the cpu frequency.

Have a look at man lshw, as it can give you a lot of info about your system.

---

### Post by raronson on 2009-07-06
```
uname -a
```Will give you kernel, OS, and processor info

```
lspci
```Will show all devices on the PCI bus

```
df -h
```Will give you human-readable output for the size of devices mounted.

```
free -m
```Will give you the amount of memory in megabytes.

As a starting point...

Hope this helps.  See man pages for these commands.

---

### Post by raronson on 2009-07-06
Lol, I think we posted at the same time, JC.  Thanks for throwing in lshw.  It didn't occur to me.

---

### Post by jonobr on 2009-07-06
If your feeling noncli, you could always, get hwinfo from synpatic

---

### Post by jonobr on 2009-07-06
AHHHHHHH
Rereading the post, you specifically mentioned cli:-)

Ignore my last post!!

---

### Post by sedawk on 2009-07-06
```

#CPU-INFO
cat /proc/cpuinfo
#MEM-INFO
cat /proc/meminfo

```

During the boot process many messages are written
to the message buffer, which you can view using
"dmesg". E.g. do
```

dmesg >~/dmesg.out

```
It is easy now to open the output file dmesg.out in
an editor. This file will tell you about
the hardware found during boot, e.g. harddisks,
network interfaces, etc.

---

### Post by blueridgedog on 2009-07-06
```
sudo lshw
```

---

### Post by capscrew on 2009-07-06
If you don't mind downloading a script; I use a script called **sysinfo** from [**_www.pixelbeat.org/scripts_**]("http://www.pixelbeat.org/scripts")

This is the output from one of my really old boxes```
sudo sysinfo
============= Drives =============
/dev/scd0: Model=CRD-8400B , FwRev=1.03 , SerialNo=1999/04/13
/dev/sda: Model=WDC WD800JB-00FMA0 , FwRev=13.03G13, SerialNo=WD-WMAJ95264393, Size=80.0 GB
0x90909090
============= CPUs =============
model name	: Pentium III (Katmai)
============= MEM =============
352 MiB
============= PCI =============
-[0000:00]-+-00.0  Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
           +-01.0-[0000:01]----00.0  ATI Technologies Inc 3D Rage Pro AGP 1X/2X
           +-07.0  Intel Corporation 82371AB/EB/MB PIIX4 ISA
           +-07.1  Intel Corporation 82371AB/EB/MB PIIX4 IDE
           +-07.2  Intel Corporation 82371AB/EB/MB PIIX4 USB
           +-07.3  Intel Corporation 82371AB/EB/MB PIIX4 ACPI
           \-0f.0  3Com Corporation 3c905C-TX/TX-M [Tornado]
============= USB =============
Bus 001 Device 001: ID 0000:0000  

```

---

