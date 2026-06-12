---
title: "Grub Screen Background Changed"
date: 2011-06-02
forum: General Help
---

### Post by MARP1961 on 2011-06-02
I have installed 2D Unity 11.04 on an old desktop PC. This afternoon I tried a newly burnt Fedora 15 disk just to see if Gnome 3 would run (no luck, better graphics needed, started in Fallback Mode). Anyway I tried the live Fedora disk out for a while then ejected it and rebooted to restart Natty. I was surprised to see the Grub screen now has an earth/space theme background with Debian logos. What happened to the default purple background? Natty booted as normal and I have not installed Fedora to the hard drive.

---

### Post by MagneticFlux on 2011-06-02
Check if there is a line containing
```
GRUB_BACKGROUND=/path/to/file.tga
```
in your /etc/default/grub file. If there is, comment it by adding # to the beginning of the line and running
```
update-grub
```
See if the problem persists.

---

### Post by MARP1961 on 2011-06-02
Sorry, but I don't know how to access the /etc/default/grub file.

---

### Post by MagneticFlux on 2011-06-02
Open the file manager from anywhere you want. Then, press file system on the places menu to your left. Double click the folder etc and then default. Double click the file named grub and it will be opened with a text editor. You may want to post its contents to the forum.

---

### Post by linuxinstalledfromhdd on 2011-06-02
> **MARP1961 said:**
> Sorry, but I don't know how to access the /etc/default/grub file.

Have you tried the grub customizer?

You can install it from the softare center.

---

### Post by MagneticFlux on 2011-06-02
> **linuxinstalledfromhdd said:**
> Have you tried the grub customizer?

You can install it from the softare center.

It once worked for me, but now it just shows things in a mixed up manner, after a kernel update. So it does not work now.
And it is not on the software centre, it has a separate ppa.

Edit: Found it, ppa:danielrichter2007/grub-customizer if you want to try
Edit 2: Tried it, and it shows all my Ubuntu entries in a custom file, but actually there is only Pardus on that. (For some obscure reason update-grub finds it but does not add it automatically)

---

### Post by MARP1961 on 2011-06-03
Thanks for all the helpful advice. I might try Grub Customizer sometime; but actually the new Grub screen looks as good as the default so I'll keep it for now. Obviously the Fedora 15 disk altered the grub background somehow.

---

### Post by MagneticFlux on 2011-06-03
I have also heard that if you put an image in /boot/grub directory it would become the GRUB background... Not sure though. (and do not forget to run update-grub on the terminal after that)

---

