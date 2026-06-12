---
title: "Error opening/initializing the selected video_out (-vo) device."
date: 2005-03-14
forum: General Help
---

### Post by plima on 2005-03-14
This error message pops up when I attempt to watch any video with Mplayer.

I am not using command line. I am using graphical interface of Mplayer.

Thank you.

plima

---

### Post by Domecq on 2005-03-16
Edit your .mplayer/gui.conf file and make sure that you have vo_driver line like this:
vo_driver = "x11"

The above line is the 2nd one in my file.

Let me know if that helps.

Domecq

---

### Post by plima on 2005-03-17
domcq,

thanks a lot!! that really resolved the problem!

plima

---

### Post by plusangel on 2006-11-04
That is still working!

Thank you :)

---

### Post by Xceptiona1 on 2006-12-10
worked for me as well, thanks!

---

### Post by userundefine on 2006-12-18
Yep, still works...

---

### Post by Contrast on 2007-02-26
Just another +1. Thanks for the help! :D

---

### Post by omac on 2007-02-27
> **Domecq said:**
> Edit your .mplayer/gui.conf file and make sure that you have vo_driver line like this:
vo_driver = "x11"

The above line is the 2nd one in my file.

Let me know if that helps.

Domecq

Thank you, you solved my problem with MPlayer too.  This plays very well.  :)

---

### Post by psi36 on 2007-03-11
Unfortunatly this didn't work for me. Still get the "Error opening/initializing the selected video_out (-vo) device." :(

Before I chenged it, the second line was: "vo_driver = "xmga""

---

### Post by gaspipe1 on 2007-03-15
ahhh whats the easiest way to find that file so I can edit it?

---

### Post by SSamiK on 2007-03-18
start a terminal and type:
```
gedit .mplayer/gui.conf
```

---

### Post by naerae on 2007-03-27
Thanks x11 helps. But mplayer doesnt expand the video into Full Screen. Just Mplayer extends into Full screen. Any opinion to solve?

---

### Post by jessegillies on 2007-03-27
if anyone is having problems making the change to the gui.conf file stick, i found that opening mplayer and changing the driver to x11 in the gui works.

---

### Post by zvacet on 2007-03-27
home>.mplayer>config
add line
** zoom = yes**

---

### Post by Ensoa on 2007-03-27
It also helped for me, Thanks!!

---

### Post by NJC on 2007-03-28
> **Domecq said:**
> Edit your .mplayer/gui.conf file and make sure that you have vo_driver line like this:
vo_driver = "x11"

The above line is the 2nd one in my file.

Let me know if that helps.



And it absolutely helped. THANKS! 

That's great ... but why oh WHY is it so hard to find that info (even via mplayer.hq?)? And WHY does X11 have to be added???

Nevermind ... I'm just venting because I spent much time fargin around trying get it working.](*,) ](*,)

---

### Post by naerae on 2007-03-29
> **NJC said:**
> And it absolutely helped. THANKS! 

That's great ... but why oh WHY is it so hard to find that info (even via mplayer.hq?)? And WHY does X11 have to be added???

Nevermind ... I'm just venting because I spent much time fargin around trying get it working.](*,) ](*,)

Good and same question. Why do we need to edit the file? Could some one inform us?

---

### Post by chinaski on 2007-03-31
> **psi36 said:**
> Unfortunatly this didn't work for me. Still get the "Error opening/initializing the selected video_out (-vo) device." :(

Before I chenged it, the second line was: "vo_driver = "xmga""
same for me

sad :(

---

### Post by Alekc on 2007-04-08
Try to set it manualy in preferences->video. It worked for me

---

### Post by Matthaeus on 2007-05-20
If you have changed the driver to x11, and you can no longer increase the size of the movie eg go to 2x or full screen, try changing the driver to xv.

Matt.

---

### Post by d_xtremw on 2007-06-29
when u change the driver to "xv" i cant see anything. just a whole set black and the occasional pixelated image on the screen every 5mins or so

---

### Post by divdude on 2007-06-29
This worked for me.
I changed the vo_driver to 
vo_driver = "gl2"

---

### Post by chrono310 on 2007-07-17
For those who report having trouble with it, make sure to perform the change after closing mplayer... if it's running I believe it resets the setting.

---

### Post by compsariomike on 2007-07-27
YESSSS!!!

It worked here as well

---

### Post by Sweet Spot on 2007-08-06
Can someone please help me. I installed Smplayer, rather than Mplayer, and am having this exact same problem. But there is no config file for smplayer, so I'm not sure of what to do at this point.

Edit: Ok, I edited the Mplayer conf file, and that works, HOWEVER. When I open a video in Mplayer, the video opens right away, but when I associate the file with Smplayer it takes forever for the file to open. I'd say a good 10 seconds, no matter what kind of file it is. Anybody know why this would happen ?

---

### Post by rvm4000 on 2007-08-06
There's a known issue with the gnome screensaver. When mplayer tries to disable there's a delay of about 10 seconds. 

Try to uncheck the option "Disable screensaver" in Preferences->General and see if this fixes the problem.

---

### Post by Sweet Spot on 2007-08-06
> **rvm4000 said:**
> There's a known issue with the gnome screensaver. When mplayer tries to disable there's a delay of about 10 seconds. 

Try to uncheck the option "Disable screensaver" in Preferences->General and see if this fixes the problem.

Brilliant !  Worked a charm. Thanks a million rvm. 

Doug

---

### Post by Tedd81 on 2007-08-12
Hello!

I was having the same fatal error, sorted now thanks to this thread!! Thanks!!

One thing, when double clicking on a video file nothing happens. I need to right click an 'open with Mplayer'.

Where do I start to sort this?

Ted.

---

### Post by joao82 on 2007-08-18
until i read this topic, i thought mplayer was the most useless piece of software i had on my pc.
this solved everyting and now i have a brand new media player to try when i can't see something on kaffeine or vlc.
this thread should be sticky.
thanks.

---

### Post by dreadie on 2007-10-04
Adding that this also worked for me, changing the gui.conf file and the config file (to fix the zoom issue). As well, MPlayer has a much more stable/working/informative/usefull mozilla plugin than does either VLC or Totem. I'd recommend MPlayer over either of the alternatives.

---

### Post by foxmulder881 on 2007-10-15
Just thought I'd add another note that this thread just helped me regarding the error message and zoom issue.

Cheers!

---

### Post by Weevil on 2008-01-25
Hmz more than 2 years after the solution got posted I still have to find this thread to get mplayer working on OpenSUSE 10.3... thanks anyway it works like a charm!

---

### Post by rousseau09 on 2008-01-31
gui.conf >> xv didnt worked. x11 worked out. i guess its just playing with the settings that works fine. 
cheers mate. i got 64bit pc and 64 bit ubuntu, hope that helps others.

---

### Post by gmoctav on 2008-05-11
finally!thanks!i almost gave up ubuntu because of that error..

---

### Post by greebothecat on 2008-06-07
changing vo_driver from xv to x11 helped - I can see the movie now
but
it won't get scaled properly when I fullscreen :/
zoom = "yes" doesn't have effect
when I put gl2 instead of x11 it does zoom but I can't use Compiz then, screen flickers when not on fullscreen (X1300 (R515) ATI card :/ on fglrx drivers :/)

so I either can watch normal and fullscreen size videos without Compiz or only fullscreen with Compiz (Composite Extension On).

anybody else with similar trouble?

---

