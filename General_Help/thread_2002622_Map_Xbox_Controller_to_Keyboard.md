---
title: "Map Xbox Controller to Keyboard"
date: 2012-06-12
forum: General Help
---

### Post by Ubun2to on 2012-06-12
I am in love with the game Marble Arena 2. However, I am also in love with my Xbox controller. Since the game isn't compatible with the Xbox controller, how do I map the keys to the keyboard? I've tried everything I've found-QJoyPad, xboxdrv, xpad, Jkeys, and tons of other stuff. All of it was unsuccessful.
I have tried everything I have found-please help.

---

### Post by Alkerzor on 2012-08-04
> **Ubun2to said:**
> I am in love with the game Marble Arena 2. However, I am also in love with my Xbox controller. Since the game isn't compatible with the Xbox controller, how do I map the keys to the keyboard? I've tried everything I've found-QJoyPad, xboxdrv, xpad, Jkeys, and tons of other stuff. All of it was unsuccessful.
I have tried everything I have found-please help.

Requesting additional help! I'm in a boat as leaky as the OP. I just want to use my wired "Microsoft X-Box 360 pad" (as named by sudo  lsinput)  as a gamepad for replaying my old cartridge games on an  emulator. The closest I've been able to get is the left joystick controlling the mouse (poorly - sticks in the corner), with A/X bound to left click. I've tried every option listed above, and then some. If anyone has any suggestions, I'm all ears! I recognize that mapping a joystick to keyboard bindings is not ideal, but I'm willing to use the d-pad if it comes to that being a limiting factor. I haven't even seen the gamepad buttons bound properly to keyboard buttons. Seeing the start button bring up the in-game menu would be a great milestone. Using Kubuntu 12.04 LTS.

---

### Post by Geezanansa on 2012-08-28
On a windows machine xpadder is great for mapping your controller to keyboard.
On a linux machine xboxdrv is the tool to map controller to keyboard.



Run from terminal ```
man xboxdrv
``` and [SIZE=4][COLOR=Red]READ[/COLOR][/SIZE] the MANUAL especially the bit that has heading RUNNING XBOXDRV(near the end)... 

```
 USING A SINGLE CONTROLLER
       Plug in your Xbox360 gamepad and then unload the xpad driver via:

       $ rmmod xpad

       If  you  want  to  permanently  unload  it  add  the  following line to
       /etc/modprobe.d/blacklist.conf:

       blacklist xpad

       Next you have to load the uinput kernel module which  allows  userspace
       programs  to create virtual input devices and the joydev module handles
       the /dev/input/jsX devices:

       $ modprobe uinput
       $ modprobe joydev

       You also have to make sure that you  have  access  rights  to  /dev/in&#8208;
       put/uinput,  either  add  yourself to the appropriate group, adjust the
       permissions or run xboxdrv as root.

       Once ensured that xpad is out of the way and  everything  is  in  place
       start the userspace driver with:

       $ xboxdrv

```

but 12.04 does not allow unloading of xpad driver (i.e. the first step after plugging in controller) 

Afraid cannot help any further as i have not managed to remap my controller for use in  games yet allthough it has to be said native support for xbox controller in 12.04 is a great thing.

The question is how can xbox controller be mapped in 12.04?

---

### Post by Ubun2to on 2012-08-29
> **Geezanansa said:**
> The question is how can xbox controller be mapped in 12.04?

The answer remains a mystery.
The sad thing is that some games still do not make use of the ability to utilize an XBox controller. I mean, using a keyboard for gaming is very much less than ideal, and it is annoying to have to use one. I remember when I made the jump from the keyboard to controllers-my fingers stopped cramping, and I was no longer tied to one location (and I was not very cramped, as multiplayer games no longer required you to be squashed together so you can use the same keyboard.).

---

### Post by Geezanansa on 2012-08-29
The only mystery is how to get xboxdrv working as you want. lol


When games are written they have code for input devices.  Different  games have different codes for different input devices.  So depending on  the game you want to use your controller with you may have to map keys  as well as using driver.  

xboxdrv is the tool to use on a linux machine to have your controller on any game.

Capeche?

So a game written for pc might only have code for keyboard and mouse,   but the same game written for xbox will have code for xbox  controller(CoD series is one example) regardless of age.

xboxdrv is a driver and keyboard/mouse emulator so that you can use your controller with any game/application on any linux machine.

There are still some who say you aint a pc gamer if you aint using keyboard.   :lolflag:


Using a xbox360 controller to me is far more intuitive than using  keyboard and mouse for gaming.  I have used xpadder with great success  on windows machines to do exactly what you want .  Just install it and  map keys then save profile and done.  Go gaming.


It is proving far more a lengthy project on ubuntu 12.04 though due to  my lack of linux know how. Seem to be missing the nice user friendly  GUI  like in windows.


Yesterday when i posted i had a controller installed but xboxdrv was not  driving it xpad was.  Since then i have managed to install xboxdrv and  get the controller giving device output to terminal.  I have not as yet  managed to map keys to my liking as i need to write a config file.


The answer to op question is xboxdrv.

As the posters in this thread are all in 12.04 flavour and not one  person has given input or direction and i can relate to the hours of  sifting through hours of outdated and irrelevant info.

I thought i would give you something to try googling or searching theses forums for.

