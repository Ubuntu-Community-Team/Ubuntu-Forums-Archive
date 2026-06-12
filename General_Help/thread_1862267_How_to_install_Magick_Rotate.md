---
title: "How to install Magick Rotate?"
date: 2011-10-16
forum: General Help
---

### Post by liviococcia on 2011-10-16
Hello Members
I've downloaded 'Magic Rotate 1.5 tar.bz2' onto my HP2710p tablet, but i cant't find how i should be installing it, i'm a linux learner and running Zorin os (but this uses Ubuntu 11.4), and am slowly learning the use of the terminal.

Any help would be great please

kind regards
Livio

---

### Post by Favux on 2011-10-16
Hi Livio,

Right click on the downloaded tar (compressed files like zip) and choose *Extract Here*.  The magick-rotation folder will appear.  In it you will see a file called magick-rotation.  Double click on it and choose *Run*.  The Installer will pop up and ask you if it is OK to install a list of things.  If you say OK it will go on to install Magick Rotation.  Then it instructs you to reboot.  When your system comes back up the Magick Rotation icon should be in your tray and working.  You might want to scan through the Magick-README.txt for further information.

---

### Post by liviococcia on 2011-10-17
> **Favux said:**
> Hi Livio,

Right click on the downloaded tar (compressed files like zip) and choose *Extract Here*.  The magick-rotation folder will appear.  In it you will see a file called magick-rotation.  Double click on it and choose *Run*.  The Installer will pop up and ask you if it is OK to install a list of things.  If you say OK it will go on to install Magick Rotation.  Then it instructs you to reboot.  When your system comes back up the Magick Rotation icon should be in your tray and working.  You might want to scan through the Magick-README.txt for further information.
Hello Favux and thanks for the help, i'm slow replying back as i've been trying to get Magick Rotation to work before i reported back, i installed it as you had instructed and it does appear in the startup icons panel on the desktop, these are my problems below..

I've been trying to update the Wacom driver, and followed the FAQ #1603, and did the instructions below..

1: I opened the Terminal window
2: The typed in below..
     sudo apt-get install git-core
3: Then....
     cd ./Desktop
4: Then..
    git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
5:Then..
    sudo apt-get update
6:Then
    sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libxinerama-dev libncurses5-dev xutils-dev autoconf libtool pkg-config libudev-dev
7:Finally the command below..
    sudo apt-get upgrade

I then checked what version was installed, it reported i still had the old one.

Also, when i flip the screen it doesn't always rotate, and the green arrow icon shows the word 'Loading..', how can start Magick Rotation up other than by running it at startup? , this is encase it's clashing with something else loading during startup.

Again, any help would be great, just to mention it does work, but it's working on and off i think because it still loading, also in the Magick Rotation settings i had to pick 'reverse the hinge' mode for it to work first off.

kind regards
Livio

PS: i think the 'CW' tablet keyboard part of Magick Rotation is the part that's causing the Loading... issue, seems to appear when the screen is turned, and the word 'Loading..' stops, from then on the screen flips correctly, the Wacom driver issue is still a problem

---

### Post by Favux on 2011-10-17
Have you installed CellWriter yet?  If not search for it and install through Software Center.

From what you show you didn't actually compile and install a newer xf86-input wacom.  In addition to the steps you showed you have to do:
```
cd xf86-input-wacom

./autogen.sh --prefix=/usr

make

sudo make install
```
Now reboot.

Magick should be started automatically every time you boot up.

---

### Post by liviococcia on 2011-10-17
Thanks Favux, i followed the rest of the instructions you posted, from the FAQ #1603 at the Magick Rotation at the launchpad website i misunderstood that section, the tablet parts working correctly, great!

Yes, CellWriter is installed but it's still showing 'Loading..' over the startup icon of the Magick Rotation app.

I read the magick rotation.txt file and have created two launchers using  the xrotate.py application file, this  seems to work really well at the moment, i don't know whats causing the slowing down when in the startup panel (systray), but i can live with this unless you know what maybe causing this issue for me?

regards

---

### Post by Favux on 2011-10-17
Sounds like you're making progress.  Portrait mode is fixed.

I don't understand what you are telling me now.  Ignore the "Loading..." tool tip for now.  The icon appears in the system tray but automatic rotation doesn't occur when you swivel your lid?  is that what you are saying?  So you have to use xrotate.py through a launcher?

