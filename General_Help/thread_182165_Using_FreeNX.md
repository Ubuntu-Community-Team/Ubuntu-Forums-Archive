---
title: "Using FreeNX"
date: 2006-05-25
forum: General Help
---

### Post by cobbweb on 2006-05-25
Hey, 
  Im trying to connect from my Ubuntu Box at school to my Windows Box at home and found a lot of posts that say using FreeNX is better/faster to use over the internet. The problem is im not sure how to even use it. How would I connect to my windows maching for a graphical remote desktop? Any help is wanted thanks, ,

 Cobbweb

---

### Post by rvergara on 2006-05-25
There is no freenx server for windows.

Freenx would be a very good connectivity solution to connect a windows client to a Linux server, not the other way around.

VNC may be a solution for your need.

Regards

Ramiro

---

### Post by cobbweb on 2006-05-25
[QUOTE=rvergara]There is no freenx server for windows.

Freenx would be a very good connectivity solution to connect a windows client to a Linux server, not the other way around.

VNC may be a solution for your need.

Regards

Ramiro[/QUOTE]



Oh, ... um same questions just with VNC ..... 


 Thanks , 
 cobbweb

---

### Post by Drain on 2006-05-25
[QUOTE=cobbweb]Im trying to connect from my Ubuntu Box at school to my Windows Box at home [edit!]  How would I connect to my windows maching for a graphical remote desktop? [/QUOTE]

[TightVNC ]("http://www.tightvnc.com/") to the rescue.  The [Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=181669") have more information about connecting the other way around (from a windows computer to a linux box), but if you put in some effort, you can figure it out yourself, and find some information from Google.

---

### Post by rvergara on 2006-05-25
[QUOTE=cobbweb]Oh, ... um same questions just with VNC ..... 


 Thanks , 
 cobbweb[/QUOTE]

Just download vnc server. Tightvnc as suggested above is a good option. VNC viewer (VINO) is already installed by default in Breezy. go to System->preferences->remote desktop

Enter the ip address of your windows box and you shold be in business.

Regards

Ramiro

---

### Post by behmann on 2006-06-01
I know this question isn't exactly in line with this thread however I didn't think it was worth starting a new thread over.

I have FreeNX runnign on a breezy box at home.  My computer at home has a 19" monitor and, while sitting in front of my home computer, the resolution is set to 1600x1200.  When I connect through FreeNX, from my 12" mac laptop, the resulution is shrunk to 1024x786.  However when I go back to the computer at home, the resolution is set (from login) to 640x480.

When I try to adjust the resolution from within Gnome, I am not given the option to change the resolution to anything other than 640x480.  However when I reboot the computer everything goes back to normal and the resolution is set back to 1600x1200.

Why is the actual computers resolution being changed and how can I prevent this from happening?

Anyone have any ideas? :-k

---

### Post by rvergara on 2006-06-01
[QUOTE=behmann]I have FreeNX runnign on a breezy box at home.  My computer at home has a 19" monitor and, while sitting in front of my home computer, the resolution is set to 1600x1200.  When I connect through FreeNX, from my 12" mac laptop, the resulution is shrunk to 1024x786.  However when I go back to the computer at home, the resolution is set (from login) to 640x480.
[/QUOTE]

Interesting problem. 

Can you please check in your mac no machine client configure windows what is 
the setting of the display? if other than available area, please change it to it and retest.

Regards

Ramiro

---

### Post by behmann on 2006-06-06
[QUOTE=rvergara]Can you please check in your mac no machine client configure windows what is 
the setting of the display? if other than available area, please change it to it and retest.[/QUOTE]

The mac noMachine client is set to "available area" however the problem still exists.  Perhaps this is an issue with the freenx server.  As a work around I simply bounce the X server and the resolution returns to normal.

---

### Post by behmann on 2006-06-06
[QUOTE=rvergara]Can you please check in your mac no machine client configure windows what is 
the setting of the display? if other than available area, please change it to it and retest.[/QUOTE]

The mac noMachine client is set to "available area" however the problem still exists.  Perhaps this is an issue with the freenx server.  As a work around I simply bounce the X server and the resolution returns to normal.

---

