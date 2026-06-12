---
title: "How to prevent access to harddisk"
date: 2011-03-12
forum: General Help
---

### Post by Achilles124 on 2011-03-12
A technical question.

Is it possible to make an USB-stick with Ubuntu on it, which **cannot** access the harddisk of the computer it uses? 

So in order to prevent anyone gaining access to the computer itself.

---

### Post by HermanAB on 2011-03-12
Howdy,

That is what encryption is for.

Use EncFS, LUKS or Truecrypt.

---

### Post by Achilles124 on 2011-03-12
I want ppl to use usb-sticks with ubuntu on it on computers that won't be mine. 

To reduce the risk for the owner of the computers, I have to disable access writing to the harddisks of the computer.

Is it possible?

---

### Post by t0p on 2011-03-12
I don't know this as a fact, but I'm pretty sure you can't stop someone from accessing someone else's computer.  I think securing the third party's computer is down to the third party himself - eg. by disabling boot from usb, password-protecting bios etc.  It is i the nature of usb-loaded live operating systems to be able to access the drives of the computers it's being run on, hence rescue disks etc.

---

### Post by mr_luksom on 2011-03-12
How much access do they need on the usb stick?

If you remove the user from the sudoers list, they will be unable to mount anything not in fstab.

---

### Post by Achilles124 on 2011-03-13
The users of the USB-stick will use the stick to learn to use image-processing. 
So, all they need is internet-access.

Storing the files can be done on the USB-stick.

---

### Post by Achilles124 on 2011-03-16
okay, ty all for answwering.

---

