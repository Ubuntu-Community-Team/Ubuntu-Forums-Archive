---
title: "Usb drive"
date: 2011-01-13
forum: General Help
---

### Post by L Style on 2011-01-13
when i connect my pen drive its not recognize by ubuntu 10.04. 

lachitha@lachitha-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1613 Kingston Technology DataTraveler 8GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


how can i fix this. After restarting its work. but after safety removing.. & plug again Its not work. Help:confused:

---

### Post by MARP1961 on 2011-01-13
Try installing 'usbmount' using the following command in the terminal:

sudo apt-get install usbmount

---

### Post by L Style on 2011-01-13
> **MARP1961 said:**
> Try installing 'usbmount' using the following command in the terminal:

sudo apt-get install usbmount
I'll install but didn't work
 Is there anyway to fix this

---

### Post by MARP1961 on 2011-01-13
Sorry, I know this usbmount has worked for some people. I am still having the same problem as you. The only way I can get my usb to work is to boot the computer with the usb already inserted. I now await those with more Ubuntu knowhow to help out.

---

### Post by L Style on 2011-01-13
> **MARP1961 said:**
> Sorry, I know this usbmount has worked for some people. I am still having the same problem as you. The only way I can get my usb to work is to boot the computer with the usb already inserted. I now await those with more Ubuntu knowhow to help out.

Oppss... why they didn't fix this bug.

---

### Post by L Style on 2011-01-15
> **L Style said:**
> when i connect my pen drive its not recognize by ubuntu 10.04. 

lachitha@lachitha-desktop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0951:1613 Kingston Technology DataTraveler 8GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


how can i fix this. After restarting its work. but after safety removing.. & plug again Its not work. Help:confused:

Is there anybody know how to fix this

---

### Post by L Style on 2011-01-15
bump

---