The icon is green, correct?  So when you click on it Enable is checked, correct?

---

### Post by liviococcia on 2011-10-17
> **Favux said:**
> Sounds like you're making progress.  Portrait mode is fixed.

I don't understand what you are telling me now.  Ignore the "Loading..." tool tip for now.  The icon appears in the system tray but automatic rotation doesn't occur when you swivel your lid?  is that what you are saying?  So you have to use xrotate.py through a launcher?

The icon is green, correct?  So when you click on it Enable is checked, correct?
What seems to be happening is..

The green icon loads in the systray, and the desktop is fully loaded up, if i rotate the screen nothing happens..it doesn't rotate the desktop...i wait and nothing happens...

..i then give up and rotate the screen back to landscape....then i try again, spinning the screen....and wait, then CellWriter appears in the systray and the desktop will go into portrait mode. 

But the above is not always consistent, i've had CellWriter appear in the systray and it still hasn't moved from landscape to portrait mode. 

I can almost rule out any hardware problem as windows vista did not have a problem rotating the screen.

That's the only way i can explain it Favux

regards

---

### Post by Favux on 2011-10-17
Alright.  Your not using a straight Ubuntu release are you?  What are you using and what Ubuntu release is it based on?

---

### Post by liviococcia on 2011-10-18
> **Favux said:**
> Alright.  Your not using a straight Ubuntu release are you?  What are you using and what Ubuntu release is it based on?
Sorry for coming back late Favux, it was 1am here in the UK

No, your right it's Zorin core 5, but it uses Ubuntu 11.04, i also run Emerald desktop manager, with Compizconfig settings manager doing various window effects.

regards

---

### Post by liviococcia on 2011-10-19
I've been trying out the xrotate.py desktop launchers i had created, and have to say they've worked great!, in fact i think being able to just 'double click' on one shortcut to rotate the desktop, then do the same on another shortcut to rotate it back, seems more suited to how i use the laptop, and how it gets used as a portable for my work.

It would still be nice to get Magick Rotation running as it should, and maybe if it's a bug issue either caused by other running apps, or certain  distribution shells, then maybe it'll be rectified in a future release, it's a great program that gets many Linux users with swivel screen laptops out of a big problem  

Thanks Favux for all the help you've given me, i really appreciate it.

regards
Livio

---

### Post by Favux on 2011-10-19
Let's try to diagnose the problem.

In Advanced Setup could you check the Debugging tool box so it is activated and Save it.  Then rotate the screen to portrait and back.  Then post the text file that will appear in the /home/yourusername directory.

---

### Post by liviococcia on 2011-10-19
> **Favux said:**
> Let's try to diagnose the problem.

In Advanced Setup could you check the Debugging tool box so it is activated and Save it.  Then rotate the screen to portrait and back.  Then post the text file that will appear in the /home/yourusername directory.
Hello Favux, i had swiveled the screen two or three times (and not in quick succession) during which time it had not moved from landscape to portrait, then on the fourth try it did, then i copied the text log below  

2011-10-19 20:16:07: checking for rotation
2011-10-19 20:16:07: /usr/bin/checkmagick32
2011-10-19 20:20:26: cur_state: 2 
2011-10-19 20:20:26: old_state: None 
2011-10-19 20:20:27: calling rotation b: 
2011-10-19 20:20:27: right
2011-10-19 20:20:27: calling cellwriter --show-window
2011-10-19 20:20:27: Change to Tablet mode
2011-10-19 20:20:27: checking for rotation
2011-10-19 20:20:27: /usr/bin/checkmagick32
2011-10-19 20:20:45: cur_state: 2 
2011-10-19 20:20:45: old_state: 2 
2011-10-19 20:20:45: checking for rotation
2011-10-19 20:20:45: /usr/bin/checkmagick32
2011-10-19 20:21:39: cur_state: 0 
2011-10-19 20:21:39: old_state: 2 
2011-10-19 20:21:40: calling rotation a: 
2011-10-19 20:21:40: normal
2011-10-19 20:21:40: calling cellwriter --hide-window
2011-10-19 20:21:40: Change to normal state
2011-10-19 20:21:40: checking for rotation
2011-10-19 20:21:40: /usr/bin/checkmagick32

....i then restarted the PC and made sure the desktop was fully loaded, then opened the file manager and deleted the first text log file (above), then swiveled the screen again, the screen did not change from landscape to portrait and no Magick text log file was generated, i flipped the screen two or three times giving plenty of time for the screen to rotate between turns, then around the fourth try the screen rotated and the text log was generated, below is the text log contents... hope this helps

