---
title: "Aero Snap function?"
date: 2009-10-18
forum: General Help
---

### Post by Hund on 2009-10-18
I would like to have a function like "Aero Snap" found in Windows.

[http://www.youtube.com/watch?v=TbsnbjkrWus](http://www.youtube.com/watch?v=TbsnbjkrWus)

Would be nice if Compipz had a plugin for this. But I cant find any info about it.

---

### Post by P4man on 2009-10-19
check out the grid plugin in compiz.
If you dont like having to use shortcuts for it, I guess its possible somehow to bind it to an edge binding in the commands plugin, but I havent figured that out yet.

---

### Post by Hund on 2009-10-19
Thx. :) Thats almous what I wanted.

---

### Post by gotsanity on 2009-10-28
I also would like to see the snap function built into compiz. Grid almost does what we are looking for but I would like to see it mouse based. Anyone know if it is even possible without some severe code hacking?

Also, on a side note the aero shake feature ([http://www.youtube.com/watch?v=_ryBmNrwqDo](http://www.youtube.com/watch?v=_ryBmNrwqDo)) is pretty sweet as well. I am sure that with enough hacking it could be done on linux as well.

---

### Post by dbyjazz on 2009-10-28
This is great. I've used in on my Windows machine and I love that feature.

---

### Post by gotsanity on 2009-10-29
I worked out the snapping windows via mouse bit. I will post again in a moment with the tutorial.

---

### Post by Hund on 2009-10-29
> **gotsanity said:**
> I worked out the snapping windows via mouse bit. I will post again in a moment with the tutorial.

Cool. :)

---

### Post by P4man on 2009-10-29
> **dbyjazz said:**
> This is great. I've used in on my Windows machine and I love that feature.

Its a nice feature, though I prefer grid and Maximumize in compiz.
Especially with dual monitor aero snap is useless, as it only snaps to the left half on the left monitor and the right half on the right monitor

---

### Post by gotsanity on 2009-10-29
**[Full Solution Here!]("http://wwww.ubuntuforums.org/showpost.php?p=9190800&postcount=45")**

Ok boys and girls, get ready to write this down.

First you need to make sure you have the following installed:

```

sudo apt-get install compizconfig-settings-manager wmctrl

```

*While that is running find out how big the dimensions of your screen is (Mine has a width of 1600 pixels by a height of 1200 pixels). Write these down you will need them later.*

Next, open compizconfig settings manager by clicking on **System > Preferences > Compizconfig Settings Manager**

At the very top is a button labeled **Commands**. Select it.

*Wmctrl will do the window sizing via the following command:*

```

wmctrl -r :ACTIVE: -e <Gravity>,<X>,<Y>,<Width>,<Height>

```

**Gravity:** Leave this 0.
**X,Y:** This is the top left position of the window (AKA: Where to start drawing the window.)
**Width,Height:** How large the window should be drawn.


Input the following (Adjusting the totals for the dimensions of your screen):

**Command Line 0** ```
wmctrl -r :ACTIVE: -e 0,0,0,800,1155
```
**Command Line 1** ```
wmctrl -r :ACTIVE: -e 0,800,0,800,1155
```
**Command Line 2** ```
wmctrl -r :ACTIVE: -e 0,0,0,1600,1155
```

And the final steps. Switch to the **Edge Bindings** tab and select the following edges:

**Run Command 0** - Left
**Run Command 1** - Right
**Run Command 2** - Top

Last step: Click **Back** and then click on **General Options**. Set your **Edge Trigger Delay** to something you find comfortable with. *Mine is set at 400.*

*Only disadvantages I have come across is that if you let the cursor hover too long over a hot point you will accidentally start resizing whatever window you have active. Also, there is a quirk with some windows that will not allow them to resize to the correct size (I am assuming due to the size of the widgets within the window).*

---

### Post by gotsanity on 2009-10-29
> **P4man said:**
> Its a nice feature, though I prefer grid and Maximumize in compiz.
Especially with dual monitor aero snap is useless, as it only snaps to the left half on the left monitor and the right half on the right monitor

Best part about having a linux app perform snapping: you can adjust the dimensions easily :popcorn:

For my next trick... Im gonna attempt to tackle Aero Shake...

---

### Post by jedi453 on 2009-10-29
Thanks gotsanity, that's pretty cool! :D

I got it to work but after some research realized there was a way to get the same functionality without having to input the dimensions manually. This could be useful because it would make the tutorial easier, and if you ever change your resolution it would be already set up for you. The other advantage is that when the window is dragged to the top, to be maximized, it is actually maximized rather than changing it's resolution to fit the screen. As a disclaimer, I'm no expert at bash scripting, so feel free to improve on the code. I also found the 'let <variable> =' command doesn't work within the Command lines.

Here's the changes:
Command Line 0:
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1
```

Command Line 1:
```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1
```

Command Line 2:
```
wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
```

Other than that it's the same, still has the same minor problems and still requires the same software to be installed. Apparently the xdpyinfo command comes preinstalled. :D

Sources:
```
http://www.cyberciti.biz/faq/how-do-i-find-out-screen-resolution-of-my-linux-desktop/
http://www.linuxforums.org/forum/linux-programming-scripting/44758-extracting-substring-string.html
http://desk.stinkpot.org:8080/tricks/index.php/2007/01/assign-output-of-shell-command-to-variable-in-bash/
http://www.gnu.org/software/bash/manual/bashref.html
http://www.softpanorama.org/Scripting/Shellorama/arithmetic_expressions.shtml

```


Thanks again gotsanity, I would have had no idea where to look without your guide. Still looking forward to the aero shake idea.;)

---

### Post by gotsanity on 2009-10-30
Yeah, maybe this weekend I can edit down the tutorial with your changes. As for the aero shake I think that one is gonna require some custom coding. I will do some digging and see what I can come up with.

---

### Post by btechcs on 2009-10-31
For multiple monitor setups, here's the trick to get the compiz,

Check the  GL_MAX_TEXTURE_SIZE using
```

glxinfo -l | grep GL_MAX_TEXTURE_SIZE

```

Mine was 2048, Now we want a horizontal resolution higher than 2048 in compiz. We can just tell compiz to ignore this limitation. BUt I did it the dirty way by changing /usr/bin/compiz script: 

```
sudo vi /usr/bin/compiz
```

Here I commented the line, TEXTURE_LIMIT=.<something>... and added TEXTURE_LIMIT=2944.

Now enable compiz with Appearance settings in ubuntu. The wallpaper will be redrawn, Hence we must enable wallpaper compiz plugin from CCSM (compizconfig setting manager). 

But to enable wallpaper plugin we must disable nautilus desktop from gconf editor. I used this trick from tombuntu:

```
Launch the Run Application dialog with Alt-F2 and run gconf-editor.
Navigate to apps->nautilus->preferences and unselect the show_desktop option.
Your desktop icons should disappear. Now enable the wallpaper plugin from CCSM
```
 

Now just add the lines as commands to compiz and enjoy

My setup is 

```
[TV connected to laptop via VGA]
 __________     ___________
 |1024x768|     |1920x1080|
 | laptop |---->| display |
 |________|     |_________|
/________/


```
win+1  --> move to laptop display
```
bash -c "wmctrl -r :ACTIVE: -b remove,maximized_horz && wmctrl -r :ACTIVE: -b remove,maximized_vert ;wmctrl -r :ACTIVE: -e 0,0,0,1024,768"
```

win+2  --> move to VGA left half display (external monitor) 
```
bash -c "wmctrl -r :ACTIVE: -b remove,maximized_horz && wmctrl -r :ACTIVE: -b remove,maximized_vert ;wmctrl -r :ACTIVE: -e 0,1025,0,960,1080"
```

win+3  --> move to VGA right half display (external monitor) 
```
bash -c "wmctrl -r :ACTIVE: -b remove,maximized_horz && wmctrl -r :ACTIVE: -b remove,maximized_vert ;wmctrl -r :ACTIVE: -e 0,1985,0,960,1080"
```


want win+3 --> restore to original pos (does not work sometimes)
```
bash -c "wmctrl -r :ACTIVE: -b toggle,maximized_vert && wmctrl -r :ACTIVE: -b toggle,maximized_horz;"
```


@frt975
Wobble does not resize like this. I wanted to use the $WIDTH trick, but just was lazy to debug the script.

I have compiz now!!

---

### Post by frt975 on 2009-10-31
i think window wobble is what you're looking for

---

### Post by Mahyar on 2009-11-12
Thanks everyone.  This works well.

Can anyone help out with the commands for four tiles, one in each corner?  That'd be sweet.

---

### Post by stinkeye on 2009-11-12
Nice work gotsanity.

---

### Post by luckymancvp on 2009-11-12
So cool, And if have function like "Show windows side by side " in Windows

---

### Post by scouser73 on 2009-11-12
Follow these instructions [[COLOR="Red"]**OMG Ubuntu: Get Aero Snap**[/COLOR]]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")

---

### Post by manicnerd on 2009-11-17
I'm having trouble setting this up because I cannot find edge bindings.  I'm using ccsm version 0.7.8.

General Options is the only option under the General category.  The tabs within General Options are: General, Display Settings, Focus & Raise Behaviour, Key Bindings, Commands, and Desktop Size.

When I run sudo apt-get install compizconfig-settings-manager wmctrl it tells me that both packages are the newest version.

Was edge bindings removed or something?


UPDATE: decided to do a fresh install of 9.10 and my ccsm version is now 0.8.2 and edge bindings is now available.

---

### Post by haan on 2009-12-04
> **Mahyar said:**
> Thanks everyone.  This works well.

Can anyone help out with the commands for four tiles, one in each corner?  That'd be sweet.

Execute the following script to generate the commands for GNOME and/or KDE for your resolution (without annoying overlapping windows). grid.sh:

```

#!/bin/bash

echo ""
echo "Ubuntu (GNOME) contains a nice utility Compiz Grid:"
echo "Tile, position and resize your windows to fit an imaginary grid."
echo "The functionality is based on Winsplit Revolution for Microsoft Windows."
echo "For more info, demos etc. see: http://winsplit-revolution.com"
echo ""
echo "This script can be used to define wmctrl commands for Kubuntu (KDE)"
echo "for your monitor resolution. These commands can be attached to"
echo "Key Bindings (keyboard shortcuts), so you have the same functionality"
echo "under KDE without the need to install a Tiling Window Manager like"
echo "xmonad, awesome or ion3."
echo ""
echo "The commands can also be used to emulate Windows 7 Aero Snap"
echo "without annoying overlapping windows."
echo "For more info about this subject see youtube or for example" 
echo "http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html"
echo ""
echo "NOTES:" 
echo "- This scipt uses xwininfo (part of x11-utils package) and wmctrl."
echo "  For (K)ubuntu:"
echo "  sudo apt-get install x11-utils wmctrl"
echo "- This script is tested with:"
echo "  Ubuntu 9.10 (resolution 1920x1200)"
echo "  Kubuntu 9.10 (resolution 1920x1200)"
echo "  Kubuntu 8.10 (resolution 1600x1200)"

# define maximum size of usable screen
wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
sleep 1

WIDTH=$((`xwininfo -id $WINDOWID | grep 'Width:' | cut -f 2 -d ':'`))
HEIGHT=$((`xwininfo -id $WINDOWID | grep 'Height:' | cut -f 2 -d ':'`))
BORDERY=$((`xwininfo -id $WINDOWID | grep 'Corners:' | cut -f 11 -d ' ' | cut -f 2 -d '-'`))
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;
sleep 1
wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HEIGHT
sleep 1

BORDER=$((`xwininfo -id $WINDOWID | grep 'Absolute upper-left X:' | cut -f 2 -d ':'`))
BOTTOM=$((`xwininfo -id $WINDOWID | grep 'Corners:' | cut -f 11 -d ' ' | cut -f 2 -d '-'`))
BORDERY=$(($BORDERY-(`xwininfo -id $WINDOWID | grep 'Corners:' | cut -f 11 -d ' ' | cut -f 2 -d '-'`)))
TOP=$((`xwininfo -id $WINDOWID | grep 'Relative upper-left Y:' | cut -f 2 -d ':'`))

if [ $TOP -eq 0 ]
then #KDE
    echo ""
    echo "----------------------"
    echo "Assuming KDE, Correct?"
    echo "----------------------"
    WIDTH=$(((`xwininfo -id $WINDOWID | grep 'Width:' | cut -f 2 -d ':'`)-2*$BORDER))
    HEIGHT=$(((`xwininfo -id $WINDOWID | grep 'Height:' | cut -f 2 -d ':'`)-2*$BORDERY))
    TITLE=$((`xwininfo -id $WINDOWID | grep 'Absolute upper-left Y:' | cut -f 2 -d ':'`))

    echo ""
    echo "Below are the wmctrl commands for KDE (Kubuntu)."
    echo ""
    echo "The Key Bindings (keyboard shortcuts) can be set in the following way:"
    echo "sudo apt-get install xbindkeys xbindkeys-config"
    echo "xbindkeys --defaults > ~/.xbindkeysrc"
    echo "echo \"xbindkeys\" > ~/.kde/Autostart/startxbindkeys.sh"
    echo "chmod u+x ~/.kde/Autostart/startxbindkeys.sh"
    echo "~/.kde/Autostart/startxbindkeys.sh"
    echo "xbindkeys-config"
    echo "finally add the commands below"
    echo ""
    echo "Centre       Control+Alt+KP_Begin:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HEIGHT"
    echo ""
    echo "Left         Control+Alt+KP_Left:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo ""
    echo "Right        Control+Alt+KP_Right:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+($BORDER))),0,$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo ""
    echo "Top          Control+Alt+KP_Up:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Bottom       Control+Alt+KP_Down:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,$(($TITLE+$BORDERY+$TOP+($HEIGHT/2-($TITLE/2+$BORDERY)))),$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Top Left     Control+Alt+KP_Home:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Top Right    Control+Alt+KP_Prior:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+($BORDER))),0,$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Bottom Left  Control+Alt+KP_End:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,$(($TITLE+$BORDERY+$TOP+($HEIGHT/2-($TITLE/2+$BORDERY)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Bottum Right Control+Alt+KP_Next:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+($BORDER))),$(($TITLE+$BORDERY+$TOP+($HEIGHT/2-($TITLE/2+$BORDERY)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
else #GNOME
    echo ""
    echo "------------------------"
    echo "Assuming GNOME, Correct?"
    echo "------------------------"
    WIDTH=$((`xwininfo -id $WINDOWID | grep 'Width:' | cut -f 2 -d ':'`))
    HEIGHT=$((`xwininfo -id $WINDOWID | grep 'Height:' | cut -f 2 -d ':'`))

    wmctrl -r :ACTIVE: -e 0,0,$TOP,$WIDTH,$(($HEIGHT-2*$BOTTOM))
    sleep 1
    TITLE=$(((`xwininfo -id $WINDOWID | grep 'Absolute upper-left Y:' | cut -f 2 -d ':'`)-$TOP-$BORDER))
    TOP=$(($TOP-$TITLE))
    
    echo ""
    echo "Below are the wmctrl commands for GNOME (Ubuntu)."
    echo "The Key Bindings (keyboard shortcuts)"
    echo "or Edge Bindings (like Aero Snap) can be set under:"
    echo "System -> Prefences -> CompizConfig Settings Manager ->"
    echo "Commands -> Commands/Key Bindings/Edge Bindings"
    echo ""
    echo "Centre       <Control><Alt>KP_5:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(($TITLE+$TOP)),$WIDTH,$HEIGHT"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HEIGHT"
    echo ""
    echo "Left         <Control><Alt>KP_4:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(($TITLE+$TOP)),$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo ""
    echo "Right        <Control><Alt>KP_6:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),$(($TITLE+$TOP)),$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),0,$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo ""
    echo "Top          <Control><Alt>KP_8:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(($TITLE+$TOP)),$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Bottom       <Control><Alt>KP_2:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Top Left     <Control><Alt>KP_7:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(($TITLE+$TOP)),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Top Right    <Control><Alt>KP_9:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),$(($TITLE+$TOP)),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),0,$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Bottom Left  <Control><Alt>KP_1:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Bottum Right <Control><Alt>KP_3:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "TIP: For GNOME (Ubuntu) Key Bindings use Compiz Grid instead. Go to:"
    echo "     System -> Prefences -> CompizConfig Settings Manager ->"
    echo "     Window Management -> Grid"
fi

wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HEIGHT

echo ""
echo "Current used values:"
echo "border: $BORDER pixels"
if [ $TOP -eq 0 ]
then #KDE
    echo "bordery: $BORDERY pixels"
fi
echo "width:  $WIDTH pixels"
echo "height: $HEIGHT pixels"
echo "bottom: $BOTTOM pixels"
echo "top:    $TOP pixels"
echo "title:  $TITLE pixels"

```

---

### Post by TurtleKing on 2009-12-15
> **gotsanity said:**
> Ok boys and girls, get ready to write this down.

First you need to make sure you have the following installed:

```

sudo apt-get install compizconfig-settings-manager wmctrl

```

[I]While that is running find out how big the dimensions of your screen is (Mine has a width of 1600 pixels by a height of 1200 pixels). Write these down you will need them later.

Next, open compizconfig settings manager by clicking on **System > Preferences > Compizconfig Settings Manager**

At the very top is a button labeled **Commands**. Select it.

*Wmctrl will do the window sizing via the following command:*

```

wmctrl -r :ACTIVE: -e <Gravity>,<X>,<Y>,<Width>,<Height>

```
[/I]Where do I type this code since you already have a code to input for command line 0? In addition, do I replace the words in the code Width & Height to the numbers of my resolution?

---

### Post by TurtleKing on 2009-12-15
hmm anybody know about this ubuntu feature anymore?

---

### Post by TurtleKing on 2009-12-16
Anybody?:confused:

---

### Post by ean5533 on 2009-12-16
> **TurtleKing said:**
> Anybody?:confused:

Read this site for an easy walkthrough:

[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

---

### Post by ST3ALTHPSYCH0 on 2009-12-16
> **P4man said:**
> Its a nice feature, though I prefer grid and Maximumize in compiz.
Especially with dual monitor aero snap is useless, as it only snaps to the left half on the left monitor and the right half on the right monitor

I realize that this is an Ubuntu forum, but I'd like to point out that you're mistaken. You can snap to the right edge of your monitor in a dual monitor setup (where the desktop is extended to the right) by using the super+right arrow key combo. Obviously, if you try to drag it it will just go onto the extended desktop.

---

### Post by TurtleKing on 2009-12-17
This program is slow and sometimes does not respond on my PC following omgUbuntu website's guide for installation. When I move the cursor to the left, to the right, or above I have to do it 4-6 times for it to respond, and sometimes it does not do anything at all. I would like to try the super-right arrow key combo, where do I look to set this up, or exactly which keys do I need to use (don't understand which key is "super")?

*Edit: okay I noticed it works when I carry the window to the left, right, and above, but I have to bury half of the window on direction mentioned for me to get it to work. This kind of defeats the purpose of making it half or viewable at all if I cannot see half of the window. I believe I might to setup the width and height of the snap function, so it does go over the screen. Any idea where do I insert this information?*

---

### Post by gb_drbob on 2010-01-04
Hello, 

I noticed that if a window is already fully maximised then you can't drag it straight from maximised to the side of the screen for the "half-fullscreen" effect. I fixed that by adding ```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz
``` to the command lines for left and right snap.

So my command0 (left snap) is now:

```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1
```and command 1 (right snap) is:

```
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1
```

---

### Post by auh2o on 2010-03-05
I have noticed a few problems with following the instructions in jedi453's post. First, if I bind run command 2 to top, my auto-hidden top toolbar won't expand. Second, any active window will snap to left or right screen edge (or maximize at top edge) merely by moving the mouse pointer there - not just by me grabbing and dragging a window. Naturally this is annoying. Thirdly, when dragging the window back from the edge, it won't resize to its original size.

There aren't any conflicts with the Rotate Cube plugin. I turned it off and nothing changed.

---

### Post by auh2o on 2010-03-06
Bumping this. See my previous post.

Is there a way to make an auto-hidden top toolbar work with *Command line 2*?

Also, I understand now why you should set an edge trigger delay at about 500. The code merely depends on the location of the mouse pointer, not that the mouse pointer is currently dragging a window. Is there any way to make the function trigger *only* on dragging windows to screen edges, and not simply by moving the mouse pointer to the screen edge? I imagine it might be hard to do, but that would make this work more like Aero Snap actually does, and remove this little edge flip delay annoyance.

As for my third problem, I've found that it is windows that take up 100% of the vertical screen space that won't resize back when pulled away from the edges. ANy way to fix this?

Edit: I've used this function for a while now, and it just gets *really* annoying the way windows will move to one side just because you have the mouse pointer there, for example using the scrollbar on a maximized window. Unless there is a way to get the "snap" to happen ONLY on drag & drop, I will say it is pretty useless to assign the edge bindings this way. Better then to assign button bindings, or use the Grid plugin instead.

---

### Post by marshall.robert on 2010-04-04
The 2 above posts by auh2o are problems for me too. This especially arises with the desktop; it will move it about if you have no other windows in focus, naturally causing issues.

If there is any way to detect whether the mouse button is down, then that would be fantastic.

---

### Post by stinkeye on 2010-04-04
If you use gnome-do, enable the window manager plugin.
Type tile until *tile windows* comes up, hit enter and it will tile open windows.
Add it to the shelf and it should come up by just typing *ti*

---

### Post by louis--taylor on 2010-04-04
This is really good! I had not found this :)
Do you know how gnome-do does this? does it interact directly with the x server or does it use some other program to do this?

---

### Post by stinkeye on 2010-04-04
> **louis--taylor said:**
> This is really good! I had not found this :)
Do you know how gnome-do does this? does it interact directly with the x server or does it use some other program to do this?

No idea.
[**_[COLOR="DarkRed"]http://do.davebsd.com/wiki/WindowManager_Plugin[/COLOR]_**]("http://do.davebsd.com/wiki/WindowManager_Plugin")

---

### Post by stinkeye on 2010-04-04
There is also a tile plugin for compiz in the **compiz-fusion-plugins-unsupported** package.
You need the version (0.8.3+git20090911-1ubuntu1) from the [**_[COLOR="DarkRed"]PPA for compiz[/COLOR]_**]("https://launchpad.net/~compiz/+archive/ppa") though.
I only download this package from the compiz ppa and then disable the repository,
 because I don't like some of the changes in the other updated packages.

---

### Post by ppp213 on 2010-04-04
Having a problem with the snap left. I am using keyboard shortcuts to get the scripts to run and am able to get snap up and snap right to work. However, when I do snap left I get an error that says "Error while trying to run (/home/king/Public/scripts/aerosnap_left) which is linked to the key (<Mod4>1)". I have double checked the script and have made sure that has permission to run as a program, but it still doesn't work. Does anyone have an idea what I should do?

---

### Post by ppp213 on 2010-04-04
Never mind. I fixed the problem

---

### Post by erjoalgo on 2010-04-11
I got this to work. However, after restart, it doesnt work. I've tried remapping to other keys and no luck. Any idea on how to start this program after reboot?

---

### Post by Chronon on 2010-04-11
BTW, this snap feature is enabled in KDE 4.4 by default.

---

### Post by JUSTINBEAIRD on 2010-04-11
> **Hund said:**
> I would like to have a function like "Aero Snap" found in Windows.

[http://www.youtube.com/watch?v=TbsnbjkrWus](http://www.youtube.com/watch?v=TbsnbjkrWus)

Would be nice if Compipz had a plugin for this. But I cant find any info about it.

kubuntu has this by default

also it can have different icons and wallpaper on different desktops
Kwin is quite nice to it is basically Compiz for kde

---

### Post by manoriax on 2010-04-21
I really like that, but I have one question: Is there a way to only activate the plugin at the time I really move a window to one of the sides of the desktop? The problem is that as soon as I move my mouse cursor to the left or the right (without having window selected) the currently active window resizes.

---

### Post by ShawnB391 on 2010-04-21
> **manoriax said:**
> I really like that, but I have one question: Is  there a way to only activate the plugin at the time I really move a  window to one of the sides of the desktop? The problem is that as soon  as I move my mouse cursor to the left or the right (without having  window selected) the currently active window resizes.

This is exactly the same problem that I'm having, and unfortunately its  causing me to not use the Aero Snap function. Can anyone come up with a  solution?

---

### Post by chriskin on 2010-04-21
> **Hund said:**
> I would like to have a function like "Aero Snap" found in Windows.

[http://www.youtube.com/watch?v=TbsnbjkrWus](http://www.youtube.com/watch?v=TbsnbjkrWus)

Would be nice if Compipz had a plugin for this. But I cant find any info about it.


i use compiz's grid alongside easystroke (a mouse gestures application)

it works better than the original aero snap to be honest, as i don't have to actually move the window, i just paint a line towards where i want it to go.

i also liked it better than the idea suggested on the posts before mine (i have tried that one as well)

---

### Post by gotsanity on 2010-04-28
> **ShawnB391 said:**
> This is exactly the same problem that I'm having, and unfortunately its  causing me to not use the Aero Snap function. Can anyone come up with a  solution?

Im hot on trail for a possible solution however it may take me some time. I know we can detect x11 input events using C++ however my code knowledge isnt quite that advanced. Basicly all we need to do is run the following pseudocode:

```

if X11InputEvent.clicked = true {
   execute resize command;
} else {
  // do nothing
}

```

I am aiming at just creating a single script that will house all the commands so we are not looking at the word salad that we posted before. Something like windowcheck.sh --maximize

I will work more on it tommorow since its my day off :)

---

### Post by gotsanity on 2010-04-29
well, I think i may have found the solution but I dont know enough about shell scripting to figure out the new issue I am having. If you know anything about shell scripting please take a look at the following code and help me debug it.

```

#!/bin/sh

if [ xinput --query-state 11 | grep down ] then
        wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
else
        exit 1
fi

```

the xinput line needs to be set to the id of your mouse (just run "xinput list" to find it out)

---

### Post by gotsanity on 2010-04-29
Fixed! Snap on grabbed windows only!

First open a terminal and type:
```
xinput list
```

make a note of your mouse's ID# and execute a few more commands:
```

cd
mkdir .scripts
cd .scripts

```

Create the following three files (**DON'T FORGET**: MOUSE="11" needs to be changed to your mouse's id# in all three files):

compizsnap-left.sh
```

#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-10))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi

```

compizsnap-right.sh
```

#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $TEMPWIDTH ]
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi

```

compizsnap-max.sh
```

#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[1\]=." | sed s/"valuator\[1\]="//)" -le 10 ]
	then
        
		wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi

```

Now, Fire up Settings > Preferences > CompizConfig Settings Manager and then select the Commands plugin.

Set Command 0:
```
sh ~/.scripts/compizsnap-left.sh
```

Set Command 1:
```
sh ~/.scripts/compizsnap-right.sh
```

Set Command 2:
```
sh ~/.scripts/compizsnap-max.sh
```

And last of all select the Edge Bindings tab and set the appropriate commands to the appropriate edges.

Thats all there is to it!

---

### Post by stinkeye on 2010-04-29
Brilliant,well done gotsanity!
Just tried it and works.
Just a bit of a noob question....
How come it works without making the scripts executable?

---

### Post by gotsanity on 2010-04-30
> **stinkeye said:**
> Brilliant,well done gotsanity!
Just tried it and works.
Just a bit of a noob question....
How come it works without making the scripts executable?

because you are telling the sh command to execute the script (at least thats how I understand it)

---

### Post by P4man on 2010-04-30
gotsanity, brilliant, it works! Not 100% reliably (especially not if you are testing dragging left, right and top without releasing) but it works pretty good if you use it 'normally'. Thanks a lot!

---

### Post by arrow.69 on 2010-04-30
Thanks gotsanity, that actually works quite well.

The one remaining discrepancy now is when the effect is triggered.  In Windows 7, the effect is triggered upon releasing the mouse button, whereas using your script, it's triggered after x amount of time.  The problem with that is with too short of a time period it can be jerky, and too long can make it seem unresponsive.  Generally I find it behaves somewhat erratically.

I think adding a while loop and one if statement we might be able to better emulate Aero Snap functionality.

(Pseudo Code)

if (mouse button is down)
{
>>>>while (mouse button is down) -> Do nothing
>>>>if (mouse is still on or close to the edge)
>>>>>>>>maximize Active Window to the left
}
else -> Do nothing

I think that could work.  The only thing I'm unsure about is the second if statement I added. I assume it's possible because Edge Bindings exist, but I have no clue how to bash script it.

Edit: So I found out adding the while loop works quite well for activating the snap on mouse release.  As for the second if statement, I'm not sure how to implement it.  xinput gives you some type of x/y coordinates so I imagine with grep magic and knowing the screen resolution something could be done.  But there's got to be an easier/better solution here.

---

### Post by arrow.69 on 2010-04-30
If anyone's interested, here's my implementation of gotinsanity's script. So far I've found my adjustments make it slightly more intuitive.  However, it also requires an extra terminal utility (xdotool), and because, for the right-most snap, my screen resolution is hard-coded, it's not as portable.  Maybe someone more knowledgeable could improve it.

In any case, here it is:


For compizsnap-left.sh:

```

#!/bin/sh

if (/usr/bin/X11/xinput --query-state 11 | grep down)
then
	while (/usr/bin/X11/xinput --query-state 11 | grep down)
	do 
	echo 'test'
	done


	if (xdotool getmouselocation | grep x:[0-7][[:space:]])
	then
        
		WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

	else
	exit 1
	fi


else
        exit 1
fi

```


compizsnap-right (notice grep x:143[3-9] is exclusive to 1440x900 screen resolution)

```

#!/bin/sh

if (/usr/bin/X11/xinput --query-state 11 | grep down)
then
	while (/usr/bin/X11/xinput --query-state 11 | grep down)
	do 
		echo 'test'
	done

	if (xdotool getmouselocation | grep x:143[3-9][[:space:]]
	then
	

	        WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1
	else
	exit 1
	fi

else
 	exit 1
fi

```


Finally, compizsnap-max:

```

#!/bin/sh

if (/usr/bin/X11/xinput --query-state 11 | grep down)
then
	while (/usr/bin/X11/xinput --query-state 11 | grep down)
	do 
		echo 'shawty'
	done

	if (xdotool getmouselocation | grep y:[0-7][[:space:]])
	then        
		wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
	else
		exit 1
	fi
else
        exit 1
fi

```


That's it!

---

### Post by gotsanity on 2010-04-30
> **arrow.69 said:**
> 
For compizsnap-left.sh:

```

#!/bin/sh

if (/usr/bin/X11/xinput --query-state 11 | grep down)
then
	while (/usr/bin/X11/xinput --query-state 11 | grep down)
	do 
	echo 'test'
	done


	if (xdotool getmouselocation | grep x:[0-7][[:space:]])
	then
        
		WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

	else
	exit 1
	fi


else
        exit 1
fi

```


we could easily grep the current mouse location (with only using native xorg binaries) out of the following command:
```
xinput --query-state <your mouse id>
```

it gives you the following lines:
```
ValuatorClass Mode=Relative Proximity=In
	valuator[0]=981
	valuator[1]=350

```

give me a few mins to play around with it on my machine and I will see if we cant combine our two scripts and figure this out once and for all.

---

### Post by arrow.69 on 2010-04-30
The nice thing about using 

```


xinput --query-stae <mouse-id>

```

is the output seems to be independent of screen resolution, at least on my system.  Changing resolution from 1440x900 to 1200x720, extreme right stays constant at valuator[0]=5470

Those numbers do seem kind of arbitrary though.  Do you know what they're meant to represent?

---

### Post by gotsanity on 2010-04-30
I never actually noticed that. I am going to do some reading on the manpages and maybe I can find out.

---

### Post by gotsanity on 2010-04-30
from what I can tell after testing it out on my own machine the values actually max out at the maximum of your screen resolution. So on my 1440x900 it has a range of

valuator[0]=0 through valuator[0]=1439
valuator[1]=0 through valuator[1]=899

however, I did notice that the mouse didnt always seem to stay at the maximum value so we may want to implement a range check instead of a max value check. I'm thinking something in the range of 10 pixels.

so, time to dive back into the code :popcorn:

---

### Post by arrow.69 on 2010-04-30
It's odd.  If I call xdotool getmouselocation, the value ranges from

x: 0-1439
y: 0-899

My resolution's the same as yours.

However with xinput --query state 11, my range is:

valuator[0]=1472-5469
valuator[1]=1408-4445

Those values mean a ratio of 3997/3037, which is different from 1440/900.  I'm running on 10.04.  If it's a problem with my particular set up, then that's fine, but if it's like this for anyone running lucid, it might cause issues because you can't simply use your resolution value to determine what your bounds for the valuator values are.  I don't see why my output would be ****ed, since I'm running a standard one screen setup with standard open Radeon drivers.

---

### Post by arrow.69 on 2010-05-01
I'm thinking the difference between our outputs might have something to do with subpixel mapping.

xinput --version outputs:

xinput version 1.5.0
XI version on server: 2.0

According to [this link]("https://fedoraproject.org/wiki/Features/XI2"), new features in XI2 include support for subpixel mapping.  That might explain why my numbers seem more arbitrary.  Of course if you're using the same version as me, my theory collapses.

---

### Post by gotsanity on 2010-05-01
I am using the same version as you. However, I know most systems are differently set up. Did you forget to change the mouse's ID (I might have been unclear in the directions). My mouse has an ID of 11. Yours may be different. xinput list should show which one you are looking for.

toss me the output of ```
xinput list
```

and just a heads up... i have a working (and hopefully resolution independent) prototype running right now. I will post the files here shortly after i fix the bugs.

---

### Post by arrow.69 on 2010-05-01
Sounds good.  No, I'm pretty positive I have the right ID.

I'm on my laptop and the Synaptics touchpad is 11.  In any case here's the output for xinput --list

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=13	[slave  keyboard (3)]

```

xinput --query-state 11 gives me relevant output.  The changes in value agree with my cursor movements.  The range of values is just odd.  As long as it's just on my system, it's not a big deal, snap is working fine with my current script.  I'm mainly just curious as to why my output is different.  Changing resolution from 640x480 to 1440x900, the ranges for valuator[0-1] stay exactly the same.

---

### Post by wgilthorpe on 2010-05-01
I would just like to say thanks for all of your work.  I am a student and do not have the time or the knowledge to contribute (yet). So, thanks on behalf of us free loaders.  I am off to bed (finals week next week), but I am super interested in seeing your solution.  During the summer I hope to work on my programming skills so that I, too, may contribute.  Thanks.

---

### Post by gotsanity on 2010-05-01
> **arrow.69 said:**
> 
xinput --query-state 11 gives me relevant output.  The changes in value agree with my cursor movements.  The range of values is just odd.  As long as it's just on my system, it's not a big deal, snap is working fine with my current script.  I'm mainly just curious as to why my output is different.  Changing resolution from 640x480 to 1440x900, the ranges for valuator[0-1] stay exactly the same.

interesting, I wonder if it has anything to do with the type of video card and/or driver you are using. I am personaly using a NVIDIA card using the non-free NV driver. Either way the nice thing is that the scripts will work independently of resolution (HOORAY FOR MATH :lolflag: ). I updated my previous howto for the complete updated instructions (even with some comments) but will post again here for posterity. Enjoy the snapping wonders cause next we tackle aero shake :popcorn:

compizsnap-left.sh
```

#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-10))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi

```

compizsnap-right.sh
```

#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $TEMPWIDTH ]
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi

```

compizsnap-max.sh
```

#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[1\]=." | sed s/"valuator\[1\]="//)" -le 10 ]
	then
        
		wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi

```

---

### Post by gotsanity on 2010-05-01
> **wgilthorpe said:**
> I would just like to say thanks for all of your work.  I am a student and do not have the time or the knowledge to contribute (yet). So, thanks on behalf of us free loaders.  

To be honest I am far from a linux or programming guru. I just enjoy linux and dont mind bashing my head against some man pages and google searches till I figure it out :P

---

### Post by arrow.69 on 2010-05-01
Good job.  As for Aero Shake I think that would be trickier.

You would need to check for an active window, someone clicking down, and the cursor x/y position 'shaking'.  That's possible.  However would you have that script constantly running in the background checking for a 'shake' event?  That's probably inefficient.

You'd need the window manager or whatever to trigger an event when it detects a window being shaken. And that's probably outside the scope of my capabilities.  Let me know if you have a better idea for how to do this.

---

### Post by gotsanity on 2010-05-01
yeah, it will definatly be more difficult. I was thinking something along the way of a modified window move plugin for compiz.

---

### Post by arrow.69 on 2010-05-01
alright.  I'm off to sharpen my C++ skills and read a alot of [documentation.]("http://wiki.compiz.org/Development/Compiz%2B%2BDocumentation")

---

### Post by arrow.69 on 2010-05-01
Some additional info on the xinput --query-state <mouse-d>

I get different ranges depending on the mouse.  So my bluetooth mouse ranges from x:0-1439, y:0-899, while my touchpad has the wider range.  Moving the mouse does not affect the touchpad's values.  Personally I'm going to stick with xdotool, which seems to get the value for the cursor.  I think xinput gives you hardware values or something like that, which then modify the cursor location on screen.  This is all guessowrk of course.

---

### Post by gotsanity on 2010-05-01
> **arrow.69 said:**
> Some additional info on the xinput --query-state <mouse-d>

I get different ranges depending on the mouse.  So my bluetooth mouse ranges from x:0-1439, y:0-899, while my touchpad has the wider range.  Moving the mouse does not affect the touchpad's values.  Personally I'm going to stick with xdotool, which seems to get the value for the cursor.  I think xinput gives you hardware values or something like that, which then modify the cursor location on screen.  This is all guessowrk of course.

Are you still having issues detecting the proper edges using the scripts I wrote? If so than were gonna have to do some more research to make it platform independent and usable by the masses.

---

### Post by arrow.69 on 2010-05-02
No, gotsanity, your script doesn't work as is for me, at least not with my touchpad.  It does work for my Bluetooth mouse, since it's valuator values are in line with yours.  The other problem with using xinput is query-state outputs the state of the pointing device, rather than the cursor.  For me that means if I move with my bluetooth mouse, then with my touchpad, it'll screw your code up.  Ideally we would access the 'core' or master pointer in xinput, but I can't do that on my system.

My code looks alot like yours, except I'm still using xdotool to get my cursor position.  I'm also using grep to determine my bluetooth mouse's ID, since that changes based on when I connect.

I think at this point, the script you wrote should be good for most users.  If anyone has implementation problems, they can always post here and we can make it better or help them out.

It would probably be better if 'CompizSnap' was implemented as an actual plug-in for Compiz.  I imagine Compiz has built-in methods for determining cursor position/grabbed windows, etc.  The bash script works well, but is more of a hack than a permanent solution.  Plus I'd like to learn how to actually develop a Compiz plug-in.  So I'll definitely look into it.

---

### Post by mixim on 2010-05-03
> **gotsanity said:**
> Enjoy the snapping wonders cause next we tackle aero shake :popcorn:

Thanks man, works almost flawlessly! :D... and about aero shake... Much better to sett lower bottom corner as active corner for showing desktop via compiz... When you do this holding a window, it stays!... Much better and easier access than aero shake :D

Thanks again dude, now I have the best of three worlds... OSX, Windows 7 and Compiz

---

### Post by TommyBrunn on 2010-05-04
Thanks everyone for making this script. I just have one minor issue that I thought I could handle on my own (but it seems I was mistaken). See, I want to make it work regardless of whether I'm using my mouse or my touchpad.

Here an example of what I tried:
```
#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="10"
TOUCHPAD="13"
USING="0"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
	USING=$MOUSE
else if /usr/bin/X11/xinput --query-state $TOUCHPAD | grep down
	USING=$TOUCHPAD
fi

if [$USING -ne "0"]; then
   	while (/usr/bin/X11/xinput --query-state $USING | grep down)
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $USING | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $TEMPWIDTH ]
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi
```

It's been a long time since I last did any bash scripting, so I'm sure I'm making some dumb mistake, but I can't figure out what it is.

Any ideas?

---

### Post by BrokeMahPC on 2010-05-04
I actually like the mouse cursor resizing windows. I have a wide screen display 1920x1080 so the mouse does not wander to the extreme left or right often.
If you use snap to stack your windows on the left half of the screen.
By clicking on the top of each window in turn and moving your mouse to the right - you can flip through them like the pages of a book.
Quicker to use the window switcher I suppose. Thank you all for this - it's a great addition.

---

### Post by gotsanity on 2010-05-04
> **TommyBrunn said:**
> Thanks everyone for making this script. I just have one minor issue that I thought I could handle on my own (but it seems I was mistaken). See, I want to make it work regardless of whether I'm using my mouse or my touchpad.

Here an example of what I tried:
```
#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="10"
TOUCHPAD="13"
USING="0"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
	USING=$MOUSE
else if /usr/bin/X11/xinput --query-state $TOUCHPAD | grep down
	USING=$TOUCHPAD
fi

if [$USING -ne "0"]; then
   	while (/usr/bin/X11/xinput --query-state $USING | grep down)
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $USING | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $TEMPWIDTH ]
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi
```

It's been a long time since I last did any bash scripting, so I'm sure I'm making some dumb mistake, but I can't figure out what it is.

Any ideas?

I am working on a method of detecting which mouse is currently in use by detecting all available pointer ids and cycling through them using a loop. I will post back when I've figured it out

---

### Post by gotsanity on 2010-05-04
I have a working beta. give this a shot and let me know how it works.

**YOU MUST CHANGE THE COMMAND LINE FROM "sh compizsnap-left.sh" to "bash compizsnap-left.sh"**
compizsnap-left.sh
```

#!/bin/bash
# ----- Don't edit below this line unless you know what you are doing.

IDS=( $(xinput list | grep "slave  pointer" | sed s/".*id=\([0-9]*\).*"/\\1/) )
for item in ${IDS[*]}
	do

		MOUSE=$item
		WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-10))
		TEMPWIDTH=$(($WIDTH-10))
		echo "Testing mouse #$item"
		echo $WIDTH
		echo $TEMPWIDTH
		if /usr/bin/X11/xinput --query-state $MOUSE | grep down
		then
		   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
			do 
				echo 'button pressed'
			done
	
			if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]
			then
				wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10
				exit 1
			else
				echo "exiting without matching"
				exit 1
			fi
		else
			echo "exiting because button isnt "
	        #exit 1
		fi
done

```

that should work with either mouse. Let me know if you run into anything like other mice having their buttons set to down even if nothing is pressed. from what I can tell in my office this works fine but your mileage may vary.

---

### Post by TommyBrunn on 2010-05-04
> **gotsanity said:**
> I have a working beta. give this a shot and let me know how it works.

It works when using the mouse, but it doesn't work with my touchpad.

```
nevon@loltop:~/games/aquaria$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 Camera                           	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
```

---

### Post by danger89 on 2010-05-04
[http://forum.compiz.org/viewtopic.php?f=136&t=12560&p=77510#p77510](http://forum.compiz.org/viewtopic.php?f=136&t=12560&p=77510#p77510)

This all just should be a option in the menu... Because alot people want to use it. Hopefully Compiz just find a solution to add this nice feature in the next release of Compiz.

---

### Post by ssc351 on 2010-05-06
hey guys, I can't get it working...here is my xinput 

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_0.3M           	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]


I tried ids of 12, 13, 14 but nada.  Also, this is a Dell laptop with both the touchpad and the little keyboard knob dealy.  not sure if that matters.  I used the code as supplied in an earlier post and didn't change anything.  What gives?

Thanks!

---

### Post by gotsanity on 2010-05-07
> **ssc351 said:**
> hey guys, I can't get it working...here is my xinput 

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_0.3M           	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]


I tried ids of 12, 13, 14 but nada.  Also, this is a Dell laptop with both the touchpad and the little keyboard knob dealy.  not sure if that matters.  I used the code as supplied in an earlier post and didn't change anything.  What gives?

Thanks!

Odd, I have a laptop with an alps touchpad and I am running into the same issue. Time to do some debugging I guess.

---

### Post by arrow.69 on 2010-05-10
I used grep to determine the ID for both my touchpad and mouse.
Then, I just tested both the touchpad and the mouse for the different states.  Basically just OR(||) the two statements.

Here's how I found the ID:

```

TouchPad=$(xinput --list | grep TouchPad | cut -c 55-56)
Mouse=$(xinput --list | grep MX1000 | cut -c 55-56)

```

and a sample if statement:

```

if (/usr/bin/X11/xinput --query-state $Mouse | grep down) || (/usr/bin/X11/xinput --query-state $TouchPad | grep down)

```

Works fine for me.  Just figure out how your mouse is identified by xinput --list and modify the grep command accordingly.

EDIT:  Nevermind me.  The way gotsanity did is is smarter and more efficient.  Should work for everyone. Ignore me, as it seems I post things without reading the thread properly.

---

### Post by gotsanity on 2010-05-10
> **arrow.69 said:**
> EDIT:  Nevermind me.  The way gotsanity did is is smarter and more efficient.  Should work for everyone. Ignore me, as it seems I post things without reading the thread properly.

Efficiant... maybe... working for everyone... no. Still working on a solution. It seems that alps touchpads are the only ones I cant get working with the previous solution. If anyone has a synaptic touchpad than please post your results and your xinput -list and xinput --query-state <touchpad id#>.

---

### Post by stinkeye on 2010-05-11
> **arrow.69 said:**
> I used grep to determine the ID for both my touchpad and mouse.
Then, I just tested both the touchpad and the mouse for the different states.  Basically just OR(||) the two statements.

Here's how I found the ID:

```

TouchPad=$(xinput --list | grep TouchPad | cut -c 55-56)
Mouse=$(xinput --list | grep MX1000 | cut -c 55-56)

```

and a sample if statement:

```

if (/usr/bin/X11/xinput --query-state $Mouse | grep down) || (/usr/bin/X11/xinput --query-state $TouchPad | grep down)

```

Works fine for me.  Just figure out how your mouse is identified by xinput --list and modify the grep command accordingly.

EDIT:  Nevermind me.  The way gotsanity did is is smarter and more efficient.  Should work for everyone. Ignore me, as it seems I post things without reading the thread properly.
That was helpful for me because my mouse id sometimes changes from 10 to 12 , so the grep command is useful.

---

### Post by arrow.69 on 2010-05-14
> **gotsanity said:**
> Efficiant... maybe... working for everyone... no. Still working on a solution. It seems that alps touchpads are the only ones I cant get working with the previous solution. If anyone has a synaptic touchpad than please post your results and your xinput -list and xinput --query-state <touchpad id#>.

Here's my output, gotsanity:

xinput --list:

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera                          	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=13	[slave  keyboard (3)]


```


xinput --query-state 11:
```

2 classes :
ButtonClass
	button[1]=up
	button[2]=up
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
	button[8]=up
	button[9]=up
	button[10]=up
	button[11]=up
	button[12]=up
ValuatorClass Mode=Relative Proximity=In
	valuator[0]=4375
	valuator[1]=3677

```

---

### Post by arrow.69 on 2010-05-14
> **stinkeye said:**
> That was helpful for me because my mouse id sometimes changes from 10 to 12 , so the grep command is useful.

I'm glad my code was helpful.  However, let me explain why gotsanity's approach is better.

He says:
```
IDS=( $(xinput list | grep "slave  pointer" | sed s/".*id=\([0-9]*\).*"/\\1/) )
for item in ${IDS[*]}
	do
        <All the checking and stuff that needs to be done>
        done

```

If you look at xinput --list, each of your pointing devices will have the string slave pointer in them.  the code above finds all the lines with slave pointer in them, isolates the ID on the line, and for each of them, will check the state and do whatever.  Using this code you shouldn't have to worry about your mouse's name or anything like that.  In fact hypothetically you wouldn't have to check xinput --list or know what's going on.

---

### Post by stinkeye on 2010-05-14
> **arrow.69 said:**
> I'm glad my code was helpful.  However, let me explain why gotsanity's approach is better.

He says:
```
IDS=( $(xinput list | grep "slave  pointer" | sed s/".*id=\([0-9]*\).*"/\\1/) )
for item in ${IDS[*]}
	do
        <All the checking and stuff that needs to be done>
        done

```

If you look at xinput --list, each of your pointing devices will have the string slave pointer in them.  the code above finds all the lines with slave pointer in them, isolates the ID on the line, and for each of them, will check the state and do whatever.  Using this code you shouldn't have to worry about your mouse's name or anything like that.  In fact hypothetically you wouldn't have to check xinput --list or know what's going on.

I don't have "slave  pointer" in the output of xinput list (in karmic)
```
glen@musicroom:~$ xinput list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech Logitech USB Headset"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Logitech G9 Laser Mouse"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
"Power Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Ideazon Zboard"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=7	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Logitech G9 Laser Mouse"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 24
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

---

### Post by jastonas on 2010-05-16
How exactly are the scripts used? Any instructions?

---

### Post by stinkeye on 2010-05-16
> **jastonas said:**
> How exactly are the scripts used? Any instructions?
See page 5 ...post#45

---

### Post by fooman on 2010-05-16
> **scouser73 said:**
> Follow these instructions [[COLOR=Red]**OMG Ubuntu: Get Aero Snap**[/COLOR]]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")

that works great for me.  :)

