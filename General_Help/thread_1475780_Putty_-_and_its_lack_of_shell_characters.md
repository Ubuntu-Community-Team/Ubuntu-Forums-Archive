---
title: "Putty - and its lack of shell characters"
date: 2010-05-07
forum: General Help
---

### Post by Irony on 2010-05-07
I am attempting to use putty in Karmic 64 bit - but on clicking open I get to a shell which I cannot type anything into;

[IMG]http://i43.tinypic.com/30tpf6b.jpg[/IMG]

Anyone know how I can enable typing into this shell?

---

### Post by dino99 on 2010-05-07
Linux comes with telnet/ssh built in. Simply use the ssh command from a terminal window / console.

at the command prompt, type in

ssh computer address

Where the computer address is the IP Address or hostname of the system you want to connect to. Enter in your username and password, and get to work!

...Connecting is just that simple.

---

### Post by unmole on 2010-05-07
Just out of curiosity...What do you need to  use putty for, instead of openssh and telnet ?

---

### Post by Irony on 2010-05-07
I am following this video;

[http://vimeo.com/8955815](http://vimeo.com/8955815)

And this link;

[http://theillustratednetwork.mvps.org/Ssh/RemoteDesktopSSH.html](http://theillustratednetwork.mvps.org/Ssh/RemoteDesktopSSH.html)

And attempting to connect my desktop ubuntu machine to a xp laptop - I can do it via vnc but want to tunnel via ssh.

Currently it is a local network but the idea is that I will then connect to a computer illiterate friends computer across the internet.

Putty doesn't work because the shell doesn't work.

---

### Post by bredman on 2010-05-07
It looks like you have established a connection to the XP machine successfully, because you didn't mention any error messages.

In this case, it seems that the XP machine is just not presenting a prompt. Did you try pressing Enter or anything similar?

I would try ssh to see if there is any difference. The general command is
ssh username@111.222.333.444

---

### Post by Irony on 2010-05-07
> **bredman said:**
> ssh username@111.222.333.444
That was the instruction I needed. I typed the laptop's username and ip address and then password and it came up with;
```

username@xpcomputername ~
$ 
```
I then opened up another terminal and typed;
```
vncviewer localhost:5900
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```
But it comes up with the error you see. Because I am not using putty but ssh where do I specify ports?

---

### Post by zaphod777 on 2010-05-07
also did you install putty from the repos? That one works better.

---

### Post by bredman on 2010-05-07
To specify a port when using ssh, use the format
ssh username@111.222.333.444:port

For example
ssh username@111.222.333.444:22
to use the default SSH port 22

I had a look at the tutorial and you have no dependency on PuTTY. All that is required is to open an SSH session, it does not matter if you use PuTTY or SSH to do this.

-- BUT --

I really hate to rain on your parade, but this is all built into Ubuntu already. Try the menu item Applications/Internet/Remote Desktop viewer. Click on Connect and specify SSH as the protocol. Enter the host in the format 111.222.333.444:port. I use RDV all the time to connect to VNC on Windows XP.

Remote Desktop Viewer also supports using a host as an SSH tunnel. I have never used this, but the manual may help.

---

### Post by Irony on 2010-05-07
> **bredman said:**
> I had a look at the tutorial and you have no dependency on PuTTY. All that is required is to open an SSH session, it does not matter if you use PuTTY or SSH to do this.

I really hate to rain on your parade, but this is all built into Ubuntu already. Try the menu item Applications/Internet/Remote Desktop viewer. Click on Connect and specify SSH as the protocol. Enter the host in the format 111.222.333.444:port. I use RDV all the time to connect to VNC on Windows XP.

Remote Desktop Viewer also supports using a host as an SSH tunnel. I have never used this, but the manual may help.
Yes but this is all new to me. I realise that Putty is using SSH but it would be nice if putty actually worked (I installed it from repos) - because it doesn't I end up doing it from CLI.

Regarding Remote Desktop Viewer, it is at best flakey mostly it won't connect saying connection closed (apparently this is a bug which has not been sorted for years) which is why I am doing vncviewer from terminal.

The instructions I've seen say in vnc to do localhost:5900 (which as I said earlier doesn't work) - why is it always localhost?

---

### Post by junapp on 2010-05-07
it is always localhost if you are tunneling. You create a tunnel from localhost: port to remotehost: port so then you use whatever client you want to connect to localhost: port, allowing ssh to handle the forwarding.

---

### Post by HermanAB on 2010-05-07
Uhmmmm, Linux to Windows?

You should enable RDP on Windows and use rdesktop from Linux.

---

### Post by Irony on 2010-05-07
> **junapp said:**
> it is always localhost if you are tunneling. You create a tunnel from localhost: port to remotehost: port so then you use whatever client you want to connect to localhost: port, allowing ssh to handle the forwarding.
So localhost is sort of like http in that the wording is redundant in that it is always the word localhost that is used?

---

### Post by Irony on 2010-05-07
> **HermanAB said:**
> Uhmmmm, Linux to Windows?

You should enable RDP on Windows and use rdesktop from Linux.
Yes I've enable remote desktop on windows.

I can connect to the xp laptop from my ubuntu machine via vncviewer but not vinagre - that is not the problem, the problem is that I am still working out the details of SSH.

I've discovered PAC - [http://sourceforge.net/projects/pacmanager/](http://sourceforge.net/projects/pacmanager/) - whilst I am comfortable at command line, I can never remember the commands so gui is easier. Unlike putty PAC works and gets to the shell giving;
```
username@server's password: 
Last login: Fri May  7 15:22:22 2010 from client.home

username@server ~
$
```

---

### Post by Irony on 2010-05-07
The problem is thus this, I issue the command;
```
vncviewer localhost:5900
```
And get the error;
```
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
```
Perhaps it is because I am currently connecting locally?

---

### Post by Irony on 2010-05-08
So this is the situation.

**I can Ultra VNC Client connect via Putty from my Desktop (Windows 7) machine to my Laptop (XP Home) with Ultra VNC Server and COPssh.**

but on rebooting into Karmic on the Desktop machine I cannot;

**Remote Desktop Client/vncviewer connect via PAC from my Desktop (Karmic) machine to my Laptop (XP Home) with Ultra VNC Server and COPssh.**

PAC ssh connects successfully but on issuing localhost:5900 in either Remote Desktop Client or vncviewer nothing happens, they just hang as though waiting for something.

Any suggestions?

---

### Post by Irony on 2010-05-08
Success!

It occurred to me that in PAC I hadn't set source and destinations ports or mentioned localhost, i.e. 5900:localhost:5900

I couldn't figure out how to do this in PAC (there are no manuals), so on a hunch I opened up Putty and it worked and got to shell - I don't think it worked before because I had not set up copssh correctly on the laptop - I thus deleted copssh making sure to delete it in the registery and delete the user it had created and any stray files I could find.

I then set it up again and I also used Ultra VNC on the laptop as before I had tightvnc which never popped up with a refuse or allow box.

In the process I learned that copssh creates a user key when a user is created and so I now have some idea of keys. I also found that using ssh requires that only port 22 needs to be opened, not 5900 which is confusing as 5900 is specified in the commands...

---

### Post by junapp on 2010-05-10
5900 is likely mentioned in the vnc instructions. You are tunneling in on port 22 - making it unnecessary to have 5900 open. If you were not using ssh to create the tunnel you could open 5900 and vnc directly to it. Having ssh handle all the connections and forwarding is considered the better approach than leaving 5900 open to the world. I wouldn't equate your thought on 'http' being the same as 'localhost'. It doesn't always have to be localhost (on the remote end).

[http://en.wikipedia.org/wiki/Tunneling_protocol#Secure_Shell_tunneling](http://en.wikipedia.org/wiki/Tunneling_protocol#Secure_Shell_tunneling)

---

### Post by Irony on 2010-05-12
I'm still puzzled as to why it is that if I am using port 22 with ssh yet the command for vncviewer is localhost:5900 - what has 5900 to do with it as port 5900 is closed both on my router and firewall.

---

### Post by bodhi.zazen on 2010-05-12
Port 5900 is your VNC connection.

You using ssh to tunnel port 5900. This encrypts your network traffic and increases security.

So, you start the ssh connection, over port 22, and ssh tunnels localhost:5900 to your ssh server, tunneling the connection.

Thus on the client you connect to localhost:5900 and ssh does the rest.

[http://en.wikipedia.org/wiki/Tunneling_protocol](http://en.wikipedia.org/wiki/Tunneling_protocol)

---

### Post by Irony on 2010-05-13
The main problem with SSHing is that it makes VNCing very slow particularly when I connect to my wireless laptop.

The slowness renders the method useless when flicking back and forth between say desktop 1 with the VNC and desktop 2 with say firefox - it then takes VNC a few minutes to start moving.

Its manageable if I just stick to one desktop but I cannot fireup any other programs on the same screen - this of course means that I cannot solve problems by for example looking at firefox and then going to VNC.

In short it is not a practical method.

---

### Post by Irony on 2010-05-13
After some searching around I issued this command which uses a 'tight' encoding;

```
vncviewer -encodings 'tight' localhost:5900
```

Another option is which uses 'copyrect tight hextile' which is 3 encodings plus an 8 bit colour scheme;

```
vncviewer -bgr233 -encodings 'copyrect tight hextile' localhost:5900
```

There are more options;

```
       vncviewer -help

<OPTIONS> are standard Xt options, or:
        -via <GATEWAY>
        -shared (set by default)
        -noshared
        -viewonly
        -fullscreen
        -noraiseonbeep
        -passwd <PASSWD-FILENAME> (standard VNC authentication)
        -encodings <ENCODING-LIST> (e.g. "tight copyrect")
        -bgr233
        -owncmap
        -truecolour
        -depth <DEPTH>
        -compresslevel <COMPRESS-VALUE> (0..9: 0-fast, 9-best)
        -quality <JPEG-QUALITY-VALUE> (0..9: 0-low, 9-high)
        -nojpeg
        -nocursorshape
        -x11cursor
        -autopass
```

[http://www.tightvnc.com/vncviewer.1.php](http://www.tightvnc.com/vncviewer.1.php)

---

