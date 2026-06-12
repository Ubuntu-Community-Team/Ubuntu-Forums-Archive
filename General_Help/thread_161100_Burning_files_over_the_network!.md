---
title: "Burning files over the network!"
date: 2006-04-16
forum: General Help
---

### Post by Tubbie on 2006-04-16
I want to burn files that are on my Windows 2003 server. I have found the program K3b to burn, but the problem is, that i can't select a network path. Also it is not possible to make a link to smb://server on my desktop or something.

Anybody any idea how to let the files on my server and burn them from my desktop?

Thnx already :)

---

### Post by Fysidiko on 2006-04-16
Can you access the network files via nautilus?
I.e. is the problem that you can't access them *in K3B* or that you can't access them *at all*?

---

### Post by Tubbie on 2006-04-16
[QUOTE=Fysidiko]Can you access the network files via nautilus?
I.e. is the problem that you can't access them *in K3B* or that you can't access them *at all*?[/QUOTE]

If i try to acces files on my server through Places > Network Servers or fill out smb:// in my file browser, everything is working fine. But if i for example want to import files from the file browser into XMMS, then they can't start. and in K3b it also isn't possible to fill out smb:// at the location bar in the program.

---

### Post by vyruss on 2006-11-07
> **Tubbie said:**
> If i try to acces files on my server through Places > Network Servers or fill out smb:// in my file browser, everything is working fine. But if i for example want to import files from the file browser into XMMS, then they can't start. and in K3b it also isn't possible to fill out smb:// at the location bar in the program.

You have to mount your SMB share as a local filesystem first:```
sudo apt-get install smbfs
```and then (supposing your share is at //192.168.0.5/lala and your username is user1)```
sudo mkdir /media/lala
sudo mount -t cifs //192.168.0.5/lala /media/lala -o user1
```

Then drop the files from /media/lala into k3b and you're all set!

---

### Post by bsussman on 2006-11-07
cd burning is terribly time sensitive,

Unless you are very lucky, burn very slowly and burn the right incense at the same time,  I would expect to produce a drink coastermore often than acceptable.

It is very cheap insurance to move the data very close to the burner - like on the same machine.

I don't even play solitaire whilst CD's are burning.

---

### Post by vyruss on 2006-11-09
> **bsussman said:**
> cd burning is terribly time sensitive,

Not after the advent of Burnfree, it isn't...

---

