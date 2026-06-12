---
title: "links2 -g in the CLI anyone?"
date: 2011-02-21
forum: General Help
---

### Post by cat0752 on 2011-02-21
(I'm running ubuntu 10.10) 

Can anyone make links2 with the -g (graphics) options work properly from the command line/terminal?  In X windows it works no problem.  However if i'm not running X, it fails to load.  Basically it says it can't open /dev/fb0 because permission is denied.  The following error is:

```
(*) DirectFB/Core: Single Application Core. (2010-07-09 12:33) 
(!) Direct/Util: opening '/dev/fb0' failed
    --> Permission denied
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
```If I run it as root it will load.  
However the resolution is completely screwed up and I couldn't even attempt to use it. 

[B]1. Can anyone help me run it as a normal user.  

2. Can anyone help me fix the resolution and possibly mouse issues?  [/B] 

Thanks for your time.

---

### Post by cat0752 on 2011-02-21
Bump

---

### Post by marshag63 on 2011-02-22
It would appear you do not have your framebuffer setup.  

"(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.'

I don't have any experience setting up framebuffer - I am quite spoiled by the INX live CD/USB I use - that's all setup already.

I would google "fbdev" and "setting up framebuffer."

You could also give INX a try:  [http://inx.maincontent.net/](http://inx.maincontent.net/)

I recommend 1.17:  [http://inx.maincontent.net/devel/unstable/lucid-inx/inx-lucid-alpha-2.iso](http://inx.maincontent.net/devel/unstable/lucid-inx/inx-lucid-alpha-2.iso)

MDG

---

### Post by nothingspecial on 2011-02-22
Change the permissions on the framebuffer by creating a udev rule
```

sudo nano /etc/udev/my-rules.d/framebuffer.rules
```

Then put a line in it like this
```

KERNEL=="fb0",  OWNER="root", MODE="0660"
```

Then add yourself to the video group
```

sudo usermod -a -G video *username*
```

Change username for your actual username, then restart.

---

### Post by cat0752 on 2011-02-27
Thanks for the replies.  

Marshag63: I never knew of INX but I think I'll try it.  Thanks for sharing that.

nothingspecial: Thanks! That worked fine for allowing me to access the framebuffer although **apparantly I don't have access to /dev/tty0 either**.  Can I set that up the same way as I did for /dev/fb0 ?

---

### Post by cat0752 on 2011-02-27
Here's the exact output:

```
   ~~~~~~~~~~~~~~~~~~~~~~~~~~| DirectFB 1.2.10 |~~~~~~~~~~~~~~~~~~~~~~~~~~
        (c) 2001-2008  The world wide DirectFB Open Source Community
        (c) 2000-2004  Convergence (integrated media) GmbH
      ----------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2010-07-09 12:33) 
(!) DirectFB/core/vt: Error opening `/dev/tty0'!
    --> Permission denied
(!) DirectFB/Core: Could not initialize 'system_core' core!
    --> Initialization error!
```

---

