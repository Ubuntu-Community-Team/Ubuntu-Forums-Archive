---
title: "boot error"
date: 2011-03-05
forum: General Help
---

### Post by Fry44 on 2011-03-05
Hi!

i have got a boot broblem:
[IMG]http://i68.servimg.com/u/f68/14/28/24/86/error_10.jpg[/IMG]

can soveone solv it?

i use ubuntu 10.10,than i installed windows xp on the other harddisk,and from the xp install i cant use ubuntu.

this is my first post,and i am hungarian,so sorry for the grammar,big picture, and other bad things :)

---

### Post by vivek.pandey on 2011-03-05
the problem here is computer is trying to search the boot loader the default device set here is cd that is clear from the figure you posted....you can do either of these 2
1) start your computer and when you see the manufactures,s name press f2 .. select the device from where to boot as hard drive instead of cd
this is the best option
2) insert the installation cd and boot your system

and also you can never go into ubuntu from windows neither can see its files from windows

---

### Post by Fry44 on 2011-03-05
1:i dont really understand this,but after bios starets i hit f2 as fast as i can (XD) but nothing,even if i change the hard disc boot piority.
2: if i insert install cd the installer starts not my system

---

### Post by vivek.pandey on 2011-03-05
when you press f2 you get an menu where you get to set the device from wher to boot you have to change it from cd. have you installed ubuntu?
second option is only to check if everything is right

you can also press f12 and select the boot option instead of pressing f2...change from cd

---

### Post by oldfred on 2011-03-05
Post this, so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Fry44 on 2011-03-06
ok i will do it.but under windows?

but if it means something i formated all hard drives exept the one with ubuntu.


and what if i put a boot code for ubuntu in the windows xp's boot.ini?

---

### Post by oldfred on 2011-03-06
The boot script is bash script and uses Linux tools. You need to use a liveCD if you cannot boot into your install. You may be able to use other Linux LiveCDs.

Grub2 does not like to be installed in a partition and is considered unreliable that way. The only way to use a boot.ini is with wubi or grub2 installed to a partition boot sector (PBR) and a image created of that PBR.

---

### Post by Fry44 on 2011-03-07
so,i have to boot from cd?

---

### Post by Fry44 on 2011-03-07
ok,i solve it by reinstalling ubuntu.

some data will lose,but i can get it.

---

