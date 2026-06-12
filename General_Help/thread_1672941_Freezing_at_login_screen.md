---
title: "Freezing at login screen"
date: 2011-01-21
forum: General Help
---

### Post by kunigami on 2011-01-21
Diagnosis: I'm running Ubuntun 10.04. It has been running smoothly for pleny of time (8~9 months). I've done the clean install (not upgrading).

One day I left the screen locked and when I returned it was frozen. I restarted and it froze in the login screen (sometimes when I restart it actually log in my account, but freezes right after some minutes). The mouse pointer still moves.

I still can log in remotely through SSH, even though the system is frozen. So I suspect it has to do with the GUI.

Here's the output of my [/var/log/Xorg.0.log]("http://pastebin.com/ZVRzGZPZ")

I think the error started in here:

```
(WW) Jan 21 11:29:46 NVIDIA(0): WAIT
(2, 6, 0x8000, 0x00007b6c, 0x0000aa04)

[mi] EQ overflowing. The server is
probably stuck in an infinite loop.

```

It seems to be a problem with my video card. How to detect if it was a driver failure or a hardware one? (I can post additional information if needed)

Also, when logging remotely and running htop, there's a root process using a hole CPU:

```
/usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-4fEOwt/database -nolisten tcp

```

I tried killing it but it is spawned again.

Any hint on how to solve this problem?


Thanks,

---

### Post by Rubi1200 on 2011-01-21
Hi and welcome to the forums :)

I don't know if this will help, but take a look here:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials)

Alternatively, try to reconfigure the graphics from either failsafe mode or recovery mode:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by kunigami on 2011-01-21
Hi! Thanks for the fast response!

I read the link you passed me and almost all the symptoms matches. Namely:

[LIST]
[*] X stops responding to input (sometimes mouse cursor can still move, but clicking has no effect)
[*] The screen displays but does not update. Sometimes there is screen corruption too, but usually there isn't.
[*] Often, X cannot be killed; only a reboot clears the state
[*] The system operates fine over SSH but not on the graphical console
[/LIST]

Except that my problem is "determinist"

[LIST]
[*] It can be hard to tie the problem to an exact test case; it seems to occur "randomly"
[/LIST]

Also,

I have some of the non-syptoms

[LIST]

[*] A backtrace appears in Xorg.0.log or elsewhere - most of the time this indicates a crash, not a freeze
[/LIST]

Seems that the driver Nouveau (for Nvidia boards) support is kinda poor for hang detection.

I have the same log described there: "[mi] EQ overflowing" 

:( It seems to be a bug of the driver.

> **Rubi1200 said:**
> 
(...)

Alternatively, try to reconfigure the graphics from either failsafe mode or recovery mode:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

I'll try doing that ASAP. I come back to tell the news!

Thanks again!

---

### Post by kunigami on 2011-01-24
Hi again,

I've run the command you suggest, but the

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```Didn't create any xorg.conf file.

By the way, removing the xorg.conf file did stop the freezing, but the screen resolution looks odd now. When I try to reconfigure this resolution, it's asked me to run the command 

```
nvidia-xconfig
```But when I run it and restart X, the screen freezes again :(

I tried installing the driver "manually" from Nvidia site, but the same error happens! :(

I'm suspecting my video card is buged.

---

### Post by Rubi1200 on 2011-01-24
Haven't tried the tips here, but looks promising:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

