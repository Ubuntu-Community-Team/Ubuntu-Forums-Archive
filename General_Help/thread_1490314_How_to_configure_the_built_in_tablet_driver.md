---
title: "How to configure the built in tablet driver"
date: 2010-05-22
forum: General Help
---

### Post by G1imt on 2010-05-22
I installed Ubuntu today, and to my great pleasure i found that my Wacom Intuos 3 tablet worked as perfectly as when the windows driver is freshly installed. Unfortunately, i installed no driver, and therefore can find no way to configure my tablet.

What i need configured is the tablet proportion (i have two screens, so the mouse moves too fast in the X direction compared to the Y direction) and what the pen buttons do in different programs. The wrong button is currently right click.

Could anyone assist me?

---

### Post by Favux on 2010-05-22
Hi G1imt,

Could you tell us what release of Ubuntu you installed?  For example Lucid Lynx (10.4).  What you do depends on the release.

---

### Post by G1imt on 2010-05-22
Ubuntu 10.04 LTS - the Lucid Lynx

---

### Post by Favux on 2010-05-22
OK, with Lucid the wacom X driver is now supplied by Xorg's xf86-input-wacom rather than the linuxwacom X driver.  The Xorg version supports Lucid's X server 1.7 which linuxwacom's doesn't.  Unfortunately that means the configuration gui wacomcpl (Wacom Control Panel) hasn't been imported yet.  However the xsetwacom commands were, after being rewritten.

So instead of configuring through wacomcpl and having it automatically add the xsetwacom commands to it's script file .xinitrc you have to do it manually.  Make a file, call it say .xsetwacom.sh, make it executable, and set it up in auto-start so it runs with every new session.

The button commands for the stylus would look like:
```
xsetwacom set stylus Button1 "Button 1"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button3 "Button 3"
```
And in this example I assigned Button2 to "Button 3" making Button2 a right mouse click.   Stylus tip is by default Button1 and assigned as a left mouse click "Button 1".

They have also changed the device naming convention in Lucid so you need to find out what your stylus is being called.  Enter in a terminal:
```
xinput --list
```
And then substitute the longer more descriptive device name, or the ID number, in for stylus in the xsetwacom commands.

Once you've got that set up we can try to deal with the dual monitors.

---

### Post by G1imt on 2010-05-22
From this
```

&#9116;   &#8627; Wacom Intuos3 6x8 eraser                	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 cursor                	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8 pad                   	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 6x8                       	id=18	[slave  pointer  (2)]

```

I substituted the pointer with the ID 16. Must i restart the computer for the settings to change? Cuz nothing happened when i ran the file;
```

codemonkey@ubuntu:~$ '/home/codemonkey/Desktop/tabletsetup.sh' 
codemonkey@ubuntu:~$ 

```

tabletsetup.sh:
```

xsetwacom set 16 Button1 "Button 1"
xsetwacom set 16 Button2 "Button 3"
xsetwacom set 16 Button3 "Button 2"

```

---

### Post by Favux on 2010-05-22
Rename it .tabletsetup.sh.  Right click on it and choose Properties.  Choose the Permissions tab.  Click on the box in front of Allow executing file as a program.   Close.  Then just double click on it and run as program.  Settings should apply.  You can also enter the commands in a terminal.

---

### Post by G1imt on 2010-05-22
I added the "." in front of the name. It made no difference. I had already made it executable. In any case, i switch between the button 2 and button 3 spots and i expect that if it works, it will switch between the middle click and right click on the stylus. Since they don't, i assume something is not working :P

I tried typing "xsetwacom set 16 Button1 "Button 2"" in the terminal to get a definitive answer if it was working or not. Needless to say, mouse 1 is still mouse 1

---

### Post by Favux on 2010-05-22
My fault.  16 is your Wacom tablet mouse/cursor.  Your stylus is 18 or "Wacom Intuos3 6x8".  So use 18 in the xsetwacom command.

---

### Post by G1imt on 2010-05-22
Success. Is there any way to make button 3 a double-click, like it is in windows?

