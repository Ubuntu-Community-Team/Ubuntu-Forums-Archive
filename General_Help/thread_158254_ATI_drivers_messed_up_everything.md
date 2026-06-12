---
title: "ATI drivers messed up everything"
date: 2006-04-10
forum: General Help
---

### Post by Bishop Hill on 2006-04-10
So I was trying to fix the resolution on my laptop (an HP with an Ati 200M graphics card) using [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) , and I noticed that a part of it said something about resolution freezing at 1024x720 (or something, I dont remember exactly) on some laptop LCD, and I have a laptop LCD which freezes at 1024x720, so I though "hey, maybe I should try this!". 

And after a lot of fiddling, I managed to get to the point were I should reboot and check to see if it worked.

Now, here is my problem: When I rebooted (if that is how you say it), everything was looking normal until the system came to the point were it should load KDE (after all the initializing text and the ubuntu logo). The LCD turns itself off for about a second (not even that) and then it turns itself on again, and after that there's nothing. The screen is on, but its completly black. The fan is on and you can hear the computer working when you press ctrl+alt+del and such, but nothing happends. I also get the same result in recovery mode.

What have I done wrong and how do I fix this, preferably without formating the drive?

---

### Post by Mark_in_Hollywood on 2006-04-10
Do you get a grub menu, and if so, have you <ESC>'ed it? There should be a recovery mode. Select recovery mode with the cursor keys. Boot there and see:

dpkg --status xserver-common
dpkg --status xserver-base

report back what they say (i.e., cut and paste the results at this thread/forum)

bon chance!

---

### Post by Bishop Hill on 2006-04-11
Since I cant print or copy/paste the text, I'll just post the most necessary output:

xserver-common installed, working properly (or something)

xserver-base not found

So I'm guessing that the problem is that xserver-base is not installed. So what do I write to install it using apt-get?

---

### Post by Bishop Hill on 2006-04-11
No one? I'm sure I havent done anything wrong....

---

### Post by Rog131 on 2006-04-12
"The LCD turns itself off for about a second (not even that) and then it turns itself on again, and after that there's nothing. The screen is on, but its completly black."

Have you tried Ctrl+Alt+F8 and then Ctrl+Alt+F7 ?

---

### Post by incubus on 2006-04-12
So you can get to a console, right? I'd say, let's first get your Xserver working again.
```

$ cd /etc/X11/
$ sudo cp xorg.conf xorg.conf.bak1
$ sudo nano xorg.conf

```

You'll probably need to switch "fglrx" to "ati" or even "vesa", if that also fails.

One question: I don't know your laptop model; so 1024x768 is the default resolution? It's not widescreen?

incubus

---

### Post by Bishop Hill on 2006-04-12
Sorry for not mentioning that, but I have a HP zv6000 (that helps a lot;)), with a widescreen LCD. When I use Windows the default resolution is 1280x800.

I will report back with resluts soon.

---

### Post by Bishop Hill on 2006-04-12
Yeah, changing the driver back to vesa did the trick. Sure, I'm stuck with 1024x720, but at least I don't have to use windows anymore.

This is something that the Ubuntu crew need to fix in dapper; better graphics support for widescreen and laptops with ati graphics.

---

