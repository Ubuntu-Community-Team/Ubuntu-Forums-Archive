---
title: "port forward firefox"
date: 2010-01-22
forum: General Help
---

### Post by hyburn on 2010-01-22
hi folks,

I'd really like to know how to port forward firefox, so I can browse and stream my movies faster... is this possible? 

thanks

-drew

---

### Post by Cabs21 on 2010-01-22
you have to adjust these settings in your router.  Type your routers IP address into your browser address bar.  You should be prompted with a user name and password.  You will have to find out what that is cause it is different for every ISP router.  Also it is my understanding that port forwarding tends to bypass any security features you might have engaged which might not be to important on gaming but is very important when surfing the web.  Even for linux.  This is also a great way to ruin your router from the inside out if you dont know what your doing so be careful and do some research first before you open your your ports to the world and let everyone in.

P.S. This works great with Torrents to increase speeds however you must monitor the port that you opened.

---

### Post by scottuss on 2010-01-22
You aren't going to see any benefits by doing this. If anything, you are going to expose your system.

---

### Post by lovinglinux on 2010-01-22
I don't understand why you need to port-forward Firefox. It is not a server. You only forward a port if you need to allow unrequested incoming connections to reach your application, for example when using a BitTorrent client or when accessing your machine remotely with ssh.

What exactly are you trying to do?

---

### Post by scottuss on 2010-01-22
> **lovinglinux said:**
> I don't understand why you need to port-forward Firefox. It is not a server. You only forward a port if you need to allow unrequested incoming connections to reach your application, for example when using a BitTorrent client or when accessing your machine remotely with ssh.

What exactly are you trying to do?

Precisely. I'm confused as to which port(s) he would want to forward. I saw someone once forward port 80 thinking that would speed up browsing ](*,)

---

### Post by hyburn on 2010-01-22
I've decided not to open my firefox to the net, especially if it will compromise my systems security. *Dont want that.

thanks for the clarity guys

---

### Post by theozzlives on 2010-01-22
I have port 80 forwarded to my web site, but I don't see any other reason.

---

### Post by lovinglinux on 2010-01-22
> **hyburn said:**
> I've decided not to open my firefox to the net, especially if it will compromise my systems security. *Dont want that.

thanks for the clarity guys

There is no reason to open your Firefox to the outside. Firefox is not a server, so it doesn't listen to any incoming connections. Even if you open any port that you might think will be related to Firefox, nothing will happen and your security will not be compromised, because there won't be any application listen to that port and thus any connection attempt coming from outside will be rejected.

If you was thinking about opening port 80, than you need to understand that this port is used by web servers to accept incoming connections from web browsers. Any connection from Firefox leaving your machine will use a random port, which will always be allowed, unless you block outgoing connections with the firewall. The destination port will be usually 80, but that concerns the destination web server, not Firefox.

---

### Post by scottuss on 2010-01-23
> **lovinglinux said:**
> There is no reason to open your Firefox to the outside. Firefox is not a server, so it doesn't listen to any incoming connections. Even if you open any port that you might think will be related to Firefox, nothing will happen and your security will not be compromised, because there won't be any application listen to that port and thus any connection attempt coming from outside will be rejected.

If you was thinking about opening port 80, than you need to understand that this port is used by web servers to accept incoming connections from web browsers. Any connection from Firefox leaving your machine will use a random port, which will always be allowed, unless you block outgoing connections with the firewall. The destination port will be usually 80, but that concerns the destination web server, not Firefox.


I agree, but the reason I said (and still say) the person would be opening their computer to exploits is because they had no idea which ports to open, thus there could be servers running on said ports. Forwarding random ports for no reason is just stupid, purely because if you think that this will speed up your browsing, you probably wouldn't know if something was bound to the port you are forwarding.

To the OP: This thread should be marked as closed now.

---

