---
title: "Using SSH to remotely login to Windows Machine"
date: 2009-07-20
forum: General Help
---

### Post by ravishi on 2009-07-20
I am running Ubuntu 8.04 and I am trying to use ssh to remotely log in to my desktop running Vista at a different location (different ISP's).  

I have Tomato running on my router and I am able to successfully ssh into it.  I can then ping my desktop on other devices on that network.  So, now I wanted to tunnel? my port to a localhost port so I can use Remote Desktop Viewer to log in to that address.  I have UltraVNC Viewer running on my Desktop at home.  It never wants to connect.  Here are the commands I am running.

ssh -L 15338:localhost:2222 root@ROUTER.IP.ADDRESS -p 2222

What I think this means.  I am using ssh to log into the router at port 2222.  I then tunnel port 222 to 15338.  I successfully log in to the router and can ping 192.168.1.146 OK.  I then leave this terminal alone and open Remote Desktop Viewer.  I use ip 192.168.1.146 and port 15338.  And then it doesn't connect.

What I've tried is to switch the ports to 2222:localhost:15338 and then using option R instead of L.  Also, I tried using telnet to connect to the remote host using this command.
[INDENT]$ telnet 192.168.1.146 15338
telnet: Unable to connect to remote host: Connection refused[/INDENT]

However, when I try this command, I get:
[INDENT]$ telnet localhost 15338
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.[/INDENT]
I only get this when I ssh with these options:
[INDENT]$ ssh -L 5901:localhost:2222 [email]root@ROUTER.IP.ADDRES[/email]S -p 2222[/INDENT]

Also, I notice when I try using this telnet command, I get the following on the routers terminal:
[INDENT]# channel 3: open failed: connect failed: 
exit[/INDENT]

What am I doing wrong?

---

### Post by blueridgedog on 2009-07-20
The -L option specifies:

```
     -L [bind_address:]port:host:hostport
             Specifies that the given port on the local (client) host is to be
             forwarded to the given host and port on the remote side.
```

So, if the remote service you want to connect to is running on port 2222 and you want to connect the local port 15338 to the remote port 2222 via a secure link, you would use:

ssh -L 15338:localhost:2222 -N -f -l root ROUTER.IP.ADDRESS

In theory, you should then be able to connect your RDP viewer to 127.0.0.1:15338 and it will connect with a service running on the ROUTER.IP.ADDRESS on port 2222.  You may need to remove the -N if your router is working with ssh v1.  The -p option you are using is for specifying a port, but you are not doing that, you are building a tunnel.

If I were setting this up, I would first get it working without the ssh component so that you have verified that you can RDP directly to the external router IP and have it be forwarded in to your PC.  When you know that is working, then you can move on to the ssh part.

---

### Post by HermanAB on 2009-07-20
Howdy,

You can set up SSH server on Windows, but it is a PITA to get it to work.  However, Vista should come with Remote Desktop.  RDP is secure, so you would be better off running that and connecting from Ubuntu using rdesktop.

VNC is insecure and should never be used over the internet.  It is OK on a private LAN for desktop support.  Tunneling VNC over SSH can be done, but SSH can do everything VNC does, so it is a waste of time doing that. 

Anyhow, if it were me, I would use RDP.  It works, it is fast and secure and we use it all the time on Windoze machines.

---

### Post by ravishi on 2009-07-21
> **blueridgedog said:**
> The -L option specifies:

```
     -L [bind_address:]port:host:hostport
             Specifies that the given port on the local (client) host is to be
             forwarded to the given host and port on the remote side.
```

So, if the remote service you want to connect to is running on port 2222 and you want to connect the local port 15338 to the remote port 2222 via a secure link, you would use:

ssh -L 15338:localhost:2222 -N -f -l root ROUTER.IP.ADDRESS

In theory, you should then be able to connect your RDP viewer to 127.0.0.1:15338 and it will connect with a service running on the ROUTER.IP.ADDRESS on port 2222.  You may need to remove the -N if your router is working with ssh v1.  The -p option you are using is for specifying a port, but you are not doing that, you are building a tunnel.

If I were setting this up, I would first get it working without the ssh component so that you have verified that you can RDP directly to the external router IP and have it be forwarded in to your PC.  When you know that is working, then you can move on to the ssh part.

Without the option -p 2222, ssh would not get very far.  In my router settings, I have set to allow ssh sessions on port 2222 so I still need -p 2222, no? 

Also, if I use RDP viewer and use 127.0.0.1:15338, how can I then connect to my computer on the network?  Would RDP viewer actually work for this IP since I doubt my router has a GUI RDP server?

Thanks for the help to both of you.  I'll give that command you gave a shot tomorrow and see how it goes.

One last question, is Linux's RDP compatible with windows?

---

### Post by blueridgedog on 2009-07-21
> **HermanAB said:**
>  However, Vista should come with Remote Desktop.  RDP is secure, so you would be better off running that and connecting from Ubuntu using rdesktop.


I believe Ravishi is trying to connect the RDP client from Ubuntu to windows.  In the original post he stated "...and open Remote Desktop Viewer. I use ip 192.168.1.146 and port 15338".  

I agree that there is no need to tunnel RDP, especially in the testing phase.

> **ravishi said:**
> Without the option -p 2222, ssh would not get very far.  In my router settings, I have set to allow ssh sessions on port 2222 so I still need -p 2222, no? 

Then you are correct, you will still need it.  However, if your router is using port 2222 for its ssh port, it can't then be forwarding port 2222 in to your Vista system's RDP port.  This clarifies (I think) my grasp of your original post.  You have an SSH server running on Vista and you are looking to connect a tunnel between them.  So, based on that you would create a connection between any high numbered port on your Ubuntu system and the RDP port on the windows system (3389 correct?) over SSH running on port 2222 because that is the port your router is letting through and that is the port your windows system is listening on for SSH connections, then RDP to that high numbered port on your Linus box.

The one change I see you need to make in your command then is to add back in your -p option and change the destination port for the tunnel to the port that you actually want to connect to (not the SSH port of 2222 but the RDP port).

Something like:

ssh -L 15338:localhost:3389 -N -f -l root ROUTER.IP.ADDRESS -p 2222

SSH will then connect port 15338 from your system via an SSH link on port 2222 through your router to the Vista system's SSH service running on port 2222 and create a tunnel to the remote port 3389.  Your RDP session to 127.0.0.1:15338 will then go via that tunnel to the Vista's port 3389.

All of this should work, but I strongly suggest you debug it one step at a time.  First get SSH point to point working, then work on the tunnel.  


> **ravishi said:**
> Also, if I use RDP viewer and use 127.0.0.1:15338, how can I then connect to my computer on the network?  Would RDP viewer actually work for this IP since I doubt my router has a GUI RDP server?


Your local port (15338 in this case) will be connected to the remote port on the Vista box (not the router as I was mistaken earlier), so you only need to RDP to your local IP as the port is your end of the tunnel.

---

