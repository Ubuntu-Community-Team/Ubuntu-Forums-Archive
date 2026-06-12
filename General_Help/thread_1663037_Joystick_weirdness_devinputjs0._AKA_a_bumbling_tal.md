---
title: "Joystick weirdness /dev/input/js0. AKA a bumbling tale of an amateur Ubuntu user"
date: 2011-01-09
forum: General Help
---

### Post by oopsie on 2011-01-09
I'm not really having any huge problems, but thought I'd post anyway in the hope that somebody can tell me what on earth is going on, or if anybody else has had similar problems maybe what I managed to randomly find out could help. I'm a complete Ubuntu amateur so it wouldn't surprise me if somebody comes along and tells my I've been doing something stupid, wrong, dangerous or just plain weird.

Many months ago, I installed a pixel art programme from the repositories, and tried to use it. But the cursor kept shooting to the top left corner of the screen. Weird, but I just moved on to other things. I probably would have forgotten about it too if it wasn't for a few weeks ago, I installed a game called Paintown, and my characters would all move to the top left corner of the screen.

A lightbulb went off in my head! Maybe my computer thinks there is a joystick attached even though there isn't. I did some Googling and learned about **/dev/input/js0** which was on my computer. I did a probably reckless thing and just deleted it.

Ta-dah, my character no longer kept moving up and to the left, and instead just responded to my keyboard controls. Success!

I've rebooted my computer many times since then, and js0 always comes back. But it's no big problem to delete it again whenever I want to use that game or other software.

Anyway, since all this got me curious about joysticks, I borrowed (stole from a family member) an xbox 360 controller, downloaded a few joypad setup programmes and a fricken awesome programme called **qjoypad** which lets me map the joypad to my keyboard. And I've been using it successfully to play various new games or emulated old games from the 80s and 90s.

By the way, setting up the dead zone for joypads in Ubuntu is a huge pain in the rear. I had to use **jscal** to set up the joystick, then manually edit the text output to increase the size of the dead zone, coming up with this monstrosity 

```
jscal -s 8,1,0,-2500,-1200,17348,15570,1,0,-25,1000,16742,16685,1,0,0,0,-2147483648,2105312,1,0,-2800,-2800,17915,15094,1,0,-300,800,16269,16560,1,0,0,0,-2147483648,2105312,1,0,0,0,536854528,536854528,1,0,0,0,536854528,536854528 /dev/input/js0

```

I have to do that every time I want to use my joypad after a reboot. I haven't figured out how to make it remember between reboots yet. But it's only a minor annoyance.

Oh it says js0, because when I plug in a joystick, it gets assigned as js1. So I just delete js0 and rename js1 as js0. It works, but it's probably not what I'm supposed to do.

Anyhoo, while learning how to do all that, I learned about **jstest**. And decided to use it on the mysterious js0. And the first line of output says

```
Joystick (A4Tech USB Full Speed) has 37 axes
```

Which I've never owned, heard of or used before. 37 axes?! wow

A bit more noseying about, I decided to just look at what js0 was doing in hex by doing **xxd /dev/input/js0**
```

0000000: e01c bc00 0000 8100 e01c bc00 0000 8101  ................
0000010: e01c bc00 0000 8102 e01c bc00 0000 8103  ................
0000020: e01c bc00 0000 8104 e01c bc00 0000 8105  ................
0000030: e01c bc00 0000 8106 e01c bc00 0000 8107  ................
0000040: e01c bc00 0000 8108 e01c bc00 0000 8109  ................
0000050: e01c bc00 0000 810a e01c bc00 0000 810b  ................
0000060: e01c bc00 0000 810c e01c bc00 0000 810d  ................
0000070: e01c bc00 0000 810e e01c bc00 0000 810f  ................
etc... blah blah blah...
0000260: e01c bc00 0180 8223 e01c bc00 0180 8224  .......#.......$
It always stops at line 260.

```

I've watched it a while, and apparently it's mostly just counting, though a few bits seem to change randomly too. I've tried hitting keys, wiggling my mouse, fiddling with the joystick and anything else I could think of. Nothing seems to influence js0 in any way I can discover.

So yeah that's about as far as I've got so far.

Anybody have a clue why it's doing this, what's going on, or can anybody point at me and and laugh saying "oh my god you noob, you should do XXXXX not XXXXX, it's obvious"

---