---

### Post by Favux on 2010-05-22
Good!  :)

Not that I know of.  In Assistive Technologies you can go to mouse and make a long click a secondary button.

OK, now that you have the script file onto the dual screen.  This thread seems to have solved it for Lucid, esp. Caos' post #10:  [http://ubuntuforums.org/showthread.php?t=1461978](http://ubuntuforums.org/showthread.php?t=1461978)

Good luck!

---

### Post by G1imt on 2010-05-22
Well i had a good run. I restarted the PC and now nothing works. Commands like "xsetwacom set 18 Button2 "Button 3"" now have absolutely no effect, even when run from a console with root privileges. Any ideas?

---

### Post by Favux on 2010-05-22
Well don't run them with root priviledges.

Don't know what you could have done to disable the xsetwacom commands.  Could you have altered the permissions on your script file?  But they don't work in a terminal either, root or no, correct?  Go ahead in Synaptic Package Manager and reinstall xserver-xorg-input-wacom and reboot.

---

### Post by G1imt on 2010-05-22
I think there's something more afoot. When the PC restarted, i was given not 3, but 5 options for boot. Usually two ubuntu options (normal and recovery) and windows. Now i got 4 ubuntu options, two different versions. Like xx.xx.01 and xx.xx.02. When i chose the latter, i hit a dead end where my monitors turned on and off in an infinite loop. So i chose the other option, and now everything seems sluggish and slow. I played a round of Heroes of Newerth, and the framerate was ridicolous (like 12fps) even on low settings.

It seems that what usually kills my ubuntu setups is a restart. That seems to **** stuff up.

---

### Post by G1imt on 2010-05-22
I somehow managed to boot using the latter of the previously mentioned boot options. Also after another xinput --list i saw that the stylus was now ID 19 for some reason, and that fixed my problem.

Back to square one! :) I'll be experimenting with mapping once I've recovered from this little nightmare.

---

### Post by Favux on 2010-05-22
Hi G1imt,

This concerns me.  You didn't have a kernel or grub2 update did you?

I'm wondering about a failing hard drive or bad RAM.

---

### Post by G1imt on 2010-05-23
I did indeed run update. One would think that'd be safe.

---

### Post by G1imt on 2010-05-25
Starting the configurewacom.sh script at startup was a bust. It seems the ID of the stylus changes each time the PC starts, so i have to manually change the script. It does work, though.

I am currently trying to get the multi-monitor stuff to work.

---

### Post by Favux on 2010-05-25
> Starting the configurewacom.sh script at startup was a bust. It seems the ID of the stylus changes each time the PC starts, so i have to manually change the script. It does work, though.
It looks like you've run into a device naming bug present in the linuxwacom 0.8.4-4 wacom.ko.  I think that is the default in Lucid.  It got fixed in 0.8.5-12.  So I think what you can do is compile 0.8.6-2 for the wacom.ko and that should fix it.  If you are interested see the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  I was hoping you could avoid it.

---

### Post by G1imt on 2010-05-26
As I'm completely useless in topics as compiling and fixing stuff in Linux, I was prepared to live with having to change the ID sometimes. Another problem I've run into though is the RIGHT CLICK mouse button will not be set to any buttons.

For instance, the following line successfully set the right click button to the left click action:
```
codemonkey@ubuntu:~$ xsetwacom set 18 Button2 "Button 1"
```

But when i try to set it to right click:
```
codemonkey@ubuntu:~$ xsetwacom set 18 Button2 "Button 2"
```

It remains left click! I can set it to scroll up and scroll down, middle click and such, just not right click (button 2). Is this a bug that also will be fixed by the new version?

// EDIT: After some arguing with the tablet and reconnecting it a few times i got it to work. I still think it's unnecessarily hard though.

---

### Post by Favux on 2010-05-26
Hi G1imt,

Right click is 3 so it would be:
```
xsetwacom set 18 Button2 "3"
```
As you can see you don't need to put button with it.

It sounds as if you got things mostly configured, nice work.

---

