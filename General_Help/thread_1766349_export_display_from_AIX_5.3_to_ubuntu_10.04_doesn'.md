---
title: "export display from AIX 5.3 to ubuntu 10.04 doesn't work"
date: 2011-05-24
forum: General Help
---

### Post by omatchu on 2011-05-24
[LEFT]Hello!

I need help. I'm am working on AIX 5.3. What I need to do is to use Netbackup window on my Ubuntu. When I try to export a simple xclock from AIX it's not working. If xclock is not working neither will Netbackup. Here is my configuration:
Ubuntu 10.04. Name: olma-laptop, ip: 192.168.2.150
AIX 5.3. Name: AIX1, ip: 192.168.2.12

. Here is what I'm doing on AIX:

# export DISPLAY=192.168.2.150:0.0
# xclock
Error: Can't open display: 192.168.2.150:0.0

I have searched through many forums without finding the solution. I've tried to:

- Open the port 23 (telnet) and 6000 (xwindow) with Firestarter
- Install a telnet server (just to check that my Lucid Lynx can be accessed
from AIX. And it's working!)
- Modify the file /etc/X11/xinit/xserverrc to allow Lucid to listen to port 6000.
To do that I have put the line "exec /usr/bin/X -nolisten tcp "$@"" as comment
- Use the command "xhost +" to allow connexion from any computer to my Lucid
- modify the file /etc/gdm/custom.conf to add the lines:
[security]
DisallowTCP=false
- shut down the firewall.
- starting xserver on AIX with the command: startx. Here is the output:
# startx
Please wait - starting your session
# 


I've done all of the above without success. I can add that when I run xclock on AIX
Firestarter does see the connection on port 6000 but nothing appears on my Lucid window.

I really need help has I'm trying to avoid the installation of Windows in dualboot :frown: !

Thanks for you help!

[/LEFT]

---

