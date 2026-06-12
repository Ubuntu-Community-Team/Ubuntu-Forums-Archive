---
title: "Speeding up Ubuntu Start Up time"
date: 2010-02-22
forum: General Help
---

### Post by Garnett on 2010-02-22
I'm sure this has been asked before, but I think my ignorance of the correct terminology is thwarting my google endeavors.

I want to try and speed up the time from switching on my machine to having the desktop loaded and ready to go.

Any tips or googleable terms would be very gratefully appreciated.

One thing that seems to be taking a lot of time is a page where I have the option to pick which Ubuntu I want to load. It says something like:-

Generic Ubuntu 9.10 Kernel
Generic Ubuntu 9.10 Kernel (Safe Mode) (I think)

and a few others. It waits there for a while before loading the standard one.

I'm sure this didn't happen last time I played with Ubuntu (8.10). Is there a way to stop it doing this? And do I lose any vital functionality disabling it?

Thanks for any help.

---

### Post by Greenwidth on 2010-02-22
```
gksudo gedit /etc/default/grub
```
to edit Grub config. 
GRUB TIMEOUT is the setting in seconds that it counts down.

```
sudo update-grub
```
afterwards to update grub.cfg.

---

### Post by Garnett on 2010-02-22
Thanks Greenwidth. So I can set it to 0 seconds? Is this the quickest? Or its there a way for it not to load these options at all?

---

### Post by Greenwidth on 2010-02-22
It might be useful to set it to a low value so it still shows, if you have a problem kernel you can boot to the old one easily.

---

### Post by derande on 2010-02-22
StartUp-Manager will allow you to set the timeout to zero and set which kernel you want to start with without manually editing grub files.
you can also use this to change splash screens, etc...
it's in ubuntu software center and starts from system > administration.

---

### Post by Mahngiel on 2010-02-22
It is wise to have some sort of timeout before Grub boots into Ubuntu.  If you do not dual boot or anything, then 0 should be fine so long as you are aware, if you have any problems in the future, to use the live CD to mount your partition and edit the grub timeout.  Also, if you are set to 0, any kernel updates could bork your progress.

---

### Post by wojox on 2010-02-22
You can also use bum (Boot up Manager). It helps with what gets loaded.

```
sudo apt-get update && sudo apt-get install bum
```

---

### Post by wojox on 2010-02-22
> **Mahngiel said:**
> It is wise to have some sort of timeout before Grub boots into Ubuntu.  If you do not dual boot or anything, then 0 should be fine so long as you are aware, if you have any problems in the future, to use the live CD to mount your partition and edit the grub timeout.  Also, if you are set to 0, any kernel updates could bork your progress.

I've heard that as well. I've been setting it to 0 from grub legacy to grub2 and yet to run into a problem. Lucky maybe. :)

---

### Post by NightwishFan on 2010-02-22
You can always just hold "shift" when booting to see the grub menu.

---

### Post by squrl on 2010-02-22
derande- 

Could you be a little more precise or specific where in System > administration I'll findc what you refer to???

Thanks

---

### Post by derande on 2010-02-22
> **squrl said:**
> derande- 

Could you be a little more precise or specific where in System > administration I'll findc what you refer to???

Thanks


Applications > Ubuntu Software Center.
Type 'startup' in the search box and install StartUp-Manager.
After it installs, it can be found in System > Administration menu.

---

