---
title: "Synergy Client on Oneiric problem"
date: 2012-01-15
forum: General Help
---

### Post by paula_ke on 2012-01-15
Hi,  I'm running the latest 1.4.6 synergy client on 11.10.   The synergy server is running on an XP box and is also running 1.4.6.  They connect fine and I can move the mouse from the server to the client.  However,  the mouse cannot access the entire screen on the client (my 11.10 system).  the client has two screens but the mouse can only access 3/4 of the main screen then hits a wall keeping it from accessing the rest of the screen space.  The touchpad/mouse connected directly to the client can access the entire screen space.

As a side note,  I tried configuring the server so the client was to the left of the server.  When I do that and move my mouse to the left on my server, it shows up at the 3/4 point of the main client screen

Has anyone else seen this problem?

BTW, when I configure synergy server on the 11.10 machine all works well.
For keyboard technical reasons (use of alt and control keys) I need the keyboard directly connected to my windoz box.

Thanks,

Paula

---

### Post by paula_ke on 2012-01-15
So, a bit more information.  I'm thinking this is a bug somewhere in X, X drivers or synergyc.  

I ran Synergyc from the command line with a high DEBUG level and not in Daemon mode.  This allowed me to see what my mouse was doing as I crossed over into the client are.  The wall I hit is at 1079 pixels from the left.  I also noticed that there was much more vertical movement  to the mouse then what was seen on the display.  3359 pixels to be precise.  

I then looked at the beginning of the DEBUG info and found the following line:
screen shape: 0,0 1080x3360 (xinerama)

As you can see, the x coordinate is 1080 and the y coordinate is 3360.  This is wrong.  
Since I have my main display configured to the left of my second display I should have a huge x coordinate value and my y value should be the max size of my largest display, which happens to be 1080.  

I verified my screen configuration using XrandR and that command returns the proper x,y screen configuration.  

I did some further testing to verify that the x and y coordinates are flipped.  I reconfigured my screens so that one was above the other.  Sure enough the screen shape line x value changed to what the Xrandr y value was and the screen shape y value changed to what the Xrandr x value was.  

I am running the Nvidia (current) drivers.  Xinerama is set to '0' in the xorg.conf file.  In researching the Nvidia site, I found that Nvidia simulates providing xinerama values so I'm thinking that either the Nvidia driver, X or SynergyC is flipping the value.  

I looked for a 'landscape' vrs 'panorama' flag for the screen section in X or the options provided by the Nvidia driver but did not find anything as I was thinking it could be a stale orientation flag that I might be able to force.

I am still looking for a solution...

Paula

---

