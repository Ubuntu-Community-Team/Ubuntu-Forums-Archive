---
title: "How to assign specific joystick device path to specific joystick or controller?"
date: 2010-10-13
forum: General Help
---

### Post by indstr on 2010-10-13
Currently I have 5 HID's I would like to use on the system at any given time. However, I have the problem of them using different device paths depending on what order I plug them in... Which wreaks havoc on qjoypad and also my music software which looks for a specific device number, which may or may not be the same as it was last time.

For example, I have 2 rock band drum controllers which I use to send MIDI signals. I need them always assigned to the same device path, so that I don't have to change the settings in my music software every time I run it, to make sure it's looking at the right controller

Or if I am going to play games with a gamepad, but I also have the drums hooked up, the gamepad may be assigned to /dev/input/js2, so I create my qjoypad profile....  Let's say the next day I reboot with the drums not plugged in, the gamepad is now /dev/input/js0, and the qjoypad profile won't work because it is looking for that gamepad at /dev/input/js2... So I would either have to create a new profile, or hook the drums back up in the same order ... Or something

It's just a mess...

Is there any way to tell Ubuntu to say "/dev/input/js0 is always Playstation gamepad", "/dev/input/js1 is always drum pad 1",  etc... 

???

Or some way to do away with /dev/input scheme altogether and somehow link directly to the name of the device? I don't know much about how this works but it seems like it should be possible somehow. I have heard about symlinking but I am not sure if it would be applicable in this situation

Any input is appreciated. 

Thanks

---

### Post by indstr on 2010-10-15
After messing about for several hours, I seem to have figured it out...

Partly due to these posts:

[http://ubuntuforums.org/showthread.php?t=472725](http://ubuntuforums.org/showthread.php?t=472725)
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)
[http://www.vendetta-online.com/x/msgboard/6/23025](http://www.vendetta-online.com/x/msgboard/6/23025)

udev is the utility which will do this. I tried to find a GUI version but failed on being able to install gudev, so I just decided to do it the hard way... 

Basically, the files located at /etc/udev/rules.d/ contain information about which device should be mapped to which location. So I created a new file for joystick settings by typing:

```
sudo gedit /etc/udev/rules.d/73-persistent-joystick.rules

```

(The number at the beginning doesn't matter from what I understand, it is the order the files are loaded. I would suggest a higher number)
Inside this file are the udev rules ... The easiest way I found to write udev rules is to just plug in the device you want to find the info on, and type:

```
udevadm info -q all -n /dev/input/js0
```
(replacing js0 with whatever device it gets mapped to initially. Of course you will be changing this later)

It pulls up a lot of info, but there are only 2 lines you need:

```
ID_VENDOR=
```
and 
```
ID_MODEL=
```

For example, for my sidewinder gamepad, the lines are:

```
ID_VENDOR=Microsoft
ID_MODEL=Microsoft_SideWinder_Plug___Play_Game_Pad

```

Now to create your udev rules inside the /etc/udev/rules.d/73-persistent-joystick.rules, I pasted the following lines into my file:

```
KERNEL=="js?", ENV{ID_VENDOR}=="©Microsoft_Corporation", ENV{ID_MODEL}=="Controller", NAME="input/js0"
KERNEL=="js?", ENV{ID_VENDOR}=="GIC_Technology_Inc.", ENV{ID_MODEL}=="GIC_USB_Joystick", NAME="input/js4"
KERNEL=="js?", ENV{ID_VENDOR}=="Microsoft", ENV{ID_MODEL}=="Microsoft_SideWinder_Plug___Play_Game_Pad", NAME="input/js5"
```

Basically meaning, Xbox 360 controller at js0, PSX adapter at js4, and sidewinder at js5.... I also have the 2 drum controllers, but it took me a while of fiddling with it to figure out why it didn't work -- The problem was that they are identical controllers, so of course they have the same ID Vendor and model...  udev didn't like that. Originally I tried assigning them to input/js2 and input/js3 respectively.. But what I found out was that it simply ignored js2 altogether, and when I plugged the first one in, it went straight to js3. When I plugged the second one in, it kicked the first one off js3 and took up the slot... First controller was no longer responding at all. 

Tried several other things... Long story short, you can't use udev rules on devices that have identical strings... So I had to leave 3 js ports open (js1,  js2, and js3), for the controllers to be automatically mapped to when they are plugged in. Why 3? Again, this took me a while to figure out, but at first I only had 2 empty slots (js1 and js2)... but for some reason they weren't mapping to js1, and only going straight to js2 and js3... At this point I had the psx controller already on js3, so the second drum pad was kicking the psx controller offline. I tried putting the psx on js4 and fortunately when I rebooted, everything was in its correct place! Xbox 360 on js0, js1 empty, js2 = drum 1, js3 = drum 2, js4 = psx adapter, and js5 = empty at first but succesfully mapped to sidewinder pad when I plugged it in.

So, in short, it was a pain in the *** but I got it working. And learned something in the process. Rock on!

---

