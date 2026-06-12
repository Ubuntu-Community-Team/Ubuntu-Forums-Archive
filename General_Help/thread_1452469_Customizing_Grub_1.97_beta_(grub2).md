---
title: "Customizing Grub 1.97 beta (grub2)"
date: 2010-04-12
forum: General Help
---

### Post by Power-Inside on 2010-04-12
My bootloader is Grub 1.97 beta (which i persume is the grub2 new beta bootloader) and I have windows 7 and kubuntu 9.10 karmic koala in it..

Firstly , I want to change the title of my bootloader.. for eg, now it is "grub 1.97 ..." etc

Secondly, I want to add something fancy like a background or some other simmilar fancy stuff.. :KS

Finally, I want to RENAME the entries in my grub list.. for eg , it says "ubuntu blah blah" but I need to change it to "kubuntu.."


I've searched everywhere like grub2's official support wiki page and all I've stumbled was several scripts n stuff... nothing straightforward as it was to  edit menu.lst in grub1 , but sadly mine is grub2.

PS> Will all the 3 steps above get reset after the grub updates itself , like after a kernel upgrade? :(

---

### Post by darolu on 2010-04-12
1.- I don't think that is possible, at least not yet. Grub 2 is really neat, but is not very mature/refined, we have to be patient.



2.- You can add a background relatively easy: copy/paste the image you want to use to /usr/share/images/grub. You should use a .png one.

Edit the /etc/grub.d/05_debian_theme file with:

```
$ gksu gedit /etc/grub.d/05_debian_theme
```

Find the line (you can use Ctrl+F) that says:

```
for i in {/boot/grub,/usr/share/images/grub}/ubuntuwhite.{png,tga} ; do
```
Edit the line (in my example it says "ubuntuwhite." with the image you want, don't forget to leave the "**.**".

Finally, in your terminal execute:
```
$ sudo update-grub
```
It is important you run update-grub every time you make a change to grub configuration.

3.- It is not recommended to do this and I haven't tried this but it may work; edit the /boot/grub/grub.cfg file directly:
```
$ gksu gedit /boot/grub/grub.cfg
```
Search for the "menuentry" lines:
```
$ menuentry "**Ubuntu, Linux 2.6.31-20-generic**"
```
Edit the string **only**, save the file and reboot.

---

