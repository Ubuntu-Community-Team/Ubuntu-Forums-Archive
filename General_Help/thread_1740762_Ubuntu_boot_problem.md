---
title: "Ubuntu boot problem"
date: 2011-04-27
forum: General Help
---

### Post by DoeJohn__ on 2011-04-27
Hi there,

I'm currently having some severe boot problems with my current laptop. 

My laptop is an old Compaq Evo n8000c, which only has Ubuntu installed on.

The problems with Ubuntu that I am having are that Ubuntu loads as far as it can to the login screen, where once I've logged in the following error messages show and the gnome GUI never loads past the warnings:

> Could not update ICEauthority file /home/john/.ICEauthority

I hit 'Close' (the only option available for the dialog box) and continue to:

> There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

...which further leads me to:
> [B]Nautilus could not create the following required folders: /home/john/ Desktop, /home/john.nautilus.

[/B]Before running Nautilus, please create these folders or set permissions such that Nautilus can create them.

However, for the warning above, the box retains a normal alert dialog box style, whereas the others were grey and only retained one button and it looked as if the GUI hadn't loaded properly. This time, there's an 'OK' button which I select,

which loads this next alert:
> [B]Update information

Record your encryption passphrase

[/B]...


There's quite a bit of text here and a "Run this action" and "close" button, I select 'close' and still nothing happens at all and I hang at the Ubuntu desktop

I realize I might not be able to fix this problem with just commands - so I'd like to reinstall Ubuntu from CD, but I can't get in to BIOS (I might have wiped COMPAQ's system BIOS accidentally from C: if it was located there) and I can't force my computer to boot from the CD ROM (well, DVD ROM).

---

### Post by dino99 on 2011-04-27
try to boot in recovery mode, then select "repair"

---

### Post by DoeJohn__ on 2011-04-27
I don't see that option in recovery mode, I only see:

> 
resume
clean
dpkg
failsafeX
grub
netroot
root


I tried dpkg as it fit the description of 'repairing broken packages' but the laptop cannot connect to the internet and it wants to connect to download/install the updates.

---

### Post by dino99 on 2011-04-27
[http://ubuntuforums.org/showthread.php?t=909356](http://ubuntuforums.org/showthread.php?t=909356)

in case of reinstall:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by DoeJohn__ on 2011-04-27
About the reinstall: I can't access anything other than terminal, so are there any *particular* commands I can execute?

---

### Post by KegHead on 2011-04-27
Hi!

How much ram do you have?

KegHead

---

### Post by DoeJohn__ on 2011-04-27
256mb, but it used to function.

---

### Post by KegHead on 2011-04-27
Hi!

Your ram used to function?

You have no bios?

KegHead

---

### Post by DoeJohn__ on 2011-04-27
'used to function' I was referring to the fact that Ubuntu used to function as a proper operating system.

I have no idea how I can access BIOS. F10 on start-up does nothing except show me a set-up system, it doesn't let me change boot order or devices or anything of that nature.

---

### Post by KegHead on 2011-04-27
Hi!

Got it!

Try f2,  or maybe 0  "zero"

KegHead

---

### Post by DoeJohn__ on 2011-04-27
F2 and 0 both don't work, I try boot hitting those keys constantly and it just boots through to Ubuntu.

---

### Post by DoeJohn__ on 2011-04-29
Any help  please? I just cd'ed to /media/ and it only shows 'floppy0' and 'floppy' so I guess that's why it doesn't recognize the disc? Any help trying to force it to reinstall?

---

