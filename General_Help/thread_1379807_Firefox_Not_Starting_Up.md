---
title: "Firefox Not Starting Up"
date: 2010-01-12
forum: General Help
---

### Post by LegendarySandwich on 2010-01-12
Hi guys. I recently reinstalled Ubuntu, so I have to to go through some of the problems I had when I first installed, and that includes problems with Firefox. However, some of the problems I've having now I never had before, such as javascript buttons weren't working and a toolbar wasn't displaying. Anyways, I wen to the profile manager and deleted the default profile, as well as all the data on it. Then I created a new one. Okay, so I then I tried to open Firefox - and I got this error message: ```
file: chrome://1clickweather/content/js/utils/debug.js
undefined
```

So I tried uninstalled Firefox and installing it again. Nope, same thing, every single time. I had to install Epiphany to post this thread. So, does anyone know what I can do? It would be great if this also solved some of the problems I've been having with Firefox.

---

### Post by Leppie on 2010-01-13
you could search for the folder containing this extension and delete it:
```
sudo find / -name 1clickweather -ok rm -R {} \;
```

---

### Post by LegendarySandwich on 2010-01-13
> **Leppie said:**
> you could search for the folder containing this extension and delete it:
```
sudo find / -name 1clickweather -ok rm -R {} \;
```
Nothing happens when I do that...?

EDIT: Or was I supposed to change something in the line? Sorry, I'm still kind of new. Maybe I should of posted this in the beginners section...

---

### Post by Leppie on 2010-01-13
> **LegendarySandwich said:**
> Nothing happens when I do that...?
and if you only take the first part:
```
sudo find / -name 1clickweather
```

---

### Post by LegendarySandwich on 2010-01-13
> **Leppie said:**
> and if you only take the first part:
```
sudo find / -name 1clickweather
```

Nothing either. I deleted the profile containing that add-on, so it should be deleted...and that's obviously the root of this problem, though I have no idea how to fix it.

---

### Post by patros on 2010-01-13
Try renaming the ".mozilla" folder in your home directory to something else. You will have to hit CTRL+H to enable viewing of hidden files. This will cause Firefox to recreate all it's per-user settings so you will lose history, bookmarks, etc. If it doesn't fix it you can rename it back.

---

### Post by LegendarySandwich on 2010-01-13
> **patros said:**
> Try renaming the ".mozilla" folder in your home directory to something else. You will have to hit CTRL+H to enable viewing of hidden files. This will cause Firefox to recreate all it's per-user settings so you will lose history, bookmarks, etc. If it doesn't fix it you can rename it back.

Actually, I just deleted my .mozilla folder to see if it would fix the problem. It didn't.

---

### Post by patros on 2010-01-13
When you uninstalled firefox did you purge the configuration? "sudo aptitude purge firefox-3.5" Should output a bunch of stuff but look for where it says something like...

Remove the following packages:
firefox
firefox-3.5-branding
firefox-3.5-gnome-support
firefox-gnome-support
ubufox

If that is all that's getting removed that should be fine, hit Y to continue. When it has done it's thing run "sudo aptitude install firefox" (this time without the 3.5). Hopefully that helps.

---

### Post by LegendarySandwich on 2010-01-13
> **patros said:**
> When you uninstalled firefox did you purge the configuration? "sudo aptitude purge firefox-3.5" Should output a bunch of stuff but look for where it says something like...

Remove the following packages:
firefox
firefox-3.5-branding
firefox-3.5-gnome-support
firefox-gnome-support
ubufox

If that is all that's getting removed that should be fine, hit Y to continue. When it has done it's thing run "sudo aptitude install firefox" (this time without the 3.5). Hopefully that helps.

I tried that, and it didn't work. It did show some packages, but none of the ones in your post.

EDIT: I deleted all the packages I could that you showed and re-installed firefox, but still the same problem...

---

### Post by patros on 2010-01-13
> **LegendarySandwich said:**
> I tried that, and it didn't work. It did show some packages, but none of the ones in your post.

EDIT: I deleted all the packages I could that you showed and re-installed firefox, but still the same problem...

When you say deleted, did you purge them or remove them?

---

### Post by LegendarySandwich on 2010-01-13
> **patros said:**
> When you say deleted, did you purge them or remove them?

Ah, forgot the purge part. Going to try that now.

---

### Post by LegendarySandwich on 2010-01-13
Argh...I did the purge, then I reinstalled it, and what do you know...say error.

---

### Post by patros on 2010-01-13
Try running "firefox -safe-mode" from a terminal

---

### Post by LegendarySandwich on 2010-01-13
> **patros said:**
> Try running "firefox -safe-mode" from a terminal

Nope, same error.

I think I really f*cked up my Firefox.

---

### Post by patros on 2010-01-13
> **LegendarySandwich said:**
> Nope, same error.

I think I really f*cked up my Firefox.

Yes, I believe you have...

---

### Post by LegendarySandwich on 2010-01-13
Hmm...maybe I need one of the really knowledgeable guys on this site?

---

### Post by patros on 2010-01-13
> **LegendarySandwich said:**
> Hmm...maybe I need one of the really knowledgeable guys on this site?

lol

---

### Post by LegendarySandwich on 2010-01-13
I don't really understand the joke, but okay.

---

### Post by patros on 2010-01-13
Ok, try downloading http://www.dwyerfamily.org/{DCBD1271-D228-4082-9FBC-36D9B7660B03}.zip

unzip and copy the {DCBD1271-D228-4082-9FBC-36D9B7660B03} folder to your .mozilla/firefox/<profile folder>/extensions folder and try running firefox in safe mode again.

---

### Post by patros on 2010-01-13
Also try "firefox -profilemanager" and create a new profile that way, make sure the new one is selected and hit start firefox

---

### Post by LegendarySandwich on 2010-01-13
> **patros said:**
> Ok, try downloading http://www.dwyerfamily.org/{DCBD1271-D228-4082-9FBC-36D9B7660B03}.zip

unzip and copy the {DCBD1271-D228-4082-9FBC-36D9B7660B03} folder to your .mozilla/firefox/<profile folder>/extensions folder and try running firefox in safe mode again.
I don't have an extensions folder, should I make one?
> **patros said:**
> Also try "firefox -profilemanager" and create a new profile that way, make sure the new one is selected and hit start firefox

That brings the same error as Firefox.

---

### Post by computer_tech4u on 2010-01-13
im trying to get my microsoft webcam vx-3000 to work in ubuntu 9.10 32 bit to work. i installed the 2.6.32.rc6 image and header. i downloaded the new gspca file. when i navagate to the file, /home/terrys/Downloads/gspca*/v4l and do the make all. it says this, root@garfield:/home/terrys/Downloads/gspca-8fabb98ec5a0/v4l# make all
Updating/Creating .config
Preparing to compile for kernel version 2.6.32
File not found: /lib/modules/2.6.32-020632rc6-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
i need much help to get this up and running. anyone out there can help me please

---

### Post by Leppie on 2010-01-13
> **computer_tech4u said:**
> im trying to get my microsoft webcam vx-3000 to work in ubuntu 9.10 32 bit to work. i installed the 2.6.32.rc6 image and header. i downloaded the new gspca file. when i navagate to the file, /home/terrys/Downloads/gspca*/v4l and do the make all. it says this, root@garfield:/home/terrys/Downloads/gspca-8fabb98ec5a0/v4l# make all
Updating/Creating .config
Preparing to compile for kernel version 2.6.32
File not found: /lib/modules/2.6.32-020632rc6-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
i need much help to get this up and running. anyone out there can help me please
is there any relationship with the original post, apart from the fact that both have something not working?

---

### Post by patros on 2010-01-13
> **LegendarySandwich said:**
> I don't have an extensions folder, should I make one?


That brings the same error as Firefox.

Firefox should create an extensions folder when it creates the ".mozilla" folder. I've created a new one on my system and installed that missing extension 1clickweather. Give it a go [http://www.dwyerfamily.org/mozilla.zip](http://www.dwyerfamily.org/mozilla.zip) just rename the enclosed directory from "mozilla" to ".mozilla"

---

### Post by LegendarySandwich on 2010-01-13
> **patros said:**
> Firefox should create an extensions folder when it creates the ".mozilla" folder. I've created a new one on my system and installed that missing extension 1clickweather. Give it a go [http://www.dwyerfamily.org/mozilla.zip](http://www.dwyerfamily.org/mozilla.zip) just rename the enclosed directory from "mozilla" to ".mozilla"
Downloaded the mozilla directory, put the extension in there...and it still didn't work.

---

### Post by LegendarySandwich on 2010-01-13
Note: I'm re-installing Ubuntu...again. So hopefully, this problem won't happen again (I'm guessing it was just a completely random bug).

---

