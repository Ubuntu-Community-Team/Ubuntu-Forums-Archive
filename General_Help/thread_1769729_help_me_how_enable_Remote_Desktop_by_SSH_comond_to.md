---
title: "help me how enable Remote Desktop by SSH comond to use UltraVNC Viewe"
date: 2011-05-28
forum: General Help
---

### Post by thxyou on 2011-05-28
hello i am new in ubuntu to day i buy a detected server and the company give me just a SSH Information
and i dont like control my server by ssh  i want  use UltraVNC to see the full screen and easy control
i use serch i find this  [http://www.ehow.com/how_7301198_enable- … buntu.html]("http://www.ehow.com/how_7301198_enable-remote-desktop-ssh-ubuntu.html")
i login and i type my user and passord
and i type this to try enable Remote Desktop
"gconftool-2 -s -t bool /desktop/gnome/remote_access/prompt_enabled false" 
and i exit from my ssh and i open the  UltraVNC and i type the ip and i wati  but icant conect 
so i think i need forward the port 5900 or what ? 
if the anser is yes  help me how forward the port 5900 with ssh comand
I am stuck here...
help me  stpe by step
and sorry for my bad english

---

### Post by ram0042 on 2011-05-28
Does that server even have a GUI like GNOME or something. make sure it does by
```
ssh user@server
password
dpkg -i | grep gnome

```Now you know if it has one or not
then you may want to check for gconf2
```
dpkg -i | less gconf-editor
```If you have all those then that code should work.

Oh and do not forget step 5 on that website you provided. You need that code entered as well.

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> Does that server even have a GUI like GNOME or something. make sure it does by
```
ssh user@server
password
dpkg -i | grep gnome

```Now you know if it has one or not
then you may want to check for gconf2
```
dpkg -i | less gconf-editor
```If you have all those then that code should work.

Oh and do not forget step 5 on that website you provided. You need that code entered as well.
sir i am new  helpme stpe by step  i open now the  putty i type my ip server 
and i type my user and i type my passord  no what i do

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> sir i am new  helpme stpe by step  i open now the  putty i type my ip server 
and i type my user and i type my passord  no what i do
type
```
[FONT=monospace]
[/FONT]dpkg -l | grep gnome
```Tell me what you see

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> type
```
[FONT=monospace]
[/FONT]dpkg -l | grep gnome
```Tell me what you see
[IMG]http://imagupload.com/images/1306596766-help.jpg[/IMG]


now what i do

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> now what i do
Did anything show up for gnome? or Xorg?

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> Did anything show up for gnome? or Xorg?
i dont know what is  gnome? or Xorg?
you see in photo ?  I SEE WHAT  YOU  SEE

---

### Post by ram0042 on 2011-05-28
Okay, it looks like dpkg is not even installed. So try to install X for the server.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> i dont know what is  gnome? or Xorg?
you see in photo ?  I SEE WHAT  YOU  SEE
Gnome is the desktop environment. Xorg is the display manager.

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> Okay, it looks like dpkg is not even installed. So try to install X for the server.
```
sudo apt-get install ubuntu-desktop
```
[IMG]http://imagupload.com/images/1306597613-help2.jpg[/IMG]
what i do now

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> what i do now
type
```
sudo apt-get install gconf-editor
```

---

### Post by bodhi.zazen on 2011-05-28
I know it is not what you are asking, but I believe you are on the wrong path here.

First, VNC is notoriously insecure and tunneling over ssh is somewhat old school. FreeNX is better, learning to use ssh -X is probably best.

Second, you do not need a graphical interface to manage a server, and certainly not gnome desktop. You will not use most of these applications and managing a server is mostly done from the command line, either restarting services or editing configuration files, neither of which is particularly enhances by gnome.

In addition, gnome introduces additional potential security vulnerabilities (if you are running a server, you should consider each application you install as potentially introducing vulnerabilities and gnome introduces a number of applications you almost certainly will never use).

I manage all my servers (and yes I have managed a number of them over the years) via ssh + screen ;)

If you feel you need a graphical interface, take a look at the web interfaces. Webmin for example. phpmyadmin as another.

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> type
```
sudo apt-get install gconf-editor
```
[IMG]http://imagupload.com/images/1306597948-help3.jpg[/IMG]
what i do now

---

