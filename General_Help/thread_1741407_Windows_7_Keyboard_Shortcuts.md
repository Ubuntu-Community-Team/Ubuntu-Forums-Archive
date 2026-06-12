---
title: "Windows 7 Keyboard Shortcuts?"
date: 2011-04-28
forum: General Help
---

### Post by avatarmonkeykirby on 2011-04-28
In windows 7 you can :

Windows logo key +Up Arrow
Maximize the window.

Windows logo key +Left Arrow
Maximize the window to the left side of the screen.

Windows logo key +Right Arrow
Maximize the window to the right side of the screen.

Windows logo key +Down Arrow
Minimize the window.

I really like these shortcuts. Is there any way to set this up, or has it been done? I'm using Lucid, but whatever.

---

### Post by Vaphell on 2011-04-28
you can find hotkey configuration in preferences menu but don't count on maximize to left/right. Window manager in lucid doesn't support that ootb but probably it's doable with some script hacking.
Unity interface of 11.04 on the other hand is a lot of like win7 with its panel (but on the left) and supports snapping to the left/right but i don't know how customizable hotkeys are.

---

### Post by yetiman64 on 2011-04-28
> **avatarmonkeykirby said:**
> In windows 7 you can :

Windows logo key +Up Arrow
Maximize the window.

Windows logo key +Left Arrow
Maximize the window to the left side of the screen.

Windows logo key +Right Arrow
Maximize the window to the right side of the screen.

Windows logo key +Down Arrow
Minimize the window.

I really like these shortcuts. Is there any way to set this up, or has it been done? I'm using Lucid, but whatever.

I do similar here using compiz, the last one I use doesn't minimize the window but returns it to its previous state.

Install compizconfig-settings-manager with Synaptic or with sudo apt-get in terminal.

**Edit:** install the program wmctrl with Synaptic or terminal using sudo apt-get.

Go to System > Preferences > CompizConfig Settings Manager > Commands.

Copy and paste into the first four command lines the commands shown in the code box below (only the command itself -not "Command #")
```
Command 0
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$((($WIDTH/2)-8)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

Command 1
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$((($WIDTH/2)-8)) && HALFP=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALFP,0,$HALF,-1

Command 2
wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

Command 3
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz


```On the key bindings tab set the key combination you wish to use for the first 4 "Run Command #", where # is the command number (0,1,2,or 3).

In the first 2 commands above the section > [noparse]$((($WIDTH/2)-8))[/noparse] the -8 can be adjusted up or down to suit your monitor. The figure of -8 suits my screen so there is no overlap of the Windows when 2 windows are side by side.

I am not sure of the command needed to minimize a window totally that you could use in command 3. I think I originally picked up this info on the omgubuntu.co.uk website, but no longer have the link, you may need to Google it if you wish to check out the source of these commands. It is not my original work that is. :)

**Edit 2**: for clarity:  command 0 and command 1 in my instructions give half screen left and right respectively, command 2 is for fullscreen, and command 3 is to revert to previous state. The effect is not identical to Windows but goes very close, you will need to experiment with it to see how it works fully and if it suits your needs.

---

### Post by waffleguy4 on 2011-05-03
I'm running 11.04 and tried the steps above with Compiz. The setup was easy to follow and seemed cool, but it never seemed to "apply". Using the super+left,right,etc keys does nothing. I would really love to have my fav. MS Windows keyboard shortcuts work in Ubuntu- I used the move window keys constantly. My fav. thing about Win 7, actually.

One possible reason for not working - my graphics driver (Nvidia) is having some problems so I'm only using the classic GUI that you choose from the login page. Not the Unity one. Obviously I'm rather new to Linux.

Any pointers to get these keyboard shortcuts working?

Thanks!

---

### Post by yetiman64 on 2011-05-03
> **waffleguy4 said:**
> I'm running 11.04 and tried the steps above with Compiz. The setup was easy to follow and seemed cool, but it never seemed to "apply". Using the super+left,right,etc keys does nothing. I would really love to have my fav. MS Windows keyboard shortcuts work in Ubuntu- I used the move window keys constantly. My fav. thing about Win 7, actually.

One possible reason for not working - my graphics driver (Nvidia) is having some problems so I'm only using the classic GUI that you choose from the login page. Not the Unity one. Obviously I'm rather new to Linux.

Any pointers to get these keyboard shortcuts working?

Thanks!

@ waffleguy4, I've only tried this on Lucid (10.04) and the OP uses Lucid. I will not be using Natty and Unity full time for a while yet, so can't advise you further at this stage sorry to say.

@ The forum in general, Has anyone else tested this in Natty and been successful ?

**Edit: @waffleguy4,** if you can work out a fix for the graphics drivers in your install you don't need to follow the instructions here at all, either for Unity or the classic interface. 

This functionality is already implemented in 11.04. I just tested in 11.04 and with proprietary drivers running didn't need to do anything special to have this work while booted into both the Unity desktop and the Classic desktop. Just dragging a window to either side or the top of the screen works. I believe this relies on compiz working correctly though.

Good luck in getting your driver situation fixed, yetiman64

---

### Post by LinuxNo0b445 on 2011-05-04
this has nothing to do with what your talking about but im new in this thing and i don't know how to create a thread. any help?

---

### Post by yetiman64 on 2011-05-04
> **LinuxNo0b445 said:**
> this has nothing to do with what your talking about but im new in this thing and i don't know how to create a thread. any help?

As you say you are new, I would suggest you post in "Absolute Beginner Talk". 

To do so open the "Absolute Beginner Talk" subforum and look for a button called "New Thread" (there are 2, one at the top and one at the bottom of the page), click on either one and an editor will open. 

Put your question in the editor and supply as much relevant info about your problem/system specs as you can think of without making it overly long. 

Also try to format your post with "whitespace" (write in sentences/paragraphs) for easier viewing by helpers (note how this line is separated from those above it :))

<removed note: moderators are leaving posts 6 & 7 here>

Good luck and welcome to the forum.
yetiman64

---

### Post by waffleguy4 on 2011-05-06
Thanks, but I really want keyboard shortcuts, not just slow mouse actions.

I think this might be what I'm looking for:
[http://ubuntuforums.org/showthread.php?t=1472747](http://ubuntuforums.org/showthread.php?t=1472747)

---

### Post by yetiman64 on 2011-05-06
> **waffleguy4 said:**
> Thanks, but I really want keyboard shortcuts, not just slow mouse actions.

I think this might be what I'm looking for:
[http://ubuntuforums.org/showthread.php?t=1472747](http://ubuntuforums.org/showthread.php?t=1472747)

Ok I understand now. With ccsm (compizconfig settings manager) installed, look at the "Grid" plugin in the "Windows management" section. 

The actions can be done with _either_ mouse or Keyboard (I assumed you would have picked that sorry). You will find a list of keyboard commands there to control it as well. Look on the bindings tab.

Anyway that link basically says the same about using "Grid", however in 11.04 you don't need to do anything as it is already implemented.

---

### Post by waffleguy4 on 2011-05-07
yetiman64, thanks, you are very right.

I figured out how to setup the Grid plugin in the compiz settings page, and I can now move windows from the left to the right half of the screen, but it still won't move it from the left to the right monitor and vice versa.

---

