---
title: "why remote desktop is slow on ubuntu ?"
date: 2010-01-06
forum: General Help
---

### Post by ibrahim.k on 2010-01-06
Hi,
I have this network
desktop ultimate edition 2.4 (ubuntu 9.4)
laptop ubuntu 9.10
ethernet network
on ubuntu remote desktop is slow in general
on windows much faster !

is there anything special that I should do ?

---

### Post by ibrahim.k on 2010-01-06
help !

---

### Post by Ghost-1-0-1 on 2010-01-06
so r u tryin to access windows from ubuntu using remote desktop? sorry just need u to clarify

---

### Post by ibrahim.k on 2010-01-06
I am trying to access ubuntu using ubuntu it is working but it is slow thats it

---

### Post by Ahadiel on 2010-01-06
> **ibrahim.k said:**
> I am trying to access ubuntu using ubuntu it is working but it is slow thats it

Do you have compiz (Desktop Effects) enabled on the computer you are trying to remote desktop in to?

---

### Post by gradinaruvasile on 2010-01-06
> **ibrahim.k said:**
> Hi,
I have this network
desktop ultimate edition 2.4 (ubuntu 9.4)
laptop ubuntu 9.10
ethernet network
on ubuntu remote desktop is slow in general
on windows much faster !

is there anything special that I should do ?

There are 2 different technologies here:
Ubuntu remote desktop uses VNC. Windows remote desktop uses RDP. 
RDP is faster than VNC by design. And the RDP server is only available for Windows and cannot be used by other operating systems, so dont ask why it is not used by Ubuntu aswell.

So, Ubuntu remote desktop != Windows remote desktop.


One thing is to use another remote desktop client and use lower colors (such as 256). I recommend (and use myself) Remmina, that is MUCH faster and has more features than the default Ubuntu remote desktop viewer (for both VNC and RDP protocols). You can get it here:

[https://launchpad.net/~llyzs/+archive/ppa](https://launchpad.net/~llyzs/+archive/ppa)

Read the installation instructions from the page.

Oh, and disable desktop effects on the target machine.

---

