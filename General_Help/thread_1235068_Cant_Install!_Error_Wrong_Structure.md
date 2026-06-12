---
title: "Cant Install! Error Wrong Structure?"
date: 2009-08-08
forum: General Help
---

### Post by SuperJuicyBerry on 2009-08-08
Im new to linux and have no idea what im doing wrong.
Every time i try download something like adobe flash player i get the error message that says wrong structer and i356 or somthing like that. How do i stop it. How come io can't download stuff?  
Here are my laptop specs if they help. Im using wubi.
amd athon x2 dual 1.9ghz 
4gb ram
Windows vista home basic
ati hd 3200.
Thanks...

---

### Post by howefield on 2009-08-08
You are trying to install a 32 bit application into a 64 bit operating system or vice versa, I would guess.

Which are you running ?

---

### Post by oldos2er on 2009-08-08
Are you running 64-bit Ubuntu? Try running **sudo apt-get update && sudo apt-get install flashplugin-nonfree** in a terminal.

---

### Post by dcstar on 2009-08-08
> **SuperJuicyBerry said:**
> Im new to linux and have no idea what im doing wrong.
Every time i try download something like adobe flash player i get the error message that says wrong structer and i356 or somthing like that. How do i stop it. How come io can't download stuff?  
.......

Do **not** "download stuff", use the package manager to install any applications you need.

You are using Linux now that organises all the software for you, the Windows way of thinking no longer applies.

---

### Post by 3rdalbum on 2009-08-08
> **dcstar said:**
> Do **not** "download stuff", use the package manager to install any applications you need.

You are using Linux now that organises all the software for you, the Windows way of thinking no longer applies.

Dcstar is generally correct, but if you are using a 64-bit system you should use the alpha 64-bit Flash Player that is available from the Adobe website. The repositories just install 32-bit Flash Player and nspluginwrapper, which doesn't work very well.

The error message is "wrong architecture", not "wrong structure". Architecture refers to the type of CPU and OS you have - that is, 64-bit. You can't install 32-bit Debian packages on a 64-bit system.* This limitation doesn't apply to just ordinary program installers that you run.

* Well, you can, but that requires doing it at the command-line; installing a package from a different CPU architecture can screw things up if you're not careful.

---

