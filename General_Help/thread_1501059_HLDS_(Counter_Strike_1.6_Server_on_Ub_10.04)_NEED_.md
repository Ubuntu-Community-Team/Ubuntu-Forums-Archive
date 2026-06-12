---
title: "HLDS (Counter Strike 1.6 Server on Ub 10.04) NEED HELP! :("
date: 2010-06-03
forum: General Help
---

### Post by xaxtree on 2010-06-03
Well I searched for a while before making this post, and not many people are receiving the same error as me.  I don't know if many people know about HLDS or half life dedicated server and linux, either way it's worth a try to ask for help.

I setup the server just find with Metamod and amxmodx, everything works other than it won't let my server connect outside of my lan.  I forwarded every single necessary port for HLDS and steam on my DIR-655 xtreme n-gigabit router, most up to date firmware as well. 

I've tried numerous ways of of starting up my server

here is what happens:
```
root@xyz:/home/d3adc0d3/server_cs# ./hlds_run -game cstrike -autoupdate +maxplayers 15 +map de_dust2 +port 27015 +ip 71.224.xxx.xxx +exec server.cfg -sv_lav 0
Auto detecting CPU
Using Pentium II Optimised binary.
Auto-restarting the server on crash
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Checking/Installing 'Counter-Strike Base Content' version 35


Checking/Installing 'Linux Server Engine' version 54


Checking/Installing 'Half-Life Base Content' version 12


HLDS installation up to date
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 70 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 0 multi object alertable sleeps

Console initialized.
scandir failed:/home/d3adc0d3/server_cs/./valve/SAVE
scandir failed:/home/d3adc0d3/server_cs/./platform/SAVE
Protocol version 48
Exe version 1.1.2.6/Stdio (cstrike)
Exe build: 16:56:12 Mar  8 2010 (4883)
STEAM Auth Server
"maxplayers" is "15"
exec <filename> : execute a script file
exec <filename> : execute a script file
WARNING: UDP_OpenSocket: port: 27015  bind: Cannot assign requested address
FATAL ERROR (shutting down): Couldn't allocate dedicated server IP port 27015.
Thu Jun  3 20:51:46 EDT 2010: Server Quit

```

heres another, I try connecting with just a port and it runs but its only on local, in the servers list the ip is 192.168.0.192:
```
root@xyz:/home/d3adc0d3/server_cs# ./hlds_run -game cstrike -autoupdate +maxplayers 15 +map de_dust2 +port 27013
Auto detecting CPU
Using Pentium II Optimised binary.
Auto-restarting the server on crash
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Checking/Installing 'Counter-Strike Base Content' version 35


Checking/Installing 'Linux Server Engine' version 54


Checking/Installing 'Half-Life Base Content' version 12


HLDS installation up to date
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 70 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 0 multi object alertable sleeps

Console initialized.
scandir failed:/home/d3adc0d3/server_cs/./valve/SAVE
scandir failed:/home/d3adc0d3/server_cs/./platform/SAVE
Protocol version 48
Exe version 1.1.2.6/Stdio (cstrike)
Exe build: 16:56:12 Mar  8 2010 (4883)
STEAM Auth Server
Server IP address 127.0.1.1:27013
   
   Metamod version 1.19p32 Copyright (c) 2001-2006 Will Day
     Patch: Metamod-P (mm-p) v32 Copyright (c) 2004-2007 Jussi Kivilinna
   Metamod comes with ABSOLUTELY NO WARRANTY; for details type `meta gpl'.
   This is free software, and you are welcome to redistribute it
   under certain conditions; type `meta gpl' for details.
   

   AMX Mod X version 1.8.1.3746 Copyright (c) 2004-2006 AMX Mod X Development Team 
   AMX Mod X comes with ABSOLUTELY NO WARRANTY; for details type `amxx gpl'.
   This is free software and you are welcome to redistribute it under 
   certain conditions; type 'amxx gpl' for details.
  
