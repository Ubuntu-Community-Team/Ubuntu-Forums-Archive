---
title: "x11 ssh vinagre alternative."
date: 2012-03-14
forum: General Help
---

### Post by max1e6 on 2012-03-14
I have an open ssh server at 192.168.2.13. The config forwards X11 and uses publicKey and RSA authentication. Its served over port 69. Password logon is disabled.

From another Ubuntu I can connect to it, log on, browse directories, etc. I am using Putty to manage the log on because, for me anyway, it provides a conveniently portable key. Putty tunnels the connection through port 5900. X11 is enabled.

I assume that, when I am logged in, my server is at localhost:5900. Running "vinagre localhost:5900" from a terminal shows no errors but gives me a black screen (so close but so far). 

I tried remmina but a simple connect attempt (at localhost:5900) throws an "Unable to connect to RDP server" error. I obviously don't know what I am doing.

I am hoping to find a rdt method that will let me view the remote desktop when I am already logged in and tunneling through 5900.  

Any ideas.

---

### Post by max1e6 on 2012-03-19
OK, here's my workout:

I setup putty as described above and verified that I can connect from a terminal. Then I restart putty and under Connection -> SSH -> Tunnels I added a Local Tunnel: Source Port = 5092, Destination: localhost:5900. Then save, start, and login.

Then at vinagre: Connect, use VNC,  Host = localhost:5092

Works now from both a vanilla Lynx remote client, and all of the Vbox machines I have. I also have a laptop with a minimal LSHW OS. It can connect to the server but I still haven't worked out the remote desktop client on this machine. But, I'm happy. 

Having a portable putty key is great if you want to get on your desktop from unforeseen machines but you want to keep the server password authentication off and only use RSA/DSA. As long as the putty Auth key isn't compromised it seems reasonably secure for my application and it beats having a crackable password and a sharkable connection.

---

