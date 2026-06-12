---
title: "Command Nautilus Opens ROX-Filer"
date: 2010-07-13
forum: General Help
---

### Post by Mark76 on 2010-07-13
Please help me to put it right.

---

### Post by deathadder on 2010-07-13
Do you mean when you run 'nautilus' from the command line you get rox-filer instead? Or is this from a launcher shortcut? If the later you can right click on the short cut and modify the "command".

If you're getting it from the command line there's 2 things I can think of at the moment, first off have you created an alias? To find out run the following command:
```
alias | grep nautilus
```
If that returns something like "alias nautilus='rox-filer'" then you have, and you'll need to remove it. It's probably stored within your ~/.bashrc file. Have a look through there for the line "alias nautilus='rox-filer'" and remove it. Once that's done you'll need to resource your bashrc.
```
source ~/.bashrc
```
If you haven't setup an alias by mistake then you may have created a symlink somehow. To check that run the following command:
```
ls -lh `which nautilus`
```
That should return the following:
```
-rwxr-xr-x 1 root root 1.2M 2009-07-17 15:44 /usr/bin/nautilus
```
If it shows something like this, then you've created a symlink and I'm not entirely sure how to fix that (without reinstalling nautilus):
```
-rwxr-xr-x 1 root root 1.2M 2009-07-17 15:44 /usr/bin/nautilus -> /usr/bin/rox-filer
```
You could probably rm /usr/bin/nautilus if it is a symlink the do a apt-get install nautilus.

---

### Post by Mark76 on 2010-07-13
Hi Deathadder

I originally got into this pickle by following the instructions in this thread (I wanted to see if it still worked).

[http://ubuntuforums.org/showthread.php?t=48169](http://ubuntuforums.org/showthread.php?t=48169)

So ls -lh `which nautilus` just returns

-rwxr-xr-x 1 mark mark 37 2010-06-11 08:33 /home/mark/bin/nautilus

---

### Post by deathadder on 2010-07-14
Looking at that other post there's 2 things you can do, firstly you can unset the NAUTILUS_REPLACEMENT variable:
```
unset NAUTILUS_REPLACEMENT
```
Or if you pass the --browse flag like so:
```
nautilus --browse
```
> 
Opens normally Nautilus if:
- the environment variable NAUTILUS_REPLACEMENT is not set
- Nautilus browser mode is requested (--browse flag) (independant from settings)
- click on computer, network servers entries in Places menu
- open network drives from Places menu (if fuse not configured)
- click on trash applet and env. var. TRASHDIR is not set
- Nautilus is configured to draw the desktop and you click on desktop icons (not a feature of the script, though 

---

### Post by Mark76 on 2010-07-14
I tried the first command (unset NAUTILUS_REPLACEMENT), then I activated Nautilus from a CL and ROX popped up again. Then I removed Nautilus and all its bits from my system (and did an autoremove --purge afterwards), rebooted, typed nautilus into a CL and ROX popped up again.

The second command just gave me the Linux equivalent of "whatchutalkinboutWillis?"

---

### Post by deathadder on 2010-07-14
It'll completely remove the changes you made (from the other thread) but you can do the following and you should get nautilus back...
```

sudo mv /usr/bin/nautilus /usr/bin/nautilus.bak
sudo mv /usr/bin/nautilus.bin /usr/bin/nautilus

```
Once you've done that, you'll need to remove these from ~/.gnomerc
```

NAUTILUS_REPLACEMENT=/usr/bin/rox
TRASHDIR=$HOME/.Trash
export TRASHDIR NAUTILUS_REPLACEMENT

```
If that's all you have in the file, you can simply rename the file like so:
```
mv ~/.gnomerc ~/.gnomerc.bak
```
You can then either unset the NAUTILUS_REPLACEMENT variable, or logout and then login again.

---

### Post by Mark76 on 2010-07-14
If I don't have a .gnomerc file (and yes I did turn on "Show Hidden" in the file browser) in ~ where would it be?

---

### Post by deathadder on 2010-07-14
As far as I'm aware if you haven't got it in your ~/ then it won't get run. I believe there's a script that gets run when you start gnome that sources it if it's present...

---

