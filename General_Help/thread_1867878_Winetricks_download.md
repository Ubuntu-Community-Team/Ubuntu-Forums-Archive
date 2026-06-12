---
title: "Winetricks download?"
date: 2011-10-23
forum: General Help
---

### Post by mellottb12 on 2011-10-23
I'm trying to install winetricks, but the download link isn't what I would consider a "download"... It's just a page with some script. I used to use windows but switched to ubuntu just recently- so is this just the way you download things in linux? No dialog boxes, just script that you put into a text editor and turn into a program? I'm confused and I'd like to know for sure what i'm supposed to do with this link... [http://winetricks.org/winetricks]("http://winetricks.org/winetricks")

Thanks!

---

### Post by btindie on 2011-10-23
That's a script that you need to download and then run, it's akin to a windows 'batch' script but far more powerful. Type the following into a terminal to download and run the script.
```
wget -O /tmp/winetricks http://winetricks.org/winetricks
chmod +x /tmp/winetricks
sudo /tmp/winetricks
```
Explanation:
1) wget downloads the file to the /tmp directory
2) chmod sets the file as being executable
3) runs the script as root

See the [install guide]("http://code.google.com/p/winetricks/wiki/Installing") for more information.

---

### Post by mellottb12 on 2011-10-23
Thank you so much! This whole operating system is so weird to me, I've never actually done this kind of thing with windows

---

### Post by linuxinstalledfromhdd on 2011-10-23
> **mellottb12 said:**
> Thank you so much! This whole operating system is so weird to me, I've never actually done this kind of thing with windows

There is a much easier way to install PlayOnLinux and Winetricks:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

about half the way down the list..:guitar:

---

