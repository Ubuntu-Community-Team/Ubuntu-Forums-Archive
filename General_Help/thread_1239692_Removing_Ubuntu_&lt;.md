---
title: "Removing Ubuntu :&lt;"
date: 2009-08-13
forum: General Help
---

### Post by KevinEvans on 2009-08-13
I need some help removing Ubuntu (i'm not sure if this is the right place...). I just installed Ubuntu on a different computer using wubi, and i need it removed on my current computer and the boot menu :/ 

I'm currently running Windows Vista and i have no idea what to do :( I read somewhere to boot from the vista cd and execute 'bootrec.exe /fixmbr' but that didnt do anything :\  

Bah, i just need to remove Ubuntu from the bootmenu, and i'll be happy :D

cheers
kevin

---

### Post by sblunix on 2009-08-13
Sooo.... You're not using GRUB?

---

### Post by KevinEvans on 2009-08-13
Edit: I am..?

Meh, when is start my computer, window's boot chooser (or w.e its called) gives me 3 options for win xp, win vista, and ubuntu. When i choose ubuntu, grub shows up and yeah...

---

### Post by michy99 on 2009-08-13
So the Ubuntu you want to remove is also Wubi install?

---

### Post by KevinEvans on 2009-08-13
Yeah...

---

### Post by michy99 on 2009-08-13
In that case, see if this helps:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by HermanAB on 2009-08-13
If it is Wubi, just boot into Windows and delete the Wubi file.

---

### Post by KevinEvans on 2009-08-13
Fixed it :) I used EasyBCD, worked like a charm.

---

### Post by bodhi.zazen on 2009-08-13
> **KevinEvans said:**
> Edit: I am..?

Meh, when is start my computer, window's boot chooser (or w.e its called) gives me 3 options for win xp, win vista, and ubuntu. When i choose ubuntu, grub shows up and yeah...

Umm ... yes you are. Wubi uses the windows boot loader. 

See [img]https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=boot-screen.jpg[/img]

If you installed with wubi this is a screen shot of your boot options. Note the words "Windows Boot Manager" on the top :twisted:

If you do not get this, then you did not install with wubi, and instead need to remove grub, which is different.

---

