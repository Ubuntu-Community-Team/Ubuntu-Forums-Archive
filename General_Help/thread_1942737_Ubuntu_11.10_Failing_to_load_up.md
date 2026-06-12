---
title: "Ubuntu 11.10 Failing to load up"
date: 2012-03-18
forum: General Help
---

### Post by LORDNINIO on 2012-03-18
I'm running 11.10 on my HP Laptop as a dual boot with Windows Vista, I upgraded from 11.04. 

Recently it has been freezing up whenever I do certain tasks, such as a lot of tabs open in Firefox. The last time this happened I had to manually turn the laptop off, now everytime I try to turn the laptop on and boot into Ubuntu it hangs on a screen full of white text, usually the last line is somehting along the lines of - 

Battery state check   OK

Then it just stops there. From what I can gather from reading this and other forums, its something to do with Ubuntu thinking it is resuming rather than loading up and it just gets stuck. 

I have managed to retrieve most of my files using live cd method in another thread on here, but it won't allow me to access things like my bookmarks etc which I really could do with getting back. 

So does anyone know how I can get it to load me into Ubuntu, so I can back everything up. 

I will probably revert back to 11.04, or maybe even 10.04 once I've got my data back, as I have had a few problems since upgrading. 

Thanks in advance for your help, 

Andrew

---

### Post by LORDNINIO on 2012-03-18
Anyone, able to help on this?

I'm getting married soon, and really need access to some of the links I have stored....any help much appreciated.

Cheers

---

### Post by winh8r on 2012-03-18
Boot up the live cd and open a terminal

then enter ```
gksu nautilus
```

then navigate to the home folder of your Ubuntu install and press control +H

then copy the .mozilla directory to an external drive, this will contain all your firefox data and profiles and can be imported into another firefox folder.

---

### Post by LORDNINIO on 2012-03-18
I'll give that a try tomorrow, 

Many thanks,

Andy

---

### Post by LORDNINIO on 2012-03-19
Tried this it comes up with - 

(gksu:5428) : Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

It repeats this 4 times.

Any other ideas?

Your help is much appreciated

---

### Post by LORDNINIO on 2012-03-19
I've managed to change the access rights to vdisk, so I have access to the .mozilla folder now. 

Where is the chromium bookmarks stored, is it in the cache folder?

Thanks again, 

Andrew

---

### Post by LORDNINIO on 2012-03-19
I've found it thanks for the help, I'll mark this as solved now

Cheers,

Andrew

---

### Post by winh8r on 2012-03-19
Glad you got it sorted out.

Good Luck.

(with the data and your wedding!)

---

