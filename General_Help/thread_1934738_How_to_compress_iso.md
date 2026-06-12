---
title: "How to compress iso?"
date: 2012-03-02
forum: General Help
---

### Post by doctortonic on 2012-03-02
[B]It is possibile to compress an iso? :popcorn:
[/B]

---

### Post by winh8r on 2012-03-02
You can compress an .iso using 7zip which is available in the Ubuntu Software Centre.

Hope this helps you.

---

### Post by doctortonic on 2012-03-02
[FONT=Georgia][SIZE=2]I didn't put the question well, and for that I am sorry.

I mean, how can be an iso compressed to be burned to a cd?[/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Georgia][SIZE=2]

If I would have an 900 Mb iso or even 1300 Mb iso, and I wish to compress it to be able to be burned to a 700 Mb CD. [/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Georgia][SIZE=2]

I know that I can use a DVD or an USB stick, but in this particular case it has to be a CD.[/SIZE][/FONT][SIZE=2] [/SIZE][FONT=Georgia][SIZE=2]

**I know that there is a way to compress a .iso image**[/SIZE][/FONT][SIZE=2]  [/SIZE][FONT=Georgia][SIZE=2] because some linux distributions use some " on the fly decompressing " this is how you will have **a 700 MB bootabile CD with 900 Mb software on it.**


In my particular position, I make a .Iso image file which has more Iso's on it and I boot them with grub4dos or syslinux. (multi boot cd) [/SIZE][/FONT][SIZE=2]  [/SIZE][FONT=Georgia][SIZE=2]

The problem is that the final Iso size is about 900 M and I just can't burn it on a simple CD, but I am thinking that if I will know how linux compress and decompress the software on the fly there will be a chance to "shrink" down a little bit the image file size for fitting to the regular cd.[/SIZE][/FONT]

---

### Post by mikewhatever on 2012-03-02
Most ISOs are already compressed, so that compressing them even further probably wouldn't do much, but even if it did, you wouldn't be able to burn it to CD as image.

---

### Post by winh8r on 2012-03-02
You need to look at lzma compression or squashfs for that I believe.

hope this helps.

---

### Post by doctortonic on 2012-03-02
[FONT=Georgia][SIZE=2]***My .ISO image is created by myself in windows with:***

[B]
Xboot                            [/B][http://sites.google.com/site/shamurxboot/](http://sites.google.com/site/shamurxboot/)



It is a nice utility like 

**unetbootin                    **[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

**pendrivelinux                **[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)



*Now I have the iso, but I need to make it smaller.* I have found this: 

[/SIZE][/FONT]*[FONT=Georgia][SIZE=2]**mkzftree**[/SIZE][/FONT]*
[FONT=Georgia][SIZE=2][B]
[http://linux.die.net/man/1/mkzftree](http://linux.die.net/man/1/mkzftree)[/B]

[/SIZE][/FONT][FONT=Georgia][SIZE=2]**-z** *level*, **--level** *level*[/SIZE][/FONT] [FONT=Georgia][SIZE=2]Select compression level (1-9, default is 9). Lower compression levels are faster, but typically result in larger output.[/SIZE][/FONT][FONT=Georgia][SIZE=2] and 

xorriso

Special features:

 File content may get zisofs or gzip compressed or filtered by external processes. 

[http://scdbackup.webframe.org/xorriso_eng.html](http://scdbackup.webframe.org/xorriso_eng.html)



**But I am not good in command line.** It say that mkzftree know's how to compress an iso and has some compression levels.

**So my guess is that I have to open somehow the image in linux or mount the image as an cd, then remake the iso from linux but this time compressed.**



[]("http://linux.die.net/man/1/mkzftree")
[/SIZE][/FONT]

---

