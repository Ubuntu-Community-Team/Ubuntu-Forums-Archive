---
title: "Computer died after editing xorg.conf"
date: 2010-06-03
forum: General Help
---

### Post by benbenny on 2010-06-03
Hello all, I'm in big trouble and I'm hoping that someone can give me some advice that will help me understand why this happened, and maybe even help me fix my computer. 

I had gotten my ubuntu karmic laptop (Toshiba A100-543) to work with an additional external monitor through editing xorg.conf. I essentially copied the sections for "screen 0", "device 0" (Nvidia Geforce GO 7600), and "monitor 0", and created (duplicate) entries screen 1, device 1 and monitor 1. This worked fine but of course the result is two independent desktops on each one of the monitors.

At this stage I decided to try to experiment a little and see if I could get a single desktop environment on both screens, such that I can move x windows in between just by dragging them with my mouse. 

I decided to try to see if I could "fool" ubuntu into doing this by getting rid of the distinction between "screen 0" and "screen 1" but leaving the sections for "device 1" and "monitor 1". The first way I tried to do this was by leaving the duplicate screen section intact but changing "screen 1" to "screen 0" in that section. So essentially now there were 2 "screen 0" entries, 1 linked to "device 0" and "monitor 0", and the other linked to "device 1" and "monitor 1". I didn't really expect this to work but I thought what the hell. I definitely didn't expect that on rebooting, just before grub menu was loaded, my laptop died and is showing no signs of life. This means its not responding at all to pushing the power button, and the LED that is normally on when it is connected to the electrical socket is also dead. 

So, can someone please 
A) explain to me why am I a stupid arrogant noob and why this had such a drastic effect?
B) Suggest to me what is wrong, and if not how to fix it, maybe point somewhere where I can find out.

Hope this is clear. I'm assuming that people know what im talking about when I refer to screen 0, monitor 0 etc with respect to xorg.conf but please let me know if the terminology is different on different systems, and whether I need to make this clearer. 

PS. I'm supposed to start a job Tuesday that is highly dependent on me being able to work from home (hence the purchase of the second monitor), and buying a new laptop would mean using my credit card and incurring interest which I hate doing.  

I know: sucks for me.

Anyway, thanks for any help.

Ben

---

### Post by TheDesertDragon on 2010-06-03
This doesn't solve the specific issue, but it does get your computer back and running! :)

Try popping in a live CD, mount the drive, on / using the live CD, finding xorg.conf on the drive via the Live CD (be careful you don't edit the one on the CD), then deleting it and restarting the computer from your harddrive.

This will entirely reset your hardware setup though, so you'll have to reenable compositing if you use that and various other changes you've made.

You may also try pressing ctrl+alt+F1 after booting the computer as normal, which should let you into a terminal. After logging in, type:

sudo rm /etc/X11/xorg.conf

Then type:
sudo restart gdm

Hope it helps! :)

---

### Post by T-rock007 on 2010-06-03
Or you could try sudo rm -rf /etc/X11/xorg.conf
But you might have a backup in your X11 folder, If you have a nvidia video card because by default when you install the nvidia drivers and get them working it automatically makes a backup of xorg.conf. So you could try restoring the backup.

---

### Post by quadproc on 2010-06-03
> **benbenny said:**
> 
So, can someone please 
A) explain to me why am I a stupid arrogant noob and why this had such a drastic effect?
B) Suggest to me what is wrong, and if not how to fix it, maybe point somewhere where I can find out.

If you are running Ubuntu 9.10 or later then the xorg.conf file is optional and most systems will run without one.  Therefore, if you boot using the recovery mode selection (usually located just after your usual boot selection) then you can change the name of xorg.conf to something like xorg.conf.bad_one, do a reboot, and use your now running system to repair the xorg.conf file.  Once the xorg.conf file is in good condition then you can put a good copy vack and can restart the X server to make it use the repaired file.

The X server is somewhat intolerant of errors, as you found.  Sometimes the server does strange things and other times it just quits.  It is useful to have an alternate booting method available such as a Live CD, a USB flash drive, or something else that you can fall back to.  Of course, the recovery boot selection will do but to use it you have to do everything through the command line which can be tedious.

I don't know if you have it set up, but the ctrl-alt-backspace key combination is good to have for killing the X server.  This can be set up in System > Preferences > Keyboard Shortcuts.  You also may have use for the function keys ctrl-alt- F6-F10 which will invoke an X session, or ctrl-alt- F1-F5 which will invoke a non-graphics terminal.

quadproc

---

### Post by benbenny on 2010-06-03
guys thanks for your quick responses but the laptop is dead. kaput. not working. Doesnt power up. Doesnt even make a sound. There is no bash.
Fixing it is going to be a hardware issue. 

So does anyone have experience disassembling Toshiba laptops?

