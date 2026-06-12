---
title: "Screen resolution is small"
date: 2011-05-25
forum: General Help
---

### Post by otinanai on 2011-05-25
Hello, I have a problem with Lubuntu. First of all I installed it on my old laptop (amd sempron 1.6GHz, 512MB ram, s3g vga) as windows seemed to slow down my system. Installation was good, but the problem is screen resolution which is only 800x600 and there is no higher res option. 

Laptop's native is 1024x768. I searched a lot about how to change it but there is no post for lubuntu (everything is for ubuntu, xubuntu, and doesn't seem to work in here). Please help me fix this... Beyond that isse i I feel Lubuntu is running much better than windows and I want to use it.

Using Lubuntu 11.04. Let me add that when I tried Lubuntu 10.04 it didn't have this problem (all resolutions where available).

---

### Post by aeiah on 2011-05-25
any fix that works for the other ubuntus should work for lubuntu - you just be using different gui tools that change the same settings.

what graphics card / drivers are you using? what's the output of ```
xrandr
```

---

### Post by otinanai on 2011-05-25
It's a VIA/S3G Unichrome ProIGP (64MB vram) and that's the output:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   720x576        60.0  
   800x480        60.0  
   720x480        60.0  
   640x480        60.0 
```

---

### Post by otinanai on 2011-05-25
Ok I tried the fololowing command:


```
xrandr -s 1024x768
```

And I get this message:

```
Size 1024x768 not found in available modes
```

How can I set this resolution? :(

---

### Post by aphatak on 2011-05-25
You need to add the missing resolution manually.  Here is a pretty good article on how to do it - "http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html".

---

### Post by otinanai on 2011-05-25
> **aphatak said:**
> You need to add the missing resolution manually.  Here is a pretty good article on how to do it - "http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html".

I created a new option as shown here:

[[IMG]http://img6.imageshack.us/img6/6140/snapshot1it.th.png[/IMG]](http://img6.imageshack.us/i/snapshot1it.png/)

But when I click apply nothing happens; and even if I get it working, I read that I will have to use some xorg.conf file to make it permanent. Well there isn't any xorg.conf in lubuntu (or at least I didn't find any). Maybe moving to older lubuntu 10.04 seems to be less trouble...

EDIT:By the way thank you all for your support, much appreciated. I may still have chances to make it working. :D

---

### Post by aphatak on 2011-05-25
I couldn't read how you created the mode - was it a screenshot? - it got blocked by the firewall I am currently behind.

Well, you are not going to find any xorg.conf in Ubuntu 10.04 either!  If you find you need one, you can create it, though.
[LIST=1]
[*]Switch to a console - with ctl-alt-F1.  You will see a character terminal and a prompt asking you to log in.
[*]Log in - use the user ID and password you get into the graphical environment.
[*]Enter the command ```
sudo service gdm stop
```[*]Enter the command ```
sudo Xorg --configure
``` This will create a file 'xorg.conf.new' in your home directory.
[*]Start the graphical interface again with sudo ```
service gdm start
```  If you do not get back to your graphical interface, key in ctl-alt-F7 (or if that doesn't work, ctl-alt-F8 ).
[/LIST]
However, before you do all that, I assume you have created a new modeline with the command 'cvt', and associated it with the display (with the command 'xrandr --newmode ...' and 'xrandr --addmode ...').  That will allow you to try your new mode / resolution out, and make sure that is what you want.  (If I remember right, it is described in the howto I referred to in the previous post.)  It is only then you should create your xorg.conf.new, edit it to include the new mode, and copy it to your /etc/X11/ directory under the name 'xorg.conf'.  And make sure you know how to undo these changes if they don't work - you can boot with your live CD and remove the offending 'xorg.conf' from /etc/X11/.

If you haven't done this before, I'll admit this is a bit of an adventure.  However, it can be done, and the satisfaction of having accomplished it is worth all the anxiety.  I should know - I have done it a couple of times, and added to my store of stories I'll tell my grandchildren about my reckless adventures as I dandle them on my knees!:)

---

