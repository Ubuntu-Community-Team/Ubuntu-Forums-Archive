---
title: "GDM login manager is not working"
date: 2009-12-06
forum: General Help
---

### Post by parson983 on 2009-12-06
Ok, previously I attempted to uninstall the GDM thing that logs you into Ubuntu 9.10 as I wanted to return to the simple functionality of typing in my username hitting tab then typing my password and hitting return. Unfortunately I think I did it wrong and now I am stuck with the system booting and me being left with the reminents of the login scripts.

If I go to another terminal, I can log in but if I try to load GDM, it comes up with [fail] in nice red letters, so I am stuck in a rut. Is there a nice easy thing I can type to reinstall the 9.10 GDM and get to my precious files or will I be condemned to using the live CD? Any and all help will be much appreciated, many thanks, Bob.

---

### Post by parson983 on 2009-12-07
Bump

Anyone? Even just give me hint where to start, if you do I will give you a cookie!

---

### Post by simple simon on 2009-12-09
I too have a GDM that appears not to be working. Click username, type in password, ubutu loding screen, video resets a few times then back to the login screen.  Selecting recovery mode in grub and proceeding with normal boot allows me to login on the command line and startx with no problem.

So, how do we fix GDM or remove it cleanly. Wisdom anyone?

Simon.

---

### Post by MooPi on 2009-12-09
I want my cookie first.

---

### Post by MooPi on 2009-12-09
Okay I'm really not that hungry. I'll help. 
parson , have you uninstalled gdm ?

---

### Post by simple simon on 2009-12-22
MooPi

I'm still interested even tho parson983 interest seems to have faded.

I can log in through recovery mode as I said previously but not through the fancy GDM login.

I have a strong feeling that the GDM-login is not picking up the fact I have changed the default resolution and is still trying at the higher resolution.  I say this as the screen resets and the ubuntu logo is off-set and bigger before falling back to the login screen.

1) how does one find out what is going on when the GDM-login thing is doing (or not) its stuff).  Fault finding diagnostics seem to be absent in karmic

2) how do I get GDM to get the right resolution?

3) If I cant do 2) how do I get rid of GDM and boot to the command line where I can startx

Thanks in advance.

Simple.

It seems to be similar to this bug:
[https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/486722](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/486722)

---