scandir failed:/home/d3adc0d3/server_cs/./valve/SAVE
scandir failed:/home/d3adc0d3/server_cs/./platform/SAVE
L 06/03/2010 - 20:40:47: -------- Mapchange to de_dust2 --------
[AMXX] Loaded 1 admin from file
[S_API FAIL] SteamAPI_Init() failed; unable to update local steamclient. Continuing with current version anyway.

Executing AMX Mod X Configuration File 
Scrolling message displaying frequency: 10:00 minutes
"maxplayers" is "15"
exec <filename> : execute a script file
exec <filename> : execute a script file
Menu item 17 added to Menus Front-End: "Plugin Cvars" from plugin "pluginmenu.amxx"
Menu item 18 added to Menus Front-End: "Plugin Commands" from plugin "pluginmenu.amxx"
Could not establish connection to Steam servers.
Reconnected to Steam servers.
   VAC secure mode is activated.

```

theres another one where i use this pcs ip but its only local, either way someone please help!

---

### Post by xaxtree on 2010-06-03
here is the output from when i enter my internal ip + a port 
```
root@xyz:/home/d3adc0d3/server_cs# ./hlds_run -game cstrike -autoupdate +maxplayers 15 +map de_dust2 +port 27015 +ip 192.168.0.192
Auto detecting CPU
Using Pentium II Optimised binary.
Auto-restarting the server on crash
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Checking/Installing 'Counter-Strike Base Content' version 35


Checking/Installing 'Linux Server Engine' version 54


Checking/Installing 'Half-Life Base Content' version 12


HLDS installation up to date
CAsyncIOManager: 0 threads terminating.  0 reads, 0 writes, 0 deferrals.
CAsyncIOManager: 71 single object sleeps, 0 multi object sleeps
CAsyncIOManager: 0 single object alertable sleeps, 0 multi object alertable sleeps

Console initialized.
scandir failed:/home/d3adc0d3/server_cs/./valve/SAVE
scandir failed:/home/d3adc0d3/server_cs/./platform/SAVE
Protocol version 48
Exe version 1.1.2.6/Stdio (cstrike)
Exe build: 16:56:12 Mar  8 2010 (4883)
STEAM Auth Server
Server IP address 192.168.0.192:27015
   
   Metamod version 1.19p32 Copyright (c) 2001-2006 Will Day
     Patch: Metamod-P (mm-p) v32 Copyright (c) 2004-2007 Jussi Kivilinna
   Metamod comes with ABSOLUTELY NO WARRANTY; for details type `meta gpl'.
   This is free software, and you are welcome to redistribute it
   under certain conditions; type `meta gpl' for details.
   

   AMX Mod X version 1.8.1.3746 Copyright (c) 2004-2006 AMX Mod X Development Team 
   AMX Mod X comes with ABSOLUTELY NO WARRANTY; for details type `amxx gpl'.
   This is free software and you are welcome to redistribute it under 
   certain conditions; type 'amxx gpl' for details.
  
scandir failed:/home/d3adc0d3/server_cs/./valve/SAVE
scandir failed:/home/d3adc0d3/server_cs/./platform/SAVE
L 06/03/2010 - 21:10:08: -------- Mapchange to de_dust2 --------
[AMXX] Loaded 1 admin from file
[S_API FAIL] SteamAPI_Init() failed; unable to update local steamclient. Continuing with current version anyway.

Executing AMX Mod X Configuration File 
Scrolling message displaying frequency: 10:00 minutes
"maxplayers" is "15"
exec <filename> : execute a script file
exec <filename> : execute a script file
Menu item 17 added to Menus Front-End: "Plugin Cvars" from plugin "pluginmenu.amxx"
Menu item 18 added to Menus Front-End: "Plugin Commands" from plugin "pluginmenu.amxx"
Connection to Steam servers successful.
   VAC secure mode is activated.
status
hostname:  South Jersey | 24/7 de_dust2
version :  48/1.1.2.6/Stdio 4883 secure  (10)
tcp/ip  :  192.168.0.192:27015
map     :  de_dust2 at: 0 x, 0 y, 0 z
players :  0 active (15 max)

#      name userid uniqueid frag time ping loss adr
0 users

```