thanks

---

### Post by jastonas on 2010-05-16
> **fooman said:**
> that works great for me.  :)

thanks

Not for me!

---

### Post by oneadvent on 2010-05-16
This just isn't working for me, I am trying to use the script that you put the mouse pad id in, and it doesn't seem to work at all. I know the mouse = 11 is right because it tells me the x / y of it when I run that command....

I think its not recognizing my mouse button is pressed. Can someone take a look here and tell me what I'm doing wrong?

my script (copied from prior user):
```
#!/bin/sh
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-10))

echo $WIDTH
TEMPWIDTH=$(($WIDTH-10))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10

	else
		echo "exiting without matching"
		exit 1
	fi
else
		echo "exiting because button isnt "
        exit 1
fi
```

and output from  xinput list
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=11	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
    &#8627; Sony Vaio Keys                          	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; UVC Camera (05ca:183d)                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

Mine is 11. Thanks for any help on this.

---

### Post by arrow.69 on 2010-05-19
Just a few notes related to the last few comments.

The tutorial at OMG:Ubuntu! is a very basic implementation of Aero Snap.  The main limitation is that the effect is activated whenever your cursor hits the edges, regardless of whether or not you're actually dragging a window.  If that's good enough for you, that's great.  It's probably simpler to stick to the tutorial.  What gotsanity's been trying to accomplish is a more precise emulation of Windows 7's Aero Snap function.

