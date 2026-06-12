---
title: "Remote login services (RDP / VNC) help needed"
date: 2009-06-27
forum: General Help
---

### Post by geejayoh on 2009-06-27
Ok,

Now, I'm not one for posting completely uninformed descriptions of problems or posting to a help forum without doing a brief search to see if my question is answered. And there seems to be a lot of talk about my problem but no actual solutions.

I am a System Admin by trade but primarily I have dealt with Windows based systems with the odd Mac / Solaris / Unix box. But I've never had to deal with remote logins for these systems and all the most linux experience I got whilst I was studying for my computer science degree was logging into a box via telnet and then publishing my project webpages.

So just so you know, you don't have to tread water with me, if you need to go into a technical explanation for something, don't hold back. If I don't understand your answer I'll probably research it all before I get another reply.

So,

I normally with a windows box, I can allow remote connections and then RDP into it using mstsc.exe if I just want a remote connection to set some process running, like a torrent at home or run an FTP where I can get all my music and videos from.

I normally have this computer hooked up to my TV as well, to use as a media centre and to facilitate this I normally also put a VNC server on the box, so I can use my laptop from the armchair to control it and play videos whilst it's still displayed on the TV.

This is the ideal set-up for me. 

So this time, in my new house, new box, I thought I would be smart and install Ubuntu on the server / media centre PC. First I thought I'd put Ubuntu server on there because I want to have an FTP server, WEB server etc on there. Unfortunately due to it being at home and for media centre use too, I had to put Ubuntu Desktop on there for the GUI interface.

So the problem.

And it's a big problem.

1. Out of the box, Ubuntu Jaunty has VNC enabled with vino-server but will only let me control the desktop when I have physically *gone *to my server and logged in. Which is a pain if every time I have to do that. Forgive me, but If I'm on my laptop and I have to restart the box for some reason or whatver, with windows I could just VNC in and login, because the server would start as a service before login, and all the shares would be active too.

2. I have seen some people suggesting editing /etc/gdm/gdm.conf and setting 
```
killInitClients=false
```and adding 
```
/usr/lib/vino/vino-server &
``` to the /etc/gdm/Init/Default file
I did this. It seems to run the vino server, but my windows VNC client (tight and ultra vnc viewer) seem to have problems connecting when they do this.

3. Then I have seen people suggesting using XDMCP. So I did that, I downloaded XMing for windows and I *CAN* connect to the server using Xming and XDMCP and it brings me to the login screen ( I had already enabled remote desktop viewing through the menu's and whatnot )

Editing gdm.conf again to enable XDMCP access as well. But with this I have soon discovered to my chagrin that if I disconnect from this session, say because I need to go out and take my laptop to with me, because of the reversed client / server architecture of the Xwindows system that kilss the session, and therefore transmission / hellanzb and whatever else I have running! How FRUSTRATING.

4. Don't get me wrong, I'm a geek and I am firmly convinced that linux / unix is better than windows, especially being free, community maintained and running on much less powerful systems. And I also refuse to believe that somehow (for ease of use / setup) that Windows has it over Linux / Ubuntu here for my requirements. 

Whilst running applications on my computer using Xserver is all well and good, without having to bring up the whole desktop (I particularly like that functionality) it's still not good enough because I need these things to be persistant from the time I connect, initiate and then disconnect, I want to be able to say remote in again, and be presented with the same desktop that was there before. with all running processes and application windows.

Now it wouldn't be so bad if it was command line either. I installed ssh on the box, so I could use putty from windows and run hellanzb that way. but once again, if I log out, then the processes die, or are put to sleep, and I don't know how I would grab them again if I ssh in a second time. 

Now I'm not here for a discussion over security or leaving holes for people to get into. I'm not a business and I won't be leaving my bank account details on it for people to read, so I forget security considerations. 

All I want dearly is within my local network be able to turn on, VNC in, then log in, run programs, disconnect, go to work, VNC again and see the same desktop that I left that morning.

The same goes for the equivalent to RDP or something that offers the same functionality so I can administer it from within and without my home network.

I don't want to seem like a naive Windows user etc, and I know that linux was never designed to be a clone of windows, but this functionality is what I'm looking for and if I cannot get it, then I will put XP back on the box and be done with it.

I boot ubuntu on my laptop too and I have really enjoyed using it so far, but for development purposes I need the Adobe software on my vista install. I could run them in Wine I guess, but meh - dual booting is good enough. 

*So in summary, can you help? The other forum internet posts just don't really seem to solve this issue, and I know the ubuntu community is helpful, kind and above all excellent at solving issues.*

N.B. I also wouldn't mind an explanation of the whole login system. At the ubuntu login screen it give options of "run xclient script", "last session" , "run GNOME" etc... what's the difference? I thought the login screen WAS Gnome (Gnome Desktop Manager) so why would I run it again?
and what's the difference between that and an X(server)client script?

Also (forgive the my interpretation of syntax here) but if it says "Last session..." I would expect it to connect to my last user session (if I hadn't explicitly logged off) but this doesn't happen?

What, who, why handles logins and sessions to linux and keeps track of them? :confused:

Looking forward to comments, suggestions and solutions,

yours, 

Geejayoh

---

### Post by geejayoh on 2009-06-30
nothing? I'm putting Windows back on. M$ 1 - Ubuntu 0

---

