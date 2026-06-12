---
title: "Please help - I edited my xorg.conf and now my PC won't start"
date: 2011-06-07
forum: General Help
---

### Post by chrisp3047 on 2011-06-07
Hi there,
 
I'd be really grateful for anyone's thoughts on my problem, it kept me awake last night!
 
My PC running 11.04 was showing a blank screen after every 10 mins while watching BBC iplayer (with all the screensaver and power saver settings switched to over 1 hour). The picture returned when I moved the mouse but it was still annoying.
 
So I googled for a solution and found this page [http://ubuntuforums.org/showthread.php?t=858658](http://ubuntuforums.org/showthread.php?t=858658). Based on this, I did the following in terminal:
 
"sudo gedit /etc/X11/xorg.conf"
 
Then when the text editor came up, I deleted 'EndSection' from the xorg.conf file, and added the following lines:
 
Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

My problem: upon rebooting the computer, I just got a purple screen with the Ubuntu logo, it went no further. I tried booting with the livecd and removing the lines I added, but it wouldn't let me save the file. I also tried booting into recovery mode but I'm not very adept at the command line navigation stuff, so I don't know how to find or re-edit the file.
 
Can anyone help? I'd be so grateful.
 
Thanks, Chris

---

### Post by Bucky Ball on 2011-06-07
Did you backup your xorg.conf before editing it????? Rule of thumb. That, as you discovered, is an important file that can screw things. 

If you backed up, that is going to be easy. If not ... 

When you boot to the terminal repeat what you did in the first place. Try:

```
sudo gedit /etc/X11/xorg.conf
```

... to get to the xorg.conf file again. 

* I'm suprised the site you were looking on didn't give you instructions to back up your xorg.conf file before changing it. They usually do.

---

### Post by mikewhatever on 2011-06-07
From the recovery mode, 

to rename the file:
```
mv /etc/X11/xorg.conf /etc/X11xorg.conf-backup
```

to remove it:
```
rm /etc/X11/xorg.conf
```

...and to edit (ctrl-o to save, ctrl-x to exit):
```
nano /etc/X11/xorg.conf
```

---

### Post by Bucky Ball on 2011-06-07
> **mikewhatever said:**
> ...and to edit (ctrl-o to save, ctrl-x to exit):
```
nano rm /etc/X11/xorg.conf
```

? Not sure about this one, MikeW ... perhaps:

```
sudo nano /etc/X11/xorg.conf
```

... to edit??

---

### Post by nothingspecial on 2011-06-07
From the recovery mode

```
sudo nano /etc/X11/xorg.conf
```

nano is an editor just like gedit, but a cli one.

Undo your changes then press Ctrl-O to save, Enter to confirm then Ctrl-X to close nano.

After that ```
sudo reboot
```

If that doesn't work, go into recovery mode again and type

```
sudo dpkg-reconfigure xserver-xorg
```

Which will hopefully set everything back to the way it was before.

---

### Post by mikewhatever on 2011-06-07
> **Bucky Ball said:**
> ? Not sure about this one, MikeW ... perhaps:

```
sudo nano /etc/X11/xorg.conf
```

... to edit??

You don't need sudo in the recovery mode.;)

---

### Post by nothingspecial on 2011-06-07
> **mikewhatever said:**
> 
```
nano rm /etc/X11/xorg.conf
```

You don't want to nano rm though :p

although it will go to /etc/X11/xorg.conf after it creates a file called rm

thing is the op probably wouldn't know that and get very confused ;)

---

### Post by chrisp3047 on 2011-06-07
Wow - thanks to all who have responded. I will have to wait until I get home from work to try to fix this.
 
I will try the following:
1. Boot into recovery mode
2. Type "nano /etc/X11/xorg.conf" (since I don't need to use sudo in recovery mode)
3. Undo the changes then press Ctrl-O to save, Enter to confirm then Ctrl-X to close nano.
4. Type "reboot"
5. If this doesn't work I'll try "dpkg-reconfigure xserver-xorg"
 
Will report back as soon as I can - thanks again for your help.

---

### Post by Bucky Ball on 2011-06-07
> **nothingspecial said:**
> You don't want to nano rm though :p

although it will go to /etc/X11/xorg.conf after it creates a file called rm

thing is the op probably wouldn't know that and get very confused ;)

My point exactly. Good plan, ChrisP.

---

### Post by mikewhatever on 2011-06-07
> **nothingspecial said:**
> You don't want to nano rm though :p

although it will go to /etc/X11/xorg.conf after it creates a file called rm

thing is the op probably wouldn't know that and get very confused ;)

Ah yes, thanks for catching that. Corrected above.

---

### Post by chrisp3047 on 2011-06-07
Hooray! It worked first time! 

Thank you so much to everyone who took the time to respond. What a nice bunch of people. I'm inspired to find out how all this Linux stuff really works!

Chris

---

### Post by Bucky Ball on 2011-06-07
Good news and enjoy! Hopefully you will have clear sailing but if the surface gets rough don't hesitate to post a new thread. ;)

PS: Next time:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```... before you begin tweaking. Then you can just reverse if you get into trouble and you have your original xorg.conf back:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

cp = copy.

---

