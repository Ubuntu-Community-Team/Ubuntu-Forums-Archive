---
title: "putty and ssh help"
date: 2010-08-19
forum: General Help
---

### Post by xjwellsx on 2010-08-19
hey all,

I am just wondering if it is possible to ssh in to my home computer without forwarding the ports in the router to my pc. I do not have access to the router because it is my apartment complex's router. I was just wondering if there was a way to point to the remote machine by using putty. 
Thanks 
Jeff

---

### Post by silbak04 on 2010-08-20
No I do not think it is possible to ssh into your home computer without forwarding the ports through the router...if that was the case then that would defeat the whole purpose of port forwarding...only way you could ever ssh into another computer without port forwarding is if you are inside your network (locally not externally) otherwise this is not possible.

If you are familiar with something like VNC...this is a remote client tool...I'm sure you can download this and be able to access your desktop through VNC client...although I have never fiddled around with VNC in ubuntu, I'm not sure how well it works...but I am sure there are other remote client tools that work in ubuntu.

Hope this helps!

---

### Post by xjwellsx on 2010-08-20
Thanks for the help. I know of ways to remote view it with things such as vnc and team viewer I was just wondering if there was a program that could point to a computer behind the router. Thanks again though.

---

### Post by DFlame on 2010-08-20
You could look up something called reverse SSH tunneling. This requires however that you set up the connection on the home computer first.

I can't offer much more detail as it isn't my forte

---

### Post by silbak04 on 2010-08-20
> **DFlame said:**
> You could look up something called reverse SSH tunneling. This requires however that you set up the connection on the home computer first.

I can't offer much more detail as it isn't my forte

Just like what DFlame mentioned...I did some more research on this, and came across SSH Tunneling, this is a bit more complex, but I think this still might do what you want.

---

### Post by Irony on 2010-08-20
Perhaps you could set putty to ssh port forward through port 80, i.e. use the internet port.

---

### Post by xjwellsx on 2010-08-20
> **Irony said:**
> Perhaps you could set putty to ssh port forward through port 80, i.e. use the internet port.

could you explain how to do this please that would be awesome if it would work.

---

### Post by Morrad on 2010-08-20
I may be wrong, but I'm pretty sure that you won't be able to ssh directly into your machine if it's behind a router you don't control regardless of what port you try.  The only reason I can think of that port 80 would be open from the outside would be if the router owner was running a webserver inside your local network, and wanted entire world to be able to access it.  And even then, port 80 would be forwarded to that server, not your PC.

Usually routers firewall incoming connections that you haven't initiated, which is a good thing.  You wouldn't want anyone out there in the world to be able to attempt a connection directly to your PC.

The earlier suggestion of reverse ssh tunneling is what you want to do.  That would only work, however, if there is a machine on outside your LAN that you have access to that can act as a middle man between you and your home PC.  Is that an option for you?

---

### Post by silverglade00 on 2010-08-20
I think you are out of luck. Without telling the router where to send the traffic, it has no way of knowing to send it to your computer. If it helps, Teamviewer has a Linux version now that works great. You can just set it up with a permanent connection and give it a good password.

---

### Post by silbak04 on 2010-08-20
Not sure if this will work but you can give it a shot:

[http://www.howtoforge.com/reverse-ssh-tunneling](http://www.howtoforge.com/reverse-ssh-tunneling)

---

### Post by xjwellsx on 2010-08-21
Thanks for all of your guy's help I believe I am out of luck, because both computer I would be using are sitting behind router that I don't have access to eg. work computer, home computer. But thanks to all who tried

---

### Post by earthpigg on 2010-08-21
> **xjwellsx said:**
> Thanks for all of your guy's help I believe I am out of luck, because both computer I would be using are sitting behind router that I don't have access to eg. work computer, home computer. But thanks to all who tried

i am convinced there is a way to make this happen.

router firewalls block incoming connections, but not outgoing connections.

you need to have the computer behind the router initiate the connection.

what is going through my head:

1) set up ddclient/dyndns or similar on your laptop or mobile computer, so it has a fixed domain even when you are at a coffee shop or library wifi. the dyndns website details how to do this & they provide this service for free. it will be something like whatever.homelinux.net.

2) every 10 minutes or so, have your desktop attempt to contact [email]joe@whatever.homelinux.net[/email] on some random port & establish the connection with a specifically-created username for this purpose (cron job). make this account on your laptop be a very restricted account - cannot read, write, or see anything.

3) sit at the coffee shop for 10 minutes or so, then run the 'users' command. when you see the limited user account as logged in, then your desktop has initiated a connection on the random port to your laptop.

4) since that connection was established from behind the apartment's firewall, it won't block communication on that port. you should now be able to ssh back to your desktop on that same port. i think.


this will take some testing, and it will be annoying driving back and forth to the coffee shop or wherever every time you want to test it.

you will need to ***not*** be behind a firewall at wherever you are at with your laptop. this may be the problematic part, as a coffee shop can be expected to have a standard default router configuration - firewall and all. if you are connected via a cell phone with tethering, that could work... where are you trying to ssh into your desktop from?


EDIT: just re-read your most recent post. this is still viable, but you need to have a 3rd computer to act as intermediary - one that you can enable port forwarding on. got any friends with an unix/linux/os x computer that would be willing to help, and has access to the router? the process described above would apply to this computer, not your laptop or work computer. ssh to the 3rd party computer from your work computer, and from there make the jump to your home desktop.

---

### Post by xjwellsx on 2010-08-22
thats my problem is that I don't have a server in the middle that I can send traffic through. I just wish there was a way like with team view were you don't have to port forward in the router. Thanks

---

### Post by Irony on 2010-08-24
> **xjwellsx said:**
> could you explain how to do this please that would be awesome if it would work.

Change 22 to 80;

[IMG]http://theillustratednetwork.mvps.org/Ssh/PuTTYSession.jpg[/IMG]

---

### Post by xjwellsx on 2010-08-26
yeah no luck with that I think I might see if I can do a port scan and see if there are any open ports and try to go through those

---

### Post by DFlame on 2010-08-26
Just a thought here, have you asked the owner of the router/connection to forward a port for you? If they're willing to make an exception for you then you'll save a lot of trouble :)

---

