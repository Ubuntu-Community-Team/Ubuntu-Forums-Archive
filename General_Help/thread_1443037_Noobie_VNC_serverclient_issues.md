---
title: "Noobie VNC server/client issues"
date: 2010-03-30
forum: General Help
---

### Post by majicdj1 on 2010-03-30
First of all, let me say that I am sure I am not the only one with this problem.  I'll give you the most background info I can because I believe the fix is very simple. I am just a ubuntu noob currently learning :)
Both machines are on a local network, I am not wishing to connect thru the internet. I just want to connect locally.
 
 1> I would like to access my ubuntu 9.10 desktop using my Win xp machine.  
2> I have configured the remote desktop server in ubuntu by checking both of the "sharing" boxes and entering a password.  I cannot find a way to set the connection port via the GUI because I have no "Advanced" tab as listed in most of the threads I have found here in the forums.
I assume that after configuring this that means the server is active.
 
3> i have installed Tight VNC as well as Real VNC on my WinXP machine. And when I run them and attempt to connect using the ip address of the ubuntu machine (192.168.0.111) it does not connect.
I have tried viewing 192.168.0.111 and also tried 192.168.0.111:5900. From what I have read I believe the default port for vnc is 5900.
My error is:  "Unable to connect to host." when using Real VNC and Tight VNC is "Failed to connect to server."
 
There is obviously something simple I am missing so point me in the right direction please. TY

---

### Post by rbc on 2010-03-30
1. Where you checked the boxes, that was System-->Preferences-->Remote Desktop?
I probably won’t be able to help you beyond this, but try these things to diagnose.
2. Can you ping the Ubuntu machine?
3. Install nmap, then go to terminal and issue this command to make sure 5900 is open:
*sudo nmap –sS –O 127.0.0.1*

---

### Post by majicdj1 on 2010-04-01
Well, port 5900 is indeed open... What's next?  :)
I'm gonna keep searching and reading...  I've learned alot so far just attempting to fix this issue.  Any continued help is greatly appreciated.
I have also determined that I CANNOT ping the unbuntu machine (192.168.0.111) from my windows xp machine.  As far as I can tell, my router has its firewall turned off too. I'm gonna double check that now just in case.

---

### Post by majicdj1 on 2010-04-01
I also installed the firestarter GUI to make sure the firewall in unbuntu is turned off.  I installed the gui for nmap to double check the fact that port 5900 is open on the unbuntu machine.  I know I am getting closer to fixing the issue....  One more push in the right direction. :)

---

### Post by majicdj1 on 2010-04-01
Update:  I can now ping the ubuntu server from my xp machine.  I can also log into the xp server from ubuntu,  all I gotta do now is make it work in the other direction and I'll be golden :)  So close.... argh!!  I can also log into the vnc server on ubuntu from the ubuntu terminal so I know the server is working.  I still cannot log into the ubuntu vnc server from my xp machine though...  someone please help!!   I HAVE to me missing something obvious.. TY TY

---

### Post by majicdj1 on 2010-04-02
Well, I finally got it going. Instead of using the port number I used the desktop number instead of the port number.  Now i would like to find out how to view the actual active desktop instead of starting a new one.  I wish i could explain that better so I hope that you understand my question.
 
TY in advance.  Ubuntu is fun!  :)

---

### Post by new_tolinux on 2010-04-02
As I did here:
Ubuntu 9.04 System - Preferences - Remote Desktop (can be slightly different, I'm not using English language)
Ticked: "Allow others to view your desktop" and "Allow others to use your desktop" (again: can be slightly different, I'm not using English language).
Unticked: Ask permission
Ticked: Ask the user for a password.
Unticked: Configure network....

Firestarter is a non-issue here, because I allowed full access to the IP-adress of my Windows desktop.

Using realvnc client I only have to enter the machine-name or the IP-adress of the machine. After that, VNC asks for a password and then I'm logged in to the current session.

The only thing I can't do (yet) is using remote desktop before I logged in physically on my Ubuntu machine.

---

### Post by majicdj1 on 2010-04-03
that still created a new desktp for me.  I would like to see same active desktop that i see on monitor connected to linux box.  I'll keep reading and working on it.  TY for all the help so far :)

---

