---
title: "how do i set up vcn4sever so i can us my pc from work"
date: 2009-09-11
forum: General Help
---

### Post by rhythmiccycle on 2009-09-11
i tried using remote desktop and its great, but it only work on my LAN

i want to use it over www, so some one told me to use vnc4server, but i don't know how to set it up.


what do I do?

---

### Post by P4man on 2009-09-11
You need to configure your router and set up portforwarding. Check your router manual how to forward port 5900 to the IP address of your machine.
If your ISP or firewall at work block port 5900, set it to some arbitrary high number on the advanced tab, something like 10111 (and forward that port on your router).

You'll also need either a static WAN IP address on your router, or something like no-ip.org to be able to contact your router from work.

---

### Post by rhythmiccycle on 2009-09-11
i forgot to mention that i'm also hosting a website (that is online and running right fine right now)

some one helped with with it, i had to make my ip static, and do something with ports.

but i want to be able to see my desktop, and edit the site (transfer files back and forth) and do other things too.

will doing what P4man is telling me to do interfere with the website i'm hosting?

Can i forward multiple ports?

---

### Post by P4man on 2009-09-11
> **rhythmiccycle said:**
> i forgot to mention that i'm also hosting a website (that is online and running right fine right now)

some one helped with with it, i had to make my ip static, and do something with ports.

but i want to be able to see my desktop, and edit the site (transfer files back and forth) and do other things too.

will doing what P4man is telling me to do interfere with the website i'm hosting?

Can i forward multiple ports?

Yes. You probably already have port 80 forwarded for your website, now do the same with 5900 for remote desktop. It won't interfere, that's why they have different ports :)

---

### Post by rhythmiccycle on 2009-09-11
> **P4man said:**
> 

You'll also need either a static WAN IP address on your router, or something like no-ip.org to be able to contact your router from work.


so does that mean i'll have 2 URL's going to my home PC, like:

mywebsite.dyndns.org
and
myremotedesktop.dyndns.org

-OR-

 will there be just one URL

with web browers and VNC viewer reacting differently to it?


-OR-
one URL with differnt ports?
mywebsite.dyndns.org:10111

---

