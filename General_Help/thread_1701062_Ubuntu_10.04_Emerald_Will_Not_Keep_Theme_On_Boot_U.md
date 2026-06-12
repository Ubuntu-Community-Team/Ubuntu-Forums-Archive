---
title: "Ubuntu 10.04: Emerald Will Not Keep Theme On Boot Up"
date: 2011-03-06
forum: General Help
---

### Post by SexySara on 2011-03-06
I just did a clean install with Lucid and I can not seem to get Emerald to keep the theme when booting up. I have to keep pressing Alt-F2 then type... ```
emerald --replace
```I had changed the settings last time and when I booted up, emerald stayed the same. I'm not sure how I changed them, I forgot. I know I did something with... ```
gconf-editor /apps/metacity 
```...but I don't remember what I did and I can't seem to find the web site that showed me how. How can I keep the themes when booting up and not have to manually do it everytime I boot up?

---

### Post by beew on 2011-03-06
Yeah, there seems to be a bug in Emerald. It happens sometimes in Lucid and Maverick, though not very frequently. The easiest way to handle this is to install Compiz fusion-icon, which allows you to switch desktop manager (compiz and metacity, for example) and window decorator by just one click.

After you install it, you want it to start automatically at boot (and you will see it on the top panel) Go to System > Preferences > Startup Applications and add the Compiz fusion-icon, the command to enter into the box is
```
fusion-icon --no-start
```So next time if Emerald is missing on boot, just  right click the fusion icon, in the drop down menu click Select Window Decorator to change it to GTK Window Decorator and then change it back to Emerald.

Others may prefer to use the command line but I find it convenient to have everything in one place.

I don't know of a permanent fix,  though on my machines it happens only once in a while.

---

### Post by SexySara on 2011-03-06
Hey thank you! I also tried something just outa the blue and seemed to work when booting up. I went to Compiz Settings Manager then in the Windows Decoration. I put...
```
emerald --replace
```... in there instead of the default command which was... ```
gtk something rather lol
``` Worked perfect! Thanks for ur idea too, I downloaded what you said for future problems lol.

---