### Post by ram0042 on 2011-05-28
> **bodhi.zazen said:**
> I know it is not what you are asking, but I believe you are on the wrong path here.

First, VNC is notoriously insecure and tunneling over ssh is somewhat old school. FreeNX is better, learning to use ssh -X is probably best.

Second, you do not need a graphical interface to manage a server, and certainly not gnome desktop. You will not use most of these applications and managing a server is mostly done from the command line, either restarting services or editing configuration files, neither of which is particularly enhances by gnome.

In addition, gnome introduces additional potential security vulnerabilities (if you are running a server, you should consider each application you install as potentially introducing vulnerabilities and gnome introduces a number of applications you almost certainly will never use).

I manage all my servers (and yes I have managed a number of them over the years) via ssh + screen ;)

If you feel you need a graphical interface, take a look at the web interfaces. Webmin for example. phpmyadmin as another.
I was going to lead him to the Xclient path. He can foward X via ssh. I do this as well and I assumed he already had ubuntu-desktop installed and it has been installed previously,

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> [IMG]http://imagupload.com/images/1306597948-help3.jpg[/IMG]
what i do now
well, it looks like gconf-editor is installed.
try
```
startx
```

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> I was going to lead him to the Xclient path. He can foward X via ssh. I do this as well and I assumed he already had ubuntu-desktop installed and it has been installed previously,
you talk with me sir ?

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> you talk with me sir ?
no I was explaining to [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"). He says that the GUI stuff for the server is a bad idea and I agree but I'm only helping with what you want me to do

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> well, it looks like gconf-editor is installed.
try
```
startx
```
[IMG]http://imagupload.com/images/1306598515-help4.jpg[/IMG]
what i do now

---

### Post by ram0042 on 2011-05-28
After the **startx** code you try that code provided by the ehow website that you tried before.

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> After the **startx** code you try that code provided by the ehow website that you tried before.
sir  i dont know  what are  talking 
i am 
stuck here
[IMG]http://imagupload.com/images/1306598515-help4.jpg[/IMG]
what is do now

---

### Post by ram0042 on 2011-05-28
what does```
gconftool-2 -s -t bool /desktop/gnome/remote_access/prompt_enabled false
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```
produce in putty?

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> what does```
gconftool-2 -s -t bool /desktop/gnome/remote_access/prompt_enabled false
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```produce in putty?
[IMG]http://imagupload.com/images/1306599246-help5.jpg[/IMG]

produce in putty?  i dont know what you talk  if you ask me are use putty   yes  i use  putty

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> [IMG]http://imagupload.com/images/1306599246-help5.jpg[/IMG]

produce in putty?  i dont know what you talk  if you ask me are use putty   yes  i use  putty
Okay so it took the code and it is implemented. So does your ultraVNC pick up the server?

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> Okay so it took the code and it is implemented. So does your ultraVNC pick up the server?
sir what are you talking  i am new ubuntu pls help me becouse the suport of the company is not work to day

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> sir what are you talking  i am new ubuntu pls help me becouse the suport of the company is not work to day

Remember the program you use to control the server in full screen?

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> Remember the program you use to control the server in full screen?
this is UltraVNC Viewer
[IMG]http://imagupload.com/images/1306600614-help6.jpg[/IMG]

and wen i try to conect my server i see this  
[IMG]http://imagupload.com/images/1306600695-help7.jpg[/IMG]

so maby the port 5900 not open in my server or  what 

help me i dont like ssh  

i want use  UltraVNC Viewer  to see the screen and start control my server

so is bosible or  is  ajust a dream

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> this is UltraVNC Viewer
[IMG]http://imagupload.com/images/1306600614-help6.jpg[/IMG]

and wen i try to conect my server i see this  
[IMG]http://imagupload.com/images/1306600695-help7.jpg[/IMG]

so maby the port 5900 not open in my server or  what 

help me i dont like ssh  

i want use  UltraVNC Viewer  to see the screen and start control my server

so is bosible or  is  ajust a dream
type this into the server
```
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5900 -j ACCEPT
```
then try to connect again with ultravnc

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> type this into the server
```
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5900 -j ACCEPT
```then try to connect again with ultravnc

[IMG]http://imagupload.com/images/1306601404-help8.jpg[/IMG]
and i go to  UltraVNC Viewer and i try conect and not work  maby i must exit from ssh ferst ?

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> [IMG]http://imagupload.com/images/1306601404-help8.jpg[/IMG]
and i go to  UltraVNC Viewer and i try conect and not work  maby i must exit from ssh ferst ?
Okay, try it but I doubt it. If it doesnt work make sure you have the correct address. You said that the company is not at work today so is that an internal address or external address? Internal address is only valid when you are in the office.

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> okay, try it but i doubt it. If it doesnt work make sure you have the correct address. You said that the company is not at work today so is that an internal address or external address? Internal address is only valid when you are in the office.
i use the same ip i use him in ssh

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> i use the same ip i use him in ssh
Does the IP address fall in between one of these

10.0.0.0 – 10.255.255.255
172.16.0.0 – 172.31.255.255
192.168.0.0 – 192.168.255.255

If the IP falls in one of those groups, then you wont be able to connect to the server from outside the company office.

---

### Post by thxyou on 2011-05-28
> **ram0042 said:**
> Does the IP address fall in between one of these

10.0.0.0 – 10.255.255.255
172.16.0.0 – 172.31.255.255
192.168.0.0 – 192.168.255.255

If the IP falls in one of those groups, then you wont be able to connect to the server from outside the company office.

is her my ip server 
172.16.0.0 – 172.31.255.255

---

### Post by ram0042 on 2011-05-28
> **thxyou said:**
> is her my ip server 
172.16.0.0 &#8211; 172.31.255.255
Okay, I forgot you are able to connect to it via SSH. so the server is local right now right? or at least via VPN?

---

### Post by perspectoff on 2011-05-28
There are extensive instructions on tunneling VNC through SSH at Ubuntuguide:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#SSH](http://ubuntuguide.org/wiki/Ubuntu:Natty#SSH)

or Kubuntuguide:

[http://www.kubuntuguide.info/index.php/Natty#SSH](http://www.kubuntuguide.info/index.php/Natty#SSH)

If your business does not have FreeNX installed as their server, you won't be able to use FreeNX, so that advice is useless.

Also, if your company does not have a VPN server (or router) running, you won't be able to connect by VPN, either. Furthermore, a VPN client is different from both an SSH client and a VNC client.

Putty is a Windows SSH client (although there is a Linux version) and UltraVNC is a Java-based client mostly used in Windows. You need neither for Linux (and to use UltraVNC in Linux means you have to first install the Java environment, the overhead for which is not necessary merely to run VNC).

Almost all Linux distros have an SSH client included by default. It creates a secure tunnel through which a VNC viewer would be used. Both the Ubuntu and Kubuntu desktops have very nice VNC clients (Vinagre and Vino in Ubuntu and Krdc in Kubuntu) included. VNC is, of course, a GUI interface, not a text-based one. I agree with the advice to install on your server either the full Ubuntu desktop (sudo apt-get install ubuntu-desktop) or Kubuntu desktop (sudo apt-get install kubuntu-desktop) if you are going to be doing a lot of GUI stuff, anyway. You'll be happier in the long run unless you are trying to force a 486 to be your server, or something.

SSH requires either a security password or a security key to establish the connection (the latter is recommended), and then VNC started. This can be done with a single command (see Ubuntuguide or Kubuntuguide for details).

For example, if using Kubuntu's default ssh client and Krdc as the VNC client, the command would be

ssh -f -l serveruser -L 5900:127.0.0.1:5900 remoteserver.computer.xyz -p 22 sleep 5; krdc vnc://127.0.0.1::5900

assuming you have an SSH security key already established. In Ubuntu the procedure is the same, except use vinagre (or vino) instead of krdc. 


A method to establish an SSH tunnel automatically using a password would resemble:

expect -c 'spawn ssh -l clientuserID -L 5900:127.0.0.1:5901 remoteserver.computer.xyz -p 22; expect assword ; send "not#1sostrong\n" ; interact'

followed by the command to start the VNC client:

krdc vnc://127.0.0.1::5900

or

vinagre vnc://127.0.0.1::5900

To do this, of course, the expect utility must first be installed:
 sudo apt-get install expect

In the example the SSH password for the user "clientuserID" is "not#1sostrong".

---

### Post by ram0042 on 2011-05-28
> **perspectoff said:**
> There are extensive instructions on tunneling VNC through SSH at Ubuntuguide:

[http://ubuntuguide.org/wiki/Ubuntu:Natty#SSH](http://ubuntuguide.org/wiki/Ubuntu:Natty#SSH)

or Kubuntuguide:

[http://www.kubuntuguide.info/index.php/Natty#SSH](http://www.kubuntuguide.info/index.php/Natty#SSH)

If your business does not have FreeNX installed as their server, you won't be able to use FreeNX, so that advice is useless.

Also, if your company does not have a VPN server (or router) running, you won't be able to connect by VPN, either. Furthermore, a VPN client is different from both an SSH client and a VNC client.

Putty is a Windows SSH client (although there is a Linux version) and UltraVNC is mostly a Windows VNC client. You need neither for Linux.

Almost all Linux distros have an SSH client included by default. It creates a secure tunnel through which a VNC viewer would be used. Both the Ubuntu and Kubuntu desktops have very nice VNC clients (Vinagre and Vino in Ubuntu and Krdc in Kubuntu) included. VNC is, of course, a GUI interface, not a text-based one. I agree with the advice to install on your server either the full Ubuntu desktop (sudo apt-get install ubuntu-desktop) or Kubuntu desktop (sudo apt-get install kubuntu-desktop) if you are going to be doing a lot of GUI stuff, anyway. You'll be happier in the long run unless you are trying to force a 486 to be your server, or something.

SSH requires either a security password or a security key to establish the connection (the latter is recommended), and then VNC started. This can be done with a single command (see Ubuntuguide or Kubuntuguide for details).

For example, if using Kubuntu's default ssh client and Krdc as the VNC client, the command would be

ssh -f -l serveruser -L 5900:127.0.0.1:5900 remoteserver.computer.xyz -p 22 sleep 5; krdc vnc://127.0.0.1::5900

assuming you have an SSH security key already established. In Ubuntu the procedure is the same, except use vinagre (or vino) instead of krdc. 


A method to establish an SSH tunnel automatically using a password would resemble:

expect -c 'spawn ssh -l clientuserID -L 5900:127.0.0.1:5901 remoteserver.computer.xyz -p 22; expect assword ; send "not#1sostrong\n" ; interact'

followed by the command to start the VNC client:

krdc vnc://127.0.0.1::5900

or

vinagre vnc://127.0.0.1::5900

To do this, of course, the expect utility must first be installed:
 sudo apt-get install expect

In the example the SSH password for the user "clientuserID" is "not#1sostrong".
That sums it up but the man needs putty becuase he is on Windows

---

### Post by perspectoff on 2011-05-28
> **ram0042 said:**
> That sums it up but the man needs putty becuase he is on Windows

Then why is he asking us what the Linux commands are?

If he is setting up both a Linux server and the Windows clients, then I have to agree with FreeNX.

Using Putty as a client on Windows and OpenSSH as a server on Linux can require some tweaking and troubleshooting, because Putty hasn't traditionally used the OpenSSH key format (although I believe the newest version of Putty does accommodate OpenSSH keys).

Ubuntuguide's instructions for Putty are here:

[http://www.kubuntuguide.info/index.php/Natty#PuTTY](http://www.kubuntuguide.info/index.php/Natty#PuTTY)

I use Putty and UltraVNC on my Windows clients, and also start them with a single command (which I place as a Windows menu item). I don't do it often (since I don't use Windows often) and will have to look up the command on the laptop from which I do it. Putty requires a specific syntax when used from the Windows command-line (or as a menu item).

---

### Post by ram0042 on 2011-05-28
> **perspectoff said:**
> Then why is he asking us what the Linux commands are?

If he is setting up both a Linux server and the Windows clients, then I have to agree with FreeNX.

Using Putty as a client on Windows and OpenSSH as a server on Linux can require some tweaking and troubleshooting, because Putty hasn't traditionally used the OpenSSH key format (although I believe the newest version of Putty does accommodate OpenSSH keys).

Ubuntuguide's instructions for putty are here:

[http://www.kubuntuguide.info/index.php/Natty#PuTTY](http://www.kubuntuguide.info/index.php/Natty#PuTTY)
Yes I have used freeNX before and it was great but what he was after was vinagre running on the server.

I used Putty only for Windows Server 2008 on my lab but I have not tried with Linux. I use my IBMs Motherboard chip to virtualize automatically at my offices. They do not need configurations. I have installed many OSs on them from the BIOS to the CLI.

But in this guys case, I cannot figure out why it is not working.

---

### Post by perspectoff on 2011-05-28
Of course, there's the eternal problem of firewalls and ports.

SSH connections are traditionally port 22, but you can only have one port 22 connection per LAN.

I use non-standard ports for my SSH connections, so that each server on the LAN can be accessed by SSH via its own dedicated port.

Of course, that entails correct port-forwarding, etc.

---

### Post by ram0042 on 2011-05-28
> **perspectoff said:**
> Of course, there's the eternal problem of firewalls and ports.

SSH connections are traditionally port 22, but you can only have one port 22 connection per LAN.

I use non-standard ports for my SSH connections, so that each server on the LAN can be accessed by SSH via its own dedicated port.

Of course, that entails correct port-forwarding, etc.
my office has configured port fowarding for my SSH sessions, however, I have just been utilizing LogMeIn for the Windows machine also. It is a spare server that I test on that is outside the office's network(internally) but of course it is port:80 been used

---

### Post by thxyou on 2011-05-28
I do not understand what do you say I do not need to understand I want the easy way to control my server by  UltraVNC Viewer
is this inbosible 
i have just acses with ssh info and the suport company is not work to day 
so why ican enter with ssh and in UltraVNC Viewer icant  
i hate ssh  iwant easy way help me if you know

---

### Post by thxyou on 2011-05-28
help me i start hate ubuntu

---

### Post by linuxinstalledfromhdd on 2011-05-28
You need to use something like Teamviewer 6 instead at this point, if you are still having trouble. 

[http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/](http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/)

Cheers :D

---

### Post by thxyou on 2011-05-28
> **linuxinstalledfromhdd said:**
> You need to use something like Teamviewer 6 instead at this point, if you are still having trouble. 

[http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/](http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/)

Cheers :D
ok you want me Go to the airport and then traveled to the Netherlands
and i go to the my DedicatedServers and i open Firefox and i type TeamViewer in google and instal him and i wait  TeamViewer to load and take the id and passowrd 

and i go to airport and then traveled to the africa my hom and iopen my pc and i open TeamViewer and i put the id and the passord of my  DedicatedServers and itart control him 
and say yahoooooooooo is work now ?
:-x  people in rthis forum i say i have only acses ssh info and i want UltraVNC Viewer
if ther is way to instal  TeamViewer from ssh help me

---

### Post by blackgr on 2011-05-30
**Solution 1:**

Your pc: 
1) sudo apt-get install xtightvncviewer
2) Open port 5500 on your router

Your dedicated box (from ssh):
1) sudo apt-get install x11vnc

Your pc:
1) xtightvncviewer -bgr233 -listen

Your dedicated box(from ssh):
1) DISPLAY=:0.0 x11vnc -loop -connect IP
(where IP is your pc's wan ip)

**Solution 2:**

Just hate ubuntu and install something non free like windows. Using Xserver on a server is plain stupid. Just get a windows box and try not to pollute the forums with trash topics on UltraVNC etc

---

### Post by thxyou on 2011-05-31
> **blackgr said:**
> **Solution 1:**

Your pc: 
1) sudo apt-get install xtightvncviewer
2) Open port 5500 on your router

Your dedicated box (from ssh):
1) sudo apt-get install x11vnc

Your pc:
1) xtightvncviewer -bgr233 -listen

Your dedicated box(from ssh):
1) DISPLAY=:0.0 x11vnc -loop -connect IP
(where IP is your pc's wan ip)

**Solution 2:**

Just hate ubuntu and install something non free like windows. Using Xserver on a server is plain stupid. Just get a windows box and try not to pollute the forums with trash topics on UltraVNC etc

i send support of my company and he say 
use this command in ssh
vncserver :1 -geometry 1024x768 -depth 16 -pixelformat rgb565

and i open UltraVNC Viewer and i connect 

so why people here dont give me this comman befor long story :P

and i use ubuntu becouse is good for host game server 
and is hard for user why dont make him like a windows
why evry time need command and terminal instal  why why 
ex if you want no-ip you must intal him by comand 

pls make him easy for noob people like me :lolflag:

---

### Post by bodhi.zazen on 2011-05-31
> **thxyou said:**
> so why people here dont give me this comman befor long story :P

Because VNC is insecure and there are better options.

So yes while you just want your question answered, the best answer is to use an alternate solution.

ssh -X 
FreeNX

---

