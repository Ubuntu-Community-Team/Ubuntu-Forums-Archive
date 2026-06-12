---
title: "ion Chipset - Error probing Smb1, Smb2"
date: 2010-11-30
forum: General Help
---

### Post by hogfan on 2010-11-30
I have been digging around to try to solve this error message, although it does not negatively affect my system other than slowing down boot time.  

I am running a minimal install of Lucid Lynx on an Acer Revo Nettop (1600).  Searching around the web I discovered that there is a Trac ticket open on this issue but still no fix.  There are reports that this has been fixed in Maverick, but I am not ready to upgrade yet.  Does anybody know if a patch for this bug has been release for Lucid?   

I am open to any work-arounds that don't negatively affect the system.  Some have stated that setting the acpi to "lax" in  the grub config file gets rid of the message, but some have reported the the system runs hotter after doing this work-around.  

Is there a "good" fix for this out there that I am missing?  Thanks so much for any assistance.


-hogfan

---

### Post by cavalier911 on 2010-11-30
```
sudo nano /etc/default/grub
```

Add what's in **bold**:

```
GRUB_CMDLINE_LINUX_DEFAULT= **acpi_enforce_resources=lax** quiet splash

```

Save/Closeout 

```
sudo update-grub
```

---

