---
title: "How do I remove boot splash and have a text based boot in Maverick"
date: 2010-12-14
forum: General Help
---

### Post by akand074 on 2010-12-14
Hey guys,

I was just wondering how I could set it to not load the boot splash and just run a text based boot instead in Maverick. 

Thanks!

---

### Post by Foxheadz on 2010-12-14
Well in plymouth manager you can give it a text theme which im guessing (havn't tried) gives all the text. you can download it here [http://sourceforge.net/projects/plymouthmanager/](http://sourceforge.net/projects/plymouthmanager/)

---

### Post by akand074 on 2010-12-14
> **Foxheadz said:**
> Well in plymouth manager you can give it a text theme which im guessing (havn't tried) gives all the text. you can download it here [http://sourceforge.net/projects/plymouthmanager/](http://sourceforge.net/projects/plymouthmanager/)

That looks like a good option. I just had a thought though, what if I just uninstalled plymouth? Then there wouldn't be a graphical boot animation, so it would default to text? Might be worth a shot, doubt it would cause any system instabilities.

---

### Post by oldos2er on 2010-12-15
Edit /etc/default/grub, change the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="text"

Run **sudo update-grub**, reboot.

---

### Post by akand074 on 2010-12-15
> **oldos2er said:**
> Edit /etc/default/grub, change the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="text"

Run **sudo update-grub**, reboot.

Awesome. I completely forgot about that. Since I have a text boot, is there really any need for plymouth? Would it be safe to remove it?

---

### Post by Rubi1200 on 2010-12-15
You do NOT want to remove plymouth!!!

Try, and watch your system die an awful death!

The suggestions posted above should suffice for your needs.

---

### Post by akand074 on 2010-12-15
> **Rubi1200 said:**
> You do NOT want to remove plymouth!!!

Try, and watch your system die an awful death!

The suggestions posted above should suffice for your needs.

Thanks for letting me know! Perfect. Thread solved.

---

### Post by tednix on 2011-01-17
I thought that it would be more "geeky" to replace the Ubuntu boot splash with the scrolling boot text.  However I didn't realise that the boot text finished with a full screen shell!  
This resulted in furthering my Linux education because I had to find a way to get into Gnome from the shell, which is "sudo gdm".  Back in the Gnome gui I thought that I would try to preserve the boot text but end in the login gui by substituting "text splash" for "text".  Personally I would be OK with all text but I'm trying to get the wife to use Linux so I wanted to keep the login as simple as possible for her account.
Long story short, that causes major Grub errors but I recovered by booting into my secondary kernel on the Grub2 screen and reverting to the original configuration.  Somehow all of this has caused my Grub2 customizer program to fail with the notice that it must be run as root. I tried sudo grub-mkconfig in the terminal but that doesn't work.

---

### Post by janeklb on 2011-03-02
> **tednix said:**
> I thought that it would be more "geeky" to replace the Ubuntu boot splash with the scrolling boot text.  However I didn't realise that the boot text finished with a full screen shell!  
This resulted in furthering my Linux education because I had to find a way to get into Gnome from the shell, which is "sudo gdm".  Back in the Gnome gui I thought that I would try to preserve the boot text but end in the login gui by substituting "text splash" for "text".  Personally I would be OK with all text but I'm trying to get the wife to use Linux so I wanted to keep the login as simple as possible for her account.
Long story short, that causes major Grub errors but I recovered by booting into my secondary kernel on the Grub2 screen and reverting to the original configuration.  Somehow all of this has caused my Grub2 customizer program to fail with the notice that it must be run as root. I tried sudo grub-mkconfig in the terminal but that doesn't work.

There is probably a syntax error in your /etc/default/grub

open it up and look for any odd things (if you don't find any, paste it in here and we can take a look)

---

### Post by tednix on 2011-03-02
Thanks for the offer of help janeklb but since my original post I've completely broken my system and went with a clean re-install about one month ago.

I think that it would be nice to have the scrolling text boot messages.  But I'm gun shy after my last attempt and will leave things as they are.

---

### Post by ApocryphalAuthor on 2011-04-01
It's been my experience that in */etc/default/grub*, if you set:
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```
you will be landed in terminal upon startup, and you'd have to manually launch gdm (*sudo gdm*) if you wanted to get into Gnome.

To have a text boot (and shut down) sequence, the user should set:
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```
as this will still get you into Gnome automatically when the machine is finished starting up.

---

