---
title: "Help creating script"
date: 2010-11-04
forum: General Help
---

### Post by Floven de Sorezé Stockeir on 2010-11-04
Hello everyone,

I wondered if anyone would help me (totally unknowing how scripts work) by giving a step by step walkthrough how to activate this script?

> **P4man said:**
> for those interested:

```
#!/bin/bash
# copy appropriate xorg.conf for your videocard
cp /etc/X11/default.conf /etc/X11/xorg.conf
if lspci | grep "VGA compatible controller: nVidia" 
then
    # nVidia card
    nvidia-xconfig
fi
if lspci | grep "VGA compatible controller: ATI Technologies" 
then
    # ATI card, loading opensource ati driver
    cp /etc/X11/ati.conf /etc/X11/xorg.conf
fi
```Save it as /etc/rc2.d/S01nvidia-xconfig
Make it executable.
Then copy a default (mostly empty) xorg.conf as /etc/X11/default.conf
And modify one that loads ati driver (i use the opensource) and save it as /etc/X11/ati.conf
install nvidia drivers (on a machine with nvidia graphics), and off you go. 

I guess it may give problems if you try it on a machine with an old   nvidia card no longer supported by the 185 drivers, but other than that,   works fine.

It's to have one Ubuntu install I can boot on different computers;..



Thank you very much!

Floven de Sorezé Stockeir

---

### Post by Floven de Sorezé Stockeir on 2010-11-04
bump

---

### Post by evilsoup on 2010-11-04
Check out [this website]("http://linuxcommand.org"), specifically [this webpage]("http://linuxcommand.org/writing_shell_scripts.php"). That will inform you about shell scripts[I].


[/I]Have you tried following the instructions in your quote?



Assuming you have already saved the script to /etc/rc2.d/S01nvidia-xconfig, to make it executable type into a terminal window:

chmod 755 /etc/rc2.d/S01nvidia-xconfig

To copy xorg.conf:

cp /etc/X11/xorg.conf /etc/X11/default.conf

I don't know about the rest of it, unfortunately. You should read [this]("https://help.ubuntu.com/community/RadeonDriver") in regards to ati drivers.

---

### Post by Floven de Sorezé Stockeir on 2010-11-04
Hello evilsoup, thank you for helping!

Yes, I tried following the instructions and so far I'm stuck at "Then copy a default (mostly empty) xorg.conf as /etc/X11/default.conf"

I don't have any experience whatsoever in writing shell scripts, so I'm a bit afraid to mess things up. I'm trying though, thanks for your links, I'm sure they will help.

But if you don't mind, can I humbly ask for a step by step explanation for these instructions?

"Then copy a default (mostly empty) xorg.conf as /etc/X11/default.conf
And modify one that loads ati driver (i use the opensource) and save it as /etc/X11/ati.conf
install nvidia drivers (on a machine with nvidia graphics), and off you go. "

I'm really too afraid to mess things up, as this is the first time I use the terminal actually..

Thank you.

---

### Post by Floven de Sorezé Stockeir on 2010-11-04
> **evilsoup said:**
> Check out [this website]("http://linuxcommand.org"), specifically [this webpage]("http://linuxcommand.org/writing_shell_scripts.php"). That will inform you about shell scripts[I].


[/I]Have you tried following the instructions in your quote?



Assuming you have already saved the script to /etc/rc2.d/S01nvidia-xconfig, to make it executable type into a terminal window:

chmod 755 /etc/rc2.d/S01nvidia-xconfig

To copy xorg.conf:

cp /etc/X11/xorg.conf /etc/X11/default.conf

I don't know about the rest of it, unfortunately. You should read [this]("https://help.ubuntu.com/community/RadeonDriver") in regards to ati drivers.

Thanks a lot! I'll keep looking for what the rest means, but this is already a great step forward, thank you!

---

### Post by evilsoup on 2010-11-04
Wait a moment
> It's to have one Ubuntu install I can boot on different computers;..

When you say that, what do you mean?

---

### Post by Floven de Sorezé Stockeir on 2010-11-04
> **Floven de Sorezé Stockeir said:**
> Hello evilsoup, thank you for helping!

Yes, I tried following the instructions and so far I'm stuck at "Then copy a default (mostly empty) xorg.conf as /etc/X11/default.conf"

I don't have any experience whatsoever in writing shell scripts, so I'm a bit afraid to mess things up. I'm trying though, thanks for your links, I'm sure they will help.

But if you don't mind, can I humbly ask for a step by step explanation for these instructions?

"Then copy a default (mostly empty) xorg.conf as /etc/X11/default.conf
And modify one that loads ati driver (i use the opensource) and save it as /etc/X11/ati.conf
install nvidia drivers (on a machine with nvidia graphics), and off you go. "

I'm really too afraid to mess things up, as this is the first time I use the terminal actually..

Thank you.

Hmm.. Does anyone know **where I can find the script that loads the ATI driver?** (I have ATI card)

I think that's the only thing I still need help for; searching the web doesn't help though I'm afraid, so I can only hope to find the answer here.

---

### Post by Floven de Sorezé Stockeir on 2010-11-04
> **evilsoup said:**
> Wait a moment

When you say that, what do you mean?

I have ubuntu installed on my external USB HDD. I could plug it into different computers and boot succesfully. Yesterday though I upgraded all my drivers & such, thus my install was only compatible anymore for the specific video card of my laptop. Now I can't boot into Ubuntu on a computer with a different video card.

I don't know if this script will solve my problem, but I won't know for sure until I try.

---

### Post by alphaamanitin on 2010-11-04
> **evilsoup said:**
> Wait a moment

When you say that, what do you mean?


He means he wants to set up an install on a external drive that uses all generic drivers, or scans the computer it is plugged into before a full boot into Ubuntu and automatically selects drivers that work for the individual computers hardware.  I know people have been looking into this type of thing, but I myself, cannot help.

AlphaA

---

### Post by Floven de Sorezé Stockeir on 2010-11-04
> **alphaamanitin said:**
> He means he wants to set up an install on a external drive that uses all generic drivers, or scans the computer it is plugged into before a full boot into Ubuntu and automatically selects drives that work for the individual computers hardware.  I know people have been looking into this type of thing, but I myself, cannot help.

AlphaA

Exactly!

---

### Post by Floven de Sorezé Stockeir on 2010-11-04
Bump

---

### Post by Floven de Sorezé Stockeir on 2010-11-05
bump

---

### Post by Floven de Sorezé Stockeir on 2010-11-06
really no-one knows how to make this script (on my first post)?

---

