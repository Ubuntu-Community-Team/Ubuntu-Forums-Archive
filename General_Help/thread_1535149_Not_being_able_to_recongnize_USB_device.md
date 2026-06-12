---
title: "Not being able to recongnize USB device"
date: 2010-07-20
forum: General Help
---

### Post by jkid on 2010-07-20
a samsung mp3 yp-u2j to be exact 






```
jkid@jkid-laptop:~$ sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.31 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Phoenix
	Version: F.14
	Release Date: 04/27/2006
	Address: 0xE5D20
	Runtime Size: 107232 bytes
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		ACPI is supported
		USB legacy is supported
		AGP is supported
		BIOS boot specification is supported


```


```
jkid@jkid-laptop:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```





this what ive tryed so far!!

---

### Post by OU_Guy on 2010-07-20
Does that mp3 have any linux drivers? If not, you could maybe mount and remount and see if you could just access the folders.

---

### Post by jkid on 2010-07-20
no that i know...and i have a hp pavilion dv4000 and jaunty....




it doesnt even mount like nothing happens when i plug it in

---

### Post by jkid on 2010-07-21
bump!!

---

### Post by muteXe on 2010-07-21
Like OU_guy suggested, have you actually tried mounting it manually??

---

### Post by jkid on 2010-07-21
no ihavent!!! cuz idont really know where is mount it at!!!

---

### Post by muteXe on 2010-07-22
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

read the bit on manual mounting.

---

