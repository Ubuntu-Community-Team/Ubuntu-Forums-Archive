---
title: "Fonts Mysteriously Changed In Browsers"
date: 2011-09-27
forum: General Help
---

### Post by scorchgeek on 2011-09-27
So I'm happily working along, and at one point I restart Google Chrome. Kaboom, all my fonts have changed. They also don't match my system fonts or what is listed in the preferences. Changing the Google Chrome font preferences doesn't seem to help, and I didn't change the system fonts at all. I even deleted my entire Chrome profile and had it remake a new one, and nothing changed.

Unfortunately, I don't know what font I had before. I do know the new one is different, and I think it's really ugly. The font also changed in Firefox.

Anyone ever had a similar problem and know what might have caused it or how to get it back?

---

### Post by Krytarik on 2011-09-27
Run the below command in the Terminal and handle the presumably upcoming confirmation dialog with the Tab and Enter keys. You may have missed this or another form of dialog in the first place.
```
sudo dpkg --configure -a
```Hope it works!

---

### Post by scorchgeek on 2011-09-27
No, didn't work. I have been using Chrome for about 6 months on this installation of the OS with no problems whatsoever.

---

### Post by Krytarik on 2011-09-27
Try what I posted here earlier today, though in that case, it's the other way around:

[http://ubuntuforums.org/showthread.php?p=11291427#post11291427](http://ubuntuforums.org/showthread.php?p=11291427#post11291427)

---

### Post by mcduck on 2011-09-28
Perhaps you recently installed the msttcorefonts package (or it came as dependency for something else you installed), which includes the basic fonts from Microsoft, and web pages now have available the fonts they were designed to use?

I don't know about the font options in Chrome/Chromium, but most browsers have an option to force the web pages to use the fonts you have configured in the browser settings instead of being able to choose their own fonts. You could try that, if you want, although it's more than likely to break a few badly designed web pages...

---

### Post by Jouke74 on 2011-09-28
I think there is an access issue (as usual) with the fonts.conf file in /etc/. I did a 

cp /etc/fonts/fonts.conf /home/{username here}/.fonts.conf
sudo chown {username here}:{username here} .fonts.conf

See how that works out?

If it fails delete the .fonts.conf file from your home directory.
Also, if you change your fonts in Ubuntu, you need to repeat this steps.

---

