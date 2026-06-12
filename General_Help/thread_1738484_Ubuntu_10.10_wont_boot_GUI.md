---
title: "Ubuntu 10.10 wont boot GUI"
date: 2011-04-24
forum: General Help
---

### Post by bdmullin on 2011-04-24
Hey so I came into a problem today after making some changes to my Ubuntu installation on my hp 1100 tablet. More specifically I installed my NVIDIA driver then restarted only for it to fail. After some work I got it to boot into a terminal without GUI. When I switch into GUI it says checking battery state but nothing happens. Thanks in advance for any help, I have spent all day googling for solutions. My install disc is two hours away so I can only use terminal. No fresh install or live cd help possible today. Im only on the internet thanks to my smart phone.

---

### Post by conradin on 2011-04-24
what is your graphics card, and have you downloaded a driver directly from nvidia? Their drivers work best.

---

### Post by shaoxiao on 2011-04-24
I faced this problem before. But my graphic driver is ATI. I suggest you remove the driver via terminal. Then download it from the official website and reinstall it.

---

### Post by bdmullin on 2011-04-24
The card is "Nvidia GeForce 4 Go 420 32mb (4x APG). I installed the driver using additional drivers from system preferences. I was following a tutorial sorta thing and it also had me edit the xorg.conf file to allow screen rotation and change the driver and stuff to NVIDIA. I already cleared all the data in xorg.conf file so it is blank and that is how I got to the terminal. An update to my progress: it now passes battery checking and is stopped at starting apparmor profiles...but still no GUI.

---

### Post by bdmullin on 2011-04-24
> **shaoxiao said:**
> I faced this problem before. But my graphic driver is ATI. I suggest you remove the driver via terminal. Then download it from the official website and reinstall it.
 how would I remove the driver from terminal? I tried sudo apt-get remove nvidia-current but it didn't seem to change anything for me.

---

### Post by shaoxiao on 2011-04-24
```
sudo apt-get &#8211;purge remove nvidia-glx
```
Then restart to see if it works.

---

### Post by conradin on 2011-04-24
Im sticking with use the NVIDIA driver. 
[http://www.nvidia.com/object/linux_display_ia32_1.0-8756.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8756.html)
it will give you options to install, modify the xorg file, etc...

I also think Lucid doesnt need to use xorg.conf, it will use it if its there, but will load automaticaly if its not there. Though the resolution wiki isnt directly related, if youve been tweaking xorg.conf you might as well check it out. You might consider removing (backing up first) your xorg.conf file.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by bdmullin on 2011-04-24
> **shaoxiao said:**
> ```
sudo apt-get –purge remove nvidia-glx
```
Then restart to see if it works.
 I tried your code and it didn't work. I received the following statement "command line option 'p' (from -purge) is not known". I tried just purge and it said " virtual packages like 'nvidia-glx' can't be removed". Finally I tried just remove and got the same message. Maybe I'm doing something wrong.

---

### Post by bdmullin on 2011-04-24
> **conradin said:**
> Im sticking with use the NVIDIA driver.[]("http://")
 site seemed useful, should have read this before hand but I can't reach a GUI to install this anymore. I only have terminal. Also my wireless driver may no longer be working but idk how to test. I ran update and it returns err or failed on everything. Wasn't doing this an hour ago. How do I test this? Im really appreciating the help. Karma is on your side.

---

### Post by shaoxiao on 2011-04-24
> **bdmullin said:**
> I tried your code and it didn't work. I received the following statement "command line option 'p' (from -purge) is not known". I tried just purge and it said " virtual packages like 'nvidia-glx' can't be removed". Finally I tried just remove and got the same message. Maybe I'm doing something wrong.
Sorry bdmullin, it is my fault.Try this.
```
sudo apt-get --purge remove nvidia-glx
```I can't make sure it will works but i actually works for me.
----------------------------------------------------------------------------------------------------------------------------------------
It seems that this method doesn't works for tablet. Sorry

---

### Post by fdrake on 2011-04-25
> **bdmullin said:**
> The card is "Nvidia GeForce 4 Go 420 32mb (4x APG). I installed the driver using additional drivers from system preferences. I was following a tutorial sorta thing and it also had me edit the xorg.conf file to allow screen rotation and change the driver and stuff to NVIDIA. I already cleared all the data in xorg.conf file so it is blank and that is how I got to the terminal. An update to my progress: it now passes battery checking and is stopped at starting apparmor profiles...but still no GUI.

```
sudo rm -f /etc/X11/xorg.conf
```
and reboot , i don't thing is the driver the issue

---

### Post by bdmullin on 2011-04-25
Yea it doesn't seem to like that command. Im not sure what else to do... Without a livecd at least.

---

### Post by bdmullin on 2011-04-25
> **fdrake said:**
> ```
sudo rm -f /etc/X11/xorg.conf
```
and reboot , i don't thing is the driver the issue
 
Just tried this and it didn't make any difference. Screen flashes a few times the drops me into command line. Switched to GUI and it is still at battery checking ok spot.

---

### Post by fdrake on 2011-04-25
```
sudo nvidia-xconfig
``` then reboot

---

### Post by bdmullin on 2011-04-25
> **fdrake said:**
> ```
sudo nvidia-xconfig
``` then reboot
 Tried the above code and it moved me in the opposite direction. Now when it boots it freezes on Ubuntu load screen and I can't get into the terminal. If I reboot and repeatedly hit esc I can find my way into the terminal. From there I log in. Then I hit control+alt+f7 and get a GUI again stuck at battery check. The only other think I can think of is that I changed a file to load xkeybingings or something like that on startup. Don't remember the name exactly.

---

### Post by fdrake on 2011-04-25
it's doing that because you removed the nvidia driver with the suggestion of the other user.so you need to reinstall it.

```
sudo apt-get install nvidia-glx
```
```
sudo nvidia-xconfig
```
```
sudo /etc/init.d/gdm restart
```

---

### Post by bdmullin on 2011-04-25
> 
 
```
sudo apt-get install nvidia-glx
```

 can't find the installation candidate for nvidia-glx

---

### Post by fdrake on 2011-04-25
> **bdmullin said:**
> can't find the installation candidate for nvidia-glx

```

sudo apt-get install nvidia-glx-185
```

---

### Post by bdmullin on 2011-04-25
I installed nvidia-gxl-185 and then ran the next two lines but nothing has changed. Im starting to think I'm really screwed here. Thanks for helping out.

---

### Post by fdrake on 2011-04-25
out of ideas for the moment since i don't know what else you have changed. I hope someone in the forum will help you out to reset all your setting. just keep this threat alive by posting new msg. . .

---

### Post by w00dr0w on 2011-04-25
I am having the same problem... I haven't done anything yet to attempt to fix it, so nothing has been messed with. I am running 10.10 and my graphics card is NVIDIA GeForce 310M. As soon as I installed the update via the Update Manager and rebooted, it just booted straight to the terminal. Any ideas where I should start? I haven't found anyone with this problem that has solved it yet....

---

### Post by conradin on 2011-04-26
> **bdmullin said:**
> site seemed useful, should have read this before hand but I can't reach a GUI to install this anymore. I only have terminal. Also my wireless driver may no longer be working but idk how to test. I ran update and it returns err or failed on everything. Wasn't doing this an hour ago. How do I test this? Im really appreciating the help. Karma is on your side.

The NVidia drivers typically require to shutdown the graphical session and run via a terminal session. YOu might have to make the script executable with the command 
```
sudo chmod +x driverName
```

---