### Post by P4man on 2009-09-11
A url would be:
[http://mycomputer.dyndns.org/](http://mycomputer.dyndns.org/)
Dyndns converts that your ip, eg:
[http://123.456.78.90/](http://123.456.78.90/)

default port for http (web) is 80, so this is the same:
[http://mycomputer.dyndns.org:80/](http://mycomputer.dyndns.org:80/)
or
[http://123.456.76.89:80/](http://123.456.76.89:80/)

VNC uses a (very) different protocol and a different port. you could reach it via
vnc://mycomputer.dyndns.org::5900
or
vnc://123.456.78.90::5900

All you have to do is forward port 5900. You can probably use the same name you got from dyndns for your webserver.

---

### Post by rhythmiccycle on 2009-09-14
i went into my router setting.
went to the "Port Forwarding / Port Triggering" part
and selected "Port Forwarding"
Then hit "add service"

I then am asked to fill out a small form:
> 
Service Name: <text box>
Protocol: <drop box: TCP, UDP, TCP/UDP>
Starting Port(1~65535): <text box>
Ending Port(1~65535):<text box>
Server IP Address: 192.168.1.<text box>


i'm not really sure what to put here
i'm guessing, 
Service name can be anything. 
protocol- i have no idea what to put.
Starting and ending ports both set to some arbitrary number like 43571.
IP set to 192.168.1.2, because that is the same ip that the website is on, and i want to have remote access to the same computer that is hosting the site.

please help.

---

### Post by P4man on 2009-09-14
> **rhythmiccycle said:**
> i went into my router setting.
went to the "Port Forwarding / Port Triggering" part
and selected "Port Forwarding"
Then hit "add service"

I then am asked to fill out a small form:


i'm not really sure what to put here
i'm guessing, 
Service name can be anything. 
Correct.
> protocol- i have no idea what to put.
TCP. Or TCP/UDP (which allows both)

> Starting and ending ports both set to some arbitrary number like 43571.

Thats high enough I guess heh. Not sure, i think the upper limit is 65563 so you're probably good.

> IP set to 192.168.1.2, because that is the same ip that the website is on, and i want to have remote access to the same computer that is hosting the site.

Sounds right. Now you do have to configure remote desktop on the server to listen to that same port you forwarded. By default it listens to 5900. If you want to change that, open gconf-editor and browse to desktop > gnome > remote_access. Set alternative_port to 43571 and check use_alternative_port.

Either that, or try forwarding port 5900 on the router.

---

### Post by rhythmiccycle on 2009-09-14
i set it up like you said,

attached are some screen shots so you can see how I did it

i tried to connect from my home network (see below) but i get connection refused.

i'm going to try again from work, to see if non-local connections act different. but i still want to connect locally, as well as over www.

> 
mrm@mrm-laptop:~$ vncviewer mywebsite.dyndns.org::45678

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Mon Sep 14 06:08:21 2009
 main:        unable to connect to host: Connection refused (111)


---

### Post by P4man on 2009-09-14
You might want to remove that dyndns name from your post, but since you posted it, I tried:

vncviewer (removed for privacy)::45678
Connected to RFB server, using protocol version 3.7
Performing standard VNC authentication
Password: 

Works for me.. I guess your work has a firewall that blocks it.
Could be because it blocks all ports except a few like 80. You could try port 8080 perhaps? It can also be a firewall that does deep packet inspection, and regardless of port will block the vnc protocol. in that case, you're pretty much screwed.

---

### Post by P4man on 2009-09-14
oh, our messages crossed :)
If you were trying that from within the local network, then use the local IP address instead of the dyndns name.

---

### Post by rhythmiccycle on 2009-09-14
> **P4man said:**
> You might want to remove that dyndns name from your post, but since you posted it, I tried:


the real site name was only up for about 5min, then i changed it to "mywebsite" i guess you were looking in during that brief window of time.

after i changed it you had already replied,

---

### Post by P4man on 2009-09-14
> **rhythmiccycle said:**
> the real site name was only up for about 5min, then i changed it to "mywebsite" i guess you were looking in during that brief window of time.

after i changed it you had already replied,

hehe. I guess I was too fast. dont worry, not gonna hack it. But you configured it right, it seems to work. Im not sure why it doesnt connect locally, but like I wrote up, you could try

```
vncviewer 192.168.x.x::45678
```

replace it with your local IP.

---

### Post by rhythmiccycle on 2009-09-14
> **P4man said:**
> oh, our messages crossed :)
If you were trying that from within the local network, then use the local IP address instead of the dyndns name.

i'm still at home, i gotta go to work in about 10min.

i tryed again with the IP, and didn't get the connection refusal, but i get  a password prompt and type "letmein" because that is the password set in the gconf-editor (see screen shot from previous post)
but the password doesn't see to work. i get "Authentication failure"

P4man, did you get a password prompt and type "letmein"?
are you using vnc4viewer?

---

### Post by rhythmiccycle on 2009-09-14
i'm off to work now, i'll try it out from there, and post how it goes

---

### Post by P4man on 2009-09-14
indeed, the password doesn't work, I hadn't noticed it was in your screenshot. it seems you entered it in gconf-editor, but afaik, in gconf-editor the password is stored encrypted. To give you an example, when i go system > preferences > remote desktop and i enter a pw there (I took "test1235') in gconf-editor is shows as "dGVzdDEyMzQ=".

---

### Post by rhythmiccycle on 2009-09-14
i'm at work now, and i seem to be able to connect

but i have the same password problem from here.

does this me that if I set the password from "system > preferences > remote desktop" rather than from "gconf-editor", then the password will work?

or do i need to disable encryption some how?

---

### Post by P4man on 2009-09-14
> **rhythmiccycle said:**
> 
does this me that if I set the password from "system > preferences > remote desktop" rather than from "gconf-editor", then the password will work?


Yes. (well, thats what I expect at least :) ).

BTW, if it works, you may find the built-in vnc server (called vino) to be slow. IT depends what you intend to do with it, and of course your internet connection speed,  but you might want to consider using FreeNX as a (much) faster alternative, if you are able/allowed to install a (windows?)  client on your work computer:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

The downside of freeNX is that it creates a separate session for the remote login, so if you want to connect to some apps already running in the local session, it doesn't work. Its like a new/separate login. But its fast :)


> or do i need to disable encryption some how?

Dont think you can. perhaps you could try to crack or reverse the encryption to find out what vnc accepts as password now :D Well, maybe not :)

---

### Post by rhythmiccycle on 2009-09-15
its working, i could see my desktop from work.
Thanks a lot P4man, i couldn't have done it with out your help.

for some reason it is only in 256 colors, buts that no big deal

the next thing i want to be able to do in transfer files. 

both computer are running ubuntu 9. (i bring my laptop to work)

i tried to just drag a file out of the viewer window, and i tried to copy and paste, but that didn't work.

what do i need to do to transfer files?

---

### Post by P4man on 2009-09-15
> **rhythmiccycle said:**
> 

both computer are running ubuntu 9. (i bring my laptop to work)

i tried to just drag a file out of the viewer window, and i tried to copy and paste, but that didn't work.

what do i need to do to transfer files?


AFAIK, neither remote desktop (vnc/vino) nor freeNX let you transfer files. FreeNX does support copy/paste but not of files.

Your best bet is probably setting up ssh, and then using scp to transfar files.

To set up ssh on the server:
```
sudo apt-get install openssh-server
```

By default it uses port 22, so forward that, or change the port.

Then to transfer files

```
scp user@host:/path/file /path
```

You can also use ssh of course to issue commands (like a remote login)

```
ssh user@host
```

Unless someone has a better idea?

---

### Post by rhythmiccycle on 2009-09-15
OK, I'll try that out tomorrow, but i just want to get some thing straight first.

so after run"sudo apt-get install openssh-server"
on my home pc (the server)

then forward another port to 22, the exact same way i did before, but use 22 rather than 45678, (and just give it another name)

than i can run the code on my laptop at work:
```

scp userNameUsedToLogOnHomePC@mywebsite.dyndns.org:22:/path/file /path

```

and it will work?
(not sure if the host is correct)

OR, i just had that thought of setting up an FTP, or is openssh better that FTP?

---

### Post by P4man on 2009-09-16
Yeah, that should work, although the same caveats relating to firewalls and ports apply.

FTP would also work, but would only let you transfer files from and to the ftp folder and needs a lot more setting up. ssh/scp has the added advantage of being able to login and execute commands, and you can do a lot more with it, forwarding ports, running X applications remotely,etc. Its worth learning, its extremely useful, powerful and yet simple.

Some more info here:
[http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks](http://www.linuxtutorialblog.com/post/ssh-and-scp-howto-tips-tricks)

and all over the web :)

---

### Post by rhythmiccycle on 2009-09-16
i tried this

```

me@my-laptop:~$ ssh userNameThatIsCUrrentlyLoggedInOnServer@mywebsite.dyndns.org::22
ssh: Could not resolve hostname mywebsite.dyndns.org::22: Name or service not known

```

i also tryed website.dyndns.org:22 i'll try using the ip next

```

ssh mike@<ip from whatismyip.com>
ssh: connect to host <ip from whatismyip.com> port 22: Connection refused

```

do you know why it was refused?

---

### Post by P4man on 2009-09-16
Did you install openssh-server on the home computer?
To test if thats working, on the "server" try loggin in locally:

```
ssh localhost
```

if that fails, your server isnt setup (or setup properly). if that works, something is blocking or not forwarding port 22. Try on the lan? Double check the port forwarding. Or perhaps your work firewall has port 22 blocked, try configuring it on a different port. To do that, have a look here:

[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

---

### Post by rhythmiccycle on 2009-09-17
for some reason "sudo apt-get install openssh-server"

didn't run the first time i did it. I installed it again it seems to be working from localhost now. 

i'll try it out from work when i get there today.

when i get this working i'll be happy.

---

### Post by rhythmiccycle on 2009-09-17
ITS WORKING!!!!

P4man you are my hero.

thank you so much!

---

