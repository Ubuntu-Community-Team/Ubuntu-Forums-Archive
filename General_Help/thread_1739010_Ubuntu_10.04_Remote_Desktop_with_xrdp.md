---
title: "Ubuntu 10.04 Remote Desktop with xrdp"
date: 2011-04-25
forum: General Help
---

### Post by ItecKid on 2011-04-25
Hello, all,

I am trying to enable rdp server on my ubuntu machine.  I installed xrdp using apt-get, but when I try to connect (setting protocol to sesman-X11rdp) it authenticates, but dies with the error "only supporting 8 and 16 bpp rdp connections".

Can anyone help me out with this error?

---

### Post by ItecKid on 2011-04-25
Ttt

---

### Post by greggc2006 on 2011-12-18
> **ItecKid said:**
> Hello, all,

I am trying to enable rdp server on my ubuntu machine.  I installed xrdp using apt-get, but when I try to connect (setting protocol to sesman-X11rdp) it authenticates, but dies with the error "only supporting 8 and 16 bpp rdp connections".

Can anyone help me out with this error?

Did you find the answer to this? I am having the same problem and Google gives me no pages that my 'newb' brain can make sense of!!!

I'm running 11.10 on both client and server if there are any fundamental differences in what you do to fix it

---

### Post by benjwgarner on 2012-03-10
> **ItecKid said:**
> Hello, all,

I am trying to enable rdp server on my ubuntu machine.  I installed xrdp using apt-get, but when I try to connect (setting protocol to sesman-X11rdp) it authenticates, but dies with the error "only supporting 8 and 16 bpp rdp connections".

Can anyone help me out with this error?

On the Windows machine you are using to connect to xrdp, open up the RDP window and click "Options". Select the "Display" tab and change the color depth to "High Color (16 bit)". This solved the error for me.

---