---

### Post by xaxtree on 2010-06-03
pretty sure there is someone out there who knows the answer...

---

### Post by jerome1232 on 2010-06-03
So if this server is behind a nat device, you need to be using your private ip and have the nat device forward the correct ports on towards your server.

What's the output of this command while the server is running, for some reason I remember the saying it bound to 127.x.x.x but it really did bind to the correct ip. 
```
sudo netstat -tlnup
```

---

### Post by xaxtree on 2010-06-03
> **jerome1232 said:**
> So if this server is behind a nat device, you need to be using your private ip and have the nat device forward the correct ports on towards your server.

What's the output of this command while the server is running, for some reason I remember the saying it bound to 127.x.x.x but it really did bind to the correct ip. 
```
sudo netstat -tlnup
```

ouput:
```
d3adc0d3@xyz:~$ sudo netstat -tlnup
[sudo] password for d3adc0d3: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      729/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      997/cupsd       
tcp6       0      0 :::22                   :::*                    LISTEN      729/sshd        
tcp6       0      0 ::1:631                 :::*                    LISTEN      997/cupsd       
tcp6       0      0 :::5900                 :::*                    LISTEN      1175/vino-server
udp        0      0 0.0.0.0:39988           0.0.0.0:*                           749/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1348/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           749/avahi-daemon: r
udp        0      0 0.0.0.0:27015           0.0.0.0:*                           1590/hlds_i686  
udp        0      0 127.0.1.1:26900         0.0.0.0:*                           1590/hlds_i686  
d3adc0d3@xyz:~$ 


```

my apologies for late response

---

### Post by xaxtree on 2010-06-03
i tried using a static ip rather then dhcp, but that didn't turn out too well

---

### Post by xaxtree on 2010-06-03
trying to keep this alive

---

### Post by jerome1232 on 2010-06-03
According to that output your server is bound to all available addresses so I think your problem lies elsewhere. Are you unable to join a game on your own server? can you connect via lan? Can other people outside your lan not join?

---

### Post by xaxtree on 2010-06-03
well depending on my startup command line, i can connect on my lan sometimes but no one outside my lan can connect even if all the correct ports are forwarded




EDIT: 

If I use 
```
./hlds_run -game cstrike -autoupdate +maxplayers 15 +map de_dust2
```
it allows me to connect on any pc in my lan, even off my windows box
even though it starts up with the server ip as 127.0.1.1:27015
the actual server ip through my servers list on steam on my windows pc is 192.168.0.192:27015

---

### Post by xaxtree on 2010-06-04
bamp...  :\

---

### Post by xaxtree on 2010-06-04
anybody...?

---

### Post by cladiron on 2010-06-04
This is the exact line i use on my tf2 dev server.
This is behind a nat router and is publicly viewable threw steams master server list.

"-game tf +ip 192.168.1.190 -port 27015 +map ctf_2fort +maxplayers 32 -autoupdate -tickrate 66 +fps_max 800"

just be sure you have your ports open on the router at [www.canyouseeme.org]("http://www.canyouseeme.org")

Ubuntu10.04
hope this helps.

edited:

so your line would be something like this if i have your static ip right.

./hlds_run -game cstrike +ip 192.168.0.192 -port 27015 +map de_dust2 +maxplayers 15 -autoupdate



One other thing, make sure you have your ip on the computer/server set to static.

---

### Post by xaxtree on 2010-06-04
thanks for your response, i've tried that but didn't seem to change anything, might as well try it again

---

