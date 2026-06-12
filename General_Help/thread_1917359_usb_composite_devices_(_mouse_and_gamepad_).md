---
title: "usb composite devices ( mouse and gamepad )"
date: 2012-01-29
forum: General Help
---

### Post by ulao on 2012-01-29
So I have a composite device that has a mouse and a joystick in one.  The way it works is:

>gamepad mode, like any normal gamepad
>mouse mode, with certain settings the mouse cursor will move according to the joystick on the Horizontal axis only. This can be controller on or off.


On windows 7 it shows up as a mouse but is also listed under game controllers. It works as it should. Its a gamepad by default and the mose mode can be turned on.

On XP it shows up as a gamepad. It works as it should. Its a gamepad by default and the mose mode can be turned on.

On Linux joystick(the application) does not see any devices but the joystick controllers the mouse. I know ximput does that intentionally. So that leads me to believe its install as a joystick and working as such. If I removed the device from the virtual pointer in xinput it stops controlling the mouse. 

So if its installed, how can I tell where its installed? I dont really understand this js0 stuff at all. jstest tells me its not there, so where is it? If its capable of controlling the mouse in x, then there is a joystick out there somewhere.

---

### Post by ulao on 2012-01-31
well today I learned about devices 

/proc/bus/input/devices

and i see my device right there, so why wont joystick(app) find it?

I: Bus=0003 Vendor=16d0 Product=04fb Version=0110
N: Name="Sub-Zero Workshop BLISS-BOX"
P: Phys=usb-0000:00:11.2-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:11.2/usb4/4-2/4-2:1.0/input/input17
U: Uniq=
H: Handlers=mouse0 event5
B: PROP=0
B: EV=1f
B: KEY=ff ffff8000 70001 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=ff
B: MSC=10

what does "H: Handlers=mouse0 event5" mean?


I also see in by-id I have

usb-Sub-Zero_Workshop_BLISS-BOX-event-mouse
usb-Sub-Zero_Workshop_BLISS-BOX-mouse

not sure what that means also.

---

### Post by Grumbel on 2012-02-07
> **ulao said:**
> what does "H: Handlers=mouse0 event5" mean?
This means that your device is available as:

```
/dev/input/mouse0
/dev/input/event5
```