By-the-way, CellWriter was always loaded successfully to the systray on both occasions of doing the above, as i already set it up to load at startup


2011-10-19 20:29:55: cur_state: 2 
2011-10-19 20:29:55: old_state: 0 
2011-10-19 20:29:56: calling rotation b: 
2011-10-19 20:29:56: right
2011-10-19 20:29:57: calling cellwriter --show-window
2011-10-19 20:29:57: Change to Tablet mode
2011-10-19 20:29:57: checking for rotation
2011-10-19 20:29:57: /usr/bin/checkmagick32
2011-10-19 20:29:58: cur_state: 2 
2011-10-19 20:29:58: old_state: 2 
2011-10-19 20:29:58: checking for rotation
2011-10-19 20:29:58: /usr/bin/checkmagick32
2011-10-19 20:30:17: cur_state: 0 
2011-10-19 20:30:17: old_state: 2 
2011-10-19 20:30:17: calling rotation a: 
2011-10-19 20:30:17: normal
2011-10-19 20:30:18: calling cellwriter --hide-window
2011-10-19 20:30:18: Change to normal state
2011-10-19 20:30:18: checking for rotation
2011-10-19 20:30:18: /usr/bin/checkmagick32

...once it's gets working, the time between flipping the monitor and the screen rotation actually happening can be a delay of anywhere between 20 to 60 seconds or more, the log file below is moving the screen from a normal laptop position to the tablet position, in this position Cellwriter also appeared on the desktop as it changed....

2011-10-19 21:09:58: cur_state: 2 
2011-10-19 21:09:58: old_state: 0 
2011-10-19 21:09:58: calling rotation b: 
2011-10-19 21:09:58: right
2011-10-19 21:09:59: calling cellwriter --show-window
2011-10-19 21:09:59: Change to Tablet mode
2011-10-19 21:09:59: checking for rotation
2011-10-19 21:09:59: /usr/bin/checkmagick32

..and the log file below is generated from moving the monitor from a tablet, back to a laptop position, again anywhere between 20 to 60 seconds for the desktop to go back to landscape, Cellwriter closes once the the desktop has changed...

  2011-10-19 21:13:44: cur_state: 0 
2011-10-19 21:13:44: old_state: 2 
2011-10-19 21:13:44: calling rotation a: 
2011-10-19 21:13:44: normal
2011-10-19 21:13:45: calling cellwriter --hide-window
2011-10-19 21:13:45: Change to normal state
2011-10-19 21:13:45: checking for rotation
2011-10-19 21:13:45: /usr/bin/checkmagick32

..hope this helps, and thanks again

regards

---

### Post by Favux on 2011-10-19
That's unusual.  I don't think I've seen Magick work intermittently before and with a long delay like that.

It's just as important to show the debug log when it didn't rotate as when it does so we can contrast the two.

Right now I suspect there is a hang being caused by CellWriter for some reason.  In Natty (11.04) the CellWriter icon wouldn't show up in the systray unless you whitelisted it first.  So Zorin is different there.  Also you shouldn't need to add CellWriter to the autostart, it should add itself automatically.  So I'm wondering if you have two instances of CellWriter running?  In your autostart is there just the entry you made for it or is there a second entry?  Either way try disabling your autostart entry for it and rebooting.  Then post the debug log if Magick doesn't work and another one with it working if it does.

---

### Post by liviococcia on 2011-10-19
> **Favux said:**
> That's unusual.  I don't think I've seen Magick work intermittently before and with a long delay like that.

It's just as important to show the debug log when it didn't rotate as when it does so we can contrast the two.

Right now I suspect there is a hang being caused by CellWriter for some reason.  In Natty (11.04) the CellWriter icon wouldn't show up in the systray unless you whitelisted it first.  So Zorin is different there.  Also you shouldn't need to add CellWriter to the autostart, it should add itself automatically.  So I'm wondering if you have two instances of CellWriter running?  In your autostart is there just the entry you made for it or is there a second entry?  Either way try disabling your autostart entry for it and rebooting.  Then post the debug log if Magick doesn't work and another one with it working if it does.
Favux, there was only one instance of CellWriter in the autostart (i looked in 'control center' under 'startup applications' for this)