### Post by cladiron on 2010-06-04
no problem, but just to a sure you. I'm am 100% that line works and is viewable in the steam browser list.
other than that i would check for a local firewall, and make sure ports are open in it as well as make sure the ports are forwarding on the router.

---

### Post by xaxtree on 2010-06-04
well all that is good and checked, but it never says added to master server list either, and i just changed my whole network to static ip to see what that changes

---

### Post by cladiron on 2010-06-04
the issue with not getting added to the master server list was suppost to have been fixed on the 2nd update from the last i think.
what we did till they had fixed it was force our servers to be removed then re-added each map change.
this is how, but really should not be needed.

in your server.cfg add this with out the quotes.   "exec master.cfg"

now create a file in your servers cfg dir called "master.cfg"

In the master.cfg copy and add the following.

```
setmaster remove 216.207.205.99:27011
setmaster remove 216.207.205.98:27011
setmaster remove 72.165.61.153:27015

setmaster add 216.207.205.99:27011
setmaster add 216.207.205.98:27011
setmaster add 72.165.61.153:27015

setmaster enable 216.207.205.99:27011
setmaster enable 216.207.205.98:27011
setmaster enable 72.165.61.153:27015
heartbeat
```

also i could suggest you subscribe to there mailing list.
[http://list.valvesoftware.com/](http://list.valvesoftware.com/)

good luck

---

### Post by cladiron on 2010-06-07
any update on your status so others can benefit from this ?  ):P

---

### Post by onio on 2010-07-28
[FONT=&quot]hello averyone

i'm setup HLDS on ubuntu10.04

