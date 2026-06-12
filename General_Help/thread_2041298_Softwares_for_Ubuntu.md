---
title: "Softwares for Ubuntu"
date: 2012-08-12
forum: General Help
---

### Post by amir786_z on 2012-08-12
Hi there guys i am using Ubuntu 12.04 precise. I want to know some useful softwares for ubuntu.

1) Windows Blind like software for themes or any other themes software for ubuntu.
2) Icon Packager like software for changing icons.
3) Rainmeter like software 
4) Cursorfx like software for changing cursors
5) Some backup software to backup my data like Easus Todo backup.
6) Software for animated wallpapers

and some other useful softwares that u recommend..;). 
Thanks :)

---

### Post by Petro Dawg on 2012-08-12
You can try the gnome-tweak-tool to get advanced settings to change icons, cursors, and window themes.

```
sudo apt-get install gnome-tweak-tool
```After installing the tweak tool you may also want to download additional icon themes like "Faenza"

```
sudo apt-add-repository ppa:tiheum/equinox
sudo apt-get update
sudo apt-get install faenza-icon-theme

```

[http://opensource.cipto.us/how-to-install-faenza-icons-in-ubuntu-12-04/279/](http://opensource.cipto.us/how-to-install-faenza-icons-in-ubuntu-12-04/279/)

Other icon themes can be obtained similarly.
 [http://www.iloveubuntu.net/4-fancy-icon-themes-ubuntu-1204-ppa-available](http://www.iloveubuntu.net/4-fancy-icon-themes-ubuntu-1204-ppa-available)

"MyUnity" is another popular customization program available from the software center. 

"CompizConfig Settings Manager" is also useful for customizing your desktop environment. 

I know there are "data back up" programs, but from what I read they don't work so great.  I could be wrong, and hopefully someone who uses a good back up program will let you know what to use.

I'll do some looking around for animated wallpaper and post back here if I find anything.

---

### Post by johnathansmith on 2012-08-12
This should help with animated wallpapers:

[Youtube guide - how to install animated wallpapers on ubuntu 12.04]("http://www.youtube.com/watch?v=wR5KvHQbwBo")

---

### Post by amir786_z on 2012-08-14
Thanks guys :):).. Some other cool software someone know about?

---

### Post by mastablasta on 2012-08-14
for incremental scheduled backups use rsync (or gui version grsync)
 
for baremetal backups and drive cloning use clonezilla or the more user friendly redo backup.

---

### Post by Zukaro on 2012-08-14
Conky is like Rainmeter, but much much harder to use.

---

### Post by mastablasta on 2012-08-14
> **Zukaro said:**
> Conky is like Rainmeter, but much much harder to use.
 
or if you use KDE (Kubuntu) you have various widgets you just click and then they show on desktop.

---

### Post by sienile on 2012-08-14
Have you look in the Ubuntu Software Center? There's lots of software specially tweaked to run great in Ubuntu. 95% of everything installed on my PC is from there.

---

### Post by lukeiamyourfather on 2012-08-14
> **amir786_z said:**
> 
1) Windows Blind like software for themes or any other themes software for ubuntu.


Themes within each desktop environment can be tweaked and changed. There's also multiple desktop environments for Ubuntu like GNOME, KDE, Xfce, LXDE, and many others (Fluxbox, Enlightenment, etc.). This gives you far more options than simple theme software like WindowsBlinds. 

> **amir786_z said:**
> 
5) Some backup software to backup my data like Easus Todo backup.


Ubuntu has backup software already installed called Deja Dup. There are a lof other options in the repositories if you don't like that one including command line options (rsync and cron, duplicity).

---

### Post by amir786_z on 2012-08-14
Thanks guys for the replies. :):).. 
1) For backup i will try Redo Backup
2) For Rainmeter i will try screenlets or Kubuntu gadgets
3) For themes i will use emerald and and Kubuntu settings
4) For cursors and icons again kubuntu settings 

Kubuntu is awesome :) loving it already.

---

### Post by amir786_z on 2012-08-16
Hey there guys it seems screenlets have some issue with Kubuntu 12.04.?? Its not working. :(

---

### Post by mastablasta on 2012-08-16
what issues exactly are you having?

---

### Post by amir786_z on 2012-08-17
> **mastablasta said:**
> what issues exactly are you having?

It wont start and keeps on crashing.:(

---

### Post by kemtnbkr on 2012-08-17
Conky is like Rainmeter, but as Zukaro stated earlier, it is more difficult to use.  

Having used both, I think after you get past the curve, conky is easier to use-- it requires editing a text file rather than clicking around, but the options make sense, etc.  There is a massive thread somewhere on this forum that would point you more in the right direction for using conky.

Personally, I like Conky.  It is so lightweight as to be completely unnoticeable.  Just expect some setup effort, no plug-and-play.

---

### Post by amir786_z on 2012-08-21
so some one knows whats wrong with screenlets? it works on kubuntu 12.04 or not?

---

### Post by oldos2er on 2012-08-21
You should start a new thread for your Kubuntu screenlets question. Also if your original question has been answered, please mark the thread as 'Solved' under Thread Tools.

---

