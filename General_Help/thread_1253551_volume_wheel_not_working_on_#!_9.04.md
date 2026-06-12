---
title: "volume wheel not working on #! 9.04"
date: 2009-08-30
forum: General Help
---

### Post by Shpongle on 2009-08-30
hey all,i installed crunchbang a couple of days ago and all is well except my volume wheel at the front of my laptop doesn't affect the volume at all, it worked on ubuntu intripid and jaunty, iv already changed my alsa-base file to be able to use the headphone jack properly , i also had to do this in ubuntu, any ideas why the wheel isnt working ,  could i perhaps use a different volume control manager?, or is it a different part of the system that handles that, any ideas?

---

### Post by Liolikas on 2009-08-30
I personally use alsamixer command in my Linux. There tons of other ways for sure.

---

### Post by tgeer43 on 2009-08-30
Based on the fact that it worked in Intrepid and Jaunty but not in Crunchbang, I'll take a guess.

Since Crunchbang is essentially a streamlined, minimalist version of Jaunty, some things had to go. Hardware support for your 'volume wheel' was probably on that list.

But the beauty of Linux is that you can probably get it working anyway. If you don't get the help that you need here, try back at the Crunchbang forums. I know they have nowhere near the traffic of these forums but they should have more expertise with this distro.

tgeer

---

### Post by Shpongle on 2009-08-30
il give it a try thanks

---

### Post by Shpongle on 2009-08-30
no it didnt work, it worked with the gnome volume applet in ubuntu but i cant install that coz its wants to install all the others packages that come with it, is there a good alternative to gnome volume applet? or something i can use instead of volwheel to manage my volume

iv already tried the crunchbang forums, thanks anyway tho

---

### Post by tgeer43 on 2009-08-30
If you are using alsa as your sound architecture (most likely) and you have the alsa-utils package installed, you can type 'alsamixer' from the command line to have a neat little volume control/mixer right there in your terminal.

tgeer

---

### Post by Shpongle on 2009-08-30
thanks but i know that, im talking about a systray applet? , because its a bit inconvenient to bring up the window and then to set it with your mouse?, especially when your used to using a wheel, the systray applet in #! is called volwheel and doesnt work the best with my hardware, i always have to manually set the volume bringing up the menu and setting it with my mouse,  the panel im using is tint2 btw

---

### Post by tgeer43 on 2009-08-30
Ok, but you didn't specify that it had to be a panel applet. In fact you said:
> "or something i can use instead of volwheel to manage my volume"Well this is still not a panel applet but you can easily remap a couple of keys to volume up, volume down, and mute. Very quick and convenient.

If you still need a panel applet, don't give up. You'll probably find what you are looking for.

tgeer

---

### Post by Shpongle on 2009-08-30
> **tgeer43 said:**
> Ok, but you didn't specify that it had to be a panel applet. In fact you said:
Well this is still not a panel applet but you can easily remap a couple of keys to volume up, volume down, and mute. Very quick and convenient.

If you still need a panel applet, don't give up. You'll probably find what you are looking for.

tgeer


sorry i should have said that, yea i have been looking into mapping the keys , il keep looking tho, thanks anyway man

---

### Post by Shpongle on 2009-08-30
ok so i ran xev in a terminal and got this output when i moved the wheel up and down


KeyRelease event, serial 36, synthetic NO, window 0x3000001,
root 0xab, subw 0x3000002, time 26530035, (41,34), root131,287),
state 0x0, keycode 123 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
XLookupString gives 0 bytes:
XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x3000001,
root 0xab, subw 0x3000002, time 26530768, (41,34), root131,287),
state 0x0, keycode 122 (keysym 0x1008ff11, XF86AudioLowerVolume), same_screen YES,
XLookupString gives 0 bytes:
XmbLookupString gives 0 bytes:
XFilterEvent returns: False

can someone please tell me how to correctly configure the wheel or explain the output , thanks

---

### Post by tgeer43 on 2009-08-30
The output from xev looks promising. The volume wheel is being recognized correctly at least.
Let's start with the easiest way:

Go to System->Preferences->Keyboard Shortcuts and see what the current shortcuts are for Volume Up and Volume Down. If they are not set to XF86AudioRaiseVolume and XF86AudioLowerVolume respectively then try clicking on the current shortcut name and when it changes to 'New shortcut...' just scroll your volume wheel in the appropriate direction. There's a good likelihood that it will pick it up and set it correctly. If so then you're good to go.

