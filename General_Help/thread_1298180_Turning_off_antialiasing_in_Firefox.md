---
title: "Turning off antialiasing in Firefox"
date: 2009-10-22
forum: General Help
---

### Post by monkman on 2009-10-22
ubuntu 9.10, 32bit, firefox 3.5.3.

i would like to know how to turn off the antialiasing in firefox. since the options in gnome have no effect in firefox.

thx!

---

### Post by monkman on 2009-10-23
for me it works with this:

create ~.fonts.conf

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts.conf file to configure system font access -->
<fontconfig>

<!-- Antialias -->

<match target="font"><edit mode="assign" name="antialias">
<bool>false</bool>
</edit>
</match>
```

---

### Post by mahy on 2009-10-30
Well, that solution is nice, it definitely turns the antialiasing in Firefox completely off, but that's not what I wanted. I just want to lower down the antialiasing to the level I use everywhere else in Gnome (optimized for LCD with full hinting).

---

### Post by monkman on 2009-10-31
you can change the settings in the "details" of your fonts...


[http://yfrog.com/efantialiasingp](http://yfrog.com/efantialiasingp)

---

### Post by ~unknown on 2009-10-31
> **mahy said:**
> Well, that solution is nice, it definitely turns the fonts in Firefox completely off, but that's not what I wanted. I just want to lower down the antialiasing to the level I use everywhere else in Gnome (optimized for LCD with full hinting).

I found a guide ([http://www.webupd8.org/2009/07/fix-fonts-in-firefox-35-and-ubuntu.html](http://www.webupd8.org/2009/07/fix-fonts-in-firefox-35-and-ubuntu.html)) on the internet that worked for me.
Make a .fonts.conf file in your home directory, and add these lines in it: ```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font" >
<edit mode="assign" name="rgba" >
<const>rgb</const>
</edit>
</match>
<match target="font" >
<edit mode="assign" name="hinting" >
<bool>true</bool>
</edit>
</match>
<match target="font" >
<edit mode="assign" name="hintstyle" >
<const>hintfull</const>
</edit>
</match>
<match target="font" >
<edit mode="assign" name="antialias" >
<bool>true</bool>
</edit>
</match>
</fontconfig>
```That makes Firefox use full hinting, and it seems to be optimized for LCD.
I haven't tried the terminal part of the guide because I don't know if it's safe, someone please check it.

---

### Post by 6205 on 2009-10-31
Yes this is very annoying, however pasting this into terminal will fix it and you don't need to create some custom configuration file

[COLOR="DarkRed"]sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig[/COLOR]

---

### Post by ~unknown on 2009-10-31
Okay, I didn't read the guide properly, they were 2 different fixes to the problem. They both work.

---

### Post by mahy on 2009-11-01
> **monkman said:**
> you can change the settings in the "details" of your fonts...


[http://yfrog.com/efantialiasingp](http://yfrog.com/efantialiasingp)

Sorry, I don't know whom you were referring to, but in case it was me, then you quite missed the point. :) My settings in Gnome are just fine, no need to adjust, but they don't apply to Firefox. I must try some ways other people posted, and keep asking if it doesn't work...

---

### Post by mahy on 2009-11-01
> **6205 said:**
> Yes this is very annoying, however pasting this into terminal will fix it and you don't need to create some custom configuration file

[COLOR="DarkRed"]sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig[/COLOR]

Great suggestion! I don't know how you came up with it, but it works! I should be writing those things down, unfortunately it's not the first such tweak I had to do in Karmic to make it more suitable.

Vidno, že Slováci sa vyznajú, hehe :P

---

### Post by another_sam on 2009-11-08
sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig

worked for me too. thank you!

this bug 67226:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/67226](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/67226)

---

### Post by tillerdemon on 2010-11-16
> **6205 said:**
> Yes this is very annoying, however pasting this into terminal will fix it and you don't need to create some custom configuration file

[COLOR=DarkRed]sudo rm /etc/fonts/conf.d/10*
sudo dpkg-reconfigure fontconfig[/COLOR]

I know this is an OLD post, but I just wanted to refresh it, I just tried this and it fixed all my issues.

Thanks,

Tiller

---

### Post by nightmorph on 2010-12-15
I don't like the "nuke everything until something works" solution, but in this case, removing the config files from /etc was the only thing that worked to bring Firefox in-line with my desktop settings.

I only use the MScore fonts, which look best with antialiasing disabled entirely. None of the ~/.fonts.conf suggestions in this thread had any effect on Firefox's antialiasing settings. Wiping the conf.d files in /etc worked just fine.

It's not the most flexible solution, and it has to be performed every time I upgrade font-related packages, but it works. No more eyestrain. No more struggling to focus on blurry fonts in my browser. It makes my Ubuntu environment useful again.

---

### Post by antevans on 2012-03-13
Ahh, that's better.

---

### Post by jgor on 2012-05-09
> **monkman said:**
> for me it works with this:

create ~.fonts.conf

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts.conf file to configure system font access -->
<fontconfig>

<!-- Antialias -->

<match target="font"><edit mode="assign" name="antialias">
<bool>false</bool>
</edit>
</match>
```

I used your code and it made fonts nice and crisp for Firefox. I just feel the need to say its missing the </fontconfig> closing tag at the end. I'm a bit of a perfectionist. :)

---

