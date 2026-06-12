---
title: "SSH from dumbphone to Ubuntu"
date: 2009-07-13
forum: General Help
---

### Post by Levviathor on 2009-07-13
I have a [LG Lotus]("http://reviews.cnet.com/cell-phones/lg-lotus-black-sprint/4507-6454_7-33350843.html?tag=mncol;rnav") with unlimited data, and was hoping to SSH to my Jaunty laptop from it.

Unfortunately, I haven't done anything of this sort before, so I'm pretty lost.

I've already installed the openssh-server package, but it sounds like some modem (I don't have a router) hacking is needed.

---

### Post by Levviathor on 2009-07-13
Bump? Anybody?

---

### Post by The Cog on 2009-07-13
You intend to connect over the internet (not bluetooth)?

Do you have an SSH client for the phone?

How does your PC connect to the internet? If it's by modem rather than a router, then I don't think any hacking is needed there. Make very sure you have good passwords - there are lots of SSH password guessing bots out there.

If you have a client on your phone and your PC is connected by modem, you should just have to enter the username/ip address into the SSH client on the phone, then fill in the password prompt.

---

### Post by Levviathor on 2009-09-03
Haven't gotten it working yet.

I'm trying to SSH over The Internet.

I'm using an app called midpSSH.

Using whatsmyip.org, I found and entered my IP address, username, and password, but it coughed up some sort of connection error.

I had set my SSH port from 22 to 2222.  I think that may have caused the problem.  I've set it back to 22, but since my phone is drying off on a shelf, testing will have to wait.

---

### Post by bacardiandwatermelon on 2009-09-03
[FONT=Microsoft Sans Serif][SIZE=2]```
sudo apt-get install ssh
``````
gksudo gedit /etc/ssh/sshd_config
```[/SIZE][/FONT][FONT=Microsoft Sans Serif][SIZE=2]Make some changes...
PermitRootLogin no
StrictModes no

[/SIZE][/FONT][FONT=Microsoft Sans Serif][SIZE=2]You will then have to setup port forwarding on your router so all requests on port 22 goto the machine running ssh.

you may want to get a dynampic ip from [www.no-]("http://www.no-")**ip**.com, some routers let you run this from the router rather than downloading software, this means you can goto a site ie blah.gotdns.com which maybe easier to remember..

When I setup putty on my n97 I setup a private and public key pair, and made other changes to the ssh_config file like this below so nobody can connect without the key file.

[/SIZE][/FONT][FONT=Microsoft Sans Serif][SIZE=2]PermitEmptyPassword no
PasswordAuthentication no

But yeah, I might have left stuff out, it has been a while since I set this up...
[/SIZE][/FONT][FONT=Microsoft Sans Serif][SIZE=2]
Oh I just re read and noticed the no router remark.. whoops :-P
[/SIZE][/FONT]

---

### Post by t0p on 2009-09-03
> **Levviathor said:**
> Haven't gotten it working yet.

I'm trying to SSH over The Internet.

I'm using an app called midpSSH.

Using whatsmyip.org, I found and entered my IP address, username, and password, but it coughed up some sort of connection error.

I had set my SSH port from 22 to 2222.  I think that may have caused the problem.  I've set it back to 22, but since my phone is drying off on a shelf, testing will have to wait.

MidpSSH is a good app.  I use it to connect to a shell account on a NetBSD machine.  I find that I have to reset line length/monitor height in my shell profile, because the usual height and length won't fit on my phone's screen.  But I don't know what the LG Lotus display is like.

Oh yeah, about your IP address: it will change every time you reconnect your server to the internet.  The easiest solution is to do what bacardiandwatermelon says, use a service like no-ip.com or [DynDNS.com]("http://www.dyndns.com/").  I've never used no-ip.com.  DynDNS will give you a free subdomain, like username.dyndns.com, and a program to run which will regularly check if your IP address has changed and update your DNS record.  So you'll always be able to use your url, username.dyndns.com, to connect to your server.  I've used this service, it works well.

The only big problem might be if your ISP has got port blocking or something like that.  But changing to a higher port number often gets around that.

---

### Post by Penguin Guy on 2009-09-03
> **Levviathor said:**
> I had set my SSH port from 22 to 2222.  I think that may have caused the problem.  I've set it back to 22, but since my phone is drying off on a shelf, testing will have to wait.
That probably was the problem, post back once you've tested it.

---

### Post by Levviathor on 2009-09-17
So, having dried off my phone, set my SSH port to 22, verified that the appropriate openssh packages are installed and running, and successfully connected to localhost, I still can't get it to work.

The Connection Information listed by the Network Manager applet told me my ip address, but connecting to that didn't work.  I suspect there may be a telco filter or firewall at play.

MidpSSH (the app I'm using on my phone) has options for using an HTTP proxy, but I have little idea what that means, and no idea how to use it.

I replaced the dev version I was using with the stable release, but I still keep getting a java connection error. (Writer: javax.microedition.io.ConnectionNotFoundException)

My current goal is to dig into this proxy/telco firewall business, but I'd still appreciate any help.

---

### Post by Levviathor on 2009-09-18
I was able to make a connection from my phone to Qwest's (my ISP) SMTP serverover port 25.  At the bare minimum this means that Sprint does not filter traffic to/from my phone on port 25.

The theory is that I could SSH over port 25, but I'm still not sure if I've found the right IP address to connect to my laptop.  Any advice on how to get my real IP address in dottedipv4 format would be amazing.

I also don't know how to either
* change which port my lt expects SSH traffic over
or
* redirect traffic to port 25 to port 22.

---

### Post by e24ohm on 2009-09-18
> **Levviathor said:**
> I was able to make a connection from my phone to Qwest's (my ISP) SMTP serverover port 25.  At the bare minimum this means that Sprint does not filter traffic to/from my phone on port 25.

The theory is that I could SSH over port 25, but I'm still not sure if I've found the right IP address to connect to my laptop.  Any advice on how to get my real IP address in dottedipv4 format would be amazing.

I also don't know how to either
* change which port my lt expects SSH traffic over
or
* redirect traffic to port 25 to port 22.

I have never seen this phone before. What OS is it running that you can install applications of this sort? This is a really interesting idea. Please provide more information when you have time.
thank you

---

### Post by Levviathor on 2009-11-20
Oops.  Sorry for the late reply.  Don't know if you'll ever see this, but here goes.

Most phones made in the last couple years have a java virtual machine (J2ME) installed, allowing them to run applications and games.  There are web browsers, gps, maps, translators, todo-lists, and more.  If your phone can play games than it has J2ME.

Unfortunately, you need a data plan to do anything cool without getting slammed by ridiculous data charges.  These are usually 15-30USD a month, so far as I know.

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
I do this often with my android phone and the only thing I could tell you is that some ports are blocked by the phone provider in some instances. I can't use FTP to connect to my phone from PC on t-mobile's network. This may be the case for your provider as well. I found open ports that I can use for certain instances by using nmap on my PC to scan my phone's IP.

---

