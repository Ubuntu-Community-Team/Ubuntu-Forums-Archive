---
title: "3 things I need to iron out"
date: 2010-07-30
forum: General Help
---

### Post by justinsn95 on 2010-07-30
1. I changed the mouse to be that cool looking, little red mouse. But it only appears as the little red mouse, when I am hovering it over a firefox window lol. At all other times, its just the plain old, white mouse. What is going on here? How do you fix this?


3.How can I make the mouse "back button" work like it does in windows? It works fine in firefox, but when I am browsing through my folders and files, its nice to just be able to hit that button and have it go back to the previous window. Without having to go up to the little back arrow in the window and click it. Just another one of those little luxuries that I have gotten used to, I guess.

---

### Post by ajgreeny on 2010-07-30
The only thing I can possibly help with is Q3, though in karmic and lucid the back button has worked automatically for me in nautilus.  I have a Trust Ami Mouse- Dual Scroll, which is now about 6 yrs old.

Entries to enable forward & backwards navigation in nautilus with mouse buttons.
```
sudo apt-get install xvkbd xbindkeys x11-utils
``````
xev | grep ', button'
```Press mouse buttons and note output, eg

state 0x10, button 8, same_screen YES
state 0x10, button 8, same_screen YES
state 0x10, button 9, same_screen YES
state 0x10, button 9, same_screen YES

Back in terminal, we need to create a new file to configuration xbindkeys.

gedit ~/.xbindkeysrc

This will load up Gedit to add content to the new file. This file needs to contain the following:

```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```Notice the &#8220;b:8&#8243; and &#8220;b:9&#8243; portions of the text. This is where I configure my mouse buttons. So, if your mouse #buttons are 6 and 7, then you need to change &#8220;b:8&#8243; and &#8220;b:9&#8243; to &#8220;b:6&#8243; and &#8220;b:7&#8243;, respectively.

Set **xbindkeys** to autostart at session start in System->Preferences->Startup Applications.

---

### Post by hhh on 2010-07-30
RE: Question 2, if you're talking about autoscrolling in Firefox, go to Edit>Preferences>Advanced?Browsing and check "Use autoscrolling".

---

### Post by justinsn95 on 2010-08-01
thanks for the help. Anyone got any idea about any of the other suff?

---

### Post by justinsn95 on 2010-08-08
Can anyone tell my why my mouse is red when hovering over Firefox, and white any other time? lol

---

### Post by Ginsu543 on 2010-08-08
This is a known [_bug_]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647") with 10.04 and Compiz and was previously discussed [_here_]("http://ubuntuforums.org/showthread.php?t=1464556"). I have the same problem, but just have learned to live with it. It used to bother me, but not anymore.

---

