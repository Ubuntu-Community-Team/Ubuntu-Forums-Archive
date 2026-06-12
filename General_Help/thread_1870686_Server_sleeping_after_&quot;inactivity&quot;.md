---
title: "Server sleeping after &quot;inactivity&quot;"
date: 2011-10-27
forum: General Help
---

### Post by vesuvian on 2011-10-27
Hi all!

I'm fairly new to Linux and am setting up a server with Xubuntu. Most stuff is going ok but I have a irritating issue: after some "inactivity" time the monitor goes black and cuts off ssh.

If I lean over and push the mouse I can reconnect via ssh absolutely fine until the screen goes black again. I'd like to get this sorted out asap so I can unplug everything and just hide the box somewhere.

As far as I can tell the power save settings are set to never go to sleep. Is there something I'm overlooking? I grepped the /etc directory for "power" but the results were too numerous to be useful!

Thanks

---

### Post by M!K3_$ on 2011-10-28
I'm assuming your server is running a GUI then?

---

### Post by vesuvian on 2011-10-28
Absolutely. I'm not one to shy away from the terminal, but I still have no idea how to do a lot of things without the help of pictures and buttons.

---

### Post by M!K3_$ on 2011-10-28
I did the same thing when I was starting messing around with servers. :)

It looks like it is disconnecting when your computer turns your video output off. That's weird though because the sshd should still be running. :S

What ssh server software are you using?

---

### Post by vesuvian on 2011-10-28
I'm using openssh

I'm starting to think it MAY (this is a weak guess at best) be the usb wireless adapter is turning off when the monitor turns off. Though the connection seems perfectly stable when I wiggle the mouse to make everything come back.

A colleague suggested there may be a "wake on network" setting somewhere which may essentially solve my problem.

Any thoughts?

---

### Post by vesuvian on 2011-10-28
Aha, started playing with iwconfig and discovered the network adapter had power save settings of it's own. I've sorted that out and will see how it goes.

---

### Post by Jose Catre-Vandis on 2011-10-28
May also be worth reading up on and trying out **screen**, which would allow you to set things running on a server then disconnect. You wouldn't then have to worry about the connection dropping. This might not be what you need, but you could then set up a small script (inside screen) that pings every five minutes to keep the connection alive?

---

### Post by M!K3_$ on 2011-10-28
In relation to what Jose has to say, screen is very useful and I suggest you learn it.

Wake on lan (WOL) wouldn't be it. That's for turning computers on with a "magic" packet(no joke, it's called a magic packet)

But the power save mode on your interface could very well be it. Let us know! :)

---

### Post by vesuvian on 2011-10-29
I'll look into screen eventually, busy weekend!

The wireless power settings have certainly helped, but eventually the connection will just start to fail. Also it takes a long time after "waking" the system before I can connect again via ssh or ftp.

This is a shame as I had hoped I could still play with server using my phone on today's 5 hour train ride!

Here's my iwconfig output:

wlan0     IEEE 802.11bg  ESSID:"BeBoxD062AD"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:76:FF:D0:62:AD
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:300824   Missed beacon:0

---

### Post by Jose Catre-Vandis on 2011-10-29
Although these are intended for a terminal session they might help:

Run them and see if your box still blanks and disconnects
```
setterm -blank 0 -powersave off -powerdown 0
```
```
xset s off 
```

This might also help:
[http://bimma.me.uk/2011/04/06/prevent-screen-blanking-on-xubuntu-cli-slim-openbox-install-on-asus-eb1012-nettop/](http://bimma.me.uk/2011/04/06/prevent-screen-blanking-on-xubuntu-cli-slim-openbox-install-on-asus-eb1012-nettop/)

---

### Post by vesuvian on 2011-10-31
Hah this is atrocious

I decided to leave the server on over the weekend on the off chance I might actually be able to ssh into it at some point. Turns out I could interact with the thing in realtime using my phone and a 3G connection while on a train!

It's pathetic that my Windows 7 machine is having so much trouble doing things like ftp and vnc with the server when they're both on the same local network.

---

### Post by M!K3_$ on 2011-10-31
> **vesuvian said:**
> It's pathetic that my Windows 7 machine is having so much trouble doing things like ftp and vnc with the server when they're both on the same local network.

What are you using for ftp on your windows box? I prefer filezilla.
I also recommend putty for ssh.

---

### Post by vesuvian on 2011-10-31
I'm using Filezilla and Putty!

Right now ftp seems to be behaving itself. Odd hiccup every now and then but otherwise it's doing alright.

And now I've tried it again, Putty seems to be working. Hmm.

Well, whatever is going on here, it certainly isn't ideal. I'd like to figure out what is making this so erratic.

---

### Post by Slim Odds on 2011-10-31
> **vesuvian said:**
> I'm using Filezilla and Putty!

Right now ftp seems to be behaving itself. Odd hiccup every now and then but otherwise it's doing alright.

And now I've tried it again, Putty seems to be working. Hmm.

Well, whatever is going on here, it certainly isn't ideal. I'd like to figure out what is making this so erratic.

Since you're running ssh on the server, I'd highly recommend that you use sftp for file transfer stuff instead of ftp

---

### Post by vesuvian on 2011-11-01
I've done a few more experiments and I am convinced this server is not acting correctly when being connected to via LAN.

At first I thought it might be because the computer I use from day to day is Windows 7, so perhaps it just inherently sucks at this.

However, I just compared connecting via ftp remotely and then locally using my phone (ie, connect to 87.194.xxx.xxx and then 192.168.1.100). Remote was instant, local timed out.

What is going on here? This is really frustrating. . .

---

### Post by M!K3_$ on 2011-11-01
That's really odd. (and that completely useless statement is all I have to say on that for now, sorry)

---

### Post by vesuvian on 2011-11-02
Bumping (sorry)

---

