---
title: "Second monitor disabled after restart"
date: 2010-02-14
forum: General Help
---

### Post by motorcity909 on 2010-02-14
Hi all

I've recently installed a second monitor and it's great having all that extra space.  

However, Ubuntu 'loses' the new monitor after a restart and I have to go into System>Preferences>Display and get the second monitor re-enabled and put to the left of my existing monitor.  Quick flicker and the second monitor is on.

I don't really want to have to do this every day so am I missing something so my second monitor is remembered?

Thanks as ever
Dave

---

### Post by audiomick on 2010-02-14
Hi.
What is your graphics card?

---

### Post by SuperSonic4 on 2010-02-14
It might help if you create an xorg.conf to manually override ubuntu's default. If you have an nvidia card this should just be ```
sudo nvidia-xconfig
```

---

### Post by motorcity909 on 2010-02-14
My card is an Nvidia GeForce FX 5700.

When I go into System>Preferences>Display I get the attached message and once I click yes, then the X-server settings opens.

All the help is much appreciated.

---

### Post by audiomick on 2010-02-14
Ok, that is in the right direction, but not quite right. That starts the nVidia settings thing as a normal user, but you need root privileges to store the xorg.conf file that it creates.

Do
```
gksu nvidia-settings
```
in a terminal. The same thing will open, but with root privileges (invoked with "gksu") Do your setup and click on "save". Then it should stick.

---

### Post by fooman on 2010-02-14
you should be using the nvidia-settings as root to make the changes "stick".

open a terminal (applications > accessories > terminal) and type:

```
gksudo nvidia-settings
```enter your password when prompted,  then press enter.  when it opens,  look under "x server display configuration".  you should an image of both your monitors.  if they are not in the right place,  just drag and drop the images around in that box so they are correct.  then click the "configure" button and choose "separate x screen".  after that,  click "apply"...you will see a warning that not all changes could be applied....click ok.  then click "save to x configuration file".

log out and back in again (or reboot) to see if they changes stuck.

hope that helps.

edit: sorry,  too slow.  audiomick beat me to it.

---

### Post by audiomick on 2010-02-14
> **fooman said:**
> ...  then click the "configure" button and choose "separate x screen"....
I disagree. I think you want to choose "twin view". That is what I am using for my dual monitor setup, and what is recommended as the method to spread your desktop across two monitors when using nVidia graphics.

Twin View is the nVidia proprietary equivalent to Xinerama. It uses one screen (not monitor in this case, but rather the screen that the x server generates to be passed on to the monitor(s) ) with the outside dimensions of both monitors put together.

---

### Post by motorcity909 on 2010-02-14
Thanks for everyone's replies.  I ran nvidia-settings as sudo and saved the configuration file.  

Rebooted and it still remembers the second screen but my top panel is now just on one (the original, right-hand) screen, whereas it was spread across the two with the apps/places/system menus in the top left.

Screengrab attached as it is now.

Cheers
Dave

---

### Post by audiomick on 2010-02-14
You happy with that?
If you want the panel on the other screen, right click on it, de-expand it, drag it across and re-expand it. I think it will stick.

---

### Post by motorcity909 on 2010-02-14
Bit more info - I've got the nvidia settings as 'twin view' (which was fine yesterday) but when I click 'left of' + apply for the position of the monitor nothing happens but if I click 'right of' it does apply and change.  So the position sticks as 'absolute'.

I've also noticed that if I roll my desktops in Compiz, the dektop octagon appears on both monitors whereas yesterday the dektop cube rolled over both screens as one.  

I'm guessing it's now an octagon as it thinks it's 2 x 4 desktops.

Any help will be much appreciated!

---

### Post by motorcity909 on 2010-02-14
> If you want the panel on the other screen, right click on it, de-expand  it, drag it across and re-expand it. I think it will stick.

Thanks Michael.  I tried that but it just expanded it on the left-hand monitor not across both.  

What I'd like is the apps/place/system menus in the top left of the left-hand monitor and the time/weather/shutdown etc in the top right of the right-hand monitor.

It does seem to be treating both screens separately - yesterday if I maximised a window it filled both monitors, today it just fills the one.  

The wallpaper is correctly spread across the two as you could tell from the screengrab.

Thanks
Dave

---

### Post by audiomick on 2010-02-14
As far as the panel goes, you could consider adding another panel to the "empty" monitor and spreading your icons around by hand. I'm actually happy that it sticks to one monitor, as my two are not the same height. This means that if the panel were expanded across both, I wouldn't see the bit on the smaller monitor.

Regarding expanding the windows: yes, they maximise onto the monitor they are on. Because of the different sized monitors again, this is also something I am happy about...
I don't know if there is any way of changing that behaviour, sorry.

---

### Post by motorcity909 on 2010-02-14
That's a good idea.

Having the menus on the original monitor which I'm using to viewing makes sense, then the new second monitor is my spare real-estate, so I've got some weather and cpu/ram screenlets over there.

I do like the fact that I can maximise windows in each monitor now rather than dragging the borders to fill the screen(s).

I've got the Compiz cube back by changing the number of desktops down to 2, which it interprets as 2 x 2 thus giving me a cube again not an octagon.

I've also added panels top and bottom of the new monitor so it matches the original.

Just weird how earlier it was all 'as one' then after applying those changes as sudo so it remembered them, it's changed something.  Funny how I can't get it to apply 'to the right of' now.

I *might* try disconnecting the new monitor completely, reverting the nvida settings to default, then once new monitor is plugged in again, run nvidia as sudo, get it to detect the new monitor and apply all those settings again.

Experience though tells me to leave it alone - it's working, so let it lie!

Thanks for all your help
Dave

---

### Post by audiomick on 2010-02-14
I wouldn't mess with it either.
If you do, save a copy of /etc/X11/xorg.conf before you do.
Save your gnome settings before you do. I don't know exactly where that is, but it is one or more of the hidden files in your home folder.
That way, if you shoot it down, you should be able to copy the files back in and get back to where you are now.

I also have observed changes between setup, save and reboot. I can't remember the details,  but how the windows maximise was one of the things. I have had to set up the twin view a couple of times now, and there was nearly always some little quirk that annoyed me until I had rebooted and given it a chance to sort itself out.

Anyway, have fun with it!

---

