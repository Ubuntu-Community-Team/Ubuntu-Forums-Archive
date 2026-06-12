---
title: "Setting up multiple pointers in ubuntu 11.10"
date: 2012-02-08
forum: General Help
---

### Post by thatrobguy on 2012-02-08
Hi, I am trying to set up a system where two people could use the same  desktop environment at the same time. I'm using Ubuntu 11.10 with  gnome3. The system has a dual monitor setup one is a projector in the  living room and the other is a monitor that can be swiveled  to face the  kitchen. There are two mice and two keyboards so that if one person is  working in one room another person could pick up a second mouse and  keyboard and look up a recipe in a different window. The system would be  flexible, you could pass windows back and forth or if one person wanted  to use both monitors they could just turn it to face them without  having to reboot.

So I found this link
[https://www.linux.com/learn/tutorials/542356-weekend-project-zap-your-coworkers-minds-with-multi-pointer-x](https://www.linux.com/learn/tutorials/542356-weekend-project-zap-your-coworkers-minds-with-multi-pointer-x)

And got it working mostly but there are a few problems.
    - for some reason when I log out the changes are reset. 
        If I write a script to make these changes how do I make it load every time I log in? 
        Do I have to or is there a config file I can change permanently?
    - The keyboards aren't acting as i would expect them to. 
       One keyboard pared with one mouse effecting only what that mouse is focused on.
       Instead it seems like there is one main focus that can be achieved by typing alt-tab or
       clicking on the titlebar of a window. Though the mice can scroll either window both
       keyboards type on the main focus only.
     - only one mouse can open apps, maybe because its the master?  
     - both pointers can activate the activities menu but only the core pointer can close it.

I thought it might be because of the way its set up here is the output from xinput -list.

```
rob@e-System:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech MX Revolution Mouse                id=10    [slave  pointer  (2)]
&#9116;   &#8627; Logitech MX5500 Keyboard                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech BT Mini-Receiver          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Logitech Logitech BT Mini-Receiver          id=12    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=14    [slave  keyboard (3)]
&#9121; Auxiliary pointer                           id=16    [master pointer  (17)]
&#9116;   &#8627; 2.4G Wireless Mouse                         id=9    [slave  pointer  (16)]
&#9116;   &#8627; Auxiliary XTEST pointer                     id=18    [slave  pointer  (16)]
&#9123; Auxiliary keyboard                          id=17    [master keyboard (16)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (17)]
    &#8627; Auxiliary XTEST keyboard                    id=19    [slave  keyboard (17)]
``` I noticed the Logitech MX5500 Keyboard is automaticly listed as a pointer but when I tried to change it got.
```
rob@e-System:~$ xinput reattach 11 "Virtual core keyboard"
X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  43 ()
  Device id in failed request: 0x17
  Serial number of failed request:  17
  Current serial number in output stream:  18

```Does  any body know where I should go from here what to try? I'd be very  thankful and I feel many others may benefit from the solution.

---

### Post by thatrobguy on 2012-02-11
I found a way to make the changes permanent. I wrote this script and saved it as .gnomerc and placed it in my home folder. Gnome automatically loads and runs it every time a session starts.

```
#! /bin/bash
#script to enable two pointers and keyboards

#name of second keyboard 
auxKey="AT Translated Set 2 keyboard"

#name of second mouse
auxMouse="2.4G Wireless Mouse"

xinput create-master Auxiliary

xinput reattach `xinput list | grep "$auxMouse" | grep -o -e 'id=[0-9]' -e 'id=[0-9][0-9]' | grep -o -e '[0-9][0-9]' -e '[0-9]'` 'Auxiliary pointer'

xinput reattach `xinput list | grep "$auxKey" | grep -o -e 'id=[0-9]' -e 'id=[0-9][0-9]' | grep -o -e '[0-9][0-9]' -e '[0-9]'` 'Auxiliary keyboard'
```

There is still problems getting the keyboards to focus properly in fact I had to cut and paste
letters just to enter the keyring password because for some reason neither keyboard would type in that window although they worked in others.

I think it's just buggy. Is there something I can do to make it work better? What if I filed a bug report is this a gnome thing or a ubuntu problem? or someone else? 

thanks

---

