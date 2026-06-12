---
title: "Use mouse buttons as modifiers"
date: 2012-07-07
forum: General Help
---

### Post by 5ER on 2012-07-07
Hello.

I have a Logitech G5 mouse and it has two very handy thumb buttons. I'd like to use these buttons as modifiers to use them with other keys AND as normal back/forward buttons when released without any other key being pressed while they were pressed down.

I have been able to do so using xte and xbindkeys (with the .xbindkeysrc script) by basically using Scroll Lock and Num Lock as variables. Yes, extremely dirty. And I only managed to use the forward button as a modifier.

What I'm looking for is a cleaner solution.


I'm really sad there's no AutoHotkey for Linux, as doing this was trivial using AHK in Windows.

---

### Post by ajgreeny on 2012-07-07
Here's my .xbindkeysrc file with all the info on how I get my five button mouse to work as forward/back control in nautilus, thunar and pcmanfm.  I know it also works without xbindkeys running for forward/back in firefox and chromium, but it is very useful in the filemanager as well.  I hope this may help you.

> # Entries to enable forward & backwards navigation in nautilus with mouse buttons.

#sudo apt-get install **xvkbd xbindkeys x11-utils**.
#Ubuntu versions before 9.04 (Jaunty Jackalope), the **x11-utils** package needs to be replaced by **xev**.

#Terminal command:-
#xev | grep ', button'         Press mouse buttons and note output, eg

#state 0x10, button 8, same_screen YES
#state 0x10, button 8, same_screen YES
#state 0x10, button 9, same_screen YES
#state 0x10, button 9, same_screen YES

#Back in terminal, we need to create a new file to configuration xbindkeys.

#gedit ~/.xbindkeysrc

#This will load up Gedit to add content to the new file. This file needs to contain the following:

#"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
#  m:0x0 + b:8
#"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
#  m:0x0 + b:9

#Notice the &#8220;b:8&#8243; and &#8220;b:9&#8243; portions of the text. This is where I configure my mouse buttons. So, if your mouse #buttons are 6 and 7, then you need to change &#8220;b:8&#8243; and &#8220;b:9&#8243; to &#8220;b:6&#8243; and &#8220;b:7&#8243;, respectively.

#Set xbindkeys to autostart at session start in System->Preferences->Startup Applications.

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

---

### Post by 5ER on 2012-07-08
Thanks for replying, that's not what I was looking for. I can assign actions to mouse buttons and I did use alt+left and alt+right for moving through history, but I did it using xte.
That's irrelevant, though. What I'm having trouble is using the buttons as modifiers (like alt and shift; so I can press a thumb button and another button at the same time and that would trigger a specific action) AND as normal buttons. They would function as normal buttons if no other key was pressed together with them.

I apologise if I was unclear.


This is how it would look in AHK:
```
WheelRight::^Tab ;ctrl + Tab for switching through tabs. This is not what I'm looking for, but it helps illustrate the contrast between this and the next binding
XButton1 & WheelRight::AltTab ;Here a thumb button (XButton1) is used as a modifier
XButton1::Send {Browser_Forward} ;Here the thumb button is used as a normal button
```

The above works flawlessly exactly the way I want. I'm trying to recreate this in Linux.

---