For oneadvent:

Last I heard there were some problems implementing the script with Alps touchpad.  My laptop has a Synaptics touchpad, so I'm afraid I can't debug that aspect.

If you have some time on your hands, maybe you'd like to try some debugging yourself.  Let me try to explain what the script is doing.  Look for the text after '#' for my comments explaining what's happening:

```


# ----- Don't edit below this line unless you know what you are doing.

# first, this code is executed when your cursor hits the edge of the screen

WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-10))  #Determine the pixel width of your monitor (used to determine the window size)

echo $WIDTH #Output this value to console (debugging)
TEMPWIDTH=$(($WIDTH-10)) # Store the value of the width minus 10 in a second variable
echo $TEMPWIDTH #Again, output this new value to console
if /usr/bin/X11/xinput --query-state $MOUSE | grep down #If you were holding down the mouse button (so if you're dragging a window)
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down) #then do nothing until the mouse is released
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]  #If you're still close enough to the edge
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10 #finally do the resizing!

	else
		echo "exiting without matching"
		exit 1 # Here, you dragged a window to the edge, but changed your mind. So when you released the mouse you were no longer on the edge
	fi
else
		echo "exiting because button isnt " 
        exit 1 # You hit the edge, but you weren't dragging a window
fi

```


If you feel like doing some debugging, try the various commands used in the script and see if the output is correct.  Maybe try running the whole script and see if there are error messages.

