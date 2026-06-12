---
title: "Mouse API or Command"
date: 2011-07-10
forum: General Help
---

### Post by sptutusukanta on 2011-07-10
What is the mouse API to detect mouse buttons status?
Or Is there any command to detect the mouse button status?

---

### Post by ajgreeny on 2011-07-10
I am not sure if this is what you really want or need, but it may give you some clues about where to look for more info.  This is what I needed to do to get my mouse side buttons to back/forward navigate in nautilus, so it may be possible to change all the syntax to get what you need working.

# Entries to enable forward & backwards navigation in nautilus with mouse buttons.

```
sudo apt-get install xvkbd xbindkeys x11-utils
```Enter command:-
```
xev | grep ', button'
```  Press mouse buttons and note output, eg
```
state 0x10, button 8, same_screen YES
state 0x10, button 8, same_screen YES
state 0x10, button 9, same_screen YES
state 0x10, button 9, same_screen YES
```Now create a new file for configuration of xbindkeys.
```
gedit ~/.xbindkeysrc

```This file needs to contain the following for the backwards/forwards navigation:
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```Notice the &#8220;b:8&#8243; and &#8220;b:9&#8243; portions of the text. This is where I configure my mouse buttons. So, if your mouse #buttons are 6 and 7, then you need to change &#8220;b:8&#8243; and &#8220;b:9&#8243; to &#8220;b:6&#8243; and &#8220;b:7&#8243;, respectively.

Set xbindkeys to autostart at session start in System->Preferences->Startup Applications.

As I say, this may not be what you are looking for;  if not ignore me and keep looking.

---

### Post by sptutusukanta on 2011-07-11
> **ajgreeny said:**
> I am not sure if this is what you really want or need, but it may give you some clues about where to look for more info.  This is what I needed to do to get my mouse side buttons to back/forward navigate in nautilus, so it may be possible to change all the syntax to get what you need working.

# Entries to enable forward & backwards navigation in nautilus with mouse buttons.



*This is a good application.* ***But it only detects the events on the particular window.*** Actually I need to get the **status of the mouse buttons _every time_**. Whether it is over some _**window does not matters**_.
**I want to listen the mouse port to get that status.** I need some sort of system calls, to accomplish the job!

---

