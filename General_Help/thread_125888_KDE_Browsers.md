---
title: "KDE Browsers?"
date: 2006-02-05
forum: General Help
---

### Post by welsh_spud on 2006-02-05
I've decided to give KDE a try on my laptop, and everything is going well. I've removed Gnome programs from the K menu, and changed all the fonts sizes.

The only problem that remains is having a nice KDE browser. I've tried Konqueror, but it seems really slow.

I'm looking for something like what Epiphany is for Gnome; a browser writen in the native toolkit so everything just blends together.

Also, any ideas on how to speed up Konqueror? Like with Firefox when you use about:config to mess with maxrequests etc.

---

### Post by wanger123 on 2006-02-05
Hey there spud, I think konq is the only truly integrated kde browser. I too had a bit of trouble adapting to it, but after about 8 months I'm very happy with it.

Some people recommend opera or firefox (probably not what you want though?)

Stick with konqueror and before you know it, you may like it :-)

wanger

---

### Post by welsh_spud on 2006-02-05
Well I've done some searching about on the net, and the reason that it was taking thirty seconds plus to load every web page was because of 'IPv6'

The solution was simple, in terminal type

```
sudo nano /etc/environment
```

then add at the bottom of the file

```
KDE_NO_IPV6=true
```

Type 'ctrl + X' to exit

Now in terminal type

```
sudo nano /etc/modprobe.d/aliases
```

and change the line;

alias net-pf-10 ipv6

to...

#alias net-pf-10 ipv6

Reboot the computer and enjoy the internet!

---

### Post by wanger123 on 2006-02-05
Ahh, great advice spud! I have also done this. Unfortunately I didnt read your original post properly (missed the part about it being slow). :rolleyes: 

wanger

---

### Post by Jucato on 2006-02-05
you could also try updating KDE to 3.5.1 as it has many bug fixes, it might also speed up your Konqueror performance.

Konqueror is a really nice app, and after having noticed Firefox eating up resources, I've decided to try out konqueror, and have been quite happy with it. It's very customizable, as far as a web browser/file manager can go. Sure it doesn't have it's own themes/extensions, but I'm not quite a fan of those (yet).

I might try out Firefox 1.5.0.1 (the latest release w/ bug fixes) to see if the memory problems are fixed. If yes, I "might" go back to Firefox. Until then, I still love my Konqi. :D

---

