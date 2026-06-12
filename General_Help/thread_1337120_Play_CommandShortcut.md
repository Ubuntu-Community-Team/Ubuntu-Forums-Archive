---
title: "Play Command/Shortcut"
date: 2009-11-25
forum: General Help
---

### Post by jwflammer on 2009-11-25
i want a second Play keyboard shortcut. Whats the command for play?

[IMG]http://gobetweenworlds.com/Screenshot.png[/IMG]

---

### Post by raktarok on 2009-11-25
Hi,
I don't know the command gnome uses to handle play operation, but I know two ways of achieving the same thing.

**Method 1**
First find out the keycode corresponding to the key you want to use as a shortcut.
For example, if you want to use F12 as the new shortcut, do this to find its keycode:
```
xmodmap -pke | grep F12
```
In my laptop, the output is like this, but it may vary from keyboard to keyboard.
```
keycode  96 = F12 XF86_Switch_VT_12 F12 XF86_Switch_VT_12 F12 XF86_Switch_VT_12
```
The keycode is 96 for the F12 key, and now, do this to duplicate it as the play button:
```
 xmodmap -e 'keycode 96 = XF86AudioPlay'
```
(XF86AudioPlay is the name of the key that handles the play operation by default, much like F12 is just a name.)
Now both the default and the F12 key work as play buttons. But this will last only for the current session, so if you want this to persist after reboot/relog-in, add the line above in your 'startup applications' list.
However, this method won't work if you want to set key combination like 'Super + p' as your shortcut. 

**Method 2**
Another way to achieve this would be to use remoot, a very useful tool that allows you to control all the popular media players with the same global keys. 
[http://www.remoot.org/](http://www.remoot.org/)
If you decide to use remoot, you will just need to add this as the command in the 'custom shortcut' dialog:
```
remoot play
``` 
Now you can set any key or key combination as your shortcut. 
Setting up remoot is a bit of a work though, but there are instructions on the website. 

Of course, an easier way than these two methods is to find the command gnome uses to handle play (if any). Personally, I find remoot very handy, and the commands to play,pause and other operations are right there. Give it a try, you may like it!

---

### Post by jwflammer on 2009-11-30
ok so i read a few books and got what i wanted it to do !!!

> 

( " you cand add the device you want to play / pause were rhythmbox is " )

Play / Pause : rhythmbox-client --play-pause 

Next Track : rhythmbox-client --next

previous : rhythmbox-client --previous

( " for volume " )

Volume Up : amixer set 'master' 5%+

Volume Down : amixer set 'master' 5%-

Volume Mute : amixer set 'master' toggle

( " the volume commads do not show the notification box " )


ya!!! i got it 

raktarok thank you for your help !!

---