You can access it via (don't think there is a tool to acces mouse0 in a userfriendly way):

```
evtest /dev/input/event5
```

If the device would be a joystick, Linux would show it as:

```
/dev/input/js0
```

And you would be able to test it via:

```
jstest /dev/input/js0
```

As for why it doesn't show up as joystick:

Try:

```
modprobe joydev
```

or if that doesn't help, run evtest as described above and post the output here.

---

### Post by ulao on 2012-02-08
doing a  modprobe joydev just gives me my prompt back.

I tried to use /dev/input/event5 in my joystick app and it said the given device is not a joystick.

evtest says:
```

Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x16d0 product 0x4fb version 0x110
Input device name: "Sub-Zero Workshop BLISS-BOX"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 256 (Btn0)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 274 (MiddleBtn)
    Event code 303 (BtnDead)
    Event code 304 (BtnA)
    Event code 305 (BtnB)
    Event code 306 (BtnC)
    Event code 307 (BtnX)
    Event code 308 (BtnY)
    Event code 309 (BtnZ)
    Event code 310 (BtnTL)
    Event code 311 (BtnTR)
    Event code 312 (BtnTL2)
    Event code 313 (BtnTR2)
    Event code 314 (BtnSelect)
    Event code 315 (BtnStart)
    Event code 316 (BtnMode)
    Event code 317 (BtnThumbL)
    Event code 318 (BtnThumbR)
    Event code 319 (?)
    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 322 (ToolBrush)
    Event code 323 (ToolPencil)
    Event code 324 (ToolAirbrush)
    Event code 325 (ToolFinger)
    Event code 326 (ToolMouse)
    Event code 327 (ToolLens)
  Event type 2 (Relative)
    Event code 0 (X)
    Event code 1 (Y)
  Event type 3 (Absolute)
    Event code 0 (X)
      Value    128
      Min        0
      Max      255
      Flat      15
    Event code 1 (Y)
      Value    128
      Min        0
      Max      255
      Flat      15
    Event code 2 (Z)
      Value    128
      Min        0
      Max      255
      Flat      15
    Event code 3 (Rx)
      Value      0
      Min        0
      Max      255
      Flat      15
    Event code 4 (Ry)
      Value      0
      Min        0
      Max      255
      Flat      15
    Event code 5 (Rz)
      Value    128
      Min        0
      Max      255
      Flat      15
    Event code 6 (Throttle)
      Value      0
      Min        0
      Max      255
      Flat      15
    Event code 7 (Rudder)
      Value      0
      Min        0
      Max      255
      Flat      15
  Event type 4 (Misc)
    Event code 4 (ScanCode)
Testing ... (interrupt to exit)

```

---

### Post by Grumbel on 2012-02-08
> **ulao said:**
> doing a  modprobe joydev just gives me my prompt back.
That's what it is supposed to do. But after running it you should have a:

/dev/input/js0

Is that not the case?

> I tried to use /dev/input/event5 in my joystick app and it said the given device is not a joystick.
An evdev (evtest /dev/input/event) is not a joydev (jstest /dev/input/js0), you can't use one in place of the other.

> ```

...
  Event type 3 (Absolute)
    Event code 0 (X)
      Value    128
      Min        0
      Max      255
      Flat      15
...

```

Hm, as far as I can tell, that should be enough. Any evdev that has a ABS_X (Absolute X) should get a joystick device when joydev is loaded. 

Does evtest output all the events and stuff when you move the stick around?

---

### Post by ulao on 2012-02-08
> Does evtest output all the events and stuff when you move the stick around? Yes.


After the mod probe I have

[B]root@spawnlinux:/dev/input# ls
by-id    event0  event2  event4  event6  mouse0
by-path  event1  event3  event5  mice[/B]

Also the parent dir, I'm told can sometimes have it
[B]root@spawnlinux:/dev# ls j* 
ls: cannot access j*: No such file or directory[/B]

I also tried 

**mknod /dev/input/js0 c 13 0**
then a chmod on it with 666 
then did the modprobe 

but the file remains blank. I read somewhere that a mknod  was needed, dont really understand that either. 

Encase this was not mentioned or not clear I want to add that this is a dual device. Its a mouse and a gamepad. In windows both show up under the devices.

---

### Post by Grumbel on 2012-02-08
> Encase this was not mentioned or not clear I want to add that this is a dual device. Its a mouse and a gamepad. In windows both show up under the devices.
Does that mean it reports both joystick and mouse events for the same movements (shouldn't have anything to do with the problem at hand, just wondering)? 

> **ulao said:**
> After the mod probe I have

root@spawnlinux:/dev/input# ls
by-id    event0  event2  event4  event6  mouse0
by-path  event1  event3  event5  mice

root@spawnlinux:/dev# ls j*
ls: cannot access j*: No such file or directory
Ok, guess I found the problem, the joydev module has an extra check to prevent it from grabbing touchpads and tablets as joysticks (linux/drivers/input/joydev.c) and you adapter has one of those buttons it checks for:

```
static bool joydev_match(struct input_handler *handler, struct input_dev *dev)
{
        /* Avoid touchpads and touchscreens */
        if (test_bit(EV_KEY, dev->evbit) && test_bit(BTN_TOUCH, dev->keybit))
                return false;

        /* Avoid tablets, digitisers and similar devices */
        if (test_bit(EV_KEY, dev->evbit) && test_bit(BTN_DIGI, dev->keybit))
                return false;

        return true;
}
```
Ok, this means you have essentially two options:

1) Patch your kernel and recompile that module (i.e. make above function always return true)

2) Use uinput to remap that evdev and have your joystick report different events. To do that you can use [xboxdrv](http://pingus.seul.org/~grumbel/xboxdrv/). The syntax should be something along the lines of:

```
./xboxdrv --ui-clear \
 --evdev /dev/input/event11 \
 --evdev-keymap BTN_A=a,BTN_B=b,BTN_C=x,BTN_X=y \
 --evdev-absmap ABS_X=x1,ABS_Y=y1 \
 \
 --ui-buttonmap a=BTN_A,b=BTN_B,x=BTN_X,y=BTN_Y \
 --ui-axismap x1=ABS_X,y1=ABS_Y
```

You have to change the event11 name to where your device is and replace add all the buttons and axis you want to use. Evdev support is xboxdrv 0.8.4 is a bit wonkey, it will be better in the next release, but you should be able to hack something working together with it.

Quick explanation for how it works (and why it's wonky):

xboxdrv reads from /dev/input/event and translates the events internally to look like an Xbox360 gamepad (that's --evdev-keymap/absmap). It then outputs the Xbox360-look-alike events to uinput (via --ui-buttonmap/axismap), which makes them available to the kernel and give you a /dev/input/js0.

---

### Post by ulao on 2012-02-08
> Does that mean it reports both joystick and mouse events for the same movements (shouldn't have anything to do with the problem at hand, just wondering)?  Agreed just wanted to lay it out there. Just means both devices should show up and both are controllable ( not necessarily at once ) by a joystick.


Being I have yet to try a recompile and I want this to be an option for other Linux users, I'm going to try the second method. I will report back. Your are a saint thus for, thank you.

---

### Post by ulao on 2012-02-08
yes this is working. Looks like I have a lot of mapping to do ;P 

Wow man, thx so much!


-- oh one more thing. How do you get it to stick? Once I run this it works still I cntl break, then its broke. If I run it again I get Device or resource busy

Also what the best way to get a list of all button I need to map over. I guess I needs a list on each device. 

guessing 
"BTN_A=a  "
BTN_A being my device?
a being the virtual 360 ?

I see that up-above its called "BtnA"

---

### Post by Grumbel on 2012-02-08
> **ulao said:**
> -- oh one more thing. How do you get it to stick? Once I run this it works still I cntl break, then its broke. If I run it again I get Device or resource busy
If you Ctrl-c the xboxdrv process, you should be able to simply restart it. If for some reason it ends up floating around in the background, use:

sudo killall -9 xboxdrv

To kill it. xboxdrv has to be running the whole time to make this work, so to make this permanent you need to hack together a [start script](https://help.ubuntu.com/community/UbuntuBootupHowto) for it or simply start it manually whenever you want to use the controller.

> guessing 
"BTN_A=a  "
BTN_A being my device?
a being the virtual 360 ?
Yep, there is an --evdev-debug option that should print all the names and allow you to see which button is named what. evtest uses slightly different names, which can makes things a bit confusing.

---

### Post by ulao on 2012-02-08
Perfect, so is this the problem?

    Event code 320 (ToolPen)
    Event code 321 (ToolRubber)
    Event code 322 (ToolBrush)
    Event code 323 (ToolPencil)
    Event code 324 (ToolAirbrush)
    Event code 325 (ToolFinger)
    Event code 326 (ToolMouse)
    Event code 327 (ToolLens)

I dont put any of that im my mouse descriptor that I know of.

Not sure you know much about the usb firmware side of things but this is my mouse part of the descriptor. As you can tell by the comments there is nothing more then a pointer and a wheel and buttons. So what does the kernel have beef with?

```

	0x05, 0x01,                    // USAGE_PAGE (Generic Desktop)
    0x09, 0x02,                    // USAGE (Mouse)
    0xa1, 0x01,                    // COLLECTION (Application)
	0x85, 0x09, 				   // Report ID (1) 
    0x09, 0x01,                    //   USAGE (Pointer)
    0xA1, 0x00,                    //   COLLECTION (Physical)
    0x05, 0x09,                    //     USAGE_PAGE (Button)
    0x19, 0x01,                    //     USAGE_MINIMUM (Button 1)
    0x29, 0x03,                    //     USAGE_MAXIMUM (Button 3)
    0x15, 0x00,                    //     LOGICAL_MINIMUM (0)
    0x25, 0x01,                    //     LOGICAL_MAXIMUM (1)
    0x75, 0x01,                    //     REPORT_SIZE (1)
    0x95, 0x03,                    //     REPORT_COUNT (3)
    0x81, 0x02,                    //     INPUT (Data,Var,Abs)
    0x75, 0x01,                    //     REPORT_SIZE (1)
    0x95, 0x05,                    //     REPORT_COUNT (5)
    0x81, 0x03,                    //     INPUT (Cnst,Var,Abs)

    0x05, 0x01,                    //     USAGE_PAGE (Generic Desktop)
    0x09, 0x30,                    //     USAGE (X)
    0x09, 0x31,                    //     USAGE (Y)
	//0x09, 0x38,                    //     USAGE (Wheel)
    0x15, 0x00,                    //     LOGICAL_MINIMUM (0)
    0x25, 0x00, 0x04,              //     LOGICAL_MAXIMUM (1k)
    0x75, 0x08,                    //     REPORT_SIZE (16)
    0x95, 0x02,                    //     REPORT_COUNT (2)
	0x81, 0x06,                    //     INPUT (Data,Var,Rel)
    0xC0,                          //   END_COLLECTION
    0xC0                          // END COLLECTION

```

---

### Post by Grumbel on 2012-02-08
> **ulao said:**
> Perfect, so is this the problem?
Only this one is actually checked:

    Event code 320 (ToolPen)

But not having the others Tool* ones there as well would certainly be more clean.

> Not sure you know much about the usb firmware side of things but this is my mouse part of the descriptor. As you can tell by the comments there is nothing more then a pointer and a wheel. So what does the kernel have beef with?
I think the problem is simply that there are to many buttons on the device. The kernel starts at 303 and then goes up to 327 with the button ids, inbetween is ToolPen and causing problems.

Looking at linux-source-3.0.0/drivers/hid/hid-input.c shows this piece of code:
```

        case HID_UP_BUTTON:
                code = ((usage->hid - 1) & HID_USAGE);

                switch (field->application) {
                case HID_GD_MOUSE:
                case HID_GD_POINTER:  code += BTN_MOUSE; break;
                case HID_GD_JOYSTICK:
                                if (code <= 0xf)
                                        code += BTN_JOYSTICK;
                                else
                                        code += BTN_TRIGGER_HAPPY;
                                break;
                case HID_GD_GAMEPAD:  code += BTN_GAMEPAD; break;
                default:

```
This looks like a bug in the Kernel. For Usage Page Joystick it correctly uses BTN_TRIGGER_HAPPY, so it doesn't run into conflicts with other buttons, but for Usage Page Gamepad it just overflows into the other button names which leads to the given conflict. So it looks like Linux currently can only handle 16 buttons for gamepads properly, as after that it will overflow and run into the tablet buttons leading to conflicts.

Is your device supposed to have 30 buttons? And if so, would it be possible to break them up into multiple separate HID devices (i.e. one for mouse, one for joystick, etc.) instead of having it all in one?

---

### Post by ulao on 2012-02-08
well here are my buttons

   
Event code 304 (BtnA) HID 0
Event code 305 (BtnB) HID 1
Event code 306 (BtnC) HID 2
Event code 307 (BtnX) HID 3
Event code 308 (BtnY) HID 4
Event code 309 (BtnZ) HID 5
Event code 310 (BtnTL) HID 6
Event code 311 (BtnTR) HID 7 ( first row )
Event code 312 (BtnTL2) HID 8
Event code 313 (BtnTR2) HID 9
Event code 314 (BtnSelect) HID 10
Event code 315 (BtnStart) HID 11
Event code 316 (BtnMode) HID 12
Event code 317 (BtnThumbL) HID 13
Event code 318 (BtnThumbR) HID 14
Event code 319 (?) HID 15 ( second row ) 

but for some reason its a '?' and I'm told by xboxdrv that that is not an event key. if I watch it from the event I see this
Event: time 1328761901.985525, type 1 (Key), code 319 (?), value 0

I should have one more row but I only use 3 of the buttons, however in the descriptor I tell it there is another row. In total it would be 24.

I can not finish mapping because of the ? thing which is really unfortunate. Kind of makes me wonder what BTN_DEAD is, since my first HID is A 304 not 303.

---

### Post by Grumbel on 2012-02-09
> **ulao said:**
> Event code 319 (?) HID 15 ( second row )
Use KEY_#319 for that.

---

### Post by ulao on 2012-02-09
ah I tried to use the number somehow... thx for that! So this works as a good temp fix for me, any idea how to get the code fixed?
Obviously I need this

       ```
 case HID_UP_BUTTON:
                code = ((usage->hid - 1) & HID_USAGE);

                switch (field->application) {
                case HID_GD_MOUSE:
                case HID_GD_POINTER:  code += BTN_MOUSE; break;
                case HID_GD_JOYSTICK:
                case HID_GD_GAMEPAD:  code += BTN_GAMEPAD; 
                                if (code <= 0xf)
                                        code += BTN_JOYSTICK;
                                else
                                        code += BTN_TRIGGER_HAPPY;
                                break;
                default:
```

so how do I make sure its in the next release or so? Also, how does one recompile kernels? Do I have to do all of this?
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by Grumbel on 2012-02-09
> **ulao said:**
> So this works as a good temp fix for me, any idea how to get the code fixed?
[http://www.kernel.org/doc/Documentation/SubmittingPatches](http://www.kernel.org/doc/Documentation/SubmittingPatches)

Never been through the process myself.

> Obviously I need this
Not quite. That code snipped has bugs, more like:

```

        case HID_UP_BUTTON:
                code = ((usage->hid - 1) & HID_USAGE);

                switch (field->application) {
                case HID_GD_MOUSE:
                case HID_GD_POINTER:  code += BTN_MOUSE; break;
                case HID_GD_JOYSTICK:
                                if (code <= 0xf)
                                        code += BTN_JOYSTICK;
                                else
                                        code += BTN_TRIGGER_HAPPY;
                                break;
                case HID_GD_GAMEPAD:
                                if (code <= 0xf)
                                        code += BTN_GAMEPAD;
                                else
                                        code += BTN_TRIGGER_HAPPY;
                                break;
                default:

```
Don't know enough about HID to tell if thats the cleanest way to fix it or if there are potential naming conflicts with joysticks and gamepads sharing the TriggerHappy buttons.

> so how do I make sure its in the next release or so? Also, how does one recompile kernels? Do I have to do all of this?
More or less. Haven't compiled a kernel myself in a long long while.

---

### Post by ulao on 2012-02-09
ok, thx for the help. Does ubuntu have a means to submit bugs easily?

---

### Post by Grumbel on 2012-02-09
> **ulao said:**
> ok, thx for the help. Does ubuntu have a means to submit bugs easily?
Yes:

[https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

Going through upstream might however be faster.

---

### Post by ulao on 2012-02-09
ok submitted in Bug [#929694]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/929694") 

Not sure what you meant by upstream?

---

### Post by Grumbel on 2012-02-09
> **ulao said:**
> Not sure what you meant by upstream?
The term "upstream" refers to the people who originally write the software (i.e. the kernel developers), as opposet to Ubuntu who just takes the software and then distributes it in packaged form, but isn't actually writing it.

---

