---
title: "Firefox inexplicably lost sound"
date: 2010-02-16
forum: General Help
---

### Post by FuzzWig on 2010-02-16
So yeah, like I said firefox inexplicably lost sound, or at least all the videos have stopped outputting sound.
I don't think i changed anything when this came about
Any suggestions?

---

### Post by Satoru-san on 2010-02-16
This will happen time to time if you do not use something like pulseaudio.

Here is the fix.

```
sudo /etc/init.d/alsasound restart
```

then restart firefox.

---

### Post by cheburashka.dave on 2010-02-16
I am having this same problem today, I will let you know what I find out.

---

### Post by FuzzWig on 2010-02-16
> **Satoru-san said:**
> This will happen time to time if you do not use something like pulseaudio.

Here is the fix.

```
sudo /etc/init.d/alsasound restart
```then restart firefox.

When I use that command it just says 
```
sudo: /etc/init.d/alsasound: command not found
```

---

### Post by Satoru-san on 2010-02-16
> **FuzzWig said:**
> When I use that command it just says 
```
sudo: /etc/init.d/alsasound: command not found
```

then do this

```
sudo /etc/init.d/alsa <tab> <tab>
```hit tab twice. this will either complete the command or will show you avalible options, if it completes it then type restart if it lists them either choose the best option or ask me by pasting the results.

EDIT: it might just be alsa. try /etc/init.d/alsa restart

---

### Post by cheburashka.dave on 2010-02-16
> **FuzzWig said:**
> So yeah, like I said firefox inexplicably lost sound, or at least all the videos have stopped outputting sound.
I don't think i changed anything when this came about
Any suggestions?

In synaptic I reinstalled the 'flash' package and 'flashplugin-nonfree-extrasound' package and now it works fine.

---

### Post by FuzzWig on 2010-02-17
> **Satoru-san said:**
> then do this

```
sudo /etc/init.d/alsa <tab> <tab>
```hit tab twice. this will either complete the command or will show you avalible options, if it completes it then type restart if it lists them either choose the best option or ask me by pasting the results.

EDIT: it might just be alsa. try /etc/init.d/alsa restart

Turns out it was 
```
sudo /etc/init.d/alsa -utils restart
```
This worked however I still don't have sound in firefox.

And this is what happens when I tab twice 
```
fuzzwig@RoryNConsPC:~$ sudo /etc/init.d/alsa-utils 
.adobe/
arrays
arrays.c
arrays.c~
.bash_history
.bash_logout
.bashrc
.blueproximity/
.cache/
.compiz/
.config/
.dbus/
Desktop/
.dmrc
Documents/
Downloads/
.dvdrip/
.dvdriprc
.esd_auth
.evolution/
.fofix/
fofix-3.120/
.fontconfig/

```

---

### Post by FuzzWig on 2010-02-17
> **cheburashka.dave said:**
> In synaptic I reinstalled the 'flash' package and 'flashplugin-nonfree-extrasound' package and now it works fine.

Oh? 
How do I do this?
I'm a little bit of an ubuntu noob lol

Edit: Aha! never mind i fixed it!
Instead of restart i put this instead and it worked
```
sudo /etc/init.d/alsa-utils reset
```

---

