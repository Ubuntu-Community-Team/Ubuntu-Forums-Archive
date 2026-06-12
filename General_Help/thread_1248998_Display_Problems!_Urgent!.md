---
title: "Display Problems! Urgent!"
date: 2009-08-24
forum: General Help
---

### Post by tom.swartz07 on 2009-08-24
Hello all,

I have a rather pressing question. I found out just earlier that ATI had released a driver set for my graphics card, and I downloaded and installed it. [http://www.ubuntugeek.com/ati-linux-video-driver-9-8-now-supports-ubuntu-9-04-jaunty.html#more-1805](http://www.ubuntugeek.com/ati-linux-video-driver-9-8-now-supports-ubuntu-9-04-jaunty.html#more-1805) UNFORTUNATELY, it didnt work, and it seems to have messed up my X display settings. 

It disabled composting (I think its called?) on my system and I was unable to use AWN to navagate easily. It also disabled my Compiz settings.

I managed to delete the main files and such, or at least most of them to count, but I still am stuck with the busted display settings. Rather than running at 1280x800 res, Im at 1024x768, no compiz, no AWN, basically everything is thrown into chaos.

Does anyone know how to help get my system back to how it was 30 minutes ago? Stupidly, I did not check to make sure that my xorg.conf file was backed up before I began. 

ANY help to get myself back on track would be wonderful and GREATLY appreciated.
Thanks to all
Tom

---

### Post by philcamlin on 2009-08-24
well you could try to  uninstall it in failsafe mode 
you should always backup your files before editing :P

---

### Post by tom.swartz07 on 2009-08-24
How do I uninstall it in failsafe mode? Would it be easier to use ```

sudo dpkg-reconfigure xserver-xorg 
```

I know I should back up... pshooo hahaha This will be the last time I forget to do that!

---

### Post by tom.swartz07 on 2009-08-24
Nevermind! I just ran
[CODE]
sudo dpkg-reconfigure xserver-xorg [CODE]

and restarted. FIXED!

Thank goodness!

---