**problem **
onio@host:~$ cd hlds
onio@host:~/hlds$ wget [http://www.steampowered.com/download/hldsupdatetool.bin](http://www.steampowered.com/download/hldsupdatetool.bin)
--2010-07-29 03:37:22--  [http://www.steampowered.com/download/hldsupdatetool.bin](http://www.steampowered.com/download/hldsupdatetool.bin)
Resolving [www.steampowered.com]("http://www.steampowered.com")... failed: Temporary failure in name resolution.
wget: unable to resolve host address `[www.steampowered.com]("http://www.steampowered.com")'
onio@host:~/hlds$ 
onio@host:~/hlds$ pwd
/home/onio/hlds
onio@host:~/hlds$


pls help me anybody?


[/FONT]

---

### Post by cladiron on 2010-07-28
> **onio said:**
> [FONT=&quot]hello averyone

i'm setup HLDS on ubuntu10.04

**problem **
onio@host:~$ cd hlds
onio@host:~/hlds$ wget [http://www.steampowered.com/download/hldsupdatetool.bin](http://www.steampowered.com/download/hldsupdatetool.bin)
--2010-07-29 03:37:22--  [http://www.steampowered.com/download/hldsupdatetool.bin](http://www.steampowered.com/download/hldsupdatetool.bin)
Resolving [www.steampowered.com]("http://www.steampowered.com")... failed: Temporary failure in name resolution.
wget: unable to resolve host address `[www.steampowered.com]("http://www.steampowered.com")'
onio@host:~/hlds$ 
onio@host:~/hlds$ pwd
/home/onio/hlds
onio@host:~/hlds$


pls help me anybody?


[/FONT]


Going to Steams website, looks like the tool is here if you want to download it, then ftp it to your server.
[http://storefront.steampowered.com/download/hldsupdatetool.bin](http://storefront.steampowered.com/download/hldsupdatetool.bin)


you could try:
wget [http://storefront.steampowered.com/download/hldsupdatetool.bin](http://storefront.steampowered.com/download/hldsupdatetool.bin)

instead of 
[FONT=&quot]wget [http://www.steampowered.com/download/hldsupdatetool.bin](http://www.steampowered.com/download/hldsupdatetool.bin)[/FONT]

---

### Post by onio on 2010-07-28
onio@host:~$ sudo [http://storefront.steampowered.com/d...updatetool.bin](http://storefront.steampowered.com/d...updatetool.bin)
sudo: [http://storefront.steampowered.com/d...updatetool.bin:](http://storefront.steampowered.com/d...updatetool.bin:) command not found
onio@host:~$
 ??????

---

### Post by cladiron on 2010-07-28
[COLOR=Red][B][COLOR=Black]You forgot   WGET[/COLOR]

"wget [http://storefront.steampowered.com/d...updatetool.bin"]("http://storefront.steampowered.com/download/hldsupdatetool.bin")

[COLOR=Black]Without the quotes.  ""


[/COLOR][/B][/COLOR]

---

### Post by onio on 2010-07-28
onio@host:~$ cd hlds
onio@host:~/hlds$ "wget http://storefront.steampowered.com/d...updatetool.bin"
-bash: wget [http://storefront.steampowered.com/d...updatetool.bin:](http://storefront.steampowered.com/d...updatetool.bin:) No such file or directory
onio@host:~/hlds$
???? :(

---

### Post by cladiron on 2010-07-28
I'm not sure why your getting that error then.

Your first post is how i normally installed the tool.
Just download the tool and upload it to your server then run the install after you chown it.

[COLOR=Red]**[http://storefront.steampowered.com/d...updatetool.bin]("http://storefront.steampowered.com/download/hldsupdatetool.bin")**[/COLOR]

---

### Post by onio on 2010-07-29
maybe my server PC not connceting network?

onio@host:~$ ping -c 4 google.com
ping: unknown host google.com
onio@host:~$

how to connect network?

use cabel working 100%
this cabel connecting anouther PC connected network

---

### Post by cladiron on 2010-07-29
> **onio said:**
> maybe my server PC not connceting network?

onio@host:~$ ping -c 4 google.com
ping: unknown host google.com


Ya it looks like your not connected.

So once you get on line, your first command to download the tool should work.

As for helping you get your internet connection work.

Is it a desktop version or command line version of 10.04 ?

If it's the desktop version, look up near the top right corner. Hover your mouse over the icons and look for "wired network connection" and make sure it's enabled.

You SHOULD  set this up with a static IP.

If it's a command line version, you will need to edit the
"etc/NetworkManager/system-connections/Auto eth0"
or
"etc/NetworkManager/system-connections/Auto eth1"

---

### Post by cranecreek on 2010-07-29
I'm not entirely sure what your trying to do but. I think the static ip is the way to go. I think you want the server available from the internet. Should this be the case go to where you registered your domain and set an A record pointing to your ip or you could simply use your ip ie 111.111.111.111/hdls hdls being the folder where the game server is installed. If you need help with server side help just ask. Also make sure you have the port forwarded on your router .

---

### Post by onio on 2010-08-02
> **cladiron said:**
> Ya it looks like your not connected.

So once you get on line, your first command to download the tool should work.

As for helping you get your internet connection work.

Is it a desktop version or command line version of 10.04 ?

If it's the desktop version, look up near the top right corner. Hover your mouse over the icons and look for "wired network connection" and make sure it's enabled.

You SHOULD  set this up with a static IP.

If it's a command line version, you will need to edit the
"etc/NetworkManager/system-connections/Auto eth0"
or
"etc/NetworkManager/system-connections/Auto eth1"

tnks my ubuntu 10.04 server,command line

i connect putty
ip 202.180.218.140

etc/NetworkManager/system-connections/Auto eth0   ?

you cheking my ip server? 

i give you user and pass
connect me

---

### Post by cladiron on 2010-08-02
i can ping your IP fine.

I have sent you a PM also.

---

### Post by onio on 2010-08-05
help me? problem.i'm hlds installing on ubuntu server.
This server is using a newer protocol ( 48 ) than your client ( 47 ).  You should check for updates to your client.

---

### Post by onio on 2010-08-25
hi
i need problem !!!
'/tmp/mysql.sock'  can't connect mysql 

i'm installing amxbans

can anybody help me?

---