IMO this line is screwing up:

```

$(/usr/bin/X11/xinput --query-state $MOUSE | grep valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]

```

Try running simply : xinput --query-state 11 Look out for valuator lines.


If your valuator values for the touchpad don't match up with your screen resolution, then for sure it won't work.

The above line should output [0,0] on the upper left corner and [1400,900] on lower right for a 1400x900 res.  So basically those values should be the same as your resolution, or close.  1 pixel difference is fine.

Let me know if you think that's the problem, I might have a solution for you.  Otherwise do keep debugging and let us know if you find something interesting.  There's some pretty smart users on this forum.

Good luck!

---

### Post by arrow.69 on 2010-05-28
For the sake of anyone who stumbles on this thread.

The Compiz Developers have implemented a compiz plug-in called Grid which emulates and builds upon Aero Snap functionality.  It will be included by default in Compiz 0.9, which is currently in beta.  So if you can't seem to figure out all this scripting, don't fret.  A more portable, universal solution will be out for everyone to enjoy soon.

---

### Post by jastonas on 2010-05-28
Grid is an existing plugin but works with keybindings.. is it the same??

---

### Post by gotsanity on 2010-05-29
grid is strictly a hotkey tiling program. it does not work with the mouse. This may change in the future but I was unable to find any information stating that the developer was working on that.

---

### Post by jastonas on 2010-05-29
Then what about this?
Its a different plugin? Grid2? Any way to test it?

> **arrow.69 said:**
> For the sake of anyone who stumbles on this thread.

The Compiz Developers have implemented a compiz plug-in called Grid which emulates and builds upon Aero Snap functionality.  It will be included by default in Compiz 0.9, which is currently in beta.  So if you can't seem to figure out all this scripting, don't fret.  A more portable, universal solution will be out for everyone to enjoy soon.

---

### Post by beany1 on 2010-05-31
Couldnt get the first bits of code to work at all with variable set for a mouse, but the beta code u put up i altered for max and right, and it works brilliantly, many thanks!



> **gotsanity said:**
> I have a working beta. give this a shot and let me know how it works.

**YOU MUST CHANGE THE COMMAND LINE FROM "sh compizsnap-left.sh" to "bash compizsnap-left.sh"**
compizsnap-left.sh
```

#!/bin/bash
# ----- Don't edit below this line unless you know what you are doing.

IDS=( $(xinput list | grep "slave  pointer" | sed s/".*id=\([0-9]*\).*"/\\1/) )
for item in ${IDS[*]}
	do

		MOUSE=$item
		WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-10))
		TEMPWIDTH=$(($WIDTH-10))
		echo "Testing mouse #$item"
		echo $WIDTH
		echo $TEMPWIDTH
		if /usr/bin/X11/xinput --query-state $MOUSE | grep down
		then
		   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
			do 
				echo 'button pressed'
			done
	
			if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]
			then
				wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10
				exit 1
			else
				echo "exiting without matching"
				exit 1
			fi
		else
			echo "exiting because button isnt "
	        #exit 1
		fi
done

```

that should work with either mouse. Let me know if you run into anything like other mice having their buttons set to down even if nothing is pressed. from what I can tell in my office this works fine but your mileage may vary.

---

### Post by mpgarate on 2010-06-02
found some great stuff in this thread, and now I have the snap working. Thanks!

---

### Post by oneadvent on 2010-06-02
> **arrow.69 said:**
> Just a few notes related to the last few comments.

The tutorial at OMG:Ubuntu! is a very basic implementation of Aero Snap.  The main limitation is that the effect is activated whenever your cursor hits the edges, regardless of whether or not you're actually dragging a window.  If that's good enough for you, that's great.  It's probably simpler to stick to the tutorial.  What gotsanity's been trying to accomplish is a more precise emulation of Windows 7's Aero Snap function.

For oneadvent:

Last I heard there were some problems implementing the script with Alps touchpad.  My laptop has a Synaptics touchpad, so I'm afraid I can't debug that aspect.

If you have some time on your hands, maybe you'd like to try some debugging yourself.  Let me try to explain what the script is doing.  Look for the text after '#' for my comments explaining what's happening:

```


# ----- Don't edit below this line unless you know what you are doing.

# first, this code is executed when your cursor hits the edge of the screen

WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2-10))  #Determine the pixel width of your monitor (used to determine the window size)

echo $WIDTH #Output this value to console (debugging)
TEMPWIDTH=$(($WIDTH-10)) # Store the value of the width minus 10 in a second variable
echo $TEMPWIDTH #Again, output this new value to console
if /usr/bin/X11/xinput --query-state $MOUSE | grep down #If you were holding down the mouse button (so if you're dragging a window)
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down) #then do nothing until the mouse is released
	do 
		echo 'button pressed'
	done
	
	if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]  #If you're still close enough to the edge
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10 #finally do the resizing!

	else
		echo "exiting without matching"
		exit 1 # Here, you dragged a window to the edge, but changed your mind. So when you released the mouse you were no longer on the edge
	fi
else
		echo "exiting because button isnt " 
        exit 1 # You hit the edge, but you weren't dragging a window
fi

```


If you feel like doing some debugging, try the various commands used in the script and see if the output is correct.  Maybe try running the whole script and see if there are error messages.

IMO this line is screwing up:

```

$(/usr/bin/X11/xinput --query-state $MOUSE | grep valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]

```

Try running simply : xinput --query-state 11 Look out for valuator lines.


If your valuator values for the touchpad don't match up with your screen resolution, then for sure it won't work.

The above line should output [0,0] on the upper left corner and [1400,900] on lower right for a 1400x900 res.  So basically those values should be the same as your resolution, or close.  1 pixel difference is fine.

Let me know if you think that's the problem, I might have a solution for you.  Otherwise do keep debugging and let us know if you find something interesting.  There's some pretty smart users on this forum.

Good luck!

Sorry it took so long. The screen resolution is set to 1600 x 900 but at the bottom right i get 1022 x 766, so that is def the problem.

---

### Post by oneadvent on 2010-06-02
```
MOUSE="11"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`1022` && HALF=$(($WIDTH/2))
```

sorry I didn't follow directions :)

I think its working now, the first time it did it it seemed to snap to the right but as if the screen was 1600 wide, so it was cut off, but the second time it seemed to snap right, and thus far this is working. 

I had manually ran one of the lines, maybe that reset some variables (guessing). Thanks for the clue to the problem, I do not know if I would have ever found it.

Thanks!

---

### Post by oneadvent on 2010-06-20
Okay sorry to bump an older thread, but the script now recognizes the right side of the screen, but it doesn't position it right, its like it positions it off the right side a little bit.

Can anyone shed light on this for me?

---

### Post by oneadvent on 2010-06-20
Actually right after I posted that last message I figured it out, thought someone else may want the answer I found:

```
if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $TEMPWIDTH ]
	then
        
		wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,900,0,800,-1
```

I wish I could tell you I had some crazy break through, but the truth is I just plugged numbers in until it did what I wanted. I figured they would be even numbers, although, I suppose that wouldn't always be true.

Good luck!

---

### Post by sam1948 on 2010-06-28
and this is why i love this OS so much.
$THANKS

---

### Post by Keypel on 2010-07-23
I can't get this to work. Nothing snaps at all. I remembered to change the mouse=11 to my correct number. This is on a fresh 10.03 install. all I did was install the compiz and do the tut on page=5 post=45

