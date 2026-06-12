---
title: "booting into the command line by default on netbook remix"
date: 2009-08-22
forum: General Help
---

### Post by damarusama on 2009-08-22
I know that sounds crazy, but I was having problem with my xorg..conf lately so my computer would load directly in the command line mode... and ... it remided me that I love to work with the command line interface!

How can I make that my default startup? (apart from putting errors in my xorg.conf!) So that nor X nor gnome start at the begning?

thanks

---

### Post by RJ12 on 2009-08-22
You would have to permanently change the runlevel or backup your info and install the server desktop edition (since I believe there is no server netbook remix)

---

### Post by damarusama on 2009-08-22
Ho so having a bad line of code in my xorg.conf IS the easiest way to boot directly in command line... intersting. So if I change permanently the run level, I still can start x from the command line right ?

---

### Post by scorp123 on 2009-08-22
> **damarusama said:**
> Ho so having a bad line of code in my xorg.conf IS the easiest way to boot directly in command line... 

```
cd /etc/init.d
sudo update-rc.d -f gdm remove

```

... Voila, no more Gnome Display Manager at boot, the system stays in text mode. If you still need a graphical program you could start the GUI via this command:
```
startx
```

(... which would be totally old-school ... :D )

---

### Post by damarusama on 2009-08-22
nice! Thanks!

I realized, watching akira for the 200th time last week, that I like old school after all ;)

---

### Post by tgeer43 on 2009-08-22
Or if you're currently booting to the desktop just go to System->Administration->Services and uncheck GDM.

tgeer

---

### Post by scorp123 on 2009-08-23
> **damarusama said:**
> nice! Thanks!

I realized, watching akira for the 200th time last week, that I like old school after all ;)

Now that you will be working in text mode more often ... maybe you'd be interested to activate the text frame buffer again so you get a higher text resolution?

Please see this posting:
[http://ubuntuforums.org/showpost.php?p=6281148&postcount=73](http://ubuntuforums.org/showpost.php?p=6281148&postcount=73)

So if you know your laptop's max. resolution (e.g. 1280x800) you can then force your kernel to apply that resolution for the text mode too ... Result: you get a nice high-resolution text mode where the console has e.g. 160 x 50 characters (I just checked with the "resize" command) instead of the dull and boring 80 x 25 standard VGA that Ubuntu uses.

If you work on the console a lot having a nice high-res text mode really is a "must have". 80x25 is just too low, IMHO.

---

