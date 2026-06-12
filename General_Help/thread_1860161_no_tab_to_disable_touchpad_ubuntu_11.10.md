---
title: "no tab to disable touchpad ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by larry3d on 2011-10-14
hi i just update my ubuntu 11.04 for the new version of ubuntu 11.10 the problem is that the virtual click i want to disable but there is no way how , i'm stuck from 5 hours ago in the same situation pleaseeeee help meee
  my computer is a desktop NF750-G55  16gbddr3 phenom ll x6

here is the image [IMG]http://a7.sphotos.ak.fbcdn.net/hphotos-ak-ash4/294503_110037235773362_100003012597544_70177_1673210113_n.jpg[/IMG]

---

### Post by larry3d on 2011-10-14
hello i have a big problem with the new update of ubuntu 11.10 everything was ok till the momment i update my 11.04 for the new version 11.10 suddenly i got unity working in my machine i got happy for a momment but after moving the mouse than everything got crazy i can't not control the cliclings i tried to desactivated but nothing because there is no tab for touchpad  . in the next link is all the problems with a video details 

[SIZE=4][COLOR=Red]**[http://www.youtube.com/watch?v=vAiFqxAnC6U](http://www.youtube.com/watch?v=vAiFqxAnC6U)**[/COLOR][/SIZE]



here the image of my problems . as you can see the is no tab for the touchpad . SO I CAN'T DESACTIVATE IT . 

I'M SORRY IF I'M TOO LOUD BUT I DON'T KNOW WHAT TO DO I'M FRUSTRATED  SO PLEASEE SOMEONE HELP ME

[IMG]http://a7.sphotos.ak.fbcdn.net/hphotos-ak-ash4/294503_110037235773362_100003012597544_70177_1673210113_n.jpg[/IMG]

---

### Post by ezramorris on 2011-10-14
Hi,
Welcome to Ubuntu Forums!

See if the Troubleshooting section on this [wiki page](https://help.ubuntu.com/community/SynapticsTouchpad#Troubleshooting) helps. :)

Ezra.

---

### Post by cariboo on 2011-10-14
Merged two similar threads. Please don't create multiple threads on the same subject.

---

### Post by larry3d on 2011-10-15
i'm sorry for this but i'm so frustated is not going to happend again

---

### Post by larry3d on 2011-10-15
hi yes i saw the wiki page but is not clear the instructions please tell me how should i do it  . i have proceed typing in my terminal  

xinput list 

larry@larry-smart:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Composite USB PS2 Converter USB to PS2 Adaptor  V2.50    id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Composite USB PS2 Converter USB to PS2 Adaptor  V2.50    id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
larry@larry-smart:~$




what i need to do pleaseee help

---

### Post by larry3d on 2011-10-15
i've reboot my computer many times and nothing is resolve.  after that i decide go to terminal and i tried diferent commands 

larry@larry-smart:~$ sudo trackpad drag
[sudo] password for larry: 
sudo: trackpad: command not found
larry@larry-smart:~$ sudo trackpad show
sudo: trackpad: command not found
larry@larry-smart:~$ sudo trackpad tap
sudo: trackpad: command not found
larry@larry-smart:~$ gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
larry@larry-smart:~$ ...........
fuira@199: command not found
larry@larry-smart:~$

---

### Post by vincegata on 2011-10-15
I have the same problem on Dell.

Follow the thread to disable your touchpad.

[http://ubuntuforums.org/showthread.php?t=1757679](http://ubuntuforums.org/showthread.php?t=1757679)

---

### Post by ezramorris on 2011-10-15
Your issue may be related to [this bug](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/565543).

Ezra.

---

### Post by larry3d on 2011-10-15
[SIZE=3]vincegata [/SIZE]thank you but i don't know how to start in terminal , i saw that you got good results

```
#!/bin/bash
cd $HOME

function messageUser()
{
    if [ "$(which notify-send)" == "" ]; then
        echo "requires... libnotify-bin for messages..."
    elif [ "$1" == "on" ]; then
        notify-send -t 800 -i /home/mike/myicon.png "Touchpad enabled..." "mike reprogramed the calculator button :)"
    elif [ "$1" == "off" ]; then
        notify-send -t 800 -i /home/mike/myicon.png "Touchpad disabled..." "mike reprogramed the calculator button :)"
    fi
}

touchPadId=$(xinput list | grep -i synaptics | grep -i touch | grep PS | cut -d "=" -f 2 | cut -b 1-2)
if [ "$touchPadId" == "" ]; then
    echo "Unable to identify device id..."
else
    if [ -a ".mike-touchPadOnOff" ]; then
        rm -rfv ".mike-touchPadOnOff"
        xinput set-prop $touchPadId 125 1
        messageUser "on"
    else
        touch ".mike-touchPadOnOff"
        xinput set-prop $touchPadId 125 0
        messageUser "off"
    fi
fi

```so what i need to type  in my terminal because i saw you got results

[SIZE=4][COLOR=Red]i think i have to make a video about this

[COLOR=Black][SIZE=2]following the same instructions as you did i got  this 


[/SIZE][/COLOR][/COLOR][/SIZE]
[LIST]
[*][SIZE=2][COLOR=Red][COLOR=Black]larry@larry-smart:~$ xinput --list-props10[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]usage :[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput get-feedbacks <device name>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-ptr-feedback <device name> <threshold> <num> <denom>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-integer-feedback <device name> <feedback id> <value>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput get-button-map <device name>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-button-map <device name> <map button 1> [<map button 2> [...]][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-pointer <device name> [<x index> <y index>][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-mode <device name> ABSOLUTE|RELATIVE[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput list [--short || --long] [<device name>...][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput query-state <device name>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput test [-proximity] <device name>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput create-master <id> [<sendCore (dflt:1)>] [<enable (dflt:1)>][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput remove-master <id> [Floating|AttachToMaster (dflt:Floating)] [<returnPointer>] [<returnKeyboard>][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput reattach <id> <master>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput float <id>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-cp <window> <device>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput test-xi2 <device>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput list-props <device> [<device> ...][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-float-prop <device> <property> <val> [<val> ...][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-atom-prop <device> <property> <val> [<val> ...][/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput watch-props <device>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput delete-prop <device> <property>[/COLOR][/COLOR][/SIZE]
[*][SIZE=2][COLOR=Red][COLOR=Black]    xinput set-prop <device> [--type=atom|float|int] [--format=8|16|32] <property> <val> [<val> ...][/COLOR][/COLOR][/SIZE]
[/LIST]
[SIZE=4][COLOR=Red][COLOR=Black]

[/COLOR] 
[/COLOR][/SIZE]

---

### Post by larry3d on 2011-10-15
vincelata way i got other codes 

larry@larry-smart:~$ xinput --list-props 10
Device 'Composite USB PS2 Converter USB to PS2 Adaptor  V2.50':
    Device Enabled (131):    1
    Coordinate Transformation Matrix (133):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (252):    0
    Device Accel Constant Deceleration (253):    1.000000
    Device Accel Adaptive Deceleration (254):    1.000000
    Device Accel Velocity Scaling (255):    10.000000
    Evdev Axis Inversion (256):    0, 0
    Evdev Axes Swap (258):    0
    Axis Labels (259):    "Rel X" (141), "Rel Y" (142)
    Button Labels (260):    "Button Left" (134), "Button Middle" (135), "Button Right" (136), "Button Wheel Up" (137), "Button Wheel Down" (138), "Button Horiz Wheel Left" (139), "Button Horiz Wheel Right" (140)
    Evdev Middle Button Emulation (261):    0
    Evdev Middle Button Timeout (262):    50
    Evdev Wheel Emulation (263):    0
    Evdev Wheel Emulation Axes (264):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (265):    10
    Evdev Wheel Emulation Timeout (266):    200
    Evdev Wheel Emulation Button (267):    4
    Evdev Drag Lock Buttons (268):    0

[B][SIZE=3][COLOR=Blue]
so don't tell me to enable is 131  [SIZE=1][COLOR=Black]before the new experiment i have to start recording every step[/COLOR][/SIZE]
[/COLOR][/SIZE][/B]

---

### Post by larry3d on 2011-10-15
acording with everything i did this in my terminal without results

larry@larry-smart:~$ xinput set-prop 2 125 0
property 125 doesn't exist, you need to specify its type and format
larry@larry-smart:~$ xinput set-prop 2 131 0
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  57 ()
  Serial number of failed request:  18
  Current serial number in output stream:  19
larry@larry-smart:~$ xinput set-prop 2 131 1
larry@larry-smart:~$


[COLOR=Red]**[SIZE=4]HELPPPPP[/SIZE]**[/COLOR]  PLEASEEEE

---

### Post by larry3d on 2011-10-15
lol guys thank you for all but after so many tweakings i decide to desconect the usb adapter for my mouse and than yeeeeeee  haaaaaaaaaaa  the stupid clicking have stop ha ha ha ha ha i feel so happy now i can go back to bussines THANK YOU FOR ALL I DON'T KNOW HOW TO EXPRESS MY HAPPYNESS:p:p:p


I DON'T EVEN KNOW HOW I MADE IT I THINK I WAS FIGURING OUT FOR ALL THE CONVERSATIONS IN OTHER THREADS HA HA HA 

IN TERMINAL I TYPE 


xinput set-prop 10 131 1


THAN I THINK I DISCONECT THE ADAPTER AND WEEEEEEEE HAAAAAAAAA

[SIZE=4][B][COLOR=Red]KEEP IN MIND THAT AFTER ALL I DON'T HAVE THE TOUCHPAD TAB BUT EVEN LIKE THAT RIGHT NOW MY MOUSE IS WORKING SOOO GOOD SO FAR THE BIGGEST PROBLEM WAS THE STUPID USB ADAPTER THAT'S MY CONCLUSION



[/COLOR][/B][/SIZE]

---

### Post by dresde on 2012-02-15
I lost my Touchpad tab when trying the Multitouch dirver, and I got it back as explained here. I hope that helps!! 
[http://askubuntu.com/a/104458/46047](http://askubuntu.com/a/104458/46047)

---

