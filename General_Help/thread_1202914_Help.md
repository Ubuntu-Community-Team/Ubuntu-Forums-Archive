---
title: "Help"
date: 2009-07-02
forum: General Help
---

### Post by ZettaGeek on 2009-07-02
Hey Everyone,

OK, so I just did a fresh install of Linux Mint (This is Ubuntu based, so I figured this would be a good place to post this.)

I installed my wireless, which was a WMP54GS, got Ndiswrapper working, and can now use the internet.

Now for my problem.. Like most people, I wanted to use Desktop Effects. So I downloaded and installed the nVidia Geforce 2 TI drivers. After the install, it told me to configure my Xorg file.. I didn't know what it wanted me to configure, so I went ahead and closed the installer, started the GDM and went to start Desktop Effects. Only it says "Desktop Effects could not be enabled" So decided to diagnose. I ran compiz in the terminal and got this output:

```

compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

What have I done wrong? I know the drivers installed since in the administration tab, I now see the nVidia Xserver Settings.

Please help!
- ZettaGeek

---

### Post by ZettaGeek on 2009-07-02
Bump for 3D support!!!

:guitar:

---

### Post by maheshasolkar on 2009-07-02
Since you aborted the installer, it might have left some things un-configured. Could you try the following, restart X and run compiz again:

```
  % sudo dpkg-reconfigure -phigh xserver-xorg
```

PS: IMHO, using a better 'Title' to your post would be a good start towards getting someone's attention.

---