If not, we can then try xmodmap to map the scroll wheel. Even if that fails there are still alternatives but let's take it one step at a time.

tgeer

---

### Post by Shpongle on 2009-08-30
hey thanks for all the help so far i really really appreciate it, im using openbox so theres no system->preferences is there a way to access it from the terminal?, i do have an rc.xml file which i have seen keybindings in not sure if thats the right file, heres whats in that file anyway 

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
    <followMouse>yes</followMouse>
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
    <name>Curdled</name>
    <titleLayout>DSLIMC</titleLayout>
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
      <weight>normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuHeader">
      <name>sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="MenuItem">
      <name>sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>normal</weight>
      <!-- 'bold' or 'normal' -->
      <slant>normal</slant>
      <!-- 'italic' or 'normal' -->
    </font>
    <font place="OnScreenDisplay">
      <name>sans</name>
      <size>8</size>
      <!-- font size in points -->
      <weight>normal</weight>
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
      <name>1</name>
      <name>2</name>
      <name>3</name>
      <name>4</name>
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
          <name>PCManFM</name>
        </startupnotify>
        <command>pcmanfm</command>
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
    <keybind key="W-g">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Graphics Editor</name>
        </startupnotify>
        <command>gimp</command>
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
        <command>vlc</command>
      </action>
    </keybind>
    <keybind key="W-v">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Volume</name>
        </startupnotify>
        <command>gnome-volume-control</command>
      </action>
    </keybind>
    <keybind key="W-u">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>SystemUpdate</name>
        </startupnotify>
        <command>system-update</command>
      </action>
    </keybind>
    <keybind key="W-c">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Clock</name>
        </startupnotify>
        <command>~/.config/gworldclock/gworldclock.sh</command>
      </action>
    </keybind>
    <keybind key="W-x">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>Logout</name>
        </startupnotify>
        <command>openbox-logout</command>
      </action>
    </keybind>
    <keybind key="W-Tab">
      <action name="ShowMenu">
        <menu>client-list-combined-menu</menu>
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
    <application name="openbox-logout">
      <decor>no</decor>
      <shade>no</shade>
      <skip_pager>yes</skip_pager>
      <fullscreen>no</fullscreen>
      <maximized>no</maximized>
      <layer>above</layer>
    </application>
  </applications>
</openbox_config>
```

---

### Post by tgeer43 on 2009-08-30
You can launch the Keyboard Shortcuts app from the command line with:
```
gnome-keybinding-properties
```tgeer

---

### Post by Shpongle on 2009-08-30
i dont have that installed theres so many dependencies on that, that if i were to install it id be installing all the bloat of gnome, is there another way , is there a way i can see what the openbox equivalent is ?

ok so i was lookin round on the net and in openbox keybindings are done in the rc.xml file see [http://icculus.org/openbox/index.php/Help:Bindings](http://icculus.org/openbox/index.php/Help:Bindings) , so how would i go about adding the wheel configurations?

---

### Post by tgeer43 on 2009-08-30
Well, you're absolutely right. It does have a crapload of dependencies so I see your point.

You can still use the xmodmap method that I mentioned earlier. It's less intuitive and there's no fancy GUI but it definitely gets the job done.

Do a little reading up on it and if you still need help, post back here.

tgeer

---

### Post by Shpongle on 2009-08-30
ok im reading up on it now, listen thanks , i really appreciate you taken the time to help me,  im gonna look into xmodmap, then il head to bed coz its half 2 in the morning here bt il let you know how i get on,

---

### Post by Shpongle on 2009-08-30
its fixed i was also asking around on linuxquestions.org and was told to add this code to my rc.xml file and i now have a functioning volume wheel , thanks for all your help though


<keybind key="XF86AudioLowerVolume">
<action name="Execute">
<execute>amixer -c 0 set Master 5%- unmute</execute>
</action>
</keybind>
<keybind key="XF86AudioRaiseVolume">
<action name="Execute">
<execute>amixer -c 0 set Master 5%+ unmute</execute>
</action>
</keybind>

---

### Post by tgeer43 on 2009-08-30
Yeah, rc.xml is apparently an openbox thing.
Please make sure to tell people in your opening post that you are running openbox. It'll save everyone some headaches.

Glad you got it worked out.

tgeer

---