[[IMG]http://img834.imageshack.us/img834/2193/screenshot1.th.gif[/IMG]](http://img834.imageshack.us/img834/2193/screenshot1.gif)

[[IMG]http://img843.imageshack.us/img843/3174/screenshoti.th.gif[/IMG]](http://img843.imageshack.us/img843/3174/screenshoti.gif)


[[IMG]http://img36.imageshack.us/img36/8400/screenshot2s.th.gif[/IMG]](http://img36.imageshack.us/img36/8400/screenshot2s.gif)

[[IMG]http://img294.imageshack.us/img294/2735/screenshot3n.th.gif[/IMG]](http://img294.imageshack.us/img294/2735/screenshot3n.gif)

---

### Post by stinkeye on 2010-07-23
Did you install wmctrl?

---

### Post by Keypel on 2010-07-23
> **stinkeye said:**
> Did you install wmctrl?

No, I thought I only had to install compiz. What is wmctrl? I'll try and google it.

EDIT

@stinkeye Thank You!!

@gotsanity Thank You for making this!!

---

### Post by sam1948 on 2010-07-23
> **Keypel said:**
> No, I thought I only had to install compiz. What is wmctrl? I'll try and google it.

EDIT

@stinkeye Thank You!!

@gotsanity Thank You for making this!!

Hi,
i know 11 pages looks like long thing, but u should try from the beginning.
i'll summarize a bit so it will be easier:
there are GUI **actions** u want to catch.
those actions are **mouse on the edge of the screen**.
u can catch them using compiz.
**after catching** them, compiz allows u to **run a command**,
this is when u will use wmctrl **to change size and location** of the window which is on top of all (the one on focus).
later there is a more complicated problem and also a nice not a beginners solution,
I think its good practice for every one so take u'r chances.
this of course until someone will pack it all to a nice script.

good luck

---

### Post by Keypel on 2010-07-23
> **sam1948 said:**
> Hi,
i know 11 pages looks like long thing, but u should try from the beginning.
i'll summarize a bit so it will be easier:
there are GUI **actions** u want to catch.
those actions are **mouse on the edge of the screen**.
u can catch them using compiz.
**after catching** them, compiz allows u to **run a command**,
this is when u will use wmctrl **to change size and location** of the window which is on top of all (the one on focus).
later there is a more complicated problem and also a nice not a beginners solution,
I think its good practice for every one so take u'r chances.
this of course until someone will pack it all to a nice script.

good luck

Yes, your correct, I should have read all 11 pages. I actually found page=5/post=45 thru a link, I tried it, It didn't work, Then I got frustrated because I'm new to Linux. Ubuntu is so new to me, it's a bit overwhelming at times especially since so many apps require an understanding of shell commands. Of course it's worth the price of breaking free of M$'s strong grip.

---

### Post by Keypel on 2010-07-27
I got the aero snap working on my laptop and now I'm trying to get it to work on my desktop.

I remember installing two things on my laptop. One of them was:

```
sudo apt-get install compizconfig-settings-manager wmctrl
```

but I don't remember what the other was.

What programs do I need to make this work on 10.04?

---

### Post by sam1948 on 2010-07-28
hi,
I think that's all,
the compiz setting manager will allow u to capture the screen side event,
if u want to be sure take the action commands (which appears earlier in this thread as "command 0" "command 1", ...)
try to run it in a terminal.
it should effect the size and location of the terminal window

---

### Post by Keypel on 2010-07-28
Hmmm... I got it working on my laptop + usb mouse but my desktop is a no go. I'll have to figure how to trouble shoot this.

---

### Post by Kurtosis on 2010-08-02
A very good and hack-less alternative to aero-snap is [Compiz Grid]("http://wiki.compiz.org/Plugins/Grid").  

It lets you use modifier key + numpad to position windows around the screen, including vertical split screen configs like aero-snap.

> sudo apt-get install compiz-fusion-plugins-extra

Then enable Grid in the Compiz Settings Manager -> Window Management.

There's no mouse support, but I actually like that better since I try to use the keyboard for as much as possible anyway.

---

### Post by datboidere2 on 2010-08-02
hi guys....so i got everything working 99% the way i like it. my only gripe was that the two windows overlapped each other slightly. probably around 5 pixels but its not big deal.  however, i have something interesting that came up. the desktop itself now snaps and resizes also. kinda weird. here's a pic.

[IMG]http://i27.tinypic.com/2d0cakj.png[/IMG]

[IMG]http://i26.tinypic.com/fbx9cp.png[/IMG]

let me know if you guys can figure out this glitch. thanks

---

### Post by datboidere2 on 2010-08-02
> **Kurtosis said:**
> A very good and hack-less alternative to aero-snap is [Compiz Grid]("http://wiki.compiz.org/Plugins/Grid").  

It lets you use modifier key + numpad to position windows around the screen, including vertical split screen configs like aero-snap.



Then enable Grid in the Compiz Settings Manager -> Window Management.

There's no mouse support, but I actually like that better since I try to use the keyboard for as much as possible anyway.

:KS perfect! exactly what i was looking for!! thanks

---

### Post by loki.verloren on 2010-08-15
following is 5 scripts i derived from ones i found on this thread and i experimented extensively with it seeking to achieve equal half-screen balance. i am not sure about the offset numbers i have used as to whether these distances are theme-dependant.

they work more simply than the others, as there is only one wmctrl command in each script that runs upon detection of button down while snapped. what i have implemented in this set are the commands that will make your window fill half the available space on the edge you drag a the furniture of a window onto - it doesn't distinguish between titlebar or edge sizing bars. the previous versions had more wmctrl commands and extra if-then tests. 

on my machine i find that the 'zoom' function which i assign to top left corner you need to leave the mouse still for a moment or often one of the side or top edge half scripts trigger. a positioning test might enable this to not be a problem, it seems to me that it should be a small section not just the single pixel in the corner, like 4 or 8 pixels, and it would make sense to have a visual cue to draw attention to the action's trigger condition. the big advantage of this method as it works for me is the windows are only resizing and this is a single command and a single action so it's fairly fast. 

i can envisage adding a test to determine the starting object-click somehow so a maximize horizontal only and vertical only could be set up to trigger from the sizing bars. 

i see this being used as a set of 'commands' to do specific window movements and how to assign them can be defined by the trigger and command link (eg, you could just use left, right and zoom and have them trigger top, left, right.

maybe a change for someone else, but instead of having to set the mouse number thing in each script, it should be possible to put 

```
MOUSE = `cat mousenumber`
```

and make the entire content of a file in the same directory called 'mousenumber' being the number you want to use.

here's the scripts:

```
#!/bin/sh
# compizsnap-bottom.sh
# snaps to bottom half 50% horizontal.
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="8"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`
HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d ' '` 
HALFWIDTH1=$(($WIDTH/2))
HALFWIDTH=$(($HALFWIDTH1-4))
HALFHEIGHT1=$(($HEIGHT/2))
HALFHEIGHT=$(($HALFHEIGHT1-56))
echo $WIDTH
TEMPWIDTH=$(($WIDTH-2))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	wmctrl -r :ACTIVE: -e 0,0,$HALFHEIGHT1,$TEMPWIDTH,$HALFHEIGHT
else
		echo "exiting because button isnt "
        exit 1
fi

```

```
#!/bin/sh
# compizsnap-left.sh
# snaps window to left hand side 50% vertical.
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="8"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`
HALF1=$(($WIDTH/2))
HALF=$(($HALF1-4))
HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d ' '` 
echo $WIDTH
TEMPWIDTH=$(($WIDTH-2))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	wmctrl -r :ACTIVE: -e 0,0,0,$HALF,$HEIGHT
else
		echo "exiting because button isnt "
        exit 1
fi
```

```
#!/bin/sh
# compizsnap-right.sh
# snaps window to 50% right hand side vertical.
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="8"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`
HALF1=$(($WIDTH/2))
HALF=$(($HALF1-2))
HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d ' '`
echo $WIDTH
TEMPWIDTH=$(($WIDTH-2))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF1,$HEIGHT
else
		echo "exiting because button isnt "
        exit 1
fi
```

```
#!/bin/sh
# compizsnap-top.sh
# snaps window to 50% top half horizontal.
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="8"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`
HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d ' '` 
HALFWIDTH1=$(($WIDTH/2))
HALFWIDTH=$(($HALFWIDTH1-4))
HALFHEIGHT1=$(($HEIGHT/2))
HALFHEIGHT=$(($HALFHEIGHT1-56))
echo $WIDTH
TEMPWIDTH=$(($WIDTH-2))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
	wmctrl -r :ACTIVE: -e 0,0,0,$TEMPWIDTH,$HALFHEIGHT
else
		echo "exiting because button isnt "
        exit 1
fi
```

```
#!/bin/sh
# compizsnap-zoom.sh
# makes window fill screen a la maximize button.
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#

MOUSE="8"

# ----- Don't edit below this line unless you know what you are doing.
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2))
HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d ' '` 
echo $WIDTH
TEMPWIDTH=$(($WIDTH-2))
echo $TEMPWIDTH
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done

	wmctrl -r :ACTIVE: -e 0,0,0,$TEMPWIDTH,$HEIGHT 
else
		echo "exiting because button isnt "
        exit 1
fi
```

---

### Post by Bonster on 2010-08-28
For people that wants to use Compiz Grid plugin with Mouse and hotcorner binding. This is what I did. No need for hotkeys

[http://www.youtube.com/watch?v=XvlTlyEasD8](http://www.youtube.com/watch?v=XvlTlyEasD8)

---

### Post by JimmyBnz on 2010-09-06
For anyone using the code from post 45 on page 5, this might help: So after trying to figure out why the right-snap wasn't working, but the other ones were, I noticed that it was due to a typo in the code for compizsnap-right.sh. The typo is in this line ```
if [ "$(/usr/bin/X11/xinput --query-state $MOUSE | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $TEMPWIDTH ]
```
The "-ge" should actually be "-le".

---

### Post by bdh333 on 2010-09-16
here is a command that will get your Synaptics touch pad id number:

 xinput list | grep "Synaptics"|cut -d' ' -f21|cut -c5,6

---

### Post by maximebf on 2010-09-25
I made a one file only version of previous scripts for the one who are interested.

In your commands use "/path/to/compizsnap left" or "/path/to/compizsnap right" or "/path/to/compizsnap top"

```
#!/bin/bash
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#
# from http://ubuntuforums.org/showpost.php?p=9207510&postcount=60

MOUSE="8"
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`
HEIGHT=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d ' '` 
HALFW=$(($WIDTH/2-5))
HALFH=$(($HEIGHT/2-5))

left() {
	wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && \
	    wmctrl -r :ACTIVE: -b add,maximized_vert && \
	    wmctrl -r :ACTIVE: -e 0,0,0,$HALFW,-10
}

right() {
    wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && \
        wmctrl -r :ACTIVE: -b add,maximized_vert && \
        wmctrl -r :ACTIVE: -e 0,$HALFW,0,$HALFW,-1
}

top() {
	wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
}
	
# ----- Don't edit below this line unless you know what you are doing.
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
    $1
else
	echo "exiting because button isnt "
    exit 1
fi
```

---

### Post by wgilthorpe on 2010-09-28
Thanks for posting this script.  I am a terminal dummy and I just want to confirm how to run this script.  I would copy the code and paste it into a text editor.  I would then save that as a file, I believe.  Then would i need to run a chmod command to make that file executable?  Also, would I need to save that file in a particular place? And last but not least, how do I figure out the path to compiz on my machine.  All help will be appreciated.

---

### Post by YSN on 2010-10-04
Hi there,

kudos to everybody, who has contributed to this project. I was able to improve it even further, by combining the solutions utilizing "xautomation" and "grid" with the scripts provided here.

Now it works perfectly on all of my systems and is even superior to Win7 aerosnap in my opinion.  

There are many advantages of this latest version:

- no more scaling issues on different systems or resolutions, since scaling is handled by "grid"

- more options than only "left", "right" and "maximize" - in this version you can as well snap the window to the top, bottom, top left, top right etc., by dragging it to the assigned edge or corner

- does not interfere with docks or existing edge or corner bindings for "exposé" or "show windows" - corners and edges get "dual-use-functionality" this way ;-)

- different from the version in post #112, snapping is not triggered when the mouse pointer just touches an edge of the desktop without dragging a window - this was pretty annoying in older versions and was corrected by contributors in this thread

- you don't always have to drag a window to an edge - often it is sufficient pressing and releasing the left mouse button at that edge, when focus is on a certain window - this way workflow is faster than on Win7, without the disadvantage of accidentally triggering the snap function (note: logically this only works, if there are no other edge bindings or docks on that particular edge - dragging the window to the edge always works!)


I will just add instructions, so newcomers don't have to read the whole thread. 

1. You need to install xautomation, ccsm and grid by running

```
sudo apt-get install xautomation compiz-fusion-plugins-extra compizconfig-settings-manager
```

in a terminal.


2. Now create a folder named ".script" in your home directory and create a text file named "compizsnap.sh" within that folder.
Paste the content shown below into that text file. 

```
#!/bin/bash
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# 
# Directions: run "xinput list" to find your mouse's ID# and then edit the MOUSE variable below: 
#
# from http://ubuntuforums.org/showpost.php?p=9207510&postcount=60

MOUSE="8"

left() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_4' 'keyup Control_L' 'keyup Alt_L'
}  

right() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_6' 'keyup Control_L' 'keyup Alt_L'
}

top() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_8' 'keyup Control_L' 'keyup Alt_L'
}

bottom() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_2' 'keyup Control_L' 'keyup Alt_L'
}

topleft() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_7' 'keyup Control_L' 'keyup Alt_L'
}

topright() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_9' 'keyup Control_L' 'keyup Alt_L'
}

bottomleft() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_1' 'keyup Control_L' 'keyup Alt_L'
}

bottomright() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_3' 'keyup Control_L' 'keyup Alt_L'
}
	
# ----- Don't edit below this line unless you know what you are doing.
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'button pressed'
	done
    $1
else
	echo "exiting because button is not pressed"
    exit 1
fi
```

Note: When pulling the window to the top edge, I replaced "maximize" with "top", since "maximize" can be achieved by double clicking as well.

3. Alter your Mouse-ID (in my version it is "8") in your script. Find it out by running ```
xinput list
``` in a terminal. Save your script.

4. Make the script file executable.

5. Now add the following lines in compizconfig-settings-manager (ccsm) "Commands":

```
~/.scripts/compizsnap.sh right
~/.scripts/compizsnap.sh left
~/.scripts/compizsnap.sh top
~/.scripts/compizsnap.sh bottom
~/.scripts/compizsnap.sh topleft
~/.scripts/compizsnap.sh topright
~/.scripts/compizsnap.sh bottomleft
~/.scripts/compizsnap.sh bottomright
```

6. Finally assign edges to your commands under "Edge Bindings" in ccsm-Commands, e.g.right edge to right, top left to topleft etc.

7. Make sure that "Grid" and "Commands" are activated in ccsm.

I'm looking forward to the next improvement by another contributor...

Enjoy

YSN

---

### Post by Keypel on 2010-10-04
Thanks YSN! I can't wait to try this.

I think it would be better if you started a new thread with a good thread title. Soon this thread will have 200 posts and any one reading will have to read up to page 17 to find your new solution.

I'm happy you added instructions for newcomers.

---

### Post by Bonster on 2010-10-05
@YSN

Pretty cool but kind of annoying since u wont be able to use Desktop Wall - flip to drag windows, This might be Ok if u only use 1 workspace.

So button binding with Grid is still the best option i think.
Plus with Grid plugin each single corner has 3 different levels of tiling, meaning if u click on it, it will go large to medium to small.

---

### Post by YSN on 2010-10-05
@Bonster

People had asked for a Win7-Aerosnap-like feature, where dragging a window to an edge does resizing. 

Others might prefer using keyboard shortcuts.

If you like to switch desktops by dragging a window to an edge, feel free to do so.

I prefer Exposé with hotcorner-binding for switching between multiple desktops. IMHO Exposé works much faster and more convenient than dragging windows to edges for this purpose, just give it a try.

Best
YSN

By the way: loads of nice tutorial videos you have on youtube :-)

---

### Post by aala on 2010-10-09
it doesn't work for me, which one should I use?:...

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

```

---

### Post by grantmeaname on 2010-10-13
Is there a way to enter two input devices, so that when I'm using my touchpad it works, and when I plug everything in at my desktop the mouse works as well? Something like Mouse="12,14"? Sorry if this is an entirely moronic question, but my google-fu is failing hard :-?

---

### Post by YSN on 2010-10-14
Hi there,
this latest version of the script now automatically checks, which device you are utilizing for CompizSnap, be it a mouse or a touchpad.

You don't need to modify the script with "xinput list" values any more, and now you can switch your input-devices with no hassle while working!

Here it is:

```
#!/bin/bash
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# from http://ubuntuforums.org/showpost.php?p=9925230&postcount=117

MOUSE=`xinput -list | grep -i 'mouse' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `
TP=`xinput -list | grep -i 'touchpad' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `

left() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_4' 'keyup Control_L' 'keyup Alt_L'
}  

right() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_6' 'keyup Control_L' 'keyup Alt_L'
}

top() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_8' 'keyup Control_L' 'keyup Alt_L'
}

bottom() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_2' 'keyup Control_L' 'keyup Alt_L'
}

topleft() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_7' 'keyup Control_L' 'keyup Alt_L'
}

topright() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_9' 'keyup Control_L' 'keyup Alt_L'
}

bottomleft() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_1' 'keyup Control_L' 'keyup Alt_L'
}

bottomright() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_3' 'keyup Control_L' 'keyup Alt_L'
}
	
# ----- Don't edit below this line unless you know what you are doing.
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
   	while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
	do 
		echo 'mouse button pressed'
	done
    $1
else if /usr/bin/X11/xinput --query-state $TP | grep down
then
   	while (/usr/bin/X11/xinput --query-state $TP | grep down)
	do 
		echo 'touchpad button pressed'
	done
    $1
else
	echo "exiting because button is not pressed"
    exit 1
fi
fi
```

Just for the absolute newcomers: I have written down an installation-guide in post number 117. Just skip article 3 of the instructions, since it is obsolete now.

Please let me know, whether it works for you. Maybe we could automate the whole installation process someday, including compiz-settings.

Have fun
YSN

P.S.: Hi Keypel, thanx for your feedback, hope the script worked for you. Feel free to open a new thread with the script, if you wish to. Maybe you could write down new instructions as well. And maybe a more experienced person could review the code, since I believe that the same result can be achieved with a few lines less (IMHO at least one conditional is superfluous).

---

### Post by teuvotohvelo on 2010-10-15
Hello everybody! I really like this function, but had problems getting it work in my Thinkpad. The reason was that i'm not using either mouse or touchpad, but Thinkpad's trackpad...

So here is modified script, that works at least with my IBM TrackPoint:
```
#!/bin/bash
#
# CompizSnap is a collaborative project from ubuntuforums.org and is free software. 
# This script adds window snapping functionality to compiz using the commands plugin.
# from http://ubuntuforums.org/showpost.php?p=9925230&postcount=117

MOUSE=`xinput -list | grep -i 'mouse' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `
TOUCHPAD=`xinput -list | grep -i 'touchpad' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `
#This applies at least to my Thinkpad trackpoint.
TRACKPAD=`xinput -list | grep -i 'trackpoint' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `

left() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_4' 'keyup Control_L' 'keyup Alt_L'
}  

right() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_6' 'keyup Control_L' 'keyup Alt_L'
}

top() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_8' 'keyup Control_L' 'keyup Alt_L'
}

bottom() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_2' 'keyup Control_L' 'keyup Alt_L'
}

topleft() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_7' 'keyup Control_L' 'keyup Alt_L'
}

topright() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_9' 'keyup Control_L' 'keyup Alt_L'
}

bottomleft() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_1' 'keyup Control_L' 'keyup Alt_L'
}

bottomright() {
xte 'keydown Control_L' 'keydown Alt_L' 'key KP_3' 'keyup Control_L' 'keyup Alt_L'
}
    
# ----- Don't edit below this line unless you know what you are doing.
if /usr/bin/X11/xinput --query-state $MOUSE | grep down
then
       while (/usr/bin/X11/xinput --query-state $MOUSE | grep down)
    do 
        echo 'mouse button pressed'
    done
    $1
else if /usr/bin/X11/xinput --query-state $TOUCHPAD | grep down
then
       while (/usr/bin/X11/xinput --query-state $TOUCHPAD | grep down)
    do 
        echo 'touchpad button pressed'
    done
    $1
else if /usr/bin/X11/xinput --query-state $TRACKPAD | grep down
then
       while (/usr/bin/X11/xinput --query-state $TRACKPAD | grep down)
    do 
        echo 'touchpad button pressed'
    done
    $1
else
    echo "exiting because button is not pressed"
    exit 1
fi
fi
fi
```

I'm not very familiar with shell scripts so this may be unefficient way of doing things, but it works at least for me ;-)

If you can't get this working with your own trackpad, try running *xinput -list*, searching your trackpad device from the output and adding it to the grep statement at line 10.

---

### Post by irritated skin on 2010-10-20
Is there anyway to change it so that my mouse hitting the edge of the screen while holding the window automatically changes the window?

---

### Post by pi_31415926535898 on 2010-11-01
I love the work you two have put in on this (gotsanity and arrow.69), but I must say that gotbletu's YouTube video kills this. As soon as I saw that Compiz supported Grid functions, I suspected it would be child's play to bind the specific Grid functions to appropriate mouse/location postures, and lo and behold, that's exactly what is described here (also on page 12 of this thread):

