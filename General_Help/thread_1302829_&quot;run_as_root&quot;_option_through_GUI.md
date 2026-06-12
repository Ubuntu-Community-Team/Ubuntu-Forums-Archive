---
title: "&quot;run as root&quot; option through GUI?"
date: 2009-10-27
forum: General Help
---

### Post by Roasted on 2009-10-27
Say I want to edit /etc/fstab. That requires root. Typically users just do this through terminal. Well, is it possible for me to navigate to /etc/fstab in the GUI and from there do something to put in my root PW and launch the editor from there? Or do I HAVE to use terminal to launch config files like that?

---

### Post by nemiux on 2009-10-27
Wait. Why can't you access etc folder? Is there an error or anything?

---

### Post by alphaniner on 2009-10-27
See [this]("http://ubuntuforums.org/showthread.php?t=1301870").  Note especially posts 3 **and** 4.

But what is so difficult about

```
gksu gedit /etc/fstab
```

?

Edit:

> ...put in my root PW...

Actually none of this will work if you're not using sudo.

---

### Post by CharlesA on 2009-10-27
Probably a permission denied error.

You can always gksudo nautilus, or gksudo gedit

EDIT: ninja'd. O_o

EDIT2: Note to self: it's gksu, not gksudo.

---

### Post by sisco311 on 2009-10-27
Just install [nautilus-gksu]("apt://nautilus-gksu") (apturl link, click to install). Then right click on the file and select *Open as administrator*

---

### Post by rippin on 2009-10-27
> **Roasted said:**
> Say I want to edit /etc/fstab. That requires root. Typically users just do this through terminal. Well, is it possible for me to navigate to /etc/fstab in the GUI and from there do something to put in my root PW and launch the editor from there? Or do I HAVE to use terminal to launch config files like that?

It's a backhanded way, but Alt+F2 the command gksu <editor> or gksu <file manager>.

---

### Post by oldfred on 2009-10-27
You can open with gksudo gedit from the open with in Nautilus. after you do it once it becomes a choice in open with, do you do not have to type anything. 

Use Naulitus/file browser, places, computer, find your filesystem, drill down thru /boot/grub so you can see menu.lst. Do not double click as it will not let you save it but right click, choose open with, in the open with window scroll to the bottom Open with other Application, at bottom where it says use other application, click on it and it will open a single line, type in gksudo gedit and it will open the file in superuser mode so you can save it. It may seem long but is easy once you right click and scroll down.

---

### Post by Roasted on 2009-10-27
> **alphaniner said:**
> See [this]("http://ubuntuforums.org/showthread.php?t=1301870").  Note especially posts 3 **and** 4.

But what is so difficult about

```
gksu gedit /etc/fstab
```

?

Edit:



Actually none of this will work if you're not using sudo.

It's not. It's just I noticed with Windows you can right click and select run as administrator. I was like hey wait, that'd be cool to right click a file and hit edit as root and bam - password in - window pops up for you to edit accordingly.

---

### Post by CharlesA on 2009-10-27
> **Roasted said:**
> It's not. It's just I noticed with Windows you can right click and select run as administrator. I was like hey wait, that'd be cool to right click a file and hit edit as root and bam - password in - window pops up for you to edit accordingly.

That could be handy for some things.

I'll stick to using gksudo gedit /directory/to/file if I need to edit something in the GUI as root. Otherwise I'll just stick to nano or vi. ;)

---

### Post by alphaniner on 2009-10-27
> **CharlesA said:**
> I'll stick to using gksudo gedit /directory/to/file

You already forgot your note to self. :p

---

### Post by CharlesA on 2009-10-27
> **alphaniner said:**
> You already forgot your note to self. :p

Nah, I did some googling, I guess you can use either gksu or gksudo. Unless [this thread]("http://ubuntuforums.org/showthread.php?t=397398") is wrong.

---

### Post by sisco311 on 2009-10-27
> **CharlesA said:**
> 
EDIT2: Note to self: it's gksu, not gksudo.

> **alphaniner said:**
> You already forgot your note to self. :p

gksudo is a symbolic link to gksu:
```
ls -al /usr/bin/gksu*
-rwxr-xr-x 1 root root 28176 2009-05-06 19:46 /usr/bin/gksu
-rwxr-xr-x 1 root root 14736 2009-07-30 20:15 /usr/bin/gksu-properties
lrwxrwxrwx 1 root root     4 2009-10-20 15:26 **/usr/bin/gksudo -> gksu**

```

> **Roasted said:**
> It's not. It's just I noticed with Windows you can right click and select run as administrator. I was like hey wait, that'd be cool to right click a file and hit edit as root and bam - password in - window pops up for you to edit accordingly.

That's what the nautilus-gksu package does, it provides a right click menu entry in nautilus to open a file as root.

---

### Post by CharlesA on 2009-10-27
> **sisco311 said:**
> gksudo is a symbolic link to gksu:
```
ls -al /usr/bin/gksu*
-rwxr-xr-x 1 root root 28176 2009-05-06 19:46 /usr/bin/gksu
-rwxr-xr-x 1 root root 14736 2009-07-30 20:15 /usr/bin/gksu-properties
lrwxrwxrwx 1 root root     4 2009-10-20 15:26 **/usr/bin/gksudo -> gksu**

```

*headdesk* I remember reading something about that now... Why didn't I remember it.. 



> That's what the nautilus-gksu package does, it provides a right click menu entry in nautilus to open a file as root.

That's good to know. Does it start automatically or does it have to be launched from terminal?

EDIT: It's an add-on right? I'm totally not with it today and too lazy to bother googling. :-P

---

### Post by sisco311 on 2009-10-27
> **CharlesA said:**
> 
That's good to know. Does it start automatically or does it have to be launched from terminal?

EDIT: It's an add-on right? I'm totally not with it today and too lazy to bother googling. :-P

yep, it's an add-on, once the package is installed you can right click on files in nautilus and select "Open as administrator".

---

### Post by CharlesA on 2009-10-27
> **sisco311 said:**
> yep, it's an add-on, once the package is installed you can right click on files in nautilus and select "Open as administrator".

Awesome! That's a good thing to know. *bookmark*

---

### Post by Roasted on 2009-10-27
> **sisco311 said:**
> yep, it's an add-on, once the package is installed you can right click on files in nautilus and select "Open as administrator".

Do you have to log out/back in to get it to start, or what? I'm running several projects across a few virtual machines now so I won't be able to reboot or log out (intentionally) for a day or so, but I installed it and it doesn't appear to be available.

---

### Post by fluffman86 on 2009-10-27
yeah, you have to log out. :(

---

### Post by 3rdalbum on 2009-10-28
Or "killall nautilus", but be careful that Nautilus isn't doing any work at this time :-)

---

### Post by Roasted on 2009-10-28
> **3rdalbum said:**
> Or "killall nautilus", but be careful that Nautilus isn't doing any work at this time :-)

I think I'll just try to be a good little patient computer user and wait until I can intentionally afford to power these virtual machines off to make the change. :)

---

### Post by jeffus_il on 2009-10-28
You can open a terminal and run > sudo su
From then on you will be root with the "#" prompt
Anything you run from this prompt will of course run as root e.g. gedit

**_"Let the sudoer beware"_** (or the su-er)

A file manager like pcmanfm has an option to open a folder as root.

There must be a myriad of ways you can damage your system!

---

