---
title: "ttf-mscorefonts-installer always running? Maybe? Only one software management tool?"
date: 2009-12-15
forum: General Help
---

### Post by flak_monkey on 2009-12-15
I'm very, very, very new to Linux. Installed it the other day, sort of thumbing through my "ubuntu for non-geeks" book. 

I'm trying to install programs like pidgin because I don't like empathy, and I keep getting "Only one software management tool may be run at a time"

I looked around on the forums, tried [http://ubuntuforums.org/showthread.php?t=1247134](http://ubuntuforums.org/showthread.php?t=1247134)
and typed killall dpkg into the terminal. Came back with "no packages killed"

then tried
sudo dpkg --configure -a
and it started going nuts with ttf-mscorefonts-installer and couldn't resolve the domain or something??? 

I noticed that this hangs up my updates and has been making a mess since I added the restricted extras trying to get flash support (still no dice there either)

I went here [http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/11/05/howto-fix-ttf-mscorefonts-installer-problems-in-ubuntu-9-10-karmic-koala/) and typed

 sudo apt-get remove ttf-mscorefonts-installer 

but it doesn't work I get

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What the hell is going on here? Why can't I install anything? Why is tt-mscorefonts-installer always attempting to run? Or am I just doing it wrong? 

 By the way I know nothing about the terminal or command line, so be basic with responses. 
Thanks for any help.

---

### Post by northern lights on 2009-12-15
Can you please post the output of ```
top
```right after getting this> 

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Thanks.

---

### Post by flak_monkey on 2009-12-15
Actually, I tried the command that gave me that error message again, after attempting to uninstall flash and failing, and it looks like it removed mscorefonts. The system is now seemingly capable of installing and removing software again??? Weiiiiird.

---

### Post by northern lights on 2009-12-15
> **flak_monkey said:**
> The system is now seemingly capable of installing and removing software again??? Weiiiiird.I'd assume you had Synaptic open, the Add/Remove dialog, or similar?!

---

### Post by flak_monkey on 2009-12-15
That's the thing! I didn't have anything open. It would even behave that way rigtht after a restart.

---