[gotbletu's howto (link)](http://www.youtube.com/watch?v=XvlTlyEasD8)

To succeed, simply install (e.g. through Synaptec) 'compizconfig-settings-manager' and 'xautomation' (and their dependencies), and find 'CompizConfig Settings Manager' under System -> Preferences. The video-guide should be straightforward from there, and while I only applied the two sides, I imagine a great many other tweaks could be made for many other applications.

Thanks to all who have worked on this!

--
Stan

---

### Post by gpwil1 on 2010-12-02
Good work on this guys! by far the best feature of windows 7.

Perhaps we could automate a script to add the compiz settings also, see:

[http://ubuntuforums.org/archive/index.php/t-640199.html](http://ubuntuforums.org/archive/index.php/t-640199.html)

has a new thread been started for this? perhaps it should be moved to the howtos...

:D

---

### Post by blank_64 on 2010-12-11
Hey, I'm trying to run YSN's code but can't seem to get it to work...

I can use "~/.scripts/compizsnap.sh right" in the terminal and get the 'exiting because no button is pressed'  response, but dragging the windows to the edges doesn't seem to work for me. (I have also checked to make sure that it's getting the right MOUSE varible...)

Are there any conflicting features in compiz that may be messing this up, or is there a way to check if I'm doing something else wrong???

EDIT: 

With a bit of testing it seems that the script works for my touchpad, but not my mouse... Weird...

---

### Post by themainliner on 2010-12-30
I like this window snapping effect, but to be honest the feature I liked most of Windows 7 was being able to double click a window edge and have that Window edge snap that way. This avoids any stray edge snaps from a wandering mouse. :D

Does anyone have any idea how to implement that? If they make the "Window Edge Double Click" toggle the snapping of the Window too that would be beyond amazing. :popcorn:

---

### Post by wathompson on 2011-01-04
So... did anyone ever figure out how to do the "aero shake?"
 
PS: Thanks to all who worked out the solution to the improved sero snap.

---

### Post by Mistraldor on 2011-01-09
Hello guys,

I followed the instructions to enable aera snap feature but it doesn't work. My Ubuntu is 10.10 64 bits. what's wrong ? :confused:

---

### Post by Chrissss on 2011-02-01
I made a couple of modifications to the script...

```
#!/bin/bash
##CompizSnap LinuxUndIch.de Edition#############################################
# By Christoph Langner <mail@christoph-langner.de>
# Released under GNU General Public License 3.0
# Copyright (c) 2011
#
# Last updated on Jan/31/2011
#
##GNU GENERAL PUBLIC LICENSE 3.0################################################
# This program is free software: you can redistribute it and/or modify it under 
# the terms of the GNU General Public License as published by the Free Software 
# Foundation, either version 3 of the License, or (at your option) any later 
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT 
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS 
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with 
# this program.  If not, see <http://www.gnu.org/licenses/> or write to the 
# Free Software Foundation, Inc., 
# 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA
#
##GENERAL INFORMATION###########################################################
# This script adds window snapping functionality to compiz using the commands
# plugin. CompizSnap LinuxUndIch.de Edition is based on the collaborative
# project from members of the ubuntuforums.org forums. The script is licensed
# under GPL v3.
#
# Help and support:
# http://wwww.ubuntuforums.org/showthread.php?t=1294661
# http://linuxundich.de/de/ubuntu/aero-snap-mit-gnome-und-compiz/
#
##END OF HEAD###################################################################

##START_OPTIONS#################################################################
# How close has to be the cursor to the edge of the screen
BORDER=3
##END_OPTIONS###################################################################

MOUSE=$(xinput -list | grep -i 'mouse' | grep -v 'Macintosh mouse button emulation' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')
TOUCHPAD=$(xinput -list | grep -i 'touchpad' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')
TRACKPAD=$(xinput -list | grep -i 'trackpoint' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')

WIDTH=$(xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x')
HEIGHT=$(xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p)
HALF=$(($WIDTH/2-10))
TEMPWIDTH=$(($WIDTH-10))


left() {
#would be nicer, but --shell option works only under maverick
#eval $(xdotool getmouselocation --shell)
X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
if [ $X -le $BORDER ]
then
	wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10
fi
}  

right() {
#eval $(xdotool getmouselocation --shell)
X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
if [ $(($WIDTH-$X)) -le $BORDER ]
then
	wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$(($HALF+18)),-10
fi
}

max() {
#eval $(xdotool getmouselocation --shell)
Y=$(xdotool getmouselocation | awk '{print $2}' | cut -d : -f 2)
if [ $(($HEIGHT-$Y)) -ge $(($HEIGHT-$BORDER)) ]
then
	wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
fi
}

    
# ----- Don't edit below this line unless you know what you are doing.
if [ -n "$MOUSE" ]
then
	if xinput --query-state $MOUSE | grep down
	then
		while (xinput --query-state $MOUSE | grep down)
		do 
			echo 'mouse button pressed'
		done
		$1 $MOUSE
	fi
fi

if [ -n "$TOUCHPAD" ]
then
	if xinput --query-state $TOUCHPAD | grep down
	then
		while (xinput --query-state $TOUCHPAD | grep down)
		do 
			echo 'touchpad button pressed'
		done
		$1 $TOUCHPAD
	fi
fi

if [ -n "$TRACKPAD" ]
then
	if xinput --query-state $TRACKPAD | grep down
	then
		while (xinput --query-state $TRACKPAD | grep down)
		do 
			echo 'touchpad button pressed'
		done
		$1 $TRACKPAD
	fi
fi

```

I prefer wmctrl over the grid plugin, beause maximized windows return to their previous size when you drag them by their title bar. I also added a if-clause to check if the mouse is near the border of the screen.

You can find a screencast under [http://linuxundich.de/de/software/aero-snap-mit-gnome-und-compiz/](http://linuxundich.de/de/software/aero-snap-mit-gnome-und-compiz/) (Sorry, the blog is written in german)

---

### Post by Forlong on 2011-02-02
Interesting project!
Chrissss, your script works great. However, I noticed it floods .xsession-errors unnecessarily (especially with the "mouse/touchpad button pressed" messages evoked by the script), so I made some enhancements.
[LIST]- By default compizsnap gives no unnecessary output
- Restore original behaviour (for troubleshooting purposes) by running Compiz like this in the terminal:
```
VERBOSE=yes compiz
```
- Restore original behaviour permanently by uncommenting this line (not recommended): [COLOR="Blue"][FONT="Courier New"]VERBOSE=yes[/FONT][/COLOR][/LIST]


[list]- Additionally, I added a check if wmctrl or xdotool is missing. If so, tell the user.
- Debian users (and it derivates like Ubuntu) will be prompted a command to install them.[/LIST]

```
#!/bin/bash
##CompizSnap LinuxUndIch.de Edition#############################################
# By Christoph Langner <mail@christoph-langner.de>
# Contributions by Nick Bauermeister <Forlong@gmx.de>
# Released under GNU General Public License 3.0
# Copyright (c) 2011
#
# Last updated on Jan/31/2011
#
##GNU GENERAL PUBLIC LICENSE 3.0################################################
# This program is free software: you can redistribute it and/or modify it under 
# the terms of the GNU General Public License as published by the Free Software 
# Foundation, either version 3 of the License, or (at your option) any later 
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT 
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS 
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with 
# this program.  If not, see <http://www.gnu.org/licenses/> or write to the 
# Free Software Foundation, Inc., 
# 51 Franklin St, Fifth Floor, Boston, MA 02110-1301 USA
#
##GENERAL INFORMATION###########################################################
# This script adds window snapping functionality to compiz using the commands plugin.
# CompizSnap LinuxUndIch.de Edition is a collaborative project from people from ubuntuforums.org
# and additions from LinuxUndIch. The script is licensed under GPL v3.
#
# Help and support:
# http://wwww.ubuntuforums.org/showthread.php?t=1294661
# http://linuxundich.de/de/ubuntu/aero-snap-mit-gnome-und-compiz/
#
##END OF HEAD###################################################################

# Check if necessary programs are installed
if [ -z $(command -v xdotool) ]; then
	MISSING=xdotool
fi

if [ -z $(command -v wmctrl) ]; then
	MISSING="wmctrl $MISSING"
fi

if [ ! -z "$MISSING" ]; then
	echo
	echo "Error (compizsnap):"
	echo "You need to install the following program(s): $MISSING"
	if [ -r /etc/debian_version ]
	then
		echo "In order to do so, run:"
		echo "sudo apt-get install $MISSING"
	fi
	exit 1
fi
## End of check, script starts here

# Uncomment to get more output for troubleshooting
# Alternatively, run Compiz like this in the command line: 'VERBOSE=yes compiz'
#VERBOSE=yes

MOUSE=$(xinput -list | grep -i 'mouse' | grep -v 'Macintosh mouse button emulation' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')
TOUCHPAD=$(xinput -list | grep -i 'touchpad' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')
TRACKPAD=$(xinput -list | grep -i 'trackpoint' | grep id= | sed 's:.*id=\([0-9]*\).*:\1:')

WIDTH=$(xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x')
HEIGHT=$(xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p)
HALF=$(($WIDTH/2-10))
TEMPWIDTH=$(($WIDTH-10))


left() {
#would be nicer, but --shell option works only under maverick
#eval $(xdotool getmouselocation --shell)
X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
if [ $X -le 10 ]
then
	wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-10
fi
}  

right() {
#eval $(xdotool getmouselocation --shell)
X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
if [ $(($WIDTH-$X)) -le 10 ]
then
	wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$(($HALF+18)),-10
fi
}

max() {
#eval $(xdotool getmouselocation --shell)
Y=$(xdotool getmouselocation | awk '{print $2}' | cut -d : -f 2)
if [ $(($HEIGHT-$Y)) -ge $(($HEIGHT-$10)) ]
then
	wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
fi
}

if [ ! "$VERBOSE" = "yes" ]
then
	QUIET=-q
fi

DEVICE=touchpad

loop() {
while (xinput --query-state $DEVICE_ID | grep $QUIET down)
do
	if [ "$VERBOSE" = "yes" ]
	then
		echo "$DEVICE button pressed"
	else
		:
	fi
done
}

# ----- Don't edit below this line unless you know what you are doing.
if [ -n "$MOUSE" ]
then
	if xinput --query-state $MOUSE | grep $QUIET down
	then
		DEVICE_ID=$MOUSE
		DEVICE=mouse
		loop
		$1 $MOUSE
	fi
fi

if [ -n "$TOUCHPAD" ]
then
	if xinput --query-state $TOUCHPAD | grep $QUIET down
	then
		DEVICE_ID=$TOUCHPAD
		loop
		$1 $TOUCHPAD
	fi
fi

if [ -n "$TRACKPAD" ]
then
	if xinput --query-state $TRACKPAD | grep $QUIET down
	then
		DEVICE_ID=$TRACKPAD
		loop
		$1 $TRACKPAD
	fi
fi

```

---

### Post by Chrissss on 2011-02-02
Hi Forling!

Nice addition. I got the feedback, that some people have problems to get it to work. I noticed that all of them have Logitech devices. xinput --list says...

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
 &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
 &#8627; Power Button                                id=6    [slave  keyboard (3)]
 &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
 &#8627; Power Button                                id=8    [slave  keyboard (3)]
 &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
 &#8627; Logitech USB Receiver                       id=10    [slave  keyboard (3)]
 &#8627; HP Webcam                                   id=12    [slave  keyboard (3)]
 &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
 &#8627; HP WMI hotkeys                              id=15    [slave  keyboard (3)]
```

or

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
&#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
&#8627; Power Button                                id=6    [slave  keyboard (3)]
&#8627; Power Button                                id=7    [slave  keyboard (3)]
&#8627; HID 046a:0001                               id=8    [slave  keyboard (3)]
```

How do we determine the correct id? There are two entries with "Logitech USB Receiver"...

---

### Post by Forlong on 2011-02-02
Well, the first output makes sense to me. I guess there's a Logitech mouse and keyboard in use. Thus, we could differentiate via 'grep pointer' (annoying to code but possible).

But the second one indicates there are two different pointing devices by Logitech in use. Is that the case?

Additionally we have to consider there might be other pointing devices with generic labelling.
"Unfortunately" my mouse is labelled properly as a Bluetooth Mouse, so this problem didn't even occur to me.

---

### Post by Chrissss on 2011-02-02
I got the answer that in the case of

```
&#9116;   &#8627; Logitech USB Receiver                       id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=10    [slave  pointer  (2)]
```

the user has a mouse and a logitech joystick. Perhaps we've got to to add a method so that the user can select the correct device.

---

### Post by Forlong on 2011-02-02
Would be interesting to know the output of
```
xinput -list --long
``` for these two. Maybe there's a way to detect which one is the mouse.

---

### Post by Chrissss on 2011-02-02
I'll try to get this info :)

---

### Post by gpwil1 on 2011-02-03
Also you could add this to the script to automate the compiz settings:


gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command0_edge "Left"
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command1_edge "Right"
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command2_edge "Top"
gconftool-2 --set --type string /apps/compiz/plugins/commands/allscreens/options/run_command3_edge "Bottom"


gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_1 "~/.scripts/compizsnap.sh left"
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_2 "~/.scripts/compizsnap.sh right"
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_3 "~/.scripts/compizsnap.sh top"
gconftool-2 --set --type string /apps/metacity/keybinding_commands/command_4 "~/.scripts/compizsnap.sh bottom"

edit - help from: 
[http://www.webupd8.org/2011/01/set-up-hot-corners-for-compiz-grid.html](http://www.webupd8.org/2011/01/set-up-hot-corners-for-compiz-grid.html)

---

### Post by Chrissss on 2011-02-03
OK, is a example...

```
$ xinput -list --long 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)] 
    Reporting 4 classes: 
        Class originated from: 11 
        Buttons supported: 13 
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right Button Side Button Extra Button Unknown Button Unknown Button Unknown Button Unknown 
        Button state: 
        Class originated from: 11 
        Detail for Valuator 0: 
          Label: Abs X 
          Range: -1.000000 - -1.000000 
          Resolution: 1 units/m 
          Mode: relative 
        Class originated from: 11 
        Detail for Valuator 1: 
          Label: Abs Y 
          Range: -1.000000 - -1.000000 
          Resolution: 1 units/m 
          Mode: relative 
        Class originated from: 11 
        Detail for Valuator 2: 
          Label: Abs Gas 
          Range: -1.000000 - -1.000000 
          Resolution: 1 units/m 
          Mode: relative 

&#9116;  &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)] 
    Reporting 3 classes: 
        Class originated from: 4 
        Buttons supported: 10 
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None 
        Button state: 
        Class originated from: 4 
        Detail for Valuator 0: 
          Label: Rel X 
          Range: -1.000000 - -1.000000 
          Resolution: 0 units/m 
          Mode: relative 
        Class originated from: 4 
        Detail for Valuator 1: 
          Label: Rel Y 
          Range: -1.000000 - -1.000000 
          Resolution: 0 units/m 
          Mode: relative 

&#9116;  &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=11    [slave  pointer  (2)] 
    Reporting 5 classes: 
        Class originated from: 11 
        Buttons supported: 13 
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right Button Side Button Extra Button Unknown Button Unknown Button Unknown Button Unknown 
        Button state: 
        Class originated from: 11 
        Keycodes supported: 248 
        Class originated from: 11 
        Detail for Valuator 0: 
          Label: Abs X 
          Range: -1.000000 - -1.000000 
          Resolution: 1 units/m 
          Mode: relative 
        Class originated from: 11 
        Detail for Valuator 1: 
          Label: Abs Y 
          Range: -1.000000 - -1.000000 
          Resolution: 1 units/m 
          Mode: relative 
        Class originated from: 11 
        Detail for Valuator 2: 
          Label: Abs Gas 
          Range: -1.000000 - -1.000000 
          Resolution: 1 units/m 
          Mode: relative 

&#9116;  &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=12    [slave  pointer  (2)] 
    Reporting 38 classes: 
        Class originated from: 12 
        Buttons supported: 7 
        Button labels: Button 0 Button Unknown Button Unknown Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right 
        Button state: 
        Class originated from: 12 
        Keycodes supported: 248 
        Class originated from: 12 
        Detail for Valuator 0: 
          Label: Abs X 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 683.000000 
        Class originated from: 12 
        Detail for Valuator 1: 
          Label: Abs Y 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 384.000000 
        Class originated from: 12 
        Detail for Valuator 2: 
          Label: Abs Z 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 3: 
          Label: Abs Rotary X 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 4: 
          Label: Abs Rotary Y 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 5: 
          Label: Abs Rotary Z 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 6: 
          Label: Abs Throttle 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 7: 
          Label: Abs Rudder 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 8: 
          Label: Abs Wheel 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 9: 
          Label: Abs Hat 0 X 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 10: 
          Label: Abs Hat 0 Y 
          Range: -1.000000 - 1.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 11: 
          Label: Abs Hat 1 X 
          Range: -1.000000 - 1.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 12: 
          Label: Abs Volume 
          Range: 0.000000 - 1023.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 13: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 14: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 15: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 16: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 17: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 18: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 19: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 20: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 21: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 22: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 23: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 24: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 25: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 26: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 27: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 28: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 29: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 30: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 31: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 32: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 33: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 34: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 
        Class originated from: 12 
        Detail for Valuator 35: 
          Label: None 
          Range: 0.000000 - 255.000000 
          Resolution: 10000 units/m 
          Mode: absolute 
          Current value: 0.000000 

&#9116;  &#8627; SynPS/2 Synaptics TouchPad                  id=16    [slave  pointer  (2)] 
    Reporting 3 classes: 
        Class originated from: 16 
        Buttons supported: 12 
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right None None None None None 
        Button state: 
        Class originated from: 16 
        Detail for Valuator 0: 
          Label: Rel X 
          Range: 1472.000000 - 5472.000000 
          Resolution: 76000 units/m 
          Mode: relative 
        Class originated from: 16 
        Detail for Valuator 1: 
          Label: Rel Y 
          Range: 1408.000000 - 4448.000000 
          Resolution: 119000 units/m 
          Mode: relative 

&#9116;  &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)] 
    Reporting 3 classes: 
        Class originated from: 17 
        Buttons supported: 5 
        Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down 
        Button state: 
        Class originated from: 17 
        Detail for Valuator 0: 
          Label: Rel X 
          Range: -1.000000 - -1.000000 
          Resolution: 1 units/m 
          Mode: relative 
        Class originated from: 17 
        Detail for Valuator 1: 
          Label: Rel Y 
          Range: -1.000000 - -1.000000 
          Resolution: 1 units/m 
          Mode: relative 

&#9123; Virtual core keyboard                      id=3    [master keyboard (2)] 
    Reporting 1 classes: 
        Class originated from: 15 
        Keycodes supported: 248 

    &#8627; Virtual core XTEST keyboard                id=5    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 5 
        Keycodes supported: 248 

    &#8627; Power Button                                id=6    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 6 
        Keycodes supported: 248 

    &#8627; Video Bus                                  id=7    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 7 
        Keycodes supported: 248 

    &#8627; Power Button                                id=8    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 8 
        Keycodes supported: 248 

    &#8627; Sleep Button                                id=9    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 9 
        Keycodes supported: 248 

    &#8627; Microsoft Microsoft® Nano Transceiver v2.0    id=10    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 10 
        Keycodes supported: 248 

    &#8627; USB2.0 UVC VGA WebCam                      id=13    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 13 
        Keycodes supported: 248 

    &#8627; Asus EeePC extra buttons                    id=14    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 14 
        Keycodes supported: 248 

    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)] 
    Reporting 1 classes: 
        Class originated from: 15 
        Keycodes supported: 248 
```

I didn't have time today to look through the output. I will do this tomorrow.

---

### Post by Forlong on 2011-02-04
@gpwil1: Configuration should be left out of the script.
First of all, it's supposed to add a feature. A configuration script just needs to  be run once. Adding config options to the script would mean configuring/checking every time the script is initiated.
Additionally, the user should configure the way he/she wants it him/herself.
For example, I don't have the "side snaps" bound to the edges but to the lower corners, because the edges are reserved for the cube plugin.
And last but not least, users should be aware of where to set/configure features.

If I find the time I will write an English How-To over the weekend, so it can be linked in the script's header.


@Chrissss: We'll need additional info what that "Microsoft® Nano Transceiver" is for in this case and why it's listed twice in the pointer section.

I guess we could narrow it down like this in the script, if no mouse is found:
```
xinput -list | grep "slave  pointer" | grep -iv "virtual\|touchpad\|trackpoint\|Macintosh mouse button emulation"
```
but the issue with multiple listings won't be solved by this.

---

### Post by gpwil1 on 2011-02-08
> **Forlong said:**
> @gpwil1: Configuration should be left out of the script.
First of all, it's supposed to add a feature. A configuration script just needs to  be run once. Adding config options to the script would mean configuring/checking every time the script is initiated.
Additionally, the user should configure the way he/she wants it him/herself.
..


I agree it would be beneficial for users to know where to configure settings, and that others configurations may be different, but disagree with your first comment. The configuration can be done once on the initiation of the script, and would only require an if statement upon rerunning.

The reasoning behind having it automated is to encourage new users to adopt ubuntu, making it easier is what its all about.


For my intended purpose setting the value through ccsm doesn't help, since I am configuring a remaster from a chrooted environment through the terminal (I don't like having to copy over configuration files, I rather have a script to configure my settings).

Anyway, it was just a suggestion. :p

---

### Post by Tlingit on 2011-02-22
Yeah only thing happened was it told me to install xdotool, then nothing happens not even any errors?

Debian squeeze,

any suggestions?

---

### Post by Forlong on 2011-02-22
Run Compiz like this in the terminal and see what it says then while triggering compizsnap
```
VERBOSE=yes compiz
```

---

### Post by raving on 2011-02-24
Ich habe ein paar Optimierungen angebracht:
1) Fenster sind auch in allen Ecken positionierbar.
2) Es werden alle Devices "slave pointer" abgefragt.
3) Korrektur: Falls man ein Fenster erst gegen den linken und dann gegen den oberen Rand schiebt, wird in den o.g. Versionen das Fenster trotzdem links ausgerichtet.
4) Man benötigt nur einen "Compiz-Command", der an jeder gewünschten Kante (u. Ecke) aktiviert wird  (ohne angehängtem Parameter). z.B. ~/bin/compizsnap