After starting the laptop up from a completely off state, the desktop fully loaded with Magick Rotation in the systray, and the 'Touch Screen - on' bubble appeared and then disapearing, i then gave it about another 20 seconds to try the rotation, once the monitor was rotated the desktop did not change, i left it in this tablet position for 5 minuets, still no change and then moved the monitor back into laptop position, looked at the text log which had been generated, see below....

2011-10-19 21:44:50: cur_state: 2 
2011-10-19 21:44:50: old_state: 0 
2011-10-19 21:44:50: calling rotation b: 
2011-10-19 21:44:50: right
2011-10-19 21:44:51: calling cellwriter --show-window
2011-10-19 21:44:51: Change to Tablet mode
2011-10-19 21:44:51: checking for rotation
2011-10-19 21:44:51: /usr/bin/checkmagick32
2011-10-19 21:46:25: cur_state: 0 
2011-10-19 21:46:25: old_state: 2 
2011-10-19 21:46:25: calling rotation a: 
2011-10-19 21:46:25: normal
2011-10-19 21:46:26: calling cellwriter --hide-window
2011-10-19 21:46:26: Change to normal state
2011-10-19 21:46:26: checking for rotation
2011-10-19 21:46:26: /usr/bin/checkmagick32
2011-10-19 21:47:20: cur_state: 1 
2011-10-19 21:47:20: old_state: 0 
2011-10-19 21:47:44: checking for rotation
2011-10-19 21:47:44: /usr/bin/checkmagick32
2011-10-19 22:20:43: checking for rotation
2011-10-19 22:20:43: /usr/bin/checkmagick32
2011-10-19 22:23:51: checking for rotation
2011-10-19 22:23:52: /usr/bin/checkmagick32
 
regards

---

### Post by liviococcia on 2011-10-19
The laptop has 2gig of ram, and everything runs well on it, but it's as if there's not enough memory for Magick, or that the magick apps not using the memory quickly enough.

Also, from when the 'Touch status -on' bubble appears and disappears, and you then move the screen the first time, that first movement doesn't do anything and you need to move it back and do it again for the rotation to occur although still very delayed, after this first rotation all subsequent rotations have a long delay before the actual desktop rotates  

regards

---

### Post by Favux on 2011-10-19
Alright, something may be wrong with checkmagick32 because we are seeing:
```
2011-10-19 21:47:44: checking for rotation
2011-10-19 21:47:44: /usr/bin/checkmagick32
2011-10-19 22:20:43: checking for rotation
2011-10-19 22:20:43: /usr/bin/checkmagick32
2011-10-19 22:23:51: checking for rotation
2011-10-19 22:23:52: /usr/bin/checkmagick32
```
without it reporting the state.

Run this command:
```
cat /sys/devices/platform/hp-wmi/tablet
```
when you are in laptop mode and again when in tablet and post the outputs.

Let's try compiling checkmagick.  In the magick-rotation folder that remained after the Installer finished should be a file called INSTALLER.txt.  Open that up and follow the steps to compile checkmagick in "COMPILE CHECKMAGICK" and post the output including the result of *uname -m*.  But don't do the move (mv) command to install it in /usr/bin yet.

---

### Post by liviococcia on 2011-10-20
> **Favux said:**
> Alright, something may be wrong with checkmagick32 because we are seeing:
```
2011-10-19 21:47:44: checking for rotation
2011-10-19 21:47:44: /usr/bin/checkmagick32
2011-10-19 22:20:43: checking for rotation
2011-10-19 22:20:43: /usr/bin/checkmagick32
2011-10-19 22:23:51: checking for rotation
2011-10-19 22:23:52: /usr/bin/checkmagick32
```
without it reporting the state.

Run this command:
```
cat /sys/devices/platform/hp-wmi/tablet
```
when you are in laptop mode and again when in tablet and post the outputs.

Let's try compiling checkmagick.  In the magick-rotation folder that remained after the Installer finished should be a file called INSTALLER.txt.  Open that up and follow the steps to compile checkmagick in "COMPILE CHECKMAGICK" and post the output including the result of *uname -m*.  But don't do the move (mv) command to install it in /usr/bin yet.
Hello Favux, this is the order of events, please see below...

1: Starting from a cold start, turned on computer, waited for desktop to load 'Touch status - on' appeared then disappeared.

2:..then i opened terminal waited another 10 seconds, entered the command at 8:59 am..
 
