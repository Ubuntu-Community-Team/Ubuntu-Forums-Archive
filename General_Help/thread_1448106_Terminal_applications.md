---
title: "Terminal applications"
date: 2010-04-06
forum: General Help
---

### Post by J V on 2010-04-06
What do people use to run multiple applications in one terminal?

Thinking of turning my GUI into a big terminal with openbox on top and was thinking, where would I find a command-line timer tool?

And if I only had one terminal, how would I switch between applications? A 5 hour timer isn't nice if it locks up the terminal for 5 hours...

---

### Post by new_tolinux on 2010-04-06
try this:
```
somecommand &
```
source: [http://ubuntuforums.org/showthread.php?t=1438512](http://ubuntuforums.org/showthread.php?t=1438512)

---

### Post by nothingspecial on 2010-04-06
```
sudo apt-get install byobu
```

```
byobu
```

Press F2 to get a new terminal (you can see them listed at the bottom) make as many as you like.

F3 and F4 to navigate back and forth between them

Ctrl A then K to close the terminal you are looking at.

Option 2

```
sudo apt-get install dvtm
```

```
dvtm
```

Ctrl G then C to split the screen

I like to make 4 windows then press Ctrl G then G to make them a nice grid.

Use Ctrl G then J and Ctrl G then K to navigate between them.

Use them together Millions and Millions of terminals in one terminal - cool eh?

---

### Post by spibou on 2010-04-06
> **J V said:**
> What do people use to run multiple applications in one terminal?
GNU screen.

---

### Post by J V on 2010-04-06
"Ctrl G then J and Ctrl G then K"

New sig for whoever wants ;P

I know about starting a command in the background, but how do I pull it back into focus, any way to get a nice little menu with running commands?

Also, is it possible to put something in the background after you started it? (ctrl z was something I remember but I think that stopped the proccess while it put it in the background)

special, I'm looking for something that will fit into my desktop: I don't want it in a window, I want the entire lower layer of the screen to consist of this terminal... As if there is a gird of 4 of them but the desktop is made of them, exit won't do anything, no panels or nautilus desktop etc, just a big terminal with windows on top... Possible?

Edit: Spibou, would that look/behave like [http://polishlinux.org/wp-content/uploads/2007/04/screen-konsole2.png](http://polishlinux.org/wp-content/uploads/2007/04/screen-konsole2.png) or [http://daveg.outer-rim.org/images/screenshots/screenshot-darkenergy-20060111.png](http://daveg.outer-rim.org/images/screenshots/screenshot-darkenergy-20060111.png) ? Possible to make it run on startup (And stop nautilus making desktop there)?

---

### Post by nothingspecial on 2010-04-06
> **spibou said:**
> GNU screen.

I should have mentioned that byobu is a pimped up version of screen.

---

### Post by J V on 2010-04-06
You can click to activate a terminal right? I don't want to have to tab between them ;)

---

### Post by nothingspecial on 2010-04-06
> **J V said:**
> 
special, I'm looking for something that will fit into my desktop: I don't want it in a window, I want the entire lower layer of the screen to consist of this terminal... As if there is a gird of 4 of them but the desktop is made of them, exit won't do anything, no panels or nautilus desktop etc, just a big terminal with windows on top... Possible?

Edit: Spibou, would that look/behave like [http://polishlinux.org/wp-content/uploads/2007/04/screen-konsole2.png](http://polishlinux.org/wp-content/uploads/2007/04/screen-konsole2.png) or [http://daveg.outer-rim.org/images/screenshots/screenshot-darkenergy-20060111.png](http://daveg.outer-rim.org/images/screenshots/screenshot-darkenergy-20060111.png) ? Possible to make it run on startup (And stop nautilus making desktop there)?

The easiest way would be to use the compiz window rules plug in.

Open a terminal, then launch byobu. Then type ```
xprop WM_NAME | cut -d\" -f2
```

Your pointer will turn into a + place it over the terminal then click. That will give you the title of a terminal running byobu.

Then set any window with that title to always appear below any other windows and appear on all desktops. I can`t remember exactly how to do it but it`s something like putting

title=window_title_you_just_discovered in the corresponding boxes.

Then set your gnome terminal profile to have no scroll bar and have a black background and however you want it to look.

Then have a command in your start up applications something like ```
gnome-terminal --geometry=??x??+0+0 -x byobu
```

The ? signify your own full screen geometry which is how many characters vertical and horizontal a fullscreen terminal is.

I know that`s all abit vague but it should get you started.

I think dvtm has mouse support but if your working in the terminal your fingers are on the keyboard anyway ;)

---

### Post by J V on 2010-04-06
Ahh but I don't want to be on compiz, its given me plenty of grief and while I love scale the cube and wobbly windows (The functional ones) I will be on openbox when I implement this terminal system... (btw, anything like scale on openbox?)

It would also be nice (But not necessary to be able to click the intersection between the terminals and drag to resize them (GtkPaned for example)

---

### Post by nothingspecial on 2010-04-06
> **J V said:**
> Ahh but I don't want to be on compiz, its given me plenty of grief and while I love scale the cube and wobbly windows (The functional ones) I will be on openbox when I implement this terminal system... (btw, anything like scale on openbox?)


Then happy obconf editing sir.

It is possible to set window rules in your obconf. What you want is to have that terminal below everything else and on all workspaces, and have no decoration, all of which I`m pretty sure is doable. I`ve not obconfed in a while.

---

### Post by J V on 2010-04-06
I'll no doubt be back on the 29th with this issue, thanks 

Edit: Will probly go with RC, don't want 1kb/s ;)

Ok, I tried screen/byobu and its freakin me out, the insane amount of commands you need... I only want a bunch of gnome-terminals on screen ffs! I think I'll have to do that because without the mouse having to ctrl+a tab through 4 windows is too complicated... it also doesn't let me scroll through man pages by wheel...

---

### Post by spibou on 2010-04-06
> **J V said:**
> 
I know about starting a command in the background, but how do I pull it back into focus, any way to get a nice little menu with running commands?

Also, is it possible to put something in the background after you started it? (ctrl z was something I remember but I think that stopped the proccess while it put it in the background)
After pressing ctrl-z you type```
jobs
```and you get a list of jobs. You type```
bg %1
```to put job 1 in the background or whichever job you want.

> special, I'm looking for something that will fit into my desktop: I don't want it in a window, I want the entire lower layer of the screen to consist of this terminal... As if there is a gird of 4 of them but the desktop is made of them, exit won't do anything, no panels or nautilus desktop etc, just a big terminal with windows on top... Possible?

I'm not sure what you're looking for here. For example what would the top of the screen have ?

> Edit: Spibou, would that look/behave like [http://polishlinux.org/wp-content/uploads/2007/04/screen-konsole2.png](http://polishlinux.org/wp-content/uploads/2007/04/screen-konsole2.png) or [http://daveg.outer-rim.org/images/screenshots/screenshot-darkenergy-20060111.png](http://daveg.outer-rim.org/images/screenshots/screenshot-darkenergy-20060111.png) ? Possible to make it run on startup (And stop nautilus making desktop there)?
The first photo shows what looks like a windows manager running on top of a terminal emulator. GNU screen on its own won't divide the terminal emulator window between different processes (as far as I know) , a process running on top of GNU screen occupies the whole window of the terminal emulator and GNU screen simply gives you a way to switch between processes. So what you need is a window manager running on top of a terminal emulator. I've never user one myself but dvtm has been mentioned already. I have a vague recollection of seeing another once but I couldn't find it in my bookmarks.

Having a background image as in your second photo is a separate issue from what we're talking about here. If the terminal emulator you are using supports background images then GNU screen won't affect that , I don't know about dvtm but I'm guessing not.

---

### Post by spibou on 2010-04-06
> **J V said:**
> 
Ok, I tried screen/byobu and its freakin me out, the insane amount of commands you need... I only want a bunch of gnome-terminals on screen ffs! I think I'll have to do that because without the mouse having to ctrl+a tab through 4 windows is too complicated... it also doesn't let me scroll through man pages by wheel...
I don't know about byobu but with GNU screen you can get by with just 2 commands , ctrl+a c to start a new process and ctrl-a <number> to go to the process you want. I wouldn't call this an insane amount of commands.

---

### Post by spibou on 2010-04-06
> **spibou said:**
> GNU screen on its own won't divide the terminal emulator window between different processes (as far as I know) , a process running on top of GNU screen occupies the whole window of the terminal emulator and GNU screen simply gives you a way to switch between processes.

According to [Wikipedia](http://en.wikipedia.org/wiki/GNU_Screen) I was mistaken , GNU screen does allow you to split the screen in half.

> So what you need is a window manager running on top of a terminal emulator. I've never user one myself but dvtm has been mentioned already. I have a vague recollection of seeing another once but I couldn't find it in my bookmarks.
[Wikipedia](http://en.wikipedia.org/wiki/GNU_Screen#Other_terminal_multiplexers) again to the rescue. What I was vaguely remembering was [twin](http://sourceforge.net/projects/twin/).

---

### Post by J V on 2010-04-06
Yes I want a terminal emulator that:

* Runs under all other windows
* Replaces the desktop (Don't need it really)
* Contains multiple terminals, preferably resize-able by mouse
* Doesn't disappear on show desktop (So ctrl d removes all windows but the terminals)
* Starts up on login
* Ignores the exit command
* Runs on all workspaces

Besides that, are there any good terminal applications to replace the clock, notification area etc? Or should I just keep a panel in there somewhere?

Edit: Terminator has fulfilled a number of these, seems to be the way to go...

---

### Post by nothingspecial on 2010-04-06
Just so we are clear byobu is GNU screen with some added functionality.

If you run byobu (screen) and press F9 a menu comes up which allows you to customize your toolbar.

In mine on my netbook you can see time, date, ipaddress, disk usage, uptime, processors and some other stuff.

[ATTACH]152516[/ATTACH]

You can see in the second screenshot, what dvtm looks like, although on a netbook it`s not ideal because of the limited screen space. If you look at the "task bar" I`ve got four shells open within screen and dvtm on the current one. Then I`ve got cmus (music player) and mc (midnight commander - cli file browser) in the top 2 windows. man cmus in the bottom right and my working shell in the bottom left.

[ATTACH]152517[/ATTACH]



Watch out, it can get awfully confusing with all these terminals open, especially if you are logged on to multiple computers in different ones. I`m forever rebooting my server when I really mean the pc.

---

### Post by J V on 2010-04-06
Don't have any other computers to ssh into :)

All I should need is 3 or 4 windows, no tabs, so that should be fine for me.

I assume openbox has a setting to disable show desktop for specific windows?

---

### Post by J V on 2010-04-06
ok, now I've installed openbox to give it a try, a few things aren't nice though...

Ctrl Alt D doesn't minimize everything any more, how do I make a script or command that will minimize all but the one window belonging to terminator?

After saying I didn't want nautilus to handle the desktop they all turned grey, I want my background!

I want terminator to stay out of the window list on my gnome-panel, how exactly do I do this?

How do I make gnome-terminal start up on login with these flags already set? (Always on the bottom, on all workspaces...)

Is there anything like the scale plugin for compiz I could get? Alt-tab sux to put it bluntly...

Alt F2 isn't opening the run dialog, and alt F1 isn't opening the menu...

Lastly, ctrl shift alt left/right won't move a window from workspace to workspace... halp? xD

---

### Post by nothingspecial on 2010-04-06
Like I said before, you are going to have to edit your rc.xml. Using obconf would be easier but you can do it in nano or whatever.

Do what I did. Find a full featured rc.xml and work from there. I found the default crunchbang one
```

<?xml version="1.0" encoding="UTF-8"?>
<openbox_config xmlns="http://openbox.org/3.4/rc">
  <resistance>
    <strength>10</strength>
    <screen_edge_strength>20</screen_edge_strength>
  </resistance>
  <focus>
    <focusNew>yes</focusNew>
    <!-- always try to focus new windows when they appear. other rules do
       apply -->
    <followMouse>no</followMouse>
    <!-- move focus to a window when you move the mouse into it -->
    <focusLast>yes</focusLast>
    <!-- focus the last used window when changing desktops, instead of the one
       under the mouse pointer. when followMouse is enabled -->
    <underMouse>no</underMouse>
    <!-- move focus under the mouse, even when the mouse is not moving -->
    <focusDelay>200</focusDelay>
    <!-- when followMouse is enabled, the mouse must be inside the window for
       this many milliseconds (1000 = 1 sec) before moving focus to it -->
    <raiseOnFocus>no</raiseOnFocus>
    <!-- when followMouse is enabled, and a window is given focus by moving the
       mouse into it, also raise the window -->
  </focus>
  <placement>
    <policy>Smart</policy>
    <!-- 'Smart' or 'UnderMouse' -->
    <center>yes</center>
    <!-- whether to place windows in the center of the free area found or
       the top left corner -->
    <monitor>Any</monitor>
  </placement>
  <theme>
    <name>CrunchBang</name>
    <titleLayout>LIMC</titleLayout>
    <!--
      avaible characters are NDSLIMC, each can occur at most once.
      N: window icon
      L: window label (AKA title).
      I: iconify
      M: maximize
      C: close
      S: shade (roll up/down)
      D: omnipresent (on all desktops).
  -->
    <keepBorder>yes</keepBorder>
    <animateIconify>yes</animateIconify>
    <font place="ActiveWindow">
      <name>sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="InactiveWindow">
      <name>sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuHeader">
      <name>sans</name>
      <size>9</size>
      <!-- font size in points -->
      <weight>normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuItem">
      <name>sans</name>
      <size>9</size>
      <!-- font size in points -->
      <weight>normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="OnScreenDisplay">
      <name>sans</name>
      <size>9</size>
      <!-- font size in points -->
      <weight>bold</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
  </theme>
  <desktops>
    <!-- this stuff is only used at startup, pagers allow you to change them
       during a session

       these are default values to use when other ones are not already set
       by other applications, or saved in your session

       use obconf if you want to change these without having to log out
       and back in -->
    <number>2</number>
    <firstdesk>1</firstdesk>
    <names>
      <name>Desktop 1</name>
      <name>Desktop 2</name>
    </names>
    <popupTime>875</popupTime>
    <!-- The number of milliseconds to show the popup for when switching
       desktops.  Set this to 0 to disable the popup. -->
  </desktops>
  <resize>
    <drawContents>yes</drawContents>
    <popupShow>Nonpixel</popupShow>
    <!-- 'Always', 'Never', or 'Nonpixel' (xterms and such) -->
    <popupPosition>Center</popupPosition>
    <!-- 'Center' or 'Top' -->
    <popupFixedPosition>
      <x>0</x>
      <y>0</y>
    </popupFixedPosition>
  </resize>
  <!-- You can reserve a portion of your screen where windows will not cover when
     they are maximized, or when they are initially placed.
     Many programs reserve space automatically, but you can use this in other
     cases. -->
  <margins>
    <top>1</top>
    <bottom>0</bottom>
    <left>0</left>
    <right>0</right>
  </margins>
  <dock>
    <position>TopLeft</position>
    <!-- (Top|Bottom)(Left|Right|)|Top|Bottom|Left|Right|Floating -->
    <floatingX>0</floatingX>
    <floatingY>0</floatingY>
    <noStrut>no</noStrut>
    <stacking>Above</stacking>
    <!-- 'Above', 'Normal', or 'Below' -->
    <direction>Vertical</direction>
    <!-- 'Vertical' or 'Horizontal' -->
    <autoHide>no</autoHide>
    <hideDelay>300</hideDelay>
    <!-- in milliseconds (1000 = 1 second) -->
    <showDelay>300</showDelay>
    <!-- in milliseconds (1000 = 1 second) -->
    <moveButton>Middle</moveButton>
    <!-- 'Left', 'Middle', 'Right' -->
  </dock>
  <keyboard>
    <chainQuitKey>C-g</chainQuitKey>
    <!-- Keybindings for desktop switching -->
    <keybind key="C-A-Left">
      <action name="DesktopLeft">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Right">
      <action name="DesktopRight">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Up">
      <action name="DesktopUp">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Down">
      <action name="DesktopDown">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Left">
      <action name="SendToDesktopLeft">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Right">
      <action name="SendToDesktopRight">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Up">
      <action name="SendToDesktopUp">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Down">
      <action name="SendToDesktopDown">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="W-F1">
      <action name="Desktop">
        <desktop>1</desktop>
      </action>
    </keybind>
    <keybind key="W-F2">
      <action name="Desktop">
        <desktop>2</desktop>
      </action>
    </keybind>
    <keybind key="W-F3">
      <action name="Desktop">
        <desktop>3</desktop>
      </action>
    </keybind>
    <keybind key="W-F4">
      <action name="Desktop">
        <desktop>4</desktop>
      </action>
    </keybind>
    <keybind key="W-d">
      <action name="ToggleShowDesktop"/>
    </keybind>
    <!-- Keybindings for windows -->
    <keybind key="A-F4">
      <action name="Close"/>
    </keybind>
    <keybind key="A-Escape">
      <action name="Lower"/>
      <action name="FocusToBottom"/>
      <action name="Unfocus"/>
    </keybind>
    <keybind key="A-space">
      <action name="ShowMenu">
        <menu>client-menu</menu>
      </action>
    </keybind>
    <keybind key="Print">
      <action name="Execute">
        <execute>scrot '%Y-%m-%d--%s_$wx$h_scrot.png' -e 'mv $f ~/images/ &amp; gpicview ~/images/$f'</execute>
      </action>
    </keybind>
    <keybind key="A-Print">
      <action name="Execute">
        <execute>scrot -d 10 '%Y-%m-%d--%s_$wx$h_scrot.png' -e 'mv $f ~/images/ &amp; gpicview ~/images/$f'</execute>
      </action>
    </keybind>
    <!-- Keybindings for window switching -->
    <keybind key="A-Tab">
      <action name="NextWindow"/>
    </keybind>
    <keybind key="A-S-Tab">
      <action name="PreviousWindow"/>
    </keybind>
    <keybind key="C-A-Tab">
      <action name="NextWindow">
        <panels>yes</panels>
        <desktop>yes</desktop>
      </action>
    </keybind>
    <!-- Keybindings for running applications -->
    <keybind key="A-F2">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Run Program</name>
        </startupnotify>
        <command>gmrun</command>
      </action>
    </keybind>
    <keybind key="A-F3">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>dmenu-bind</name>
        </startupnotify>
        <command>~/.config/dmenu/dmenu-bind.sh</command>
      </action>
    </keybind>
    <keybind key="W-f">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Thunar</name>
        </startupnotify>
        <command>thunar</command>
      </action>
    </keybind>
    <keybind key="W-t">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Terminal</name>
        </startupnotify>
        <command>terminator</command>
      </action>
    </keybind>
    <keybind key="W-w">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Web Browser</name>
        </startupnotify>
        <command>firefox</command>
      </action>
    </keybind>
    <keybind key="W-l">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Lock screen</name>
        </startupnotify>
        <command>gnome-screensaver-command -l</command>
      </action>
    </keybind>
    <keybind key="W-e">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Editor</name>
        </startupnotify>
        <command>gedit</command>
      </action>
    </keybind>
    <keybind key="W-m">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Mediaplayer</name>
        </startupnotify>
        <command>totem</command>
      </action>
    </keybind>
    <keybind key="W-v">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>xfce4-mixer</name>
        </startupnotify>
        <command>xfce4-mixer</command>
      </action>
    </keybind>
    <keybind key="W-g">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Gimp</name>
        </startupnotify>
        <command>gimp</command>
      </action>
    </keybind>
    <keybind key="W-x">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Logout</name>
        </startupnotify>
        <command>/usr/bin/openbox-logout</command>
      </action>
    </keybind>
    <keybind key="W-space">
      <action name="ShowMenu">
        <menu>root-menu</menu>
      </action>
    </keybind>
    <keybind key="A-C-q">
      <action name="ShowMenu">
        <menu>root-menu</menu>
      </action>
    </keybind>
  </keyboard>
  <mouse>
    <dragThreshold>8</dragThreshold>
    <!-- number of pixels the mouse must move before a drag begins -->
    <doubleClickTime>200</doubleClickTime>
    <!-- in milliseconds (1000 = 1 second) -->
    <screenEdgeWarpTime>400</screenEdgeWarpTime>
    <!-- Time before changing desktops when the pointer touches the edge of the
       screen while moving a window, in milliseconds (1000 = 1 second).
       Set this to 0 to disable warping -->
    <context name="Frame">
      <mousebind button="A-Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="A-Left" action="Click">
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="A-Left" action="Drag">
        <action name="Move"/>
      </mousebind>
      <mousebind button="A-Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="A-Right" action="Drag">
        <action name="Resize"/>
      </mousebind>
      <mousebind button="A-Middle" action="Press">
        <action name="Lower"/>
        <action name="FocusToBottom"/>
        <action name="Unfocus"/>
      </mousebind>
      <mousebind button="A-Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="A-Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
      <mousebind button="C-A-Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="C-A-Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
      <mousebind button="A-S-Up" action="Click">
        <action name="SendToDesktopPrevious"/>
      </mousebind>
      <mousebind button="A-S-Down" action="Click">
        <action name="SendToDesktopNext"/>
      </mousebind>
    </context>
    <context name="Titlebar">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Move"/>
      </mousebind>
      <mousebind button="Left" action="DoubleClick">
        <action name="ToggleMaximizeFull"/>
      </mousebind>
      <mousebind button="Middle" action="Press">
        <action name="Lower"/>
        <action name="FocusToBottom"/>
        <action name="Unfocus"/>
      </mousebind>
      <mousebind button="Up" action="Click">
        <action name="Shade"/>
        <action name="FocusToBottom"/>
        <action name="Unfocus"/>
        <action name="Lower"/>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="Unshade"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="ShowMenu">
          <menu>client-menu</menu>
        </action>
      </mousebind>
    </context>
    <context name="Top">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize">
          <edge>top</edge>
        </action>
      </mousebind>
    </context>
    <context name="Left">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize">
          <edge>left</edge>
        </action>
      </mousebind>
    </context>
    <context name="Right">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize">
          <edge>right</edge>
        </action>
      </mousebind>
    </context>
    <context name="Bottom">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize">
          <edge>bottom</edge>
        </action>
      </mousebind>
      <mousebind button="Middle" action="Press">
        <action name="Lower"/>
        <action name="FocusToBottom"/>
        <action name="Unfocus"/>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="ShowMenu">
          <menu>client-menu</menu>
        </action>
      </mousebind>
    </context>
    <context name="BLCorner">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize"/>
      </mousebind>
    </context>
    <context name="BRCorner">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize"/>
      </mousebind>
    </context>
    <context name="TLCorner">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize"/>
      </mousebind>
    </context>
    <context name="TRCorner">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Drag">
        <action name="Resize"/>
      </mousebind>
    </context>
    <context name="Client">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Middle" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
    </context>
    <context name="Icon">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
        <action name="ShowMenu">
          <menu>client-menu</menu>
        </action>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="ShowMenu">
          <menu>client-menu</menu>
        </action>
      </mousebind>
    </context>
    <context name="AllDesktops">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="ToggleOmnipresent"/>
      </mousebind>
    </context>
    <context name="Shade">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="ToggleShade"/>
      </mousebind>
    </context>
    <context name="Iconify">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="Iconify"/>
      </mousebind>
    </context>
    <context name="Maximize">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Middle" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="ToggleMaximizeFull"/>
      </mousebind>
      <mousebind button="Middle" action="Click">
        <action name="ToggleMaximizeVert"/>
      </mousebind>
      <mousebind button="Right" action="Click">
        <action name="ToggleMaximizeHorz"/>
      </mousebind>
    </context>
    <context name="Close">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
        <action name="Unshade"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="Close"/>
      </mousebind>
    </context>
    <context name="Desktop">
      <mousebind button="Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
      <mousebind button="A-Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="A-Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
      <mousebind button="C-A-Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="C-A-Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
    </context>
    <context name="Root">
      <!-- Menus -->
      <mousebind button="Middle" action="Press">
        <action name="ShowMenu">
          <menu>client-list-combined-menu</menu>
        </action>
      </mousebind>
      <mousebind button="Right" action="Press">
        <action name="ShowMenu">
          <menu>root-menu</menu>
        </action>
      </mousebind>
    </context>
    <context name="MoveResize">
      <mousebind button="Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
      <mousebind button="A-Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="A-Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>
    </context>
  </mouse>
  <menu>
    <!-- You can specify more than one menu file in here and they are all loaded,
       just don't make menu ids clash or, well, it'll be kind of pointless -->
    <!-- default menu file (or custom one in $HOME/.config/openbox/) -->
    <!-- system menu files on Debian systems 
    <file>/var/lib/openbox/debian-menu.xml</file>
    <file>debian-menu.xml</file> -->
    <file>menu.xml</file>
    <hideDelay>200</hideDelay>
    <middle>no</middle>
    <submenuShowDelay>100</submenuShowDelay>
    <applicationIcons>yes</applicationIcons>
  </menu>
  <applications>
    <!--
  # this is an example with comments through out. use these to make your
  # own rules, but without the comments of course.

  <application name="first element of window's WM_CLASS property (see xprop)"
              class="second element of window's WM_CLASS property (see xprop)"
               role="the window's WM_WINDOW_ROLE property (see xprop)">
  # the name or the class can be set, or both. this is used to match
  # windows when they appear. role can optionally be set as well, to
  # further restrict your matches.

  # the name, class, and role use simple wildcard matching such as those
  # used by a shell. you can use * to match any characters and ? to match
  # any single character.

  # when multiple rules match a window, they will all be applied, in the
  # order that they appear in this list


    # each element can be left out or set to 'default' to specify to not 
    # change that attribute of the window

    <decor>yes</decor>
    # enable or disable window decorations

    <shade>no</shade>
    # make the window shaded when it appears, or not

    <position>
      # the position is only used if both an x and y coordinate are provided
      # (and not set to 'default')
      <x>center</x>
      # a number like 50, or 'center' to center on screen. use a negative number
      # to start from the right (or bottom for <y>), ie -50 is 50 pixels from the
      # right edge (or bottom).
      <y>200</y>
      <monitor>1</monitor>
      # specifies the monitor in a xinerama setup.
      # 1 is the first head, or 'mouse' for wherever the mouse is
    </position>

    <focus>yes</focus>
    # if the window should try be given focus when it appears. if this is set
    # to yes it doesn't guarantee the window will be given focus. some
    # restrictions may apply, but Openbox will try to

    <desktop>1</desktop>
    # 1 is the first desktop, 'all' for all desktops

    <layer>normal</layer>
    # 'above', 'normal', or 'below'

    <iconic>no</iconic>
    # make the window iconified when it appears, or not

    <skip_pager>no</skip_pager>
    # asks to not be shown in pagers

    <skip_taskbar>no</skip_taskbar>
    # asks to not be shown in taskbars. window cycling actions will also
    # skip past such windows

    <fullscreen>yes</fullscreen>
    # make the window in fullscreen mode when it appears

    <maximized>true</maximized>
    # 'Horizontal', 'Vertical' or boolean (yes/no)
  </application>

  # end of the example
-->
    <application name="gmessage">
      <decor>no</decor>
      <shade>no</shade>
      <skip_pager>yes</skip_pager>
      <skip_taskbar>yes</skip_taskbar>
      <fullscreen>no</fullscreen>
      <maximized>no</maximized>
    </application>
  </applications>
</openbox_config>
```

You`ll have a lot to take out but at least it`s all done for you. Have a look at the keybinding section near the top, that has keybindings for showing/switching desktops etc (hint W stands for the key with the windows picture on it)

---

### Post by J V on 2010-04-06
I'll work on that tomorrow, right now I can't log in with session set to gnome/openbox (it kicks back to login screen, looks like X crashed)

---

