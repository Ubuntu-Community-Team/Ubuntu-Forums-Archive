---
title: "Kinda Broke X-Server"
date: 2006-06-14
forum: General Help
---

### Post by BetaMaster on 2006-06-14
Okay, so I recently installed XGL. It worked, but was glitchy. So I tried uninstalling it. Unfortunately, there's no INSTRUCTIONS to uninstall XGL on the interweb, so I was reading back through instructions in reverse, trying to fix it. In the end, I broke X-server.
When I start up, I get the prompt. I type 'startx' and get this error:
```
xauth: creating new authority file /home/sven/.xserverauth.5834
xauth: creating new authority file /home/sven/.Xauthority
xauth: creating new authority file /home/sven/.Xauthority

X: cannot read /etc/X11/X symbolic link (Invalid argument), aborting.
<pause> giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.
sven@ubuntu:~$ _   (Only included that to show that it finished)
```
Ooookay, so, any ideas? I've reinstall x11-common, and that didn't fix anything. I seriously screwed this up. Without reinstalling Ubuntu, can anyone give advice on how to fix this?

Thanks in advance!

---

### Post by BetaMaster on 2006-06-14
I don't like doing this, but I would really like a response to this...Please, anyone?

---

### Post by joshrobinson on 2006-06-14
[QUOTE=BetaMaster]I don't like doing this, but I would really like a response to this...Please, anyone?[/QUOTE]

have you tried

```
sudo ln -sf /usr/bin/Xorg /etc/X11/X
```

then 
```
startx
```

if that doesnt work try reconfiguring the original xserver
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kvonb on 2006-06-14
I'm not an expert but you sound a little desperate so I'll try to help you :)

It looks like the symbolic link "X" is not pointing to the correct executable, my "X" link points to /usr/bin/Xorg.

Try this from the command line:

sudo mv /etc/X11/X /etc/X11/old_X
sudo ln -s /usr/bin/Xorg /etc/X11/X 

Then type X and then enter, it should start X, if not, you might want to follow the chain, ie look at /usr/bin/Xorg and see if it is actually there (it is a 1.5mb executable on my machine).

Hope this helps,

Regards,

Kev :)

---

### Post by BetaMaster on 2006-06-14
[QUOTE=joshrobinson]have you tried

```
sudo ln -sf /usr/bin/Xorg /etc/X11/X
```

then 
```
startx
```

if that doesnt work try reconfiguring the original xserver
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]
I tried this, and it worked! I had to reconfigure the xserver, but it's working now! Thanks!

However, XGL is still installed. Does anybody have any advice for uninstalling XGL?

---

### Post by joshrobinson on 2006-06-14
[QUOTE=BetaMaster]I tried this, and it worked! I had to reconfigure the xserver, but it's working now! Thanks!

However, XGL is still installed. Does anybody have any advice for uninstalling XGL?[/QUOTE]

did you make changes to your gdm.conf and gdm.conf-custom files when installing xgl?

you really dont have to remove xgl unless you want to make room for other things to be installed.. but xgl and compiz arent really big in size

if you did change your gdm.conf and gdm.conf-custom you should go back and change it back to normal, it might not start x correctly when you reboot
if you reboot the computer and X starts up fine, i would just leave it how it is

---

### Post by BetaMaster on 2006-06-14
[QUOTE=joshrobinson]did you make changes to your gdm.conf and gdm.conf-custom files when installing xgl?

you really dont have to remove xgl unless you want to make room for other things to be installed.. but xgl and compiz arent really big in size

if you did change your gdm.conf and gdm.conf-custom you should go back and change it back to normal, it might not start x correctly when you reboot
if you reboot the computer and X starts up fine, i would just leave it how it is[/QUOTE]
Well, I'm in Ubuntu now. XGL still is installed, but it's working fine, without the bugs I was getting before (Windows kept going black and staying black, the entire window would be solid black), so I guess I don't need to uninstall it anymore :D
Is it common for Ubuntu to hang on loading Window Manager, the fourth item, when the desktop is loading, every time? I can still run programs, but that window stays open in the background for 5-10 minutes.

---

### Post by joshrobinson on 2006-06-14
[QUOTE=BetaMaster]Well, I'm in Ubuntu now. XGL still is installed, but it's working fine, without the bugs I was getting before (Windows kept going black and staying black, the entire window would be solid black), so I guess I don't need to uninstall it anymore :D
Is it common for Ubuntu to hang on loading Window Manager, the fourth item, when the desktop is loading, every time? I can still run programs, but that window stays open in the background for 5-10 minutes.[/QUOTE]

well with the symbolic link we replaced, with the sudo ln -sf command, you arent in Xgl right now, you are using the standard X, but reboot your computer and see if it starts X up normally again.. so we can go from there

as for the window manager thing staying open, thats weird and doesnt happen to me.. if you click the splash screen it should go away for you.. what are yoru comptuer specs?

---

### Post by BetaMaster on 2006-06-15
[QUOTE=joshrobinson]well with the symbolic link we replaced, with the sudo ln -sf command, you arent in Xgl right now, you are using the standard X, but reboot your computer and see if it starts X up normally again.. so we can go from there

as for the window manager thing staying open, thats weird and doesnt happen to me.. if you click the splash screen it should go away for you.. what are yoru comptuer specs?[/QUOTE]
I know I shouldn't be in XGL right now, but I have the spinning cube while switching workspaces, I have the liquidy-cloth-effects for dragging windows, and I have the window-tiler for F12. I'm in XGL.
I haven't tried clicking the spash screen, I'll have to try that.
My specs are:
Ubuntu Dapper Drake 6.06 (obviously)
1.00 GB RAM
GeForce 6600GT 128 MB
P4 2.67 GHz CPU

---

### Post by joshrobinson on 2006-06-15
[QUOTE=BetaMaster]I know I shouldn't be in XGL right now, but I have the spinning cube while switching workspaces, I have the liquidy-cloth-effects for dragging windows, and I have the window-tiler for F12. I'm in XGL.
I haven't tried clicking the spash screen, I'll have to try that.
My specs are:
Ubuntu Dapper Drake 6.06 (obviously)
1.00 GB RAM
GeForce 6600GT 128 MB
P4 2.67 GHz CPU[/QUOTE]

you must have edited your gdm.conf files then for it to still start xgl.. thats good that it works now though :-p i wish xgl would work right on my computers

---

### Post by BetaMaster on 2006-06-15
[QUOTE=joshrobinson]you must have edited your gdm.conf files then for it to still start xgl.. thats good that it works now though :-p i wish xgl would work right on my computers[/QUOTE]
Yeah, I did edit my gdm.conf files, I believe. I went through like four instructional sites before I got it to work. I probably borked something along the lines, and shouldn't have used so many methods. Oh well, it works not. Thanks for the help, everyone!

---

