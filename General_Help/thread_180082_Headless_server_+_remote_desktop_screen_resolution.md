---
title: "Headless server + remote desktop screen resolution"
date: 2006-05-21
forum: General Help
---

### Post by unholy1 on 2006-05-21
Hi,

I've recently aquired an old PC which I'd like to use as a headless server. I've successfully loaded Ubuntu on to it, and I can connect to the desktop via VNC, however whenever I restart the server without a monitor attached to it the resolution defaults down to 640x480. 

Everything in /etc/X11/xorg.conf looks correct to support a higher resolution, and it works when I start up with a monitor connected, but I don't want to leave a monitor in the closet with the PC... 

Any suggestions?

Thanks!

---

### Post by Bazon on 2006-05-21
what resolution are you talking about?

I select the resolution of my remote desktop with the -g Parameter:

```
rdesktop -g 1024x768 192.168.1.33
```
starts my Remotedesktop in 1024 x 768 pix solution.

There are other usefull options: -a 16 gives you 16bit color depth.

rdesktop --help for more optiions. :)

---

### Post by unholy1 on 2006-05-21
Well, the resolution on my main desktop PC (a WinXP machine) is 1280x1024. The ubuntu machine works fine at this resolution when the monitor is connected to it, however when I put the ubuntu server in the closet and use WinVNC to connect to the machine from my desktop PC, the screen seems to be set at 640x480 resolution (and is the only option listed when I go to System menu -> preferences -> screen resolution)...

I'm using WinVNC, not rdesktop, sorry :s

---

### Post by Bazon on 2006-05-21
ah, sorry, I don't have experience in that direction. (Although as far as I know 'VNC' is the name of the protocol rdesktop uses, that's why I suggested that....)

But anyway, I think the resoltion can be handled by the remote desktop program.

---

### Post by Slim Odds on 2006-05-21
[QUOTE=Bazon]ah, sorry, I don't have experience in that direction. (Although as far as I know 'VNC' is the name of the protocol rdesktop uses, that's why I suggested that....)

But anyway, I think the resoltion can be handled by the remote desktop program.[/QUOTE]

No, rdesktop uses RDP, not VNC

---

### Post by Bazon on 2006-05-21
@Slimm Odds: Ah, thanks, OK! :)

---

### Post by unholy1 on 2006-05-26
So... no suggestions as to what to do? All I need to do is change the resolution on my remote server, since it's not "auto detecting" a monitor (since nothing is physically connected). How can I do that?

Thanks

---

### Post by ifokkema on 2006-05-26
[QUOTE=unholy1]So... no suggestions as to what to do? All I need to do is change the resolution on my remote server, since it's not "auto detecting" a monitor (since nothing is physically connected). How can I do that?[/QUOTE]

Hi,

You need to fiddle with the VNC server settings. I've never set up VNC with Ubuntu before, but with Debian Sarge you needed to put some lines in the /etc/services and /etc/inetd.conf to set up multiple ports for different VNC settings (resolution, color depth).

I bet there's some basic VNC server settings file. Then there probably is a 'geometry' setting somewhere.

HTH,

Ivo

---

### Post by unholy1 on 2006-05-26
aha... thanks ifokkema. I'm getting a little closer now. Further Googling led me to [a question on Experts Exchange]("http://www.experts-exchange.com/Operating_Systems/X_Windows/Q_21750722.html"), which unfortunately doesn't provide a definite answer but gives a few hints. Looks like the VNC server is picking up the X server resolution, which is defaulting to 640x480 because it can't auto detect (because no monitor is attached). 

Unfortunately I don't know how to override this setting! Adding a $geometry=1024x768 to /etc/vnc.conf doesn't seem to help.

Anyone have any further ideas?

---

### Post by steve.horsley on 2006-05-26
X seems to do hardware discovery every time it starts, and if it can't find the monitor details it defaults to 640x460. 

I think I found a way to stop that discovery. You have to enter a horizontal and vertical refresh range into the monitor section of /etx/X11/xorg.conf. Like this:
```
Section "Monitor"
        Identifier      "E-171"
        Option          "DPMS"
        HorizSync     31-95
        VertRefresh    50-60       
EndSection


```
Don't change any existing lines - just insert the horizontal and vertical sync lines. It may be a good idea to look up the frequencies of the monitor you intend to use when remote access breaks. Now you should be able to select a resolution you like and have it start that way without a monitor connected.

---

### Post by Inevitable Glitch on 2006-05-28
Hi, I'm new to Ubuntu and I'm having this exact same problem.  Please let me know if that is a viable solution, or if you have found another.

---

