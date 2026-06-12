---
title: "cannot open: no such file or directory"
date: 2010-12-03
forum: General Help
---

### Post by mike22112211 on 2010-12-03
im trying to get my usb wireless card to work with ubuntu feisty fawn. i have downloaded ndiswrapper to install drivers. when i try to extract it i get this message 

cannot open: no such file or directory

any ideas?

---

### Post by AlphaLexman on 2010-12-03
What are you trying to extract? a .tar? .tar.gz? .deb?

Can you post the exact command you enter to get the error message?

---

### Post by mike22112211 on 2010-12-04
i have downloaded ndiswrapper and have tried to extract it with the command

tar zxvf ndiswrapper-1.56.tar.gz

---

### Post by mike22112211 on 2010-12-08
any help?

---

### Post by wojox on 2010-12-08
> **mike22112211 said:**
> ubuntu feisty fawn. any ideas?

Upgrade. Your using an EOL which isn't secure and no longer supported.

---

### Post by mcduck on 2010-12-08
> **mike22112211 said:**
> i have downloaded ndiswrapper and have tried to extract it with the command

tar zxvf ndiswrapper-1.56.tar.gz

You need to run th command in the same location where the file is.

If you donwloaded the file to your desktop, try this:

```
cd ~/Desktop
tar zxvf ndiswrapper-1.56.tar.gz
```

---

### Post by Spyderkid on 2010-12-08
could you run lsusb

we might be able to get it working without ndiswrapper because it can be unstable.



post the results please when the wireless usb is plugged in

---

### Post by mike22112211 on 2010-12-09
i entered:

cd ~/Desktop and it seemed to work. i now have "ndiswrapper-1.56" on my desktop. i read the install page but am running into a problem. i enter:

make uninstall 
make

and get the message

make: *** no rule to make target uninstall. stop
make: *** no targets specified and no makefile found. stop

any ideas? i will continue to try to get it working. thanks

---

### Post by mike22112211 on 2010-12-09
i entered lsusb and got the following:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by mike22112211 on 2010-12-13
ive got some new info. i tried lsusb with the card plugged in and got the following message

Bus 002 Device 002: ID 148f:9021 Ralink Technology, Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

when i type iwconfig i get this:

lo        no wireless extensions.

eth0    no wireless extensions.

any ideas?

---

### Post by mike22112211 on 2010-12-15
just trying to keep this current. any ideas on how to get ndiswrapper working or the lsusb message? thanks

---

