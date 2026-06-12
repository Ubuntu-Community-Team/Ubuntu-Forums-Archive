---
title: "Screen Resolution Out-of-range at Boot Ubuntu 10.04"
date: 2011-05-09
forum: General Help
---

### Post by Lloyd Ewing on 2011-05-09
While trying to get the system to boot with the screen resolution I need, somehow I apparently set it to a value that my monitor will not display. When my Ubuntu 10.04 boots, the screen just displays an out-of-range message and the system is completely unusable. 

I tried removing the file:  ~/.config/monitors.xml
as described on this page
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
but that had no effect.

Someone told me to install a different display board, but that gave the same results.  The system was working fine except for the resolution problems with the Nvidia driver.  The display board is an Nvidia GEForce2 MX400 64MB AGP and the driver I installed is the recommended one from Nvidia.

I hope someone can help because I have been unable to do anything with on my computer for several weeks.  Thanks for any help,

Lloyd

---

### Post by Wim Sturkenboom on 2011-05-09
Check if a file called xorg.conf exists in /etc/X11. If so, make a backup of it.

Did you try recovery mode with failsafe X?

Other things to try
1)
Check if a file called xorg.conf exists in /etc/X11. If so
1a)
verify the contents. It might contain a HorizSync and a VertRefresh that don't match your monitor's specs. Or an incorrect resolution. Fix it up (if you have the knowledge)
1b)
Make a backup of it and delete it. Restart the x-server (or reboot the system).

---

### Post by Lloyd Ewing on 2011-05-09
Wim,
Thanks for the suggestions.

I tried the recovery mode option in the grub menu.  It gives me the same out-of-range error.  Is that the same as failsafe X?

1a) I went through my /etc/X11/xorg.conf file a couple of days ago and compared it against a man page that describes the file.  The only thing I could find to change was the ranges for the HorizSync and a VertRefresh.  I set them to match the specs for the monitor and got the same out-of-range error.  It seems like there should be a way to give it a file with exact specs that describe the model of the monitor I am using, but I don't see a way to do that.  

1b) I tried booting the system after deleting the xorg.conf file  just now and got the same out-of-range message.

As nearly as I can remember, the last thing I did before the system became unusable was I tried to get the system to boot with the vertical rate to 60 Hz.  All of the settings I changed up to that point were make in GUI mode.  I think I was having a problem because when I tried to set the vertical rate to 60 Hz, the software would go into an interlaced mode.  I don't think my monitor does interlaced mode.  I had hoped to find a setting in xorg.conf which would specify a non-interlaced mode, but I couldn't find a way.

---

### Post by Wim Sturkenboom on 2011-05-09
failsafeX is an option (in a simple menu) once you are in recovery mode. But you don't see the menu so that does not help.

