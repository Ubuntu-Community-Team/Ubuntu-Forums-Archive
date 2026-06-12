---
title: "media keys &amp; volume wheel on keyboard not working"
date: 2012-04-05
forum: General Help
---

### Post by doogiekd on 2012-04-05
dear friends, 

i am having trouble getting the media keys to work on my dell rt7d40 wireless keyboard. the keyboard has a volume wheel as well as the stop, next & previous buttons.

notes: the other hot keys on the keyboard do work, such as the calculator button and browser launch button. all other keys (alphabet, numbers, ect) function normally.

this is the part of my lxde-rc.xml file that shows the hot keys & commands:

XF86AudioLowerVolume">
* * * <action name="Execute">
* ** *    <command>amixer -q sset Master 3%-</command>
* *   </action>
  * </keybind>

  * <keybind key="XF86AudioMute">
* * * <action name="Execute">
* ** *    <command>amixer -q sset Master toggle</command>
* *   </action>
  * </keybind>

  * <keybind key="XF86WWW">
* * * <action name="Execute">
* ** *    <command>x-terminal-emulator</command>
* *   </action>
  * </keybind>

  * <keybind key="XF86Calculator">
* * * <action name="Execute">
* ** *    <command>galculator</command>
* *   </action>
  * </keybind>

  * <keybind key="XF86MyComputer">
* * * <action name="Execute">
* ** *    <command>pcmanfm</command>
* *   </action>
  * </keybind>

  * <keybind key="XF86Terminal">
* * * <action name="Execute">
* ** *    <command>x-terminal-emulator</command>
* *   </action>
 *  </keybind>

action taken so far:

1. tried using xbindkeys and copied the commands from the above file for each key.

notes: the buttons & wheeel are recognized - i can see flash of the select field when activating these keys in xbindkeys.

2. i tried removing the commands in lxde-rc.xml and trying again with xbindkeys alone. 

neither actions worked.

any ideas on how i can get these media keys to work?

thanks, 

doogiekd

---

### Post by doogiekd on 2012-04-09
solved! thanks to the great help from the lubuntu irc.

solution:

replace "amixer -q sset Master 3%-" with "amixer -c 1 sset Master playback 3%+"

adjust the command as necessary for volume up or down (3%-). 

you may need to try different number after -c to correctly identify your sound card from 0, 1, 2, 3.

thanks to my lubuntu peeps!

---