But first, why oh why has this happened? and more importantly - what has happened?

cheers

Edit:
yes I know about booting from LiveCD and all that, and about reinstating the old xorg.conf file - I did make backups of course.

---

### Post by bodhi.zazen on 2010-06-03
> **T-rock007 said:**
> Or you could try sudo rm -rf /etc/X11/xorg.conf
But you might have a backup in your X11 folder, If you have a nvidia video card because by default when you install the nvidia drivers and get them working it automatically makes a backup of xorg.conf. So you could try restoring the backup.

You do not need the -r and probably not the -f either :twisted:

boot to recovery mode, This will be command line only.

```
rm /etc/X11/xorg.conf
```

Configure X

```
nvidia-xonfig
```Reboot and rather then editing xorg.conf, use nvidia-settings

```
gksu nvidia-settings
```

---

### Post by _Mark_ on 2010-06-03
Try taking the battery out leaving for 10 minutes with no power and try again, no guarantee this will help  but worth a go

Can't see what you were doing would cause this unlucky coincidence i guess, a pain in the a**e no doubt

---

### Post by sgosnell on 2010-06-03
I don't think the xorg.conf edit was what killed your laptop.  Computers die.  You might try removing the battery and power, letting it sit for awhile, and then restarting it.  Try it without a battery, to see if it's just a battery problem.

---

### Post by benbenny on 2010-06-03
Good point. haven't tried to take out the battery yet. Thanks. 

So probably a coincidence?   What i was trying to do is not completely stupid?

Anybody know what sort of configuration would work to create a single Desktop across both monitors?

Cheers to all of you.

---

### Post by bodhi.zazen on 2010-06-03
> **benbenny said:**
> Good point. haven't tried to take out the battery yet. Thanks. 

So probably a coincidence?   What i was trying to do is not completely stupid?

Anybody know what sort of configuration would work to create a single Desktop across both monitors?

Cheers to all of you.

nvidia-settings is used to configure your monitor and it has several options available to you for configuring desktops.

---

### Post by benbenny on 2010-06-03
> **bodhi.zazen said:**
> nvidia-settings is used to configure your monitor and it has several options available to you for configuring desktops.

Thanks. I see that now. My two screens have different resolutions. 
Save me some time by telling me how to deal with this?

Cheers


PS
Took out my battery and the laptop came back to life. Hallelujah.

---

### Post by bodhi.zazen on 2010-06-03
> **benbenny said:**
> Thanks. I see that now. My two screens have different resolutions. 
Save me some time by telling me how to deal with this?

Cheers


PS
Took out my battery and the laptop came back to life. Hallelujah.

nvidia settings should allow you to set the resolution of each monitor as well.

Look through the menues

[IMG]http://blog-pics.chewearn.com/2008-10/nvidia-settings15.gif[/IMG]

---

### Post by sgosnell on 2010-06-03
> What i was trying to do is not completely stupid?I wouldn't call it the smartest thing anyone has done in the entire history of mankind, but we've probably all tweaked things until they broke before.  I still do that, and did it today.  But I learned something, so it's all good.

Can't help much with the monitor problem, I don't mess with that much.  I do connect an external monitor to my laptop now and then, but there's no drama, I just connect it and it works.  I've never seen the need to edit xorg.conf, I just use System/Preferences/Monitors and tell it where to place the external monitor.  I like it on the left of the laptop monitor, but that's just me.  Mirroring the monitors (having the same image on both) doesn't work for me, because my laptop is a widescreen and the monitor isn't.  The configuration I get isn't ideal, but it works.

---

### Post by benbenny on 2010-06-03
> **bodhi.zazen said:**
> nvidia settings should allow you to set the resolution of each monitor as well.

Look through the menues

[IMG]http://blog-pics.chewearn.com/2008-10/nvidia-settings15.gif[/IMG]

Only way to get them to match is to go down all the way to 1024x768

But even when I try that it doesn't let me change the resolution for the laptop screen. 
 
I get the error:

> Failed to set MetaMode (1) 'CRT-0: 1024x768 @1024x768 +1024+0, DFP-0: 1024x768 @1024x768 +0+0' (Mode 2048x768, id: 51) on X screen 0.

---

### Post by bodhi.zazen on 2010-06-03
> **benbenny said:**
> Only way to get them to match is to go down all the way to 1024x768

But even when I try that it doesn't let me change the resolution for the laptop screen. 
 
I get the error:

That is either a hardware problem (you monitors will not do what you request) or a problem with the nvidia driver.

You best option is to post on the nvidia (linux) forums .

---

### Post by benbenny on 2010-06-04
> **bodhi.zazen said:**
> That is either a hardware problem (you monitors will not do what you request) or a problem with the nvidia driver.

You best option is to post on the nvidia (linux) forums .


Nothing is ever easy.
Thank you sir!

---