Does your xorg.conf have a section like below? If so, change the driver in that section to vesa (I've marked the line in bold). Leave the identifier as is in your xorg.conf .

If not, add it. I'm getting on territory that I'm not familiar with (would be trial and error for me), so not sure how to advice further in this case.

```

Section "Device"
    Identifier     "NVIDIA Corporation NV44 [GeForce 6200 TurboCache]"
**    Driver         "nvidia"**
EndSection

```

If that gets you going, you  might be able to take it from there with another driver.

---

### Post by Lloyd Ewing on 2011-05-09
Wim,
I tried changing the driver line:
    Driver         "vesa"
and I get the same out-of-range message.

Wim,  Thanks very much for your suggestions.  If you think of something else that I might try, please let me know.

Lloyd

---

### Post by Duncan Williams on 2011-05-09
Heres some suggestions but I am no expert.
> Boot from livecd and access and reset your video card (drivers) from there.
> Backup your important stuff using windows.
[http://www.google.com/search?q=read%20linux#sclient=psy&hl=en&source=hp&q=access+linux+from+windows&aq=4&aqi=g-c4g3g-c3&aql=&oq=access+linux&psj=1&bav=on.2,or.r_gc.r_pw.&fp=e7386a9c3eba4fdd]("http://www.google.com/search?q=read%20linux#sclient=psy&hl=en&source=hp&q=access+linux+from+windows&aq=4&aqi=g-c4g3g-c3&aql=&oq=access+linux&psj=1&bav=on.2,or.r_gc.r_pw.&fp=e7386a9c3eba4fdd")

Then re-install ubuntu from scratch.

---

### Post by Lloyd Ewing on 2011-05-09
Duncan, I don't understand.
How would I access and reset the video card drivers after booting from the live CD?
How could I use Windows to backup important stuff?  I don't have Windows on this system, if that is what you are thinking.
What does that link for a Google search have to do with this problem, or is it a typo?

On Ubuntu 10.04, is there not better way to fix this problem than reinstalling the whole system?

---

### Post by ThatCoolGuy220 on 2011-05-09
@Lloyd Ewing

Im new on this linux world but i had same problem on my Old desktop PC:

Try one of the below 


Press: Alt+F2 or Ctrl+F2, you can Use F4, F5, F3 too .

This is to change screen resolutions What happened to me was 2 things:


:-1 Case:

I got a Terminal.

:-2 Case:

Got ubuntu splash screen and after that live.

---

### Post by Lloyd Ewing on 2011-05-10
CoolGuy220,
I tried hitting each of those keys after the out-of-range message was displayed, and nothing happened.  Is that what you meant?  I haven't read anything about using function keys to reset resolution in Ubuntu, are you sure you didn't have windows on that machine?

---

### Post by ThatCoolGuy220 on 2011-05-10
Nope but it was long time ago 

Try Crtrl+Alt+F7, Here Crtl+Alt+F2 sends  me to a code wall to login but when pressing Crtrl+Alt+F7 it get back to normal

I would look deeper so see if i could find that Post again 

Ah also try to do the bootable USB with diferent program like:

Unetbootin, Linux USB creator, Pendrive linux.


Also u can do Unetbootin equivalent on Puppy but thats irrelevan for this case....

---

### Post by Duncan Williams on 2011-05-10
Yes I thought you had windows on dual boot.
The google links shows different ways of copying files of ubuntu with windows as per backing them up.
If you do a new install of ubuntu it should leave your existing partition intact so you can still access any files you have there.
I had a few video problems not long ago and in the end did a clean install and all good now.

---

### Post by ThatCoolGuy220 on 2011-05-10
Here (it works with linux live usb creator though)

[http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/](http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/)


Also you could try what this guy did:

 Edit  usplash.conf

This Code
 ```
sudo gedit /etc/usplash.conf
```Change values acording to your screen right resolution in my case  

xres=1024 
yres=768.
 

Then: execute 

```
sudo update-initramfs -u 
```


Reboot.
 



But for me The Ctr+Alt+F7 worked after i could see what was going on i installed bad thing was that i had to do it everytime then i changed my PC and it worked without tricks...........





Oh and im a newb on linux Learning some and sharing my experiences Hope u install ubuntu its an awesome O.S

---

### Post by Lloyd Ewing on 2011-05-28
I finally was able to get my system running without reinstalling Ubuntu.

I think I tried everything that had been suggested and couldn't get any of them to work, but the last post by CoolGuy has a link to a blog >  [http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/](http://blog.siliconforks.com/2010/05/07/monitor-out-of-range-installing-ubuntu-lucid-lynx/)  
At the bottom of that post to the blog, it mentioned editing the file:
/etc/default/grub
and changing the line:
GRUB_CMDLINE_LINUX=""

Making the change recommended there didn't help. but I noticed that this line had something extra on it:  vga=792
I found that deleting these characters would allow me to get a usable display, but I would have to edit the file from grub each time I booted the system to get it to work

As soon as I got a boot with a usable screen, I got rid of the driver from Nvidia and also uninstalled Startup-Manager, which I suspect caused the worst part of my problems.  For now I am running the system without the driver from Nvidia and wondering if it is feasible to use this proprietary driver for Ubuntu.  If I am going to use it I will have to find some other way to install it, because the Ubuntu install does NOT work for this driver.

As nearly as I can remember, it seems like Startup-Manager was responsible for getting my system into a completely unusable state.  When I installed the driver from Nvida, I had to manually change the Nvidia setting every time after I booted the system before I could get a usable display.  I tried installing Startup-Manager and using it to set what I thought would be reasonable display parameters (1024x768).  This experience with Startup-Manager leads me to think that it is DANGEROUS and only users who understand its source code should use it.  It does not have help or any other documentation for the user that I can find.

---

