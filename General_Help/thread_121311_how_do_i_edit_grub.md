---
title: "how do i edit grub"
date: 2006-01-24
forum: General Help
---

### Post by electpoopie on 2006-01-24
Ok, I need to edit grub so that i can NOT dual boot, if you know what I mean

ok just to let u no windows and ubuntu are on two different harddrives

---

### Post by Elvish Legion on 2006-01-24
[QUOTE=electpoopie]Ok, I need to edit grub so that i can NOT dual boot, if you know what I mean[/QUOTE]


Why do you want to do this?

---

### Post by RAOF on 2006-01-24
Well, the file that you want to edit is /boot/grub/menu.lst - that's where grub reads its menu stuff from.  You'll need root privs to edit it - just type ```
sudo gedit /boot/grub/menu.lst
``` into a console, and you'll be set.
(oh, and that's a letter 'l', rather than a '1', or a '|' :))

---

### Post by RAOF on 2006-01-24
Oh, and to remove the ability to dual-boot, just comment out (add a # to the start of the line) the section that looks like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by electpoopie on 2006-01-24
ok i tried that but it wont work and btw my ubuntu and windows r on 2 seperate hard disks
lemme upload my menu.lst

---

### Post by RAOF on 2006-01-24
Change this bit:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```
to
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
#title		Windows XP Media Center Edition
#root		(hd1,1)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
#title		Windows NT/2000/XP
#root		(hd1,0)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1

```
Grub will no longer have the option to boot into Windows.

---

### Post by electpoopie on 2006-01-24
nonono


i dont want that screen to pop up at allll

---

### Post by RAOF on 2006-01-24
[QUOTE=electpoopie]nonono


i dont want that screen to pop up at allll[/QUOTE]
Oh, well then look up the top of the menu.lst.  There's a line which says something like "##Uncomment the next line to hide the menu.  Pressing esc will show the menu again".  Remove the '#' from the start of the line after that.  Tada!  No more menu.

---

### Post by electpoopie on 2006-01-25
[QUOTE=RAOF]Oh, well then look up the top of the menu.lst.  There's a line which says something like "##Uncomment the next line to hide the menu.  Pressing esc will show the menu again".  Remove the '#' from the start of the line after that.  Tada!  No more menu.[/QUOTE]

sry lol sho me and wut is ur AIM, MSN, or YAHOO  ? (PM ME)
i just want it to load up like windows does and i dont wanna choose anything

---

### Post by RAOF on 2006-01-25
[QUOTE=electpoopie]sry lol sho me and wut is ur AIM, MSN, or YAHOO  ? (PM ME)
i just want it to load up like windows does and i dont wanna choose anything[/QUOTE]
I **still** don't have AIM, MSN, or YAHOO ;)

just change this:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
to
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```
It won't ask you anything, just boot straight in to Ubuntu.

---

### Post by omair.majid on 2006-01-25
change the line

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
```

to 
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout          1
```

this will select the default option after 1 second. I suggest you have a small delay ( like one or 2 seconds ) just so that when you want to choose another option you get the time to.

---

### Post by electpoopie on 2006-01-25
ty so much


P.S. GET AIM :)

---