cat /sys/devices/platform/hp-wmi/tablet 

the result in the terminal was 0, and i flipped the screen to tablet position, and waited until 9:04am....result: no rotation

3:..9:04am entered the terminal command again while still in tablet mode but desktop still at landscape, the result in the terminal was 0, and went ahead and moved the screen back to laptop position.....result: no reaction

4:...9:06am entered the terminal command again the terminal result was 0, rotated to tablet position, 10 seconds later the desktop rotated to portrait view

5... 9.09am entered the terminal command again the terminal result was 1, rotated to laptop position, 20 seconds later the desktop rotated to landscape view

6... 9.11am entered the terminal command again the terminal result was 0, rotated to tablet position, 40 seconds later the desktop rotated to portrait view

7... 9.13am entered the terminal command again the terminal result was 1, rotated to laptop position, 5 seconds later the desktop rotated to landscape view.


...below is the text log when i did the trial above...

2011-10-20 08:57:37: checking for rotation
2011-10-20 08:57:37: /usr/bin/checkmagick32
2011-10-20 09:07:24: cur_state: 2 
2011-10-20 09:07:24: old_state: None 
2011-10-20 09:07:24: calling rotation b: 
2011-10-20 09:07:24: right
2011-10-20 09:07:25: calling cellwriter --show-window
2011-10-20 09:07:25: Change to Tablet mode
2011-10-20 09:07:25: checking for rotation
2011-10-20 09:07:25: /usr/bin/checkmagick32
2011-10-20 09:10:38: cur_state: 0 
2011-10-20 09:10:38: old_state: 2 
2011-10-20 09:10:38: calling rotation a: 
2011-10-20 09:10:38: normal
2011-10-20 09:10:39: calling cellwriter --hide-window
2011-10-20 09:10:39: Change to normal state
2011-10-20 09:10:39: checking for rotation
2011-10-20 09:10:39: /usr/bin/checkmagick32
2011-10-20 09:12:48: cur_state: 2 
2011-10-20 09:12:48: old_state: 0 
2011-10-20 09:12:49: calling rotation b: 
2011-10-20 09:12:49: right
2011-10-20 09:12:49: calling cellwriter --show-window
2011-10-20 09:12:49: Change to Tablet mode
2011-10-20 09:12:49: checking for rotation
2011-10-20 09:12:49: /usr/bin/checkmagick32
2011-10-20 09:14:08: cur_state: 0 
2011-10-20 09:14:08: old_state: 2 
2011-10-20 09:14:08: calling rotation a: 
2011-10-20 09:14:08: normal
2011-10-20 09:14:08: calling cellwriter --hide-window
2011-10-20 09:14:09: Change to normal state
2011-10-20 09:14:09: checking for rotation
2011-10-20 09:14:09: /usr/bin/checkmagick32


Favux when i ran the command uname -m the result in the terminal window was..

i686

and when i did the 'compile checkmagick' it produced a file called 'checkmagic32' into the extracted magick-rotation folder, i did not do the steps in the instructions to 'move' or 'install' it, but i did check to see that there was a file call 'checkmagic32' in the usr/bin location, and there is.

Thanks for all this help

regards

---

### Post by Favux on 2011-10-20
Nice work!  Now we're getting somewhere.

The good news is the problem does not appear to be with Magick Rotation.  You've shown the checkmagick compile works fine without errors and that it is in the right location.

The terminal command:
```
cat /sys/devices/platform/hp-wmi/tablet
```
is an alternate way to check on your tablet's hinge switch reported value through hp-wmi.  As you can see in laptop it is suppose to report 0 and when rotated to tablet it should report 1.  The lag in it reporting 1 or the absence of a reported 1 altogether means the problem is elsewhere and not with Magick Rotation.  While Magick depends on hp-wmi too it uses it in a different way and the tablet file in platform/hp-wmi should report 0 or 1 "instantly".

At this point it well could be hardware related or it could have to do with the hp-wmi chain.

I don't know where the actual switch that we're getting a signal from is located.  It may be different for different laptops.  Maybe actually in the swivel hinge.  Maybe somewhere else that is engaged when the lid is rotated and folded down.  So if it is the hardware what it looks like is a bad connection/contact.  As if it is dirty/oxidized or there is a weakened spring say, so that the switch is sending a signal intermittently.

If it is the hp-wmi chain we can check on that a little.  I think it is probably something like:

switch > BIOS > wmi > hp-wmi

Enter the following command in a terminal:
```
lsmod
```
In the *list modules* output you should see wmi (it will probably refer to hp-wmi) and hp_wmi.  Sometimes the hp-wmi doesn't auto-load, but I don't think that is your problem.  Otherwise you wouldn't ever get the switch signal.  You could also look over the BIOS settings and see if there is anything to do with the switch.  There might not be.  Does your BIOS show conflicts?  Maybe there is a conflict with the switch and something else?

I might ask Jayhawk to look this over if he has time.  Honestly the lag time part doesn't make much sense to me.

---

### Post by liviococcia on 2011-10-20
> **Favux said:**
> Nice work!  Now we're getting somewhere.

The good news is the problem does not appear to be with Magick Rotation.  You've shown the checkmagick compile works fine without errors and that it is in the right location.

The terminal command:
```
cat /sys/devices/platform/hp-wmi/tablet
```
is an alternate way to check on your tablet's hinge switch reported value through hp-wmi.  As you can see in laptop it is suppose to report 0 and when rotated to tablet it should report 1.  The lag in it reporting 1 or the absence of a reported 1 altogether means the problem is elsewhere and not with Magick Rotation.  While Magick depends on hp-wmi too it uses it in a different way and the tablet file in platform/hp-wmi should report 0 or 1 "instantly".

At this point it well could be hardware related or it could have to do with the hp-wmi chain.

I don't know where the actual switch that we're getting a signal from is located.  It may be different for different laptops.  Maybe actually in the swivel hinge.  Maybe somewhere else that is engaged when the lid is rotated and folded down.  So if it is the hardware what it looks like is a bad connection/contact.  As if it is dirty/oxidized or there is a weakened spring say, so that the switch is sending a signal intermittently.

If it is the hp-wmi chain we can check on that a little.  I think it is probably something like:

switch > BIOS > wmi > hp-wmi

Enter the following command in a terminal:
```
lsmod
```
In the *list modules* output you should see wmi (it will probably refer to hp-wmi) and hp_wmi.  Sometimes the hp-wmi doesn't auto-load, but I don't think that is your problem.  Otherwise you wouldn't ever get the switch signal.  You could also look over the BIOS settings and see if there is anything to do with the switch.  There might not be.  Does your BIOS show conflicts?  Maybe there is a conflict with the switch and something else?

I might ask Jayhawk to look this over if he has time.  Honestly the lag time part doesn't make much sense to me.
Hello Favux, i did the lsmod command and hp-wmi was there, but i found this evening when i tried Magick rotation it would not rotate the screen at all no matter how man times flipped the screen, i thought something might have happened to the installation with everything i've been trying out, the text log showed just this below...

2011-10-20 20:01:37: checking for rotation
2011-10-20 20:01:37: /usr/bin/checkmagick32

So i deleted everything regarding Magick Rotate, including the startup item under control center > startup applications, and downloaded the .tar again, i thought i'd restart the laptop before i installed it again, but when i restarted the laptop Magic Rotation was in the systray still.

How do i remove/uninstall all the elements of Magick Rotation completely, so i can re-install it again?

I would like to leave the updated Wacom driver alone though

Any help would be great thanks

regards

---

### Post by Favux on 2011-10-20
Reinstalling Magick again should overwrite the old files except the .xml and that shouldn't matter.  Just quit the Magick Rotation icon in the systray or disable it in Start Up Applications.

---

### Post by Favux on 2011-10-20
Reinstalling Magick again should overwrite the old files except the .xml and that shouldn't matter.  Just quit the Magick Rotation icon in the systray or disable it in Start Up Applications.

All the files and their locations should be in the install_log and in the README.  I haven't written an uninstaller yet.

---

### Post by liviococcia on 2011-10-20
> **Favux said:**
> Reinstalling Magick again should overwrite the old files except the .xml and that shouldn't matter.  Just quit the Magick Rotation icon in the systray or disable it in Start Up Applications.
Favux, i deleted everything related to Magic Rotation, including the checkmagic32 file, then restarted the laptop and it did not appear in the systray.

I re-downloaded Magic Rotation and re-installed, but still it's not rotating at all, so i looked at the debugging text, see below..

 2011-10-20 19:54:29: checking for rotation
