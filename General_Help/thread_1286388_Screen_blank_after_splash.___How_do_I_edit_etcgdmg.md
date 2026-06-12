---
title: "Screen blank after splash.   How do I edit etc/gdm/gdm.config?"
date: 2009-10-08
forum: General Help
---

### Post by Gosport on 2009-10-08
I was half way through installing a new printer driver when I attempted to switch users (because I needed to log in as the primary user to do this type of thing and I had forgotten where I was).

I got some message about "Out of scan range" or something.

I found some help on the web at:[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

All the instructions are Greek to me.   How do I edit etc/gdm/gdm.config?  
[FONT=monospace]

[/FONT]    sudo nano /etc/gdm/gdm.conf seemed to work but it gave me a blank DOS looking screen with instruction at the bottom like   "^G" to do this or "^D" to do that though none of them seemed to have any effect.  I couldn't get out without fording the computer off with the power swith.

---

### Post by Gosport on 2009-10-08
Ok I have looked up instructions to use nano.  The "^" simply means that you hold down the control button.  When I try to open gdm.conf the file seems to be blank.  Does Jaunty still have this file?  

Also, I was using proprietary ATI video driver.  Don't know if that matters.

Any Ideas or links that may help me?

Thank you!

---

### Post by c0mput3r_n3rD on 2009-10-08
> **Gosport said:**
> I was half way through installing a new printer driver when I attempted to switch users (because I needed to log in as the primary user to do this type of thing and I had forgotten where I was).

I got some message about "Out of scan range" or something.

I found some help on the web at:[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

All the instructions are Greek to me.   How do I edit etc/gdm/gdm.config?  
[FONT=monospace]

[/FONT]    sudo nano /etc/gdm/gdm.conf seemed to work but it gave me a blank DOS looking screen with instruction at the bottom like   "^G" to do this or "^D" to do that though none of them seemed to have any effect.  I couldn't get out without fording the computer off with the power swith.

Open a terminal; Applications -> Accessories -> Terminal, and type:
```

gedit /etc/gdm/gdm.config

```

---

### Post by Gosport on 2009-10-08
gedit /etc/gdm/gdm.conf  gives me **something** Warning  **Somethign**  Can not open display.

---

### Post by c0mput3r_n3rD on 2009-10-08
> **Gosport said:**
> gedit /etc/gdm/gdm.conf  gives me **something** Warning  **Somethign**  Can not open display.

Trying doing this as super user? "sudo gedit/etc/gdm/gdm.config"?  I just tried it it worked just fine.

---

### Post by Gosport on 2009-10-08
Thanks, I'll give it a try.

---

### Post by Gosport on 2009-10-09
Nope, but "sudo nano etc/gdm/gdm.conf"  got me in.

Now I don't know what to do.

I set AutomaticLoginEnable=true and AutomaticLogin="my primary user account"

Didn't seem to do anythign.

I still see the splash screen then a blank screen (I can almost make out the ubuntu logo spread out across the top for a min.  No Ubuntu chime music or anything.


I set things back at they were: AutomaticLoginEnable=false and AutomaticLogin="blank"

---

### Post by Gosport on 2009-10-09
Can someone explain the instructions below to me.  I think this may be my solution but I don't know what they are talking about.

**Problem:  Monitor shows "Out of Range"**

 This typically happens when the graphics card is trying to use a resolution (and refresh rate) beyond what the monitor is capable of handling. 
First, look and see if a resolution is hardcoded in your xorg.conf.  These days this is rarely needed, but if you're using an xorg.conf from an older install or something, it could be set.  Try moving aside your xorg.conf and boot without any xorg.conf so it's all auto-detected, or disable the resolution lines. 
If booting with an auto-detected configuration doesn't work, then there is a deeper problem. Usually this indicates that the EDID information your monitor is providing is incorrect. 
**Workaround (for GNOME)**: 

[LIST]
[*]Start up Ubuntu in Recovery Mode and get a root prompt 
[*]Set GNOME to auto-login, by editing /etc/gdm/gdm.conf and setting AutomaticLoginEnable=true and AutomaticLogin to your preferred user account. 
[*]In your ~/.xprofile add a line to specify a safer resolution: 
[/LIST]

  # Depending on your video card, your output may be 
  # 'VGA-0', 'VGA0', 'DVI', 'LVDS', etc. instead of 'VGA'
  xrandr --output VGA --mode 1024x768You should be able to use System > Preferences > Screen Resolution to fine tune your resolution from here, or see [Configuring Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") for ways to configure resolutions manually.

---

### Post by Gosport on 2009-10-09
Also, what is "~/.xprofile"?  It doesn't seem to be in the gdm.conf file.

At the prompt I tried "sudo gedit ~/.xprofile" then "sudo nano ~/.xprofile" and just "~/.xprofile" and all I got was that the file doesn't exist.

---

### Post by Gosport on 2009-10-09
My monitor keeps saying that for the best resolution I should use 1440X900

This is what I did: sudo nano/etc/usplash.conf and I adjusted the resolution numbers to 1440 and 900  then at the shell prompt I wrote: sudo dpkg -reconfigure -phigh usplash

Nothing!

I'm a little concerned that I don't hear the log in chime.  It makes me think that there is more to this than the monitor.

---

### Post by Gosport on 2009-10-09
I have looked on the web and found nothing that that can help a noob like me fix this.  No one seems to know how to help here either.   Is it possible that installing a printer can cause a unrecoverable error in Ubuntu??

Can someone at least point me in the direction of the best way to reinstall/recover Ubuntu without loosing all my files?

---

### Post by Gosport on 2009-10-09
What do you thing may be going on?  Where should I start?

---

