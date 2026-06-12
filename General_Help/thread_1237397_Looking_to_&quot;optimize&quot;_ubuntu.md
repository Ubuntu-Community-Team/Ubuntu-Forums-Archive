---
title: "Looking to &quot;optimize&quot; ubuntu"
date: 2009-08-11
forum: General Help
---

### Post by Jago6060 on 2009-08-11
So I've noticed that there are some things that I don't particularly need that come by default in Ubuntu.  I realize some of these things may not be able to be remedied but i figured I'd ask.

-The first thing is the GRUB loader.  Is there anyway I can just tell it to skip ahead and load Ubuntu?

-For whatever reason, my work computer(running Ubuntu) tries to find a floppy drive even though it doesn't have one.  Is there any way to stop it from looking for it via Ubuntu?  I've checked the BIOS and can't see anything that will tell it to skip looking for the floppy.

-Firefox:Runs fast at first but gets slower as I use it.  I'm not sure if this is an Ubuntu or FF problem but suggestions would appreciated.

-After many many many program installs and uninstalls, I'm assuming that there are a bunch of floating files or unhinged dependencies.  Perhaps this is a flashback from Windows :-)  but if I'm correct in my assumption, how do I remedy the loose files and such?

---

### Post by bodyharvester on 2009-08-11
> **Jago6060 said:**
> -The first thing is the GRUB loader.  Is there anyway I can just tell it to skip ahead and load Ubuntu?

i dont know what GRUB is but if its loading before ubuntu it must be bloody miportant to ubuntu, so dont go near it, my advice is to stand 3 feet from the comp when you see that word

> **Jago6060 said:**
> -For whatever reason, my work computer(running Ubuntu) tries to find a floppy drive even though it doesn't have one.  Is there any way to stop it from looking for it via Ubuntu?  I've checked the BIOS and can't see anything that will tell it to skip looking for the floppy.

it must be old if its looking for a floppy:confused:

> **Jago6060 said:**
> -Firefox:Runs fast at first but gets slower as I use it.  I'm not sure if this is an Ubuntu or FF problem but suggestions would appreciated.

which version do you have?

> **Jago6060 said:**
> -After many many many program installs and uninstalls, I'm assuming that there are a bunch of floating files or unhinged dependencies.  Perhaps this is a flashback from Windows :-)  but if I'm correct in my assumption, how do I remedy the loose files and such?

yeah but im not sure, someone verify it please,

sudo apt-get install autoclean

sudo apt-get clean

sudo apt-get autoremove

DO NOT RUN THESE COMMANDS - WAIT FOR SOMEONE TO VERIFY THEM its a good habit to get into ;)

---

### Post by computerfreak on 2009-08-11
for having your computer go to ubuntu and skip the floppy, go into you bios and change the boot order to have your hard drive boot first. and for your firefox problem, you could clear out all the temp files, history, etc. by going to tools > clear private data or ctrl-shift-del. or you could use another browser. another great browser in ubuntu is opera. im pretty sure you can import bookmarks and you get a lot of other handy tools that come with it. i hope this helped! :)

---

### Post by michy99 on 2009-08-11
To go straight into Ubuntu, install Startup Manager.```
sudo apt-get install startupmanager
```Once installed, it will be under System->Administration. Make sure Ubuntu is the default, and set timeout to 0.

Note: This can make it difficult to get to recovery mode if you ever need to.

---

### Post by Jago6060 on 2009-08-11
> **bodyharvester said:**
> i dont know what GRUB is but if its loading before ubuntu it must be bloody miportant to ubuntu, so dont go near it, my advice is to stand 3 feet from the comp when you see that word



it must be old if its looking for a floppy:confused:



which version do you have?



yeah but im not sure, someone verify it please,

sudo apt-get install autoclean

sudo apt-get clean

sudo apt-get autoremove

DO NOT RUN THESE COMMANDS - WAIT FOR SOMEONE TO VERIFY THEM its a good habit to get into ;)

Firefox 3.5

---

### Post by bodyharvester on 2009-08-11
i think there is a firefox 3.5.2 that may help, or just use opera browser

the commands do work ;) i used them myself

---

### Post by computerfreak on 2009-08-11
> **michy99 said:**
> timeout to 0.
Note: This can make it difficult to get to recovery mode if you ever need to.

i would set it to 2 or 3 in case you really ever do need to get into recovery mode.
EDIT: setting grub to have Ubuntu as the default OS will not fix floppy problem, just so you know, because grub is saved on the had drive.

---