Für Optimierungs- und Korrekturvorschläge wäre ich dankbar.
Hier ist das Script:

```

#!/bin/bash
##################################################################
#
# Angelehnt an:
# http://wwww.ubuntuforums.org/showthread.php?t=1294661
# http://linuxundich.de/de/ubuntu/aero-snap-mit-gnome-und-compiz/
#
##################################################################

DEVICES=`xinput -list | grep "slave  pointer" | grep -iv "virtual" | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `
DEVICE_ARRAY=($DEVICES)

DX=2
DY=42
WIDTH=$(xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x')
HEIGHT=$(xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p)
WIDTH=$((WIDTH+1-1))    #Damit Leerzeichen in WIDTH u. HEIGHT wegfallen... Geht bestimmt "schöner"
HEIGHT=$((HEIGHT+1-1))
HWIDTH=$(($WIDTH/2-$DX))
HHEIGHT=$(($HEIGHT/2-$DY))
TOLERANCE=3


do_choice() {
    X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
    Y=$(xdotool getmouselocation | awk '{print $2}' | cut -d : -f 2)
    #Horizontal
    C=0    #center
    if [ $X -le $TOLERANCE ]; then
        C=1    #left
    fi
    if [ $X -ge $(($WIDTH-$TOLERANCE)) ]; then
        C=2    #right
    fi
    #Vertikal
    if [ $Y -le $TOLERANCE ]; then
        C=$((C+3))    #top
    fi
    if [ $Y -ge $(($HEIGHT-$TOLERANCE)) ]; then
        C=$((C+6))    #bottom
    fi

    case $C in
    # 0) center
    1) wmctrl -r :ACTIVE: -b remove,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HWIDTH,0 ;;             #left
    2) wmctrl -r :ACTIVE: -b remove,maximized_horz && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$((HWIDTH+DX)),0,$HWIDTH,0 ;;     #right
    3) wmctrl -r :ACTIVE: -b remove,maximized_vert && wmctrl -r :ACTIVE: -b add,maximized_horz && wmctrl -r :ACTIVE: -e 0,0,0,0,$HHEIGHT ;;            #top 
    6) wmctrl -r :ACTIVE: -b remove,maximized_vert && wmctrl -r :ACTIVE: -b add,maximized_horz && wmctrl -r :ACTIVE: -e 0,0,$((HHEIGHT+DY)),$WIDTH,$HHEIGHT ;; #bottom
    4) wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,0,0,$HWIDTH,$HHEIGHT ;;                     #topleft
    5) wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,$((HWIDTH+DX)),0,$HWIDTH,$HHEIGHT ;;                 #topright
    7) wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,0,$((HHEIGHT+DY)),$HWIDTH,$HHEIGHT ;;                 #bottomleft
    8) wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,$((HWIDTH+DX)),$((HHEIGHT+DY)),$HWIDTH,$HHEIGHT ;;         #bottomright 
    esac
}


#Ermittlem, ob Button gedrückt ist
DOWN=0
for i in ${!DEVICE_ARRAY[@]}
do
    if [ `xinput --query-state ${DEVICE_ARRAY[i]} | grep down` ]; then
        DOWN=1
    fi
done

#Button gerückt?
if  [ $DOWN -gt 0 ]; then
    #Prüfe solange, bis Button losgelassen wurde...
    while [ $DOWN -gt 0 ]
    do 
        DOWN=0
        for i in ${!DEVICE_ARRAY[@]}
        do
            if [ `xinput --query-state ${DEVICE_ARRAY[i]} | grep down` ];then
                DOWN=1
            fi
        done
    done
    #...dann nehme Aktionen vor.
    do_choice
fi

```

---

### Post by plafuro on 2011-03-06
Hi everyone!

As the last script on [this thread]("http://ubuntuforums.org/showthread.php?t=1294661") didn't quite cut it for me (working on several screens here), I made some additions to it (became kind of a monster :P)... Maybe other people find it useful.

**Big Thanks to raving** for giving me a good basis to start from!

@raving: Ich hoffe das ist ok für dich!! Ich wäre auch für Verbesserungen, Kritik und mögliche Zusammenarbeit dankbar!! :)

-----

**BIG BOLD DISCLAIMER: This is my first serious attempt to bash scripting, so it may not be beautiful or structured and MANY things could be done better. Just share your thoughts and we will together improve the script!! Oh, and of course you use it on your own resposibility :)**

So now the script will work on **multiple displays** with multiple screens, and will provide f**eedback to the user** of the future position of the window through compiz's firepaint. It's not the classiest solution to it, but was the first resource i had at hand when building this (if anyone has a suggestion on how to draw rectangles easily from a bash script with no further dependencies, let me know!). You can adjust the effect with ccsm.

At the moment the script is configured so that the upper and left corner of side X react exactly the same as the action for side X itself, and the center of the screen just aborts any operation (you can, however, while you still hold your mouse button, still select a sector of the screen to resize your window). As this is based on raving's code, all areas in the screen could be configured to perform a different action.

**Keeping the name of the script as compizconfig is important!!** As moving the mouse to a different edge of the window could trigger different copies of it, I tried to make the script aware of this fact -**based on the filename**.

TL;DR Some improvements made. Here is the code, hope you enjoy it :P


```

#!/bin/bash
#####################################################################
#
# Based on:
# http://wwww.ubuntuforums.org/showthread.php?t=1294661
# http://linuxundich.de/de/ubuntu/aero-snap-mit-gnome-und-compiz/
#
# Extended by plafuro (ubuntuforums) on 2011/3/6
#	- Now it also works on any screen of any display
#	- Particles used for feedback to the user 
#	  (Needs compiz and firepaint plugin, adjust firepaint settings
#	  for desired effect). A better way of drawing this (i.e. with
#	  primitives) is very welcome!.
#		
######################################################################

## Holding the mouse next to the edge may trigger several copies 
## we will try to avoid that

if [ $(echo `ps -ef |grep -c compizsnap.sh`) -gt 5 ]; then
exit
fi

### Store all pointer devices in an array

DEVICES=`xinput -list | grep "slave  pointer" | grep -iv "virtual" | grep id= | sed 's:.*id=\([0-9]*\).*:\1:' `
DEVICE_ARRAY=($DEVICES)
DX=2
DY=42

### On which screen are we? 
### This will allow the script to work for all screens on the current display

THISSCREEN=$(echo $DISPLAY  | cut -f 2 -d '.')
THISSCREEN=$(($THISSCREEN+1))
XINFOSTR=$(xdpyinfo -display $DISPLAY |grep 'dimensions:' | sed -n ''$THISSCREEN'p')

### General screen information
### Tolerance can be adjusted based on user preference 

WIDTH=$(echo $XINFOSTR | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x')
HEIGHT=$(echo $XINFOSTR | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 2 -d 'x' | cut -f 1 -d p)
WIDTH=$(($WIDTH+1-1))    #Damit Leerzeichen in WIDTH u. HEIGHT wegfallen... Geht bestimmt "schöner"
HEIGHT=$(($HEIGHT+1-1))
HWIDTH=$(($WIDTH/2-$DX))
HHEIGHT=$(($HEIGHT/2-$DY))
VTOLERANCE=$(($HEIGHT/5))
HTOLERANCE=$(($WIDTH/5))
XROOT=$(xwininfo -root | grep id: | awk '{ print $4 }')

### Position of the mouse
SECTOR=0

### Coordenates for effects
Particle1X=0
Particle2X=0
Particle3X=0
Particle4X=0
Particle1Y=0
Particle2Y=0
Particle3Y=0
Particle4Y=0
NEWMOUSEPOSITION=0
OLDMOUSEPOSITION=0


### The tolerance can be adjusted for a better recognition of the
### screen sector. This works well on 1280x1024 and 1920x1080

VTOLERANCE=$(($HEIGHT/5))
HTOLERANCE=$(($WIDTH/5))


##############################################################
### mousePosition
### This will store mouse position in the screen 
### as a sector (upperleft, upperright, top, bottom, etc)
##############################################################

mousePosition(){

    X=$(xdotool getmouselocation | awk '{print $1}' | cut -d : -f 2)
    Y=$(xdotool getmouselocation | awk '{print $2}' | cut -d : -f 2)

    TEMP=0
    #Horizontal
    if [ $X -lt $(($HWIDTH-$HTOLERANCE)) ]; then
        SECTOR=1    					#left
	TEMP=1
    fi

    if [ $X -gt $(($HWIDTH+$HTOLERANCE)) ]; then
        SECTOR=2    					#right
	TEMP=1
    fi

    #Vertikal
    if [ $Y -lt $(($HHEIGHT-$VTOLERANCE)) ]; then
        SECTOR=$((C+3))    				#top
	TEMP=1
    fi 

    if [ $Y -gt $(($HHEIGHT+$VTOLERANCE)) ]; then
        SECTOR=$((C+6))    				#bottom
	TEMP=1
    fi

    if [ $TEMP -lt 1  ];then
	SECTOR=0					#center
    fi

    NEWMOUSEPOSITION=$SECTOR

    case $SECTOR in
    0)  #CENTER
	particlesCenter		;;
    3)  #TOP
	particlesTop		;;   
    1)  #LEFT
	particlesLeft		;;   
    2)  #RIGHT
	particlesRight		;;         
    6)  #BOTTOM
	particlesBottom		;;   
    4)  #UPPERLEFT
	particlesUpperLeft	;;   
    5)  #UPPERRIGHT
	particlesUpperRight     ;;   
    7)  #LOWERLEFT
	particlesLowerLeft      ;;   
    8)  #LOWERRIGHT
	particlesLowerRight     ;;   
    esac

}

########################################################################
### do_SECTOR
### This function triggers the action corresponding to a certain sector
########################################################################

do_Sector() {

    case $SECTOR in
    0) do_center     ;;
    3) do_top	     ;;   
    1) do_left       ;;
    2) do_right      ;;       
    6) do_bottom     ;;
    4) do_upperleft  ;;
    5) do_upperright ;;
    7) do_lowerleft  ;;
    8) do_lowerright ;;
    esac
}

##########################################################################
### particlesXXX
### Particle positions for the different sectors in the screen/behaviours
##########################################################################

particlesTop(){
	
	#Particle1X=0
	#Particle1Y=0

	#Particle2X=0
	#Particle2Y=$WIDTH

	#Particle3X=0
	#Particle3Y=$HHEIGHT

	#Particle4X=$WIDTH
	#Particle4Y=$HHEIGHT

	particlesFullScreen
}


particlesBottom(){


	Particle1X=0
	Particle1Y=$((HHEIGHT+DY))
	Particle2X=$WIDTH
	Particle2Y=$((HHEIGHT+DY))
	Particle3X=0
	Particle3Y=$HEIGHT
	Particle4X=$WIDTH
	Particle4Y=$HEIGHT

}

particlesLeft(){

	Particle1X=0
	Particle1Y=0

	Particle2X=$HWIDTH
	Particle2Y=0

	Particle3X=0
	Particle3Y=$HEIGHT

	Particle4X=$HWIDTH
	Particle4Y=$HEIGHT


}

particlesRight(){


	Particle1X=$HWIDTH
	Particle1Y=0

	Particle2X=$WIDTH
	Particle2Y=0

	Particle3X=$HWIDTH
	Particle4X=$WIDTH
	Particle3Y=$HEIGHT
	Particle4Y=$HEIGHT

}

particlesUpperRight(){

particlesRight

}

particlesUpperLeft(){

particlesLeft

}


particlesLowerRight(){

particlesRight

}

particlesLowerLeft(){

particlesLeft

}

particlesFullScreen(){


	Particle1X=0
	Particle1Y=0

	Particle2X=$WIDTH
	Particle2Y=0

	Particle3X=0
	Particle4X=$WIDTH
	Particle3Y=$HEIGHT
	Particle4Y=$HEIGHT

}

particlesCenter(){

clearParticles
	Particle1X=0
	Particle1Y=0
	Particle2X=0
	Particle2Y=0
	Particle3X=0
	Particle4X=0
	Particle3Y=0
	Particle4Y=0

}

###############################################################
### do_XXX
### Actions for the different sectors in the screen/behaviours
###############################################################


do_top(){

#wmctrl -r :ACTIVE: -b remove,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HHEIGHT
do_FullScreen
}

do_bottom(){
wmctrl -r :ACTIVE: -b remove,maximized_vert & wmctrl -r :ACTIVE: -e 0,0,$((HHEIGHT+DY)),$WIDTH,$HHEIGHT

}

do_right(){
wmctrl -r :ACTIVE: -b remove,maximized_horz & wmctrl -r :ACTIVE: -b add,maximized_vert & wmctrl -r :ACTIVE: -e 0,$((HWIDTH+DX)),0,$HWIDTH,0

}


do_left(){

wmctrl -r :ACTIVE: -b remove,maximized_horz & wmctrl -r :ACTIVE: -b add,maximized_vert & wmctrl -r :ACTIVE: -e 0,0,0,$HWIDTH,0

}


do_upperleft(){

do_left

}


do_lowerleft(){

do_left

}


do_upperright(){

do_right

}


do_lowerright(){

do_right

}

do_center(){

clearParticles

}

do_FullScreen(){

wmctrl -r :ACTIVE: -b add,maximized_vert & wmctrl -r :ACTIVE: -b add,maximized_horz

}

####################################################################
### createXXX and clearParticles
### These funcions are meant for section previsualisation purposes,
### not really needed, but wanted to give the user some feedback 
### on what will happen if mouse button is released
####################################################################

createSingleParticle(){

dbus-send --type=method_call --dest=org.freedesktop.compiz/org/freedesktop/compiz/dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/firepaint/allscreens/add_particle org.freedesktop.compiz.activate string:'root' int32:$XROOT string:'x' double:$1 string:'y' double:$2

}

createParticles(){

## For the sake of performance we will avoid drawing along the x axis 
## if the line to draw is at the very top or the very bottom

if [ $Particle1Y -gt 0 ]; then
createParticleLineX $Particle1X $Particle2X $Particle1Y 
fi

if [ $Particle3Y -lt $HEIGHT ]; then
createParticleLineX $Particle3X $Particle4X $Particle3Y 
fi

createParticleLineY $Particle2Y $Particle3Y $Particle2X 
createParticleLineY $Particle1Y $Particle3Y $Particle1X

}

createParticleLineY(){

for (( i=$1; i<$2; i=$i+40 )) 
do

createSingleParticle $3 $i

done

}

createParticleLineX(){


for (( i=$1; i<$2; i=$i+40)) 
do

createSingleParticle $i $3

done

}

clearParticles(){

dbus-send --type=method_call --dest=org.freedesktop.compiz/org/freedesktop/compiz/dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/firepaint/allscreens/clear_key org.freedesktop.compiz.activate string:'root' int32:$XROOT

}

##############################################################
### "Main" process
##############################################################

#Ermittlem, ob Button gedrückt ist || Check for button being pressed down
DOWN=0
for i in ${!DEVICE_ARRAY[@]}
do
    if [ `xinput --query-state ${DEVICE_ARRAY[i]} | grep down` ]; then
        DOWN=1
    fi
done

## Button gerückt?  || Is the button pressed?
if  [ $DOWN -gt 0 ]; then

    mousePosition
    createParticles
    OLDMOUSEPOSITION=$NEWMOUSEPOSITION			    ## Before starting the loop, save current mouse position

    ## Prüfe solange, bis Button losgelassen wurde... || Wait until button is released
    
    while [ $DOWN -gt 0 ]    
    do 

	mousePosition 					    ## Store mouse position

	if [ $NEWMOUSEPOSITION != $OLDMOUSEPOSITION ]; then ## If the mouse has moved, clear and redraw
	   clearParticles
	   createParticles	
	fi
	
        
	OLDMOUSEPOSITION=$NEWMOUSEPOSITION
        DOWN=0

        for i in ${!DEVICE_ARRAY[@]}
        do
            if [ `xinput --query-state ${DEVICE_ARRAY[i]} | grep down` ];then
                DOWN=1
		
            fi
        done

    done   
    ## ...dann nehme Aktionen vor.  || When the mouse is released, clear and resize the window
    clearParticles
    do_Sector
fi

```

