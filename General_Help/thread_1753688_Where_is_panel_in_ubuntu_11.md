---
title: "Where is panel in ubuntu 11"
date: 2011-05-09
forum: General Help
---

### Post by shubham.joy on 2011-05-09
Hello I recently upgraded to my ubuntu to 11.04. My expectations were high, but now I got to say I am quite disappointed. Specially with the unity desktop.I am facing the following problems:

1. Where is the panel , which used to show the applications like GNOME 2 IP Messanger ?
2. installing simple compiz-config manager shows dependency problems.
3. I used to pin applications like task manager and network manager on the pane, but now how to do them ?
4. If I use the compiz config settings manager and use emerald theme manager the taskbar disappears and I am unable to move/resize windows.
5. Many a times mouse clicked and keyboard shortcuts (specially ctrl+alt+T ) didnt work and hence I had to restart.

Please, if someone has solution to this problem guide me. Specially point 1. Rest all is fine if I dont use theme (but I want to ).

I am not precisely a newbie but a little far from intermediate. and being an IT student ( 3rd year ) do not have any problem with CLI.

---

### Post by ghostborg on 2011-05-09
To get away from Unity-Log out and then click on your log in name
but before you type in your password look at the bottom of the screen and you will notice options, select Ubuntu Classic and that will give you Ubuntu 11.04 Natty with the familiar Gnome interface with your panels. Also double check your language setting mine was set for English Canada as I live near a border in the US.
Then type in your password to login and you should now be in Ubuntu 11.04 Classic.
You might also want to set this as the default in the Startup Manager.

As far as Compiz goes I ran into the same problem when I tried to change some settings and didn't realize that it disabled Window features like Move and a few others so you will need to checkbox those again. Also look for Window decorator and make sure that is checked and I think Composite and Open GL too. I am not in front of a Ubuntu machine right now so I'm doing this from memory. I use the full Compiz setting manager and not the Simple and I have seen others complain about dependency problems with it. I did not have a dependency problem with the Full. You also might wand to install the fusion-icon which is nice to put in you Startup Applications so you can reload the desktop decorator if it crashes. 
It would probably be best to restart after you get the basics working.
Good Luck

---

### Post by gcvisel on 2011-05-09
> **shubham.joy said:**
> Hello I recently upgraded to my ubuntu to 11.04. My expectations were high, but now I got to say I am quite disappointed. Specially with the unity desktop.I am facing the following problems:
 
1. Where is the panel , which used to show the applications like GNOME 2 IP Messanger ?
2. installing simple compiz-config manager shows dependency problems.
3. I used to pin applications like task manager and network manager on the pane, but now how to do them ?
4. If I use the compiz config settings manager and use emerald theme manager the taskbar disappears and I am unable to move/resize windows.
5. Many a times mouse clicked and keyboard shortcuts (specially ctrl+alt+T ) didnt work and hence I had to restart.
 
Please, if someone has solution to this problem guide me. Specially point 1. Rest all is fine if I dont use theme (but I want to ).
 
I am not precisely a newbie but a little far from intermediate. and being an IT student ( 3rd year ) do not have any problem with CLI.
 
   I fought those kind of problems for a week or so, and then went into Login Manager and set my default Desktop Environment to Ubuntu Classic, and all was back to normal.  Dunno if they will keep it in the next release, but I sure hope so.  This thing feel like Big Brother has invaded Linux!
 
   That's not much of an answer, but Unity is not much of a usable desktop.
 
Gerry

---

### Post by TheNerdAL on 2011-05-09
Is unity 2D installed? Check synaptic.
Also check System Monitor to see if compiz is running.
Which 3D drivers have you installed?

---

