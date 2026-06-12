---
title: "x2go stopped working"
date: 2011-10-19
forum: General Help
---

### Post by exsysprog on 2011-10-19
I'm at a bit of a loss.  I set up an x2go client on Windows7 to log into my 11.04 machine.  All was well for past two days. Today I go to fire up my windows client session and it says "can't start x server. please check your settings".  the xming x11 server is where it's supposed to be according to the path in the settings.  If I navigate to it and double click on it it brings up a xterminal (not connected to anything) as I would expect.  I've searched around to no avail.

Any x2go experience / advice ??

---

### Post by Reno_1 on 2011-11-25
I have the same problem :
client : Windows 7
server : Ubuntu 11.10

When I try to connect : "Can't start X Server. Please check your settings". And these are the default settings!

Nobody finds out what's blocking?

EDIT : Yes!!! I just tried something and it seems to solve the problem. In the settings, there's a field name "command", its value was (for me) : C:\Program Files\Xming\Xming.exe
So I thought : may be the space caractere is causing trouble.
==> I reinstalled XMing in C:\Xming and modify x2go setting (not directly the "command" field, but the "working directory field") and now it "works"!! (yes, I putted some " " 'cause now, I just have other issues about RSA keys etc..)

Tell me if it worked for you ;)

---

### Post by exsysprog on 2012-01-03
Thanks REno .. I've been tied up for a while but I will take a look at this again and post results here.

---

### Post by BenPope on 2012-01-04
I couldn't log in to my Ubuntu 11.10 installation from Windows or Ubuntu 11.10 and I had a different error to you, so I don't think this fixes it.

I should say that this used to work, and I'm doing it through ssh, and I can ssh into the machine just fine.

OK, just tried to connect locally to my own machine, I get the same problem as remotely:

Dialog Box:
X2Go - 51
The connection with the remote server was shut down.
Please check the state of your network connection.
[OK]

Console output:
start new ssh connection 

setting SSH DIR to  "/home/ben/ssh" 
ssh connection ok 

continue normal x2go session 

"x2gostartagent 800x600 adsl 16m-jpeg-9 unix-kde-depth_24 us pc105/us 1 D GNOME" 

Agent output: "52
de3ca0c7fa5dcc7845e7d720a09a4882
26180
ben-52-1325674967_stDGNOME_dp24
30001
30002
30003
" 
starting nxproxy with:  "nxproxy -S nx/nx,options=/home/ben/.x2go/S-ben-52-1325674967_stDGNOME_dp24/options:52" 

"
NXPROXY - Version 3.5.0

Copyright (C) 2001, 2011 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '26224'.
Session: Starting session at 'Wed Jan  4 19:02:48 2012'.
Info: Connecting to remote host 'localhost:31001'.
Info: Connection to remote proxy 'localhost:31001' established.
" 

Generating public/private rsa key pair.
Your identification has been saved in /home/ben/.x2go/ssh/gen/key.c23334.
Your public key has been saved in /home/ben/.x2go/ssh/gen/key.c23334.pub.
The key fingerprint is:
<snip>
The key's randomart image is:
+--[ RSA 1024]----+
<snip>
key created on:  "/home/ben/.x2go/ssh/gen/key.c23334" 
starting fs tunnel for: "ben-52-1325674967_stDGNOME_dp24" 
fs port:  "30003" 
setting SSH DIR to  "/home/ben/ssh" 
setting SSH DIR to  "/home/ben/ssh" 
exported key  "/home/ben/.x2go/ssh/gen/key.c23334" 
key removed 
"Info: Connection with remote proxy completed.
" 

"Warning: Unrecognized session type 'unix-kde-depth_24'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_24'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Session: Session started at 'Wed Jan  4 19:02:49 2012'.
" 

"Info: Established X server connection.
" 

"Info: Using shared memory parameters 1/2048K.
" 

"Error: Failure reading from the peer proxy.
" 

"Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Terminating session at 'Wed Jan  4 19:02:49 2012'.
Session: Session terminated at 'Wed Jan  4 19:02:49 2012'.
" 

deleting proxy 

nxproxy not running 

proxy deleted 

check command message




On the server: /var/log/auth.log

Jan  4 22:01:49 yyls03 sshd[20261]: Accepted password for ben from w.x.y.z port 53077 ssh2
Jan  4 22:01:49 yyls03 sshd[20261]: pam_unix(sshd:session): session opened for user ben by (uid=0)
Jan  4 22:01:53 yyls03 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session9 (system bus name :1.61 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_HK.UTF-8)
Jan  4 22:01:53 yyls03 polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session9 (system bus name :1.61, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_HK.UTF-8) (disconnected from bus)
Jan  4 22:01:54 yyls03 su[20874]: Successful su for ben by root
Jan  4 22:01:54 yyls03 su[20874]: + ??? root:ben
Jan  4 22:01:54 yyls03 su[20874]: pam_unix(su:session): session opened for user ben by (uid=0)
Jan  4 22:01:55 yyls03 su[20874]: pam_unix(su:session): session closed for user ben
Jan  4 22:01:55 yyls03 sshd[20261]: pam_unix(sshd:session): session closed for user ben

---

### Post by BenPope on 2012-01-30
Well, things changed a bit since there have been a bunch of updates to x2go... I could log in, but not get any menus.

Anyway, I found something here:
[http://www.nomachine.com/tr/view.php?id=TR10I02623]("http://www.nomachine.com/tr/view.php?id=TR10I02623")

Specifcally, Unity 3D doesn't work, to get Unity 2D do:
```
sudo rm /tmp/unity_support_test.*
```

Then it works.

---

### Post by king.crimson on 2012-03-18
In order to connect to a server in Unity 2D session, you can also explicitly order x2go client in the session type, without changing anything in the server.

In the session type select 'Custom desktop' and add the following in the command:
```
gnome-session --session=ubuntu-2d
```

---

