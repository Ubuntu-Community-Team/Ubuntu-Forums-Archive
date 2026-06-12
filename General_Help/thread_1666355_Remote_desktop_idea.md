---
title: "Remote desktop idea"
date: 2011-01-13
forum: General Help
---

### Post by josepaul on 2011-01-13
hey guys, am moving to college hostel next year and am wondering what ill do with my gaming desktop. And an idea struck me when I heard of remote desktop. 

If I kept the desktop in my dorm room and I get, say a small cheap netbook or laptop and run something like VNC through the local network, would I be able to use the full power of the desktop (not gaming, but all the applications) at full speed? (even though the laptop will have a rubbish processor/ graphics card etc)

EDIT: I'm not sure this is in the right forum, @mods; feel free to move it if you feel so.

---

### Post by davidmohammed on 2011-01-13
yes - lots of threads on this

rdesktop
x11vnc
teamviewer
nomachine

are all that come to mind

my personal favorite is nomachine since i manage another PC located miles away over an encrypted internet link.

---

### Post by kn0w-b1nary on 2011-01-13
Hello,

As far as i know, yes. Using KFRB is a good way to start. You can also use VNC and use a vnc viewer like vinagre.

While your framerate will be lower (bad for FPS games), it will not effect your processing power and computer speed. KFRB allows you to easily password protect your session, as well as set a time-out. (i.e. after 30  mins. no more connections allowed and current ones closed. Only disadvantage is that it has to be started manual on the machine you want to connect to.

(Note: KRFB is a KDE application.)

i have only done this in debian though, :D

---

### Post by josepaul on 2011-01-13
> **davidmohammed said:**
> my personal favorite is nomachine since i manage another PC located miles away over an encrypted internet link.

That's quite cool, did you experience any lag? and what speed connection did you have?

---

### Post by josepaul on 2011-01-13
> **kn0w-b1nary said:**
> Hello,

As far as i know, yes. Using KFRB is a good way to start. You can also use VNC and use a vnc viewer like vinagre.

While your framerate will be lower (bad for FPS games), it will not effect your processing power and computer speed. KFRB allows you to easily password protect your session, as well as set a time-out. (i.e. after 30  mins. no more connections allowed and current ones closed. Only disadvantage is that it has to be started manual on the machine you want to connect to.

(Note: KRFB is a KDE application.)

i have only done this in debian though, :D

I won't be playing any games :P but will be using some processing intensive software, my question is, apart from the frame rate of what you see, does the laptop's processor do any processing?

---

### Post by davidmohammed on 2011-01-13
nomachine is quite flexible - it can work from modem type speeds (28kbps) through to LAN speeds - at lower speeds the graphical quality and update speed is obviously much slower than running at LAN speed.  Since my internet speed is 1.5 meg I run at the "adsl" setting.  It is very responsive - you just cant really view any application with frequent screen changes - e.g. a flash video in firefox.

---

### Post by kn0w-b1nary on 2011-01-13
> **josepaul said:**
> I won't be playing any games :P but will be using some processing intensive software, my question is, apart from the frame rate of what you see, does the laptop's processor do any processing?

Not noticeably when running VNC or KFRB, and that was on a low-end old dell desktop. I doubt there would be any problems on a higher-end one. You should be able to use those power-hungry programs just fine. :D

---

### Post by DanHorniblow on 2011-01-13
Remote desktop is a brilliant way to make use of a PC. I am studying at college and have found the college computers quite poor, so I have setup remote desktop to my gaming pc at home and it works a treat :)

However I am using windows 7 and RDP as i still use the pc when i go home for gaming occasionally.

I have also setup a home web server running ubuntu server 10.10, I have setup remote SSH to that as well.

It is surprisingly easy :)

---

### Post by josepaul on 2011-01-13
> **DanHorniblow said:**
> Remote desktop is a brilliant way to make use of a PC. I am studying at college and have found the college computers quite poor, so I have setup remote desktop to my gaming pc at home and it works a treat :)

However I am using windows 7 and RDP as i still use the pc when i go home for gaming occasionally.

I have also setup a home web server running ubuntu server 10.10, I have setup remote SSH to that as well.

It is surprisingly easy :)

Wow, this is exactly what i was looking for. What kinda stuff can you use on it (high processing demand that runs smoothly)? Is there any lag? What internet speed do you use. And do you tell your parents to turn it on/off everyday or just leave it on all the time?

---

### Post by spencerownside on 2011-01-18
i have searched some other threads, but this thread is the most active and closest that i have seen to what i am trying to do. i am trying to do something similar to original thread- 
i have a studio in my house and am trying to connect multiple pcs to a network and enable remote desktop between them. specifically here, i have a laptop that is ubuntu and i want to use it to access and control a cakewalk program on a separate xp desktop pc. i am curious firstly, considering the OS differences and the sort of specific nature of the cakewalk program, is this even possible? i personally am the drummer and i would love to just use a laptop next to my kit to press the "record" button instead of having to get up and walk to the cakewalk-desktop every time i need to do something. 
ideas, suggestions, thoughts, etc?

---

### Post by josepaul on 2011-01-18
> **spencerownside said:**
> i have searched some other threads, but this thread is the most active and closest that i have seen to what i am trying to do. i am trying to do something similar to original thread- 
i have a studio in my house and am trying to connect multiple pcs to a network and enable remote desktop between them. specifically here, i have a laptop that is ubuntu and i want to use it to access and control a cakewalk program on a separate xp desktop pc. i am curious firstly, considering the OS differences and the sort of specific nature of the cakewalk program, is this even possible? i personally am the drummer and i would love to just use a laptop next to my kit to press the "record" button instead of having to get up and walk to the cakewalk-desktop every time i need to do something. 
ideas, suggestions, thoughts, etc?

Yeah, this should be quite easy, if you install VNC on your desktop and set it up as the server and click accept connections, and then go to remote desktop on your laptop and choose VNC and the IP address of your desktop (local ip)

---

### Post by spencerownside on 2011-01-18
so there is where my "newbieness" shows. what is vnc? i'm using ubuntu studio and there is a program called "remote desktop viewer" already installed under my 'inet' menu option? 
when i look at the software center i see a couple programs that have remote descriptions and i see a couple programs that have "vnc" somewhere in their descriptions but no program called "VNCblahblah". 
appreciate the help and such, and sorry about the lacking jargon knowledge.

---

### Post by josepaul on 2011-01-19
> **spencerownside said:**
> so there is where my "newbieness" shows. what is vnc? i'm using ubuntu studio and there is a program called "remote desktop viewer" already installed under my 'inet' menu option? 
when i look at the software center i see a couple programs that have remote descriptions and i see a couple programs that have "vnc" somewhere in their descriptions but no program called "VNCblahblah". 
appreciate the help and such, and sorry about the lacking jargon knowledge.

install VNC server on your XP machine, then use Applications>Internet>Remote Desktop viewer on your ubuntu laptop

[http://www.realvnc.com/products/free/4.1/winvnc.html](http://www.realvnc.com/products/free/4.1/winvnc.html)

---

