---
title: "xstartup issues while using vncviewer"
date: 2011-06-22
forum: General Help
---

### Post by sunandi on 2011-06-22
I have installed vnc4server, but when I use vncviewer it shows me just a grey screen and nothing else.
This my xstartup file
!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#—————————–

#!/bin/sh

# Uncomment the following two lines for normal desktop:

unset SESSION_MANAGER
#gnome-session &
x-window-manager &

# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
 #[ -x $HOME/.vnc/xstartup ] && exec $HOME/.vnc/xstartup

[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources

xsetroot -solid grey

vncconfig -iconic &

xterm -geometry 80×24+10+10 -ls -title “$VNCDESKTOP Desktop” &
#twm &

please point me what is wrong

---

### Post by Toz on 2011-06-22
Which version/flavour of ubuntu are you using?

Maybe x-window-manager isn't properly starting a window manager. Try commenting out the line: > x-window-manager &
and add at the end of the file:```
gnome-session &
``` (assuming gnome is your window manager)

---

### Post by sunandi on 2011-06-22
I am uding ubuntu 11.04
I tried genome-session & also but didnt help

---

### Post by Toz on 2011-06-22
You mean **gnome-session &** right?

Try also commenting out the line:```
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
```

Can you post back the current contents of your .xstartup file? Where is your .xstartup file located? Which directory?

---

### Post by sunandi on 2011-06-22
My Current xstartup is :
----------------------------------------------------------------------------------------------------------
!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#—————————–

#!/bin/sh

# Uncomment the following two lines for normal desktop:

unset SESSION_MANAGER
gnome-session &
#x-window-manager &

# exec /etc/X11/xinit/xinitrc

#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
 #[ -x $HOME/.vnc/xstartup ] && exec $HOME/.vnc/xstartup

[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources

xsetroot -solid grey

vncconfig -iconic &

xterm -geometry 80×24+10+10 -ls -title “$VNCDESKTOP Desktop” &
#twm &
--------------------------------------------------------------------------------------------------------------

Directory Is: /home/sunandi/.vnc/xstartup

---

### Post by Toz on 2011-06-22
Try moving the gnome-session command to the end:
```
#!/bin/sh
unset SESSION_MANAGER
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80×24+10+10 -ls -title “$VNCDESKTOP Desktop” &
gnome-session &
```

Also, make sure your .xstartup file is executable.

---

### Post by sunandi on 2011-06-22
I copied what you gave to my xstartup but it still didnt work!!!

sunandi@ubuntu:~$ ll ~/.vnc/xstartup
-rwxr-xr-x 1 sunandi sunandi 208 2011-06-23 06:49 /home/sunandi/.vnc/xstartup*

---

### Post by Toz on 2011-06-22
In your ~/.vnc directory there should be a log file. Can you post back the contents of the file?

Can you also confirm that vnc4server is running:```
ps -ef | grep vnc
```

And lastly, which computer has the server component installed and from which computer are you trying to connect?

---

### Post by sunandi on 2011-06-22
sunandi@ubuntu:~$ cat ~/.vnc/xstartup
#!/bin/sh
unset SESSION_MANAGER
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80×24+10+10 -ls -title “$VNCDESKTOP Desktop” &
gnome-session &


-=============
sunandi@ubuntu:~$ ps -ef | grep vnc
sunandi   1951     1  3 06:49 pts/0    00:01:17 Xvnc4 :1 -desktop ubuntu:1 (sunandi) -auth /var/run/gdm/auth-for-sunandi-ZifTBZ/database -geometry 1024x768 -depth 16 -rfbwait 30000 -rfbauth /home/sunandi/.vnc/passwd -rfbport 5901 -pn -fp /usr/X11R6/lib/X11/fonts/Typeg wheth1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb
sunandi   1957     1  0 06:50 pts/0    00:00:01 vncconfig -iconic
sunandi  11004  1781  0 07:32 pts/0    00:00:00 grep --color=auto v


================
Both the machines are same, I am just testing whether the vncserver configurations are correct or not.
Vnc server is running!

---

### Post by Toz on 2011-06-22
What about the vnc log file in your ~/.vnc folder? Does it say anything that might be helpful?

---

### Post by sunandi on 2011-06-23
My sincere appology... i missed to give the vnc logs
I am pasting the logs here

Thanks a lot for helping me to narrow down the issue


=====================================================================================
[email]sunandi@ubuntu:~/.vnc[/email]$ cat ubuntu:1.log

Xvnc Free Edition 4.1.1 - built Apr  9 2010 18:47:36
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Thu Jun 23 07:34:30 2011
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
gnome-session[418]: WARNING: Failed to acquire org.gnome.SessionManager
xterm:  bad command line option "(sunandi)"

usage:  xterm [-/+132] [-C] [-Sccn] [-T string] [-/+ah] [-/+ai] [-/+aw]
    [-b number] [-/+bc] [-bcf milliseconds] [-bcn milliseconds] [-bd color]
    [-/+bdc] [-bg color] [-bw number] [-/+cb] [-cc classrange] [-/+cjk_width]
    [-class string] [-/+cm] [-/+cn] [-cr color] [-/+cu] [-/+dc]
    [-display displayname] [-e command args ...] [-fa pattern] [-fb fontname]
    [-/+fbb] [-/+fbx] [-fd pattern] [-fg color] [-fi fontname] [-fn fontname]
    [-fs size] [-fw fontname] [-fwb fontname] [-fx fontname] [%geom] [#geom]
    [-geometry geom] [-help] [-/+hm] [-/+hold] [-iconic] [-/+ie] [-/+im]
    [-into windowId] [-/+j] [-/+k8] [-kt keyboardtype] [-/+l] [-/+lc]
    [-lcc path] [-leftbar] [-lf filename] [-/+ls] [-/+maximized] [-/+mb]
    [-mc milliseconds] [-/+mesg] [-/+mk_width] [-ms color] [-n string]
    [-name string] [-nb number] [-/+nul] [-/+pc] [-/+pob] [-rightbar] [-/+rv]
    [-/+rvc] [-/+rw] [-/+s] [-/+samename] [-/+sb] [-selbg color] [-selfg color]
    [-/+sf] [-/+si] [-/+sk] [-sl number] [-/+sm] [-/+sp] [-/+t] [-ti termid]
    [-title string] [-tm string] [-tn name] [-/+u8] [-/+uc] [-/+ulc] [-/+ulit]
    [-/+ut] [-/+vb] [-version] [-/+wc] [-/+wf] [-xrm resourcestring]
    [-ziconbeep percent]

Type xterm -help for a full description.


Thu Jun 23 07:34:36 2011
 Connections: accepted: 0.0.0.0::45441
 SConnection: Client needs protocol version 3.8
 SConnection: Client requests security type VncAuth(2)

Thu Jun 23 07:34:38 2011
 VNCSConnST:  Server default pixel format depth 16 (16bpp) little-endian rgb565
 VNCSConnST:  Client pixel format depth 6 (8bpp) rgb222
 VNCSConnST:  Client pixel format depth 24 (32bpp) little-endian rgb888
gnome-session[418]: Gtk-CRITICAL: IA__gtk_main_quit: assertion `main_loops != NULL' failed
gnome-session[418]: WARNING: GSIdleMonitor: Unable to initialize Sync extension
GNOME_KEYRING_CONTROL=/tmp/keyring-efrfMH
SSH_AUTH_SOCK=/tmp/keyring-efrfMH/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-efrfMH
SSH_AUTH_SOCK=/tmp/keyring-efrfMH/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-efrfMH
SSH_AUTH_SOCK=/tmp/keyring-efrfMH/ssh

** (gnome-settings-daemon:432): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:432): WARNING **: Could not acquire name
Window manager warning: Log level 32: could not find XKB extension.
Cannot register the panel shell: there is already one running.

** (process:437): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

** (bluetooth-applet:442): WARNING **: Applet is already running, exiting
Failed to play sound: File or data not found
The program 'gnome-power-manager' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 103 error_code 1 request_code 149 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

** (polkit-gnome-authentication-agent-1:452): WARNING **: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Cannot register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject

** (nm-applet:440): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

An instance of nm-applet is already running.

Thu Jun 23 07:34:45 2011
 Connections: closed: 0.0.0.0::45441 (Clean disconnection)
 SMsgWriter:  framebuffer updates 13
 SMsgWriter:    hextile rects 10, bytes 37448
 SMsgWriter:    ZRLE rects 2, bytes 2214
 SMsgWriter:    raw bytes equivalent 4292816, compression ratio 108.234986

** (gnome-screensaver:1356): WARNING **: screensaver already running in this session
Failure: Module initalization failed

(nautilus:27414): Unique-DBus-WARNING **: Error while sending message: Connection was disconnected before a reply was received
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
=====================================================================================

---

### Post by Toz on 2011-06-23
Doesn't look like gnome-session is working. Try this in your .xstartup file:```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
. /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
```

Make sure you restart the vncserver service.

Also, are you using the unity interface? Any chance you can try with just the classic interface and see if it connects?

---

### Post by sunandi on 2011-06-23
You are simply Awesome !!!!
It worked :-)

BUT

When I tried to vnc from my windows machine it couldnt connect. It posps following error
"Reading Version Failed: not an RFB server?"
Do you wish to attempt to reconnect to ubunt:1

but it is working when I try to vnc from the same machine

---

### Post by sunandi on 2011-06-23
Ya and also it is not Unity its the classic desktop

---

### Post by Toz on 2011-06-23
We're almost there....
> **sunandi said:**
> When I tried to vnc from my windows machine it couldnt connect. It posps following error
"Reading Version Failed: not an RFB server?"
Do you wish to attempt to reconnect to ubunt:1

but it is working when I try to vnc from the same machine

What command do you enter when connecting from the same machine?
What command (or parameters) are you using when connecting from the Windows machine?

Your server is listening on port 5901. Did you specify this in the Windows client and does your ubuntu box have a firewall enabled?```
sudo ufw status
```

Also, the following might help as well:```
sudo netstat -tupan | grep LISTEN
```

---

### Post by sunandi on 2011-06-23
sunandi@ubuntu:~/Kernel_View$ sudo ufw status
[sudo] password for sunandi: 
Status: inactive
sunandi@ubuntu:~/Kernel_View$ sudo netstat -tupan | grep LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      818/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      899/cupsd       
tcp6       0      0 :::22                   :::*                    LISTEN      818/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      899/cupsd       
sunandi@ubuntu:~/Kernel_View$ 

I am trying to open the vnc from a windows machine
I tried 
1. ubuntu:1:5901
2. ubuntu:1

and both didnt work with same error message

---

### Post by Toz on 2011-06-23
Hmmmm. It doesn't look like vnc is listening. Try these:
```
ps -ef | grep -i vnc | grep -v grep
sudo netstat -a | grep 5901
sudo netstat -a | grep -i vnc
```

On your windows machine, does the hostname **ubuntu** resolve to the proper ip address:```
ping ubuntu
```

You can also try connecting to:
```
ubuntu:5901
```
or
```
xxx.xxx.xxx.xxx:5901
```
where xxx.xxx.xxx.xxx is ubuntu's ip address.

---

### Post by sunandi on 2011-06-23
Hmmmm. It doesn't look like vnc is listening. Try these:
ps -ef | grep -i vnc | grep -v grep
sudo netstat -a | grep 5901
sudo netstat -a | grep -i vnc
---------------Output-----------------
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ ps -ef | grep -i vnc | grep -v grep
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ sudo netstat -a | grep 5901
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ sudo netstat -a | grep -i vnc
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 

Note: all three didnt give any output
----------------------------------------

On your windows machine, does the hostname **ubuntu** resolve to the proper ip address:ping ubuntu
[sunandi] Yes my windows client machine is able to ping ubuntu

You can also try connecting to:
ubuntu:5901 or
[sunandi] Same error
xxx.xxx.xxx.xxx:5901 where xxx.xxx.xxx.xxx is ubuntu's ip address.
[sunandi] Nothing happened

---

### Post by Toz on 2011-06-23
In your previous post #9, vncserver was running (see results of ps -ef | grep vnc command). Try starting up the vnc server on the ubuntu machine and running the commands from post 17 again.

---

### Post by sunandi on 2011-06-23
Yeah it wasnt up!! but I started the server and still windows client giving the same error

sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ ps -ef | grep -i vnc | grep -v grep
sunandi  17781     1  0 Jun23 pts/0    00:00:00 Xvnc4 :1 -desktop ubuntu:1 (sunandi) -auth /home/sunandi/.Xauthority -geometry 1024x768 -depth 16 -rfbwait 30000 -rfbauth /home/sunandi/.vnc/passwd -rfbport 5901 -pn -fp /usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/Speedo/,/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ sudo netstat -a | grep 5901
tcp6       0      0 [::]:5901               [::]:*                  LISTEN     
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ sudo netstat -a | grep -i vnc
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ 



Thanks for keeping the patience till now... i really appriciate and thanksful to u

---

### Post by Toz on 2011-06-23
> **sunandi said:**
> sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ sudo netstat -a | grep 5901
tcp6       0      0 [::]:5901               [::]:*                  LISTEN     


Its listening on ipv6 (not ipv4). How do you startup vncserver? What command do you use?

---

### Post by sunandi on 2011-06-23
I just gave this
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$ vncserver

New 'ubuntu:1 (sunandi)' desktop is ubuntu:1

Starting applications specified in /home/sunandi/.vnc/xstartup
Log file is /home/sunandi/.vnc/ubuntu:1.log
sunandi@ubuntu:~/Kernel_View/ubuntu-natty$

---

### Post by Toz on 2011-06-23
I've been researching this and have found out that vnc4server, for some reason, only binds to ipv6 (upstream changes?). I haven't been able to find why or how. However, the tightvncserver package successfully binds to ipv4. 

I suggest removing the package **vnc4server** and installing **tightvncserver**. The packages are similar. Just tested it here successfully.

It should then work.

---

### Post by sunandi on 2011-06-24
Even thightvncserver is not working :-(

sunandi@ubuntu:~$ sudo netstat -a | grep 5901
tcp        0      0 *:5901                  *:*                     LISTEN 

Now its ipv4.

sunandi@ubuntu:~$ vncserver

New 'X' desktop is ubuntu:1

Starting applications specified in /home/sunandi/.vnc/xstartup
Log file is /home/sunandi/.vnc/ubuntu:1.log

sunandi@ubuntu:~$ sudo netstat -a | grep 5901
tcp        0      0 *:5901                  *:*                     LISTEN  
   
sunandi@ubuntu:~$ ps -ef | grep -i vnc | grep -v grep
sunandi  18334     1  0 11:18 pts/0    00:00:00 Xtightvnc :1 -desktop X -auth /home/sunandi/.Xauthority -geometry 1024x768 -depth 24 -rfbwait 120000 -rfbauth /home/sunandi/.vnc/passwd -rfbport 5901 -fp /usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb
sunandi@ubuntu:~$ 
sunandi@ubuntu:~$ sudo netstat -a | grep -i vnc
sunandi@ubuntu:~$ 
sunandi@ubuntu:~$ 



It gives the same error

---

### Post by Toz on 2011-06-24
Please post back the contents of **/home/sunandi/.vnc/ubuntu:1.log**
How are you connecting from Windows? Are you using name or ip address? Exactly what happens when you try? Any error messages on Windows box?

---

### Post by sunandi on 2011-06-24
My Bad the IP address worked :-)
Thanks a hell lot to You Toz..... its working great

Learned a lot in last few days :-)

I am new to ubunu, so will have many more questions... hope I will get your remarkable help on those querries to!!
Thanks again

---

### Post by Toz on 2011-06-24
Glad to hear it worked. I learned something as well - vnc4server only binds to ipv6 by default. Now I need to find out why.

Anyways, if you don't mind, can you flag this thread as Solved from the "Thread Tools" link above?

---

### Post by Toz on 2011-06-24
Just a follow-up note. Found that vnc4server is actually listening on both ipv4 & ipv6:> $ netstat -tupan | grep vnc
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      24967/Xvnc4     
tcp6       0      0 :::5901                 :::*                    LISTEN      24967/Xvnc4     


The interesting thing is that the default port 5901 is bound to ipv6 whereas port 6001 is bound to ipv4. Connecting to the ipv4 listener would require connecting to port 6001 (not 5901).

Interesting.

---

### Post by sunandi on 2011-06-27
Hi Toz,
Need your expertize in another thread ([COLOR=#980101]****[/COLOR] 			 			[/etc/lilo.conf file not found in ubuntu 11.04]("http://ubuntuforums.org/showthread.php?t=1786865"))
Can you please respond, it will be very helpful to me :-)

---

