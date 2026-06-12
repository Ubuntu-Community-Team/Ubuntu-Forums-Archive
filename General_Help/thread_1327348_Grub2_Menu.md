---
title: "Grub2 Menu"
date: 2009-11-15
forum: General Help
---

### Post by blegs38552 on 2009-11-15
I am running Ubuntu 9.10 and already miss the Grub .lst editing.

I want to do the following (I was able to change my default O/S to Windows 7 using the Startup Manager app):

[LIST=1]
[*]Change to background color to blue and the foreground color to white
[*]Remove (or hide) the memtest entries
[*]Reorder the operating systems so that Windows 7 appears on top followed by Ubuntu 9.10
[/LIST]

All of this was easy in the Grub .lst file, but seems to be extremely complicated in Grub2.

Can someone give me the exact steps that I have to follow to accomplish the above?

Thanks in advance.

---

### Post by Gr8world on 2009-11-15
The colors you can change in /etc/grub.d/05_debian_theme

I didn't find how to re-range the boot menu yet..

---

### Post by Gr8world on 2009-11-15
See this tread... You'll find everything there.

---

### Post by blegs38552 on 2009-11-15
> **Gr8world said:**
> See this tread... You'll find everything there.

1. No link for thread.
2. I have looked at various threads, but to put it mildily, the process is complicated and convoluted. Please post the link, but I can only hope that someone will develop an app to give us a front end into grub2 with more features than startup manager supports today.

---

### Post by tom4everitt on 2009-11-15
Easiest is probably to change default OS to the second entry instead of the first one. This is set in the file /etc/default/grub, and the line to edit is

GRUB_DEFAULT=0

to 

GRUB_DEFAULT=1

or 

GRUB_DEFAULT=saved

(you can read more about this here [https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29))

After you've done your changes, execute:

```

sudo update-grub

```

EDIT: See oldfreds' solution below, it's much better!!!!!!
The other option, which I think should work, is to do the following changes in the /etc/grub.d folder.

Rename the file 30_os-prober to 06_os-prober (this is the script that finds windows, and giving it a lower integer prefix than 10_linux, should make your windows entry appear above your linux entry). Do this with:

```

sudo mv 30_os-prober 06_os-prober

```

EDIT: See oldfreds' solution below, it's much better!!!!!!
To remove the memtest entries, simply remove executing permission for 20_memtest86+. Do this with:

```

sudo chmod u-x 20_memtest86+

```

After you've done your changes, run

```

sudo update-grub

```

for your changes to take effect.

---

### Post by blegs38552 on 2009-11-15
> **tom4everitt said:**
> Easiest is probably to change default OS to the second entry instead of the first one. This is set in the file /etc/default/grub, and the line to edit is

GRUB_DEFAULT=0

to 

GRUB_DEFAULT=1

or 

GRUB_DEFAULT=saved

(you can read more about this here [https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29))

After you've done your changes, execute:

```

sudo update-grub

```


The other option, which I haven't tried myself, nor heard of anyone who did, is to do the following change in the /etc/grub.d folder.

Rename the file 30_os-prober to 06_os-prober (this is the script that finds windows, and giving it a lower integer prefix than 10_linux, should make your windows entry appear above your linux entry). Do this with:

```

sudo mv 30_os-prober 06_os-prober

```

Your first suggestion will only change the default O/S, which I have already done. It does not change the order (this can be done in startup manager). 

The /etc/default/grub file is read only (by design), so this is not the way to go in any case.

I will look at your link and see if it helps.

---

### Post by tom4everitt on 2009-11-15
Actually, /etc/default/grub is supposed to be editable (as I understand it).

The file that is not editable is /boot/grub/grub.cfg It is auto-generated from files in /etc/grub.d and /etc/default/grub by the update-grub command


The link is really good, I believe my second suggestion about how to change the order should work right away though. (I edited it a bit, forgot some stuff when first posting.)

---

### Post by Gr8world on 2009-11-15
oh, sorry or the link... Here it is...
[http://ubuntuforums.org/showthread.php?t=1282257](http://ubuntuforums.org/showthread.php?t=1282257)

---

### Post by ranch hand on 2009-11-15
You guys are a little out of date.

See the link in my sig.  The first 3 links in it are in depth.  All by refugees from the KK testing forum.

---

### Post by oldfred on 2009-11-15
Herman shows some of the colors and editing debian theme.
[http://members.iinet.net.au/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net.au/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)

gksudo gedit /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom

He also creates a 06_Custom entry to be the first entry. You could copy your windows entry to 06_custom and turn off the osprober in grub.

gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER="true"
from:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

After all changes:
sudo update-grub

---