---

### Post by s-p-n on 2011-03-22
I've never contributed to Ubuntu before, and never coded in bash (or any shell) language before today. If I am misinformed, used bad practice, or if it doesn't work for your laptop/sketch pad/tablet PC/iPad/whatHaveYou, PLEASE forgive me, and if you know it, post the info that can help me improve it. 

Such as the name of the device (IE: Microsoft Mouse/Laptop Touchpad/iPad touchscreen [Anyone got Ubuntu on their iPad? :P]) along with the result of this command in the terminal:
```

xinput list

```Regardless of my shell script savvy, I do know my way around a couple handfuls of other programming/scripting languages- - And was surprised at myself for not knowing BASH prior to reading this thread.

So I wrote this because I noticed all of the other bash scripts ran loops without any delays, which ran my dual-core, hyper-threaded, Over-Clocked processor up to around 60%-80% from a very unsteady 0%-25%. 

That's really unnecessary- it's a snap feature- and a few milliseconds delay will steady out the processor nicely. 

I took gotsanity's bash script which automatically gets the pointer by seeing which one is being pressed (which, correct me if I'm wrong, should always work? Or do I have to add support for touch-pads, too?)

I didn't want to use the "grid" thing.. At one point I did but couldn't get it to work exactly right, and it didn't add anything special to what I already had.. I don't care about the corner ones.

It differs a little tho- because that loop runs as a stand-alone. I re-coded it to use much less nesting (conditions/loops inside each other).

So- all in all, it's the same- but with a few efficiency improvements, and a little bit easier tutorial to install (combined into one single script).

I also added a comment for just about every line.. So anyone developing on this script shouldn't have any problems figuring it out.

So.... Let's get started! :p

1.) Open a Terminal

2.) Install compiz **wmctrl**: (Window Management Control), and the settings manager.
```

sudo apt-get install compizconfig-settings-manager wmctrl

```3.) Create & Enter ~/.scripts directory:
```

cd 
mkdir .scripts
cd .scripts
nautilus ~/.scripts

```4.) While inside "~/.scripts/", create a file named "ubuntu-snap" and paste this code in it; save it.
```

#!/bin/bash

#
# CREDITS: gotsanity, s-p-n, others from http://ubuntuforums.org/showthread.php?t=1294661
# 

# How long to wait for mouse release each iteration
delay=0.05 # you can set this to whatever you want (in seconds)
#default delay is 0.05 seconds (50ms)


# ----- Don't edit below this line unless you know what you are doing.


# Create an array of available "slave pointer" flagged input devices
#--# (hopefully, all availabe mice)
IDs=( $(xinput list | grep "slave  pointer" | sed s/".*id=\([0-9]*\).*"/\\1/) )

# Cycle through all "items" in the IDs array
#--# (read above for info on what IDS is)
for mouse in ${IDs
[*]}
do
    # If this is true, we should have the correct pointer
    if ( /usr/bin/X11/xinput --query-state $mouse | grep down )
    then
        # Found the right mouse, now break out of this loop
        break
    fi
done


# Attempt to set a width & half
width=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`


# while the mouse is down
while (/usr/bin/X11/xinput --query-state $mouse | grep down)
do
    # (sleeping each iteration results in much less overhead CPU)
    sleep $delay
   
    # Waiting for a release..
    continue
done

#left function
left() {
    # condition for if() statement
    if [ "$(/usr/bin/X11/xinput --query-state $mouse | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -le 10 ]
    then
        # snap window to the left half of the screen
        wmctrl -r :ACTIVE: -e 0,0,0,$(($width/2)),-1
   
        # maximize vertically (So height can revert back to what it was)
        wmctrl -r :ACTIVE: -b add,maximized_vert
    fi
}

#right function
right() {
    # condition for if() statement
    if [ "$(/usr/bin/X11/xinput --query-state $mouse | grep "valuator\[0\]=." | sed s/"valuator\[0\]="//)" -ge $(($width-10)) ]
    then
        # Generate HALF variable so we don't have to call this division twice..
        half=$(($width/2))
   
        # snap window to the right half of the screen
        wmctrl -r :ACTIVE: -e 0,$half,0,$half,-1
   
        # maximize vertically (So height can revert back to what it was)
        wmctrl -r :ACTIVE: -b add,maximized_vert
    fi
}

#maximize function
maximize() {
    # condition for if() statement
    if [ "$(/usr/bin/X11/xinput --query-state $mouse | grep "valuator\[1\]=." | sed s/"valuator\[1\]="//)" -le 10 ]
    then
        # snap window to maximized
        wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
    fi
}
not

# $1 is the first command-line argument (next to $0, which is the filename)
#--# Ex: bash $0 $1. So $0 must be the filename. We're not starting to count with 1, as expected ;)
#-- --# If you run the command "bash ~/.scripts/ubuntu-snap left" the left function will run
case $1 in
    'left') left ;;
    'right') right ;;
    'maximize') maximize ;;
esac

```5.) Now open up CompizConfig Settings Manager (CCSM) By going to System->Preferences->CompizConfig Settings Manager
or (if you have Gnomenu) by searching "CompizConfig"

6.) Click on (and enable) "Commands" and type (or c&p) these 3 commands (0, 1, 2):
```

bash ~/.scripts/ubuntu-snap left
bash ~/.scripts/ubuntu-snap right
bash ~/.scripts/ubuntu-snap top

```7.) (While still in "Commands" section) Click on the "Edge Bindings" tab.
8.) Set the first 3 edge bindings (0, 1, 2) to "Left", "Right", and "Top"

You should now have an Ubuntu "snap" feature.

Note that I do this in courtesy of your CPUs, as all the scripts I've tested (and I looked at a few that appeared to) run up my CPU. 

Therefore, I've used a sleep statement to avoid this. 

Depending on your CPU (mine doesn't even quite "max out" with the "while(waiting) continue"), but it's also brand new, 3.5Ghz via OC, and hyper-threaded.. 

With that said, you might want to set the delay higher (for better performance), or lower (for quicker snap). I chose 50ms because you won't even notice the difference from before.. unless your CPU was overloading, in which case it'll be much more responsive. ;) If your computer is STILL using excess wanted CPU because of this script, you should try increasing the delay to a quarter second (.25 or 250ms). Adjust higher as needed, lower as wanted, 0 to defeat the purpose :o.

As is, for me, the 50ms pause isn't noticeable for the snap duration or the CPU usage.

:popcorn: 

If anyone wants to add the corner bindings, please continue the development
):P

Edit: Next, I want to add a shading/overlay on the desktop to signal where the window is going to snap & resize to, and temporarily hide the window. Like on Windows 7, it'll make the window invisible and show an outline of where the window is going to be when you release the mouse button.

Also, I want to assemble all the parts of this tutorial to install via a single script. (It can be a .deb package, a tar.gz, or a shell script- something that's easy.. like a one-click install)

Problem is, I don't know where/how to manipulate the window and desktop in such a way to hide the window and display a shaded box on the desktop.. And I don't know how to execute an "apt-get" in a bash script, or exactly the right way to dynamically add compiz commands & bindings.

---

### Post by gpwil1 on 2011-03-28
> **s-p-n said:**
> 
Problem is, I don't know where/how to manipulate the window and desktop in such a way to hide the window and display a shaded box on the desktop.. And I don't know how to execute an "apt-get" in a bash script, or exactly the right way to dynamically add compiz commands & bindings.


Check my previous post to see how to automate the compiz commands and bindings.

---

### Post by spaceporker on 2011-04-03
s-p-n, your script is awesome. I was using a grid script before and it was pretty unreliable. Yours is fast, responsive, and the windows go back to their original size which is sweet.

I've had just two problems with it.
1. Your third compiz command (command 2) says top, when it should say maximize, or it won't work.
2. The active window is snapped when my mouse goes to any of the edge-binding areas, even when I am not dragging the window there. 

Other than those things, I really like your script.

---

### Post by JBauerIV on 2011-05-04
> **plafuro said:**
> Hi everyone!

As the last script on [this thread]("http://ubuntuforums.org/showthread.php?t=1294661") didn't quite cut it for me (working on several screens here), I made some additions to it (became kind of a monster :P)... Maybe other people find it useful.



I've tried everything to get this to work with my dual-monitor setup, and I'm hitting dead ends. Perhaps I'm installing the scripts wrong?

I pasted the code into a file named compizsnap.sh in ~/.scripts, set 'bash ~/.scripts/compizsnap.sh' without quotes as command 0 in ccsm, and set every edge binding for command 0. No change. I have firepaint installed and activated as well. Help me out!

EDIT: I installed xdotool and now it's working I believe, but I can't get it to snap to only the right half of my right monitor, for example. It fills up the entire right screen, the entire left screen, or the bottom half of the screen across both monitors. I believe the problem is with "echo $DISPLAY  | cut -f 2 -d '.'". Since I am using TwinView, this will return 0 no matter which monitor I run the command on. Any ideas?

---

### Post by sam1948 on 2011-05-15
ubuntu 11.04 (((:
congreg's 
[http://www.youtube.com/watch?v=zPd8yq-IHvI](http://www.youtube.com/watch?v=zPd8yq-IHvI)

---

### Post by opodaniel on 2011-07-30
Hello
I just change my laptop, I have an Soni Vaio with Sandy Bridge Intel graphic card and AMD Radeon&#8482; HD 6630M . The problem is that aero functions are not working at this moment so I need to manual arrange 2 windows in order to see them side by side. 
I installed Ubuntu 11.04 Alternative and kept my /home from the other laptop. Normally this function comes by default on 11.04 and I don't know where the problem is and how to fix it. 
Help would be greatly appreciated.

---

### Post by sam1948 on 2011-08-01
> **opodaniel said:**
> Hello
I just change my laptop, I have an Soni Vaio with Sandy Bridge Intel graphic card and AMD Radeon™ HD 6630M . The problem is that aero functions are not working at this moment so I need to manual arrange 2 windows in order to see them side by side. 
I installed Ubuntu 11.04 Alternative and kept my /home from the other laptop. Normally this function comes by default on 11.04 and I don't know where the problem is and how to fix it. 
Help would be greatly appreciated.

hi,
this is one long thread and it dealt with previous ubuntu versions.
I would highly recommend to open a new thread and someone who had the same problem will notice.
br

---

### Post by opodaniel on 2011-08-02
Thanks for your reply. I found the problem to be the radeon video card . The drivers are far from being perfect since the card is new arrived on the market... I am talking about Radeon 6630M. Since the drivers were unfit, all effects were disabled hence the problems. I couldn't watch a movie with my laptop :) .
I manage to block the Radeon card and I use now the Intel integrated graphic card ( Sandy Bridge CPU).

---

### Post by looniichoon on 2011-08-19
Hi folks,

I realise this thread is about compiz snap, however I'm a keyboard junkie so don't really like moving my hand to the mouse in order to drag windows. I spent some time with Xmonad and really liked the tiling and ability to change the split size with the keyboard. This was the only feature I realised I missed in gnome. 

I therefore shamelessly grabbed the scripts from this thread and hacked them about to do some rudimentary calcs on the current state of the window and calculate what the 'next' size would go to.

The idea is that when you first run 'snap_left' it snaps to the left but taking up 2/3 of the screen. If you run it on the same window again, it goes to 1/2, then 1/3 then it maximises, then starts the cycle again. There are 4 scripts, one for each of left, right, up, down.

I thought some folks on here may appreciate it. They are all zipped in the attachment along with a file called set_snap_keys which if you run will bind the 4 commands to <Ctrl><Super>+Arrow keys.

This does not rely on compiz, they work with metacity etc too.

Enjoy.

---

### Post by dustigroove on 2011-10-18
> **looniichoon said:**
> I thought some folks on here may appreciate it. They are all zipped in the attachment along with a file called set_snap_keys which if you run will bind the 4 commands to <Ctrl><Super>+Arrow keys.

This does not rely on compiz, they work with metacity etc too.

Enjoy.

This is excellent for those of us not moving on to 11.04 or 11.10 for various reasons, thank you.

---

### Post by katutxakurra on 2011-11-12
What I would like to do is to add new window buttons for this. I want to have 5 window buttons, 4 arrows and an X.
Left arrow -> resizes the window to half of the screen and left
Right arrow -> resizes the window to half of the screen and right
Down arrow -> minimize window
Up arrow -> maximize window
X -> close window

Any idea of how can I do this?
Somebody else thinks that is a brilliant idea? :D

Thanks!
I use ubuntu 10.10

---

### Post by looniichoon on 2011-11-12
Yes, it is a great idea. I know it is not possible in metacity as that only supports the standard functions. It may be possible in compiz with an extension, but I don't know of one that is already available with that functionality. Sorry.

---

