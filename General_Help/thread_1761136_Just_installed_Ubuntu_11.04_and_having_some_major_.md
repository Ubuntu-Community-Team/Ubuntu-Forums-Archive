---
title: "Just installed Ubuntu 11.04 and having some major issues"
date: 2011-05-17
forum: General Help
---

### Post by imsojdm on 2011-05-17
I just installed Ubuntu 11.04 32 bit from Ubuntu.com and burned the iso to a cd, and then used the cd to install Ubuntu on my desktop. This desktop is a Dell Dimension 4600C that was running Windows xp. I have Ubuntu via the windows installer on my laptop so I already knew I liked Ubuntu, hence why I made it the actual operating system on this desktop. Well, I installed it with the cd, made an account and now once I log in it acts really strange. Whenever I click anywhere, the toolbar at the top and bottom just disappear. When I try right clicking it just flickers and won't let me do anything. After dragging around the mouse I can sometimes get the toolbar to pop up but I still can't click on anything. When I click on Applications or System the screen just flickers and you see the drop down box for half a second, then it goes away. I tried restarting and nothing really has seemed to work. I'm comfortable with linux as far as the command line goes but I can't even get to the command prompt. I did manage to open up firefox amazingly but it just froze after 10 seconds. Any help would be great

---

### Post by IWantFroyo on 2011-05-17
During boot up, hold down 'esc' just as the screen goes away from your manufacturer's screen.
You'll get to GRUB. Push 'e' on the first option, and add 'edd=on' (without the 's) to it. It doesn't really matter where you put it here.

When you get to the desktop, it its fixed, hit <ctrl><alt><t> and type:
```
sudo gedit /etc/default/grub
```

Change this:
```
GRUB_CMDLINE_LINUX=""
```
To this:
```
GRUB_CMDLINE_LINUX="edd=on"
```

Save, and run:
```
sudo update-grub
```

On the other hand, if you can get to a terminal without the grub stuff, and do the /etc/default/grub stuff, it should work as well.

EDIT: I had this problem with the Natty betas, and this is what worked for me. Let us know if it works for you. Thanks!

---

### Post by imsojdm on 2011-05-17
when I hold down escape after the dell boot screen my computer beeps really fast and then goes to some sort of command line. I entered e and it said command not found or something of that nature. Then after a few seconds it automatically started the gui and took me to the log in prompt

---

### Post by drs305 on 2011-05-17
imsojdm,

Welcome to the Ubuntu forums.


With Grub 2, it's the SHIFT key you hold down to display the Grub menu. Then 'e' to edit the first menu entry. The line you add options to is the line starting with 'linux'.

If the previous suggestion didn't work, try removing "quiet splash vt.handoff=7" and add "nomodeset" (no quotes). CTRL-x to boot. 

If it boots you will have to add your video card's driver. Press the Super key or ALT-F2, type additional drivers, then click on the icon that appears.

---

### Post by imsojdm on 2011-05-17
Thanks for the warm welcome. I managed to get to the grub screen by holding in alt and then I added the nomodeset and used ctrl-x to boot. This changed my resolution but then prompted me to log in, I logged in and then everything worked fine (other than the resolution being weird). I did alt-f2 and then searched for additional drivers but nothing matched my search. I restarted to see if it fixed the problem and the next time I logged in it was still acting all funny just as before.

---

### Post by drs305 on 2011-05-17
> **imsojdm said:**
> Thanks for the warm welcome. I managed to get to the grub screen by holding in alt and then I added the nomodeset and used ctrl-x to boot. This changed my resolution but then prompted me to log in, I logged in and then everything worked fine (other than the resolution being weird). I did alt-f2 and then searched for additional drivers but nothing matched my search. I restarted to see if it fixed the problem and the next time I logged in it was still acting all funny just as before.

Any changes you made at the Grub menu are non-persistent. You would have to repeat them unless you are able to change your configuration after you get into your OS. 

When you say you searched for additional drivers, did you actually find the 'Additional Drivers' applet and let it try to find a driver for you. I just want to make sure I made my instructions clear enough.

For the time being, if using the nomodeset kernel option is preferable to what you had, you can make it permanent by doing this:
gksu gedit /etc/default/grub

Find this line and make it look like:
> GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
Save the file, then run this to make the change permanent:```

sudo update-grub
```

This is not the solution, it's just a workaround. Another helper who has been working on a Natty bug with the interaction of Grub and Natty says to try adding "vga=769 text" instead of nomodeset. (769 is 640x480, 771 is 800x600, and 773 is 1024x768 - pick one you know will work). It will take you to a screen logon. Sign in and then run:
```
sudo service gdm start
```
I'm not very familiar with what's going on with the video issues, but this may give you a start.

---

### Post by imsojdm on 2011-05-18
I'm not sure how I would go about finding the Additional Drivers applet, when I searched through all the files on the system it said that my search had no matches. 

I talked to my friends dad and he said he's 99% sure I need video drivers since mine are out of date I guess since the desktop is like 5 years old. Seems like that's what you guys are trying to help me figure out which is good.

---

### Post by drs305 on 2011-05-18
> **imsojdm said:**
> I'm not sure how I would go about finding the Additional Drivers applet, when I searched through all the files on the system it said that my search had no matches. 

In Natty, either click on the 'home' button (the upper left icon on the top panel), or press the Super (Windows) key. This should open Dash in the upper left. Start typing Additional Drivers and an icon should appear. Click the Additional Drivers icon and it should open the applet and search for available drivers.

---

### Post by klyick on 2011-07-21
> **drs305 said:**
> In Natty, either click on the 'home' button (the upper left icon on the top panel), or press the Super (Windows) key. This should open Dash in the upper left. Start typing Additional Drivers and an icon should appear. Click the Additional Drivers icon and it should open the applet and search for available drivers.

Additional drivers shows nothing. Enable is greyed out.

---