2011-10-20 19:54:29: /usr/bin/checkmagick32
2011-10-20 19:56:07: killall checkmagick32
2011-10-20 19:56:07: cur_state: 143 
2011-10-20 19:56:07: old_state: None 
2011-10-20 20:19:59: checking for rotation
2011-10-20 20:19:59: /usr/bin/checkmagick32
2011-10-20 20:25:04: cur_state: 1 
2011-10-20 20:26:57: checking for rotation
2011-10-20 20:26:57: /usr/bin/checkmagick32
2011-10-20 20:30:13: killall checkmagick32
2011-10-20 20:30:13: cur_state: 143 
2011-10-20 20:30:13: old_state: None 
2011-10-20 20:41:57: checking for rotation
2011-10-20 20:41:59: /usr/bin/checkmagick32

..as you can see there's still a problem, it's showing killall checkmagic32, any ideas whats happened?

regards
Livio

---

### Post by Favux on 2011-10-20
Your switch failed completely?

I'd have to check the code but I think the killall is from the code terminating checkmagick because there isn't anything to read.  Do you get the change from 0 to 1 with:
```
cat /sys/devices/platform/hp-wmi/tablet
```
at all anymore?

---

### Post by liviococcia on 2011-10-20
Favux, i think your right, the command is showing 1 all the time now, it must be broke, this lsmod below

Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
snd_hda_codec_analog    75442  1 
arc4                   12473  2 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_analog,snd_hda_intel
rfcomm                 38125  8 
iwlagn                284745  0 
tpm_infineon           17324  0 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
sco                    17827  2 
bnep                   17785  2 
iwlcore               148964  1 iwlagn
l2cap                  48656  16 rfcomm,bnep
snd_seq_midi           13132  0 
mac80211              257001  2 iwlagn,iwlcore
snd_rawmidi            25269  1 snd_seq_midi
[COLOR="Red"]hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi[/COLOR]
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
cfg80211              156212  3 iwlagn,iwlcore,mac80211
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_tis                13993  0 
hp_accel               21632  0 
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
lis3lv02d              19285  1 hp_accel
tpm                    21251  2 tpm_infineon,tpm_tis
tpm_bios               13460  1 tpm
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
input_polldev          13735  1 lis3lv02d
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41704  0 
hid                    77084  1 usbhid
i915                  451033  4 
sdhci_pci              13623  0 
firewire_ohci          31504  0 
drm_kms_helper         40745  1 i915
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
drm                   184164  5 i915,drm_kms_helper
crc_itu_t              12627  1 firewire_core
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
e1000e                138627  0 
ramzswap               13202  0 
xvmalloc               13453  1 ramzswap


regards

---

### Post by Favux on 2011-10-20
That's too bad.  Check HP support and see if there is a PDF for your tablet PC.  Fixing the switch may not be all that hard if we knew where it was.

---

### Post by liviococcia on 2011-10-20
> **Favux said:**
> That's too bad.  Check HP support and see if there is a PDF for your tablet PC.  Fixing the switch may not be all that hard if we knew where it was.
Thanks Favux, I've gone back to using the xrotate file, I think this ways working well so I'm happy, I created two shortcuts one for the Laptop view, one for the Tablet view.

I've also setup Cellwriter to run at startup, so it's now in the systray, I don't think I'll bother to get the laptop hinge repaired, as I bought it as a used item although it was working when it was running Vista, must have been all the flipping of the screen that finished it off.

I'm writing this post using Cellwriter, so please excuse the gramma.

Now all I need to do is sort out Cellwriter to appear at the Zorin login screens.

Thanks again for all the help you've given me.

Kind regards
Livio

---

### Post by liviococcia on 2011-10-20
Just to let anyone know, to get Cellwriter to appear at the login screens just type...

sudo gedit /etc/gdm/Init/Default

..then insert before the last entry line of 'exit0' the command below..

cellwriter &--show-window

So it looks like the example below, notice, keep the line spacing also...

.........fi
......fi
...fi
fi

cellwriter &--show-window

exit 0


On my laptop Cellwriter now appears as an icon to the bottom panel on the login screen, also if you first set it up this way, it will ask you to 'Train' it again, when the desktop opens Cellwriter will remain open and you may have two instances of it, so, because i'm not running Magick Rotation i removed the entry in 'Startup applications' i had created, and will re-'Train' this GDM version

Hope this is useful to a member, but remember it's at your own risk, and if you do mess it up, just start-up your computer using the Live cd of your distribution and correct any mistakes.

regards

---

