---
title: "Gtk Web Browser!!!"
date: 2006-06-27
forum: General Help
---

### Post by Gonzakpo on 2006-06-27
Hello everyone, hola a todos.

I've looking for a lightweight web browser BUT i couln'd found anyone yet (yes i know that dillo, link, etc. exists, but they suck :P)

Yesterday, searching, i found this [http://www.osnews.com/story.php?news_id=8322](http://www.osnews.com/story.php?news_id=8322)

Netfront is the name of the GTK browser and i want to try it out BUT the problem is that i don't know how to install it, and the readme files are in chinese!! :S.

You can download the package from here [http://www.access.co.jp/nf/data/NF32SAR20LINUXGTKD.zip](http://www.access.co.jp/nf/data/NF32SAR20LINUXGTKD.zip)

Well, that's all. I hope anyone can help me. 

Also, if you know a REALLY GOOD gtk browser, don't hesitate to tell me about it!.
I'm trying to optimize my computer because it's an old one, that's why I'm asking for this.

Thanks!

---

### Post by 23meg on 2006-06-27
I'm not sure if it will be light enough for your purposes (you didn't list specs) but check out Epiphany.

---

### Post by Gonzakpo on 2006-06-27
I forgot to mention something! 

the package link i posted is for the GTK+ version (3.2) 

But in the OSNEWS web, they recommend the GTK version, but i couldn't find it. Anyway, the "news" from OSNEWS it's older than the package, so maybe the GTK+ bugs that they mention are already fixed.

---

### Post by Gonzakpo on 2006-06-27
My specs are:

Celeron 850 Mhz 
Bus 100
256 Dimm Ram
HD 20 GB
video 16mb

Also, I'm using XFCE! not Gnome! 

Goodbye

---

### Post by tobiaspb on 2006-06-27
Hi.

Thanks for mentioning it. It has the wrong permissions to get it to execute so you have to change the permissions to get it to work.

Go into where you unpacked it and enter the directories: NF32SAR10LINUXGTKD/NF32SAR10LINUXGTKD/proj/ExecutableFile

And type in:

```
chmod 755 netfront
```

Now you should be able to run it with:

```
./netfront
```

Move the file to a directory in your path (like /home/<youruserdir>/bin) and you just have to type netfront to get it running, or add a icon in your menus. :-)

I hope this helped.

- Pabl2k

---

### Post by Gonzakpo on 2006-06-27
WOW! thank you for answering sooo fast and wasting your time on my problem :)

But i don't understand something, when you used chmod or execute ./netfront
there isn't any folder called like that ("netfront"). 
Maybe I'm making a mistake, or you get confused. Probably it's my mistake, I'm still in the process of learning! :)

Well, i'll wait for your answer! :)

---

### Post by Gonzakpo on 2006-06-27
also, there are two folders! one that says MANTAVISTA and another that says REDHAT

which you I chose if I'm using xubuntu? :s

---

### Post by Gonzakpo on 2006-06-27
i'VE already solved it the questin about the directory, it was wrong.

I  run the Red hat version, now i'll test the one for montevista...

---

### Post by yarlson on 2006-06-27
[QUOTE=Gonzakpo]Hello everyone, hola a todos.

I've looking for a lightweight web browser BUT i couln'd found anyone yet (yes i know that dillo, link, etc. exists, but they suck :P)

Yesterday, searching, i found this [http://www.osnews.com/story.php?news_id=8322](http://www.osnews.com/story.php?news_id=8322)

Netfront is the name of the GTK browser and i want to try it out BUT the problem is that i don't know how to install it, and the readme files are in chinese!! :S.

You can download the package from here [http://www.access.co.jp/nf/data/NF32SAR20LINUXGTKD.zip](http://www.access.co.jp/nf/data/NF32SAR20LINUXGTKD.zip)

Well, that's all. I hope anyone can help me. 

Also, if you know a REALLY GOOD gtk browser, don't hesitate to tell me about it!.
I'm trying to optimize my computer because it's an old one, that's why I'm asking for this.

Thanks![/QUOTE]


Try [dillo]("http://packages.ubuntulinux.org/dapper/web/dillo")

---

### Post by Gonzakpo on 2006-06-27
first, i linked the wrong package, this works better, but still buggy

[http://www.access.co.jp/nf/data/NF32SAR11LINUXGTKD.zip](http://www.access.co.jp/nf/data/NF32SAR11LINUXGTKD.zip)

Also, i couldn't try the GTK (1.2.x) version (netfront 3.1) , :S ...if anyone found it, please post the link here! 

Anyway, I'm dissaponted, the browser  worked even better than dillo, but it's not that fast, it almost freeze my computer! (probably the GTK 1.2 version works better!) ...

---

