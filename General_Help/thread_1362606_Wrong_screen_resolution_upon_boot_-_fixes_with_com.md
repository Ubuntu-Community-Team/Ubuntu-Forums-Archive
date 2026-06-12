---
title: "Wrong screen resolution upon boot - fixes with command"
date: 2009-12-23
forum: General Help
---

### Post by lsutiger on 2009-12-23
I have an Nvidia graphics card, and I am using the restricted drivers. When I boot, the screen resolution is too high, and the refresh rate too low. 

The way it fixes itself is quite strange.

After boot, I open a terminal, and give the command ```
gksudo nvidia-settings
```
As soon as I enter my password and press enter, the screen turns black for a second, then the settings correct themselves....Whaaaa?

If I use sudo nvidia-settings or nvidia-settings it does not work. If I use sudo nvidia-settings, the correct refresh rate and resolution is not listed.

Has anyone had a similar problem?

---

### Post by pbrane on 2009-12-23
I run **nvidia-settings --load-config-only** as a startup application. I've read that other people run nvidia-settings as root but that doesn't do anything for me. If you run *man nvidia-settings* in a terminal, you'll see this:

```

3. Loading Settings Automatically
       The NVIDIA X driver does not preserve values set  with  nvidia-settings
       between  runs  of  the X server (or even between logging in and logging
       out of X, with xdm(1), gdm, or kdm ).   This  is  intentional,  because
       different users may have different preferences, thus these settings are
       stored on a per-user basis in a configuration file stored in the user's
       home directory.

```

---