### Post by Tim Thumb on 2006-05-31
I was having the same issue and I tried steve.horsley's method which appears to work perfectly. Just wondering what this actually means though:

```
HorizSync     31-95
VertRefresh    50-60
```

I presume 50-60 is the refresh rate (mine is then set to 60, so why the 50?) and 31-95 somehow sets up the screen resolution - mine is now set to 1024x768. So how do you do other refresh rates and resolutions?

Also wondering what happens if I want to add a monitor in the future. Will X overide these new settings if it picks up a monitor first or do these settings need deleting?

---

### Post by steve.horsley on 2006-05-31
Yes, 50-60 is the vertical refresh rate, in refreshes per second. The time it takes to scan the whole screen from top to bottom.

The HorizSync is the number of horizontal lines per second, in kilohertz: 31000 - 95000 lines per second in the above case. Should be in your monitor manual. X documentation always comes with dire warnings that getting these numbers wrong can destroy your monitor and turn your first-born into a puddle of slime.

If you add a new monitor, you should correct these values or just delete them to let hardware discovery do its thing. There is a command something like
sudo dpkg reconfigure xserver-xorg
that will re-do the hardward discovery, ask lots of awkward questions and re-write your xorg.conf file.

---

### Post by Tim Thumb on 2006-05-31
Understood - thanks.

---

### Post by conro on 2006-05-31
The X.org config isn't going to effect your resolution over vnc.. it actually uses a different display then your monitor. you need to pass your desired resolution as an argument to the server as you start it..

logon to the remote box through ssh. then stop the vnc server, and start a new one with the desired resolution

```

conor@skank:~$ ssh conor@192.168.0.2
conor@slut:~$ killall vncserver
conor@slut:~$ vncserver -geometry 1024x768 :1
conor@slut:~$ exit
conor@skank:~$ vncviewer 192.168.0.2:1

```

look at the man pages if you need more info
```

prompt: man vncserver

```

---

### Post by n00b2ubuntu on 2006-06-04
If you used this guide to configure VNC:

[http://www.ubuntuforums.org/showthread.php?t=122402](http://www.ubuntuforums.org/showthread.php?t=122402)

Then you can change the screen resolution in the /etc/xinet.d/Xvnc file

e.g. -geometry 1024x768

---

### Post by nbateshaus on 2006-08-22
> **n00b2ubuntu said:**
> Then you can change the screen resolution in the /etc/xinet.d/Xvnc file

That's part of the beauty of using vino instead of Xvnc - since you're connected to a [ahem] *real* X server, you get to use the RANDR (Resize AND Rotate) extension, which allows you to dynamically resize your desktop as you VNC in from different machines.

I've run into other X extensions issues when using Xvnc (incl. the new vnc4server in dapper), largely things looking for the XFree86-Misc extension. Anyway, I've found that my (sadly, complicated) setup to allow me to VNC to my headless box running a real X server with vino meets all my needs; this tip was the final thing that made it go.

-nik

---

### Post by tehnad on 2008-03-12
> **steve.horsley said:**
> X seems to do hardware discovery every time it starts, and if it can't find the monitor details it defaults to 640x460. 

I think I found a way to stop that discovery. You have to enter a horizontal and vertical refresh range into the monitor section of /etx/X11/xorg.conf. Like this:
```
Section "Monitor"
        Identifier      "E-171"
        Option          "DPMS"
        HorizSync     31-95
        VertRefresh    50-60       
EndSection


```
Don't change any existing lines - just insert the horizontal and vertical sync lines. It may be a good idea to look up the frequencies of the monitor you intend to use when remote access breaks. Now you should be able to select a resolution you like and have it start that way without a monitor connected.

I realize that this thread is somewhat dead but this solution seems to be the correct one for the actual issue that this thread started over. I am using 7.10 Gusty and had the same issue happen with remote resolution when running headless. Modification of the "Monitor" section adding sync and refresh rates solved my problem on all three of the servers that I have tried it on. Thanks...

---

### Post by dark_phantom on 2008-03-12
I was looking for a way to log in remotely,  I will give VNC a try.

> **conro said:**
> The X.org config isn't going to effect your resolution over vnc.. it actually uses a different display then your monitor. you need to pass your desired resolution as an argument to the server as you start it..

logon to the remote box through ssh. then stop the vnc server, and start a new one with the desired resolution

```

conor@skank:~$ ssh conor@192.168.0.2
conor@slut:~$ killall vncserver
conor@slut:~$ vncserver -geometry 1024x768 :1
conor@slut:~$ exit
conor@skank:~$ vncviewer 192.168.0.2:1

```

look at the man pages if you need more info
```

prompt: man vncserver

```

Great hostnames! rofl

---

