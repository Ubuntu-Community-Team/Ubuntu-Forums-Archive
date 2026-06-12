---
title: "No fonts or text are showing"
date: 2009-09-14
forum: General Help
---

### Post by xItachi on 2009-09-14
Hi, after installing some updates yesterday with Update Manager, the next time I logged into Ubuntu, there was no text or fonts loaded in GNOME.  All other programs including Firefox do not have text or fonts either.  Check it out.

[IMG]http://i25.photobucket.com/albums/c81/xItachi/Screenshot.png[/IMG]

Any ideas?

P.S. I tried navigating to System > Preferences > Appearance > Fonts and tried to see if the font size was set to 0 or something, I increased the font size for several items and it was still ineffective.

Thanks

---

### Post by P4man on 2009-09-15
have you tried another theme?

---

### Post by xItachi on 2009-09-15
Yeah, I have tried switching to other themes besides Human

---

### Post by P4man on 2009-09-15
thats weird. perhaps its a problem with the font configuration

Maybe try this:
```

sudo dpkg-reconfigure fontconfig
```

and/or
```

sudo dpkg-reconfigure fontconfig-config

```

(I got no idea what the difference between both is, perhaps someone else can enlighten us?)

---

### Post by xItachi on 2009-09-16
P4man, I tried:

```
sudo dpkg-reconfigure fontconfig
```

I couldn't see the text, so I did this:

```
sudo dpkg-reconfigure fontconfig > /home/stephen/Desktop/log.txt
```

Then I copied the log.txt file onto my Windows partition.  It contains the following:

```
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/sazanami /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-liberation /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/vlgothic /usr/share/fonts/truetype/ttf-bengali-fonts /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/wqy /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-kannada-fonts /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/alee /usr/share/fonts/truetype/ttf-telugu-fonts /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-oriya-fonts /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/sazanami /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-liberation /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/vlgothic /usr/share/fonts/truetype/ttf-bengali-fonts /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/wqy /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-kannada-fonts /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/alee /usr/share/fonts/truetype/ttf-telugu-fonts /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-oriya-fonts /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/sazanami /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-liberation /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/vlgothic /usr/share/fonts/truetype/ttf-bengali-fonts /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/wqy /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-kannada-fonts /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/alee /usr/share/fonts/truetype/ttf-telugu-fonts /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-oriya-fonts /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/sazanami /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-liberation /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/vlgothic /usr/share/fonts/truetype/ttf-bengali-fonts /usr/share/fonts/type1/gsfonts /usr/share/fonts/truetype/wqy /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-kannada-fonts /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/alee /usr/share/fonts/truetype/ttf-telugu-fonts /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-oriya-fonts /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/truetype/kochi
Regenerating fonts cache... done.
```

Then I tried this:

```
sudo dpkg-reconfigure fontconfig-config
```

and that brought me to a blue screen with a red cursor to select options, however I cannot read the text, so maybe if it isn't any trouble you could run that command to tell me which ones to choose?

I restarted/relogged in and nothing happened.  This is the second time I have had problems after installing recommended updates from Update Manager, and now I have decided from this point on to not install any updates for Ubuntu besides the bi-annual releases.  What do you think about this?

Thanks

---

### Post by P4man on 2009-09-16
try running those from a tty. Press control alt F1. Im hoping that will at least show readable text?

---

### Post by xItachi on 2009-09-16
I was able to do that in a tty.  However, still nothing :(

---

### Post by P4man on 2009-09-16
I got no idea then :(
Perhaps you can try creating a new user, and log in with that user?
Or run xfix from the recovery console?

Im just guessing as you, I got no idea whats happening..

---

### Post by xItachi on 2009-09-16
I think I'm just going to re-install Ubuntu :( Thanks for the ideas though

---