### Post by acarlstein on 2011-03-18
I have being also trying to get the joystick working properly in linux (Ubuntu) unsuccessfully.

I have a person that need special equipment to play video games.
I would like to modify a joystick so he can use it.

However, anything related with joysticks in the linux/Ubuntu community seems to be impossible to deal with.

1. Why do the mouse and joystick have to be considerate the same for xorg? 

2. Why is so hard to reconfigure a joystick?

3. Why the Ubuntu community have Allergies with anything related with joysticks?

---

### Post by miklewal on 2011-11-25
Hi, I have been having the same problem with my HP dv3 laptop. When I use jstest I get the following information:
jstest /dev/input/js0
Driver version is 2.1.0.
Joystick (ST LIS3LV02DL Accelerometer) has 3 axes (X, Y, Z)
and 0 buttons ().
Testing ... (interrupt to exit)
Axes:  0:     0  1:-32767  2:-32767

The Axes numbers change whenever I move the laptop, so it seems that there is an inbuilt accelerometer which is being installed as a a joystick device as /dev/input/js0. So no strange bug as such, but it does mean that when I write a (wxpython) program which needs to see if a joystick is present, it does mean that a joystick is detected, even though am actual joystick is not present! Incidently, I have found similar behaviour with wxpython under windows on different machines. Sometimes a keyboard appears as /dev/input/js0.

If you plug an actual joystick in it is then installed as /dev/input/js0. Not sure how to work round this as it seems there are several devices which install as a (fake) joystick as /dev/input/js0

---

### Post by ulao on 2012-01-29
> 1. Why do the mouse and joystick have to be considerate the same for xorg?
because that is the defult for xinput. You can simply remove it. 

xinput list
You will see your controller under "Virtual core pointer"

to disable it from the list of virtual pointer do this
xinput --set-prop "your device as it spears in the list" "Device Enabled" 0



> 2. Why is so hard to reconfigure a joystick?

Its not, its actually quite simple. but lke all things Linux if it does not you are sol. Like yourself it does not work for me with some joysticks. Others pop up and are ready to go. I wish I knew where the usb logs were. From the net they are at /var/logs/messages but that file is never written to when I plug in a joystick. 

> 3. Why the Ubuntu community have Allergies with anything related with joysticks? Again, it works for them so they dont want to get infected by helping you.

---

### Post by Grumbel on 2012-02-08
> 2. Why is so hard to reconfigure a joystick?
If you are into writing some code, it is actually quite easy to create virtual input devices via uinput on Linux that behave however you want them to be.

Aside from that, the configurability of joystick in Linux is limited, the joydev interface allows button and axes swapping, as well as deadzone changes and calibration (jstest and jscal). GUI tool is available for the job at:

[http://pingus.seul.org/~grumbel/jstest-gtk/](http://pingus.seul.org/~grumbel/jstest-gtk/)

Problem is, most games do not use the joydev interface, but evdev via SDL, so that's of limited use.

For full joystick reconfiguration there is also:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

Unlike the name suggest, it can actually be used to fully reconfigure any Linux input device, not just Xbox360 gamepads. It's still not quite finished and little rough around the edges, but should be able to handle most reconfiguration needs.

As to the OP: As somebody else already said, that is likely the accelerometer of yoru laptop or another kind of sensor stuff. One way to get rid of it would be to remove and blacklist the joydev module, but that would disable all joystick use. Another way might be to change the rules for js0 so that the device gets another name or isn't created at all.

---

### Post by Yfrwlf on 2012-10-27
Thanks for this, helped me solve my issue.  I have a X7 model XL-760H mouse.  Something in it, probably one of the buttons or something, was showing up as a joystick, and the joystick is at a 0,0 axis by default, so it would mess up many games, constantly move the menu selection or game character, and completely prevent functionality.

For the longest time I just kept deleting /dev/input/js0, but that was stupid.

Finally, I ran:

> xinput list

My problematic device was

> A4TECH USB Device

There were two of them, so

> xinput --set-prop "A4TECH USB Device" "Device Enabled" 0

did not work since there were two of those devices.  Instead I randomly chose one of them and specified the number in place of the name:

> xinput --set-prop 8 "Device Enabled" 0

I then tested a game and it worked!  No more joystick!  Running "xinput list --long" showed that device as disabled.

I assume I should contact the Xorg project for telling them that my mouse model does not contain a joystick, so that this problem won't effect other Linux users?

---

