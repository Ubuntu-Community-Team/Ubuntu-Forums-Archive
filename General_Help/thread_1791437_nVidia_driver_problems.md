---
title: "nVidia driver problems"
date: 2011-06-26
forum: General Help
---

### Post by profozone on 2011-06-26
Greetings all.  I know this has been addressed and I've tried a few of the methods but no go.

I have new hardware and I'm doing  a dual boot, hoping that Ubuntu will be my primary OS, but I'm having trouble ringing it out.

I installed Ultimate Edition 2.6.1 and in the past with an old machine I could turn on visual effects.  With this machine, when I try to, it says it's looking for a driver, blinks a bit and then comes back with a message saying "Desktop visual effects cannot be enabled."

I assume that I don't have the nVidia driver loaded.  When I go to Hardware Drivers, it says "No proprietary drivers are in use on this system."

In synaptic, the latest driver does not show up.

I followed the instructions on this site that someone put up which required adding some lines to the "Blacklist" then purging old drivers.  It said to expect an error and what to do then, but I never got the error.  When I tried to do the rest of the commands anyway, nothing seemed to happen.  One of the steps was to download the latest driver, which I did.  It was a .run file.

When I double click on the .run file it says that gedit cannot run the file because it did not know what encryption was used.

When I try to run it from a terminal, it either says that the command was not found or just nothing seems to happen.

Help!

My video card is a GTX570.

Thank you.

---

### Post by profozone on 2011-06-26
Oh, in case you don't know Ultimate Edition, it uses Ubuntu 10.04.  Thanks.

---

### Post by profozone on 2011-06-27
Bump.  Anybody?

---

### Post by VanR on 2011-06-27
have you tried in terminal

sudo apt-get install nvidia-current

If that gives you an Nvidia driver you may or may not have to run 

sudo nvidia-xconfig

---

### Post by Frogs Hair on 2011-06-27
I was wondering what Nvidia card you have if no drivers were located when you opened hardware and drivers / additional drivers .

---

### Post by profozone on 2011-06-28
I tried both of those.

My card is an nVidia GTX570

---

### Post by Ozymandias_117 on 2011-06-28
I'm assuming your problem with the .run file is that you didn't make it executable.

```
cd /path/to/installer
chmod +x installer_name.run
sudo ./installer_name.run
```

Edit: Just remember, if you use this method, you MUST manually reinstall your driver after EVERY kernel update (And most xorg updates too).

---

### Post by profozone on 2011-06-28
I tried that and got this error.  

[IMG]http://carphotos.cardomain.com/ride_images/2/4537/1869/23840934004_large.jpg[/IMG]

The name of the installer is:

NVIDIA-Linux-x86_64-275.09.07.run

Did I need the "x" in the command line you specified?

It looks like this is what is on the nVidia website.  I haven't tried this yet.  Should I?

**Linux/x86-64** (64-bit):[INDENT][FONT=Courier New]# chcon -t texrel_shlib_t /usr/lib64/xorg/modules/drivers/nvidia_drv.so
# chcon -t texrel_shlib_t /usr/lib64/xorg/modules/extensions/libglx.so.1.0.9631
# chcon -t texrel_shlib_t /usr/lib64/libGLcore.so.1.0.9631
# chcon -t texrel_shlib_t /usr/lib64/tls/libnvidia-tls.so.1

Thanks again.
[/FONT][/INDENT]

---

### Post by pqwoerituytrueiwoq on 2011-06-28
[http://ubuntuforums.org/showpost.php?p=10991979&postcount=5](http://ubuntuforums.org/showpost.php?p=10991979&postcount=5)
that will help you and i don't feel lie re-typing/formating that

---

### Post by profozone on 2011-07-01
Thank you pqwoe I believe that successfully installed my video driver.  And the effects are pretty cool.

Unfortunately, that seems to have broken some things.  When I go into appearance and try to get everything looking the way it did before (not sure why it changed in the first place), I can only adjust the background color.  I can't change the pointer, the font color, the window border.  What's the deal now?  Do I have to somehow uninstall a theme or something?

I did this once before, with no problems, but now it doesn't work the same way.

---