I have the utmost confidence xboxdrv is the answer to our question which  should not be " how can xbox controller be mapped in 12.04?" but "how  do i use xboxdrv to map xbox controller to keyboard in 12.04?


After installing xboxdrv from Ubuntu Software Centre and plugging in controller: run in terminal
man xboxdrv  and get reading!

sudo rmmod xpad  

use lsmod to list loaded modules to make sure uinput and joydev are loaded.
uiinput does not show using lsmod and research shows it loads at boot ( no need to sudo modprobe uinput) 


then try sudo xboxdrv 

Referring to this thread and all 33 pages of it [http://ubuntuforums.org/showthread.php?t=825464&page=33](http://ubuntuforums.org/showthread.php?t=825464&page=33) will highlight a few querks and tweaks to get going.(As well as provide access to xboxdrv developer input.)

---

### Post by Geezanansa on 2012-08-29
To get xboxdrv working 
install xboxdrv using ubuntu software centre
plug in controller
run xboxdrv

In order to run xboxdrv the way you want read man xboxdrv

To get xboxdrv doing what i wanted just simply used gedit to make this 
```
sudo xboxdrv -s --device-name "Razer Onza TE" --device-by-id 1689:fd00 --type xbox360 \
--deadzone 9000 --dpad-as-button --trigger-as-button --ui-axismap "x2=REL_X:10,y2=REL_Y:10,x1=KEY_A:KEY_D,y1=KEY_W:KEY_S" --ui-buttonmap "tl=KEY_LEFTSHIFT,tr=KEY_LEFTCTRL" --ui-buttonmap "a=KEY_SPACE,b=KEY_C,x=KEY_1,y=KEY_R" --ui-buttonmap "lb=KEY_Q,rb=KEY_E" --ui-buttonmap "lt=BTN_RIGHT,rt=BTN_LEFT" --ui-buttonmap "dl=KEY_4,dr=KEY_F,du=BTN_MIDDLE,dd=KEY_TAB" --ui-buttonmap "back=KEY_ESC,start=KEY_ENTER"
```
and then simply open and copy n paste to terminal each time i want to use that profile for xboxdrv.  

Many things are possible with this tool and an infinite amount possible with ubuntu.  Really like your sig Ubun2tu > *Early man sometimes evolved not by adapting him to better suit his  environment, but by adapting his environment to better suit him*


Isn't that what ubuntu is all about?.              adapting environments...:lolflag:

---

### Post by Ubun2to on 2012-08-29
I had tried using xboxdrv, but had no success.
I will try what you suggested in the morning, as I really need to catch up on my sleep (I feel like I'm gonna slam my face into the keyboard pretty soon).

---

### Post by Geezanansa on 2012-08-30
Have not played Marble Arena 2 but if controls are 
#W, A, S, D to move around
#Arrow keys to rotate the camera
#Mouse wheel to zoom in/out
#Space Key or Right Mouse Button to jump


#<F1> to bring up the keys windows
#<Esc> to close dialogs or bring up the main menu
#<F10> to pause/unpause the game
#<R> to respawn
#<TAB> to see your stats in multiplayer games
#<T> to write messages in multiplayer games

#<F5> quick save
#<F6> quick load
#<F8> load autosave

then run xboxdrv 
```
sudo xboxdrv -s \
--deadzone 9000 --dpad-as-button --trigger-as-button --ui-axismap "x1=KEY_A:KEY_D,y1=KEY_W:KEY_S" --ui-axismap "x2=KEY_LEFT:KEY_RIGHT,y2=KEY_UP:KEY_DOWN" --ui-buttonmap "a=KEY_SPACE,b=KEY_F1,x=KEY_R,y=KEY_F10" --ui-buttonmap "lt=REL_WHEEL:-1:150,rt=REL_WHEEL:1:150" --ui-buttonmap "lb=KEY_TAB,rb=KEY_T" --ui-buttonmap "dl=KEY_F6,dr=KEY_F8,du=KEY_F5" --ui-buttonmap "back=KEY_ESC"
```

that is if xboxdrv supports your controller without enforcing device bus location and type;  like what i had to do.(i.e. by adding this " --device-by-id 1689:fd00 --type xbox360 " before the "\".  The by-id value will probably be different for your controller though)

---

### Post by JamesTheAwesomeDude on 2013-06-11
#-oOh, now I see how xboxdrv works!

What do I type to remap the + pad? Currently, my command looks like this:

```
sudo xboxdrv -s --type xbox360 \
--deadzone 9000 \
--dpad-as-button \
--trigger-as-button \
--ui-axismap "x2=REL_X:10,y2=REL_Y:10,x1=KEY_A:KEY_D,y1=KEY_W:KEY_S" \
--ui-buttonmap "tl=KEY_LEFTSHIFT,tr=KEY_LEFTCTRL" \
--ui-buttonmap "a=KEY_SPACE,b=KEY_C,x=KEY_1,y=KEY_R" \
--ui-buttonmap "lb=KEY_Q,rb=KEY_E" \
--ui-buttonmap "lt=BTN_RIGHT,rt=BTN_LEFT" \
--ui-buttonmap "dl=KEY_LEFT,dr=KEY_RIGHT,du=KEY_UP,dd=KEY_DOWN" \
--ui-buttonmap "back=KEY_ESC,start=KEY_ENTER"
```.. I can use the left control stick, but the + pad doesn't do anything.

Also, what is the code for the XBox button in the middle of the controller?

---

