---
title: "Connecting Ubuntu to Ubuntu through VNC. Remote Desktop."
date: 2011-04-19
forum: General Help
---

### Post by winchendonsprings on 2011-04-19
[SIZE=2]The scenario is as follows - I will be moving across  the country and my desktop will stay here powered and online, while I  move with a laptop. I need a way to connect to the desktop for file  streaming(music and movies) as well as using the virtual machines. I  have thought about SSH and VNC. [/SIZE][SIZE=2]
[/SIZE]
  [SIZE=2]I need something failsafe. That's priority one. I won't be around to  fix it if it breaks. I can set the computer to come on in the BIOS at a  certain time if the power went out. But if I can get in remotely the  whole setup is useless.[/SIZE][SIZE=2]
[/SIZE]
  [SIZE=2]SSH only provides terminal use, correct? So if I chose that route I  would be able to access the computer via command line and play music and  movies with mplayer and such, correct? But I would not be able to run  the virtual machines? Because there will be no GUI, right?[/SIZE][SIZE=2]
[/SIZE]
  [SIZE=2]I have been playing with Vinagre and Vino through the host and guest  of a virtual machine and I cannot get it to connect. Is there a better  application? x11vnc? I have forwarded port 5900 on the router and have  upnp enabled. Got a better remote desktop suggestion?[/SIZE]

  [SIZE=2]I would like to run this setup headless.(no monitor) I also would  like to run it without a gpu if that is possible to make it more energy  efficient.[/SIZE][SIZE=2]
[/SIZE]
  [SIZE=2]Both computers are 64 bits and will be running Ubuntu 10.10 and soon 11.04.[/SIZE][SIZE=2]
[/SIZE]
  [SIZE=2]Are these crappy ideas to begin with? Should I go another route to get my files and access the virtual machines?[/SIZE]

---

### Post by krunge on 2011-04-20
If you want it to be failsafe make sure you have SSH enabled and it restarts properly at reboot including any SSH server port (22) redirection from your router.  If you can SSH in then you can do ANYTHING (run shell commands, run X gui apps, or do VNC tunnelling.)

I can show you what command to run to do the VNC tunnelling thru the SSH tunnel (and since you require failsafe I recommend doing it this way instead of relying on a VNC server to start automatically.)  But first a couple things:

Will you be able to get your IP address remotely?  Sometimes an ISP will change it on a reboot/reset (e.g. power outage you lose your DHCP lease.) Do you have dyndns or something like that (and does it start properly upon reboot?)

Streaming "music and movies"? What's that about?? Sounds goofy to me to want to stream those through a SSH link to your laptop. (Not that it can't be done in some cases at some tolerable level of performance, but it makes me wonder what you are trying to acheive, so I ask...)

---

### Post by winchendonsprings on 2011-04-20
@krunge Thanks for the info.

Last night I set up a dyndns account and configured it with my router. 

I feel vnc may not be the best solution for my situation. I would like to run the virtual machines remotely but that is not absolutely crucial. I can copy them to the laptop.

> If you want it to be failsafe make sure you have SSH enabled and it  restarts properly at reboot including any SSH server port (22)  redirection from your router.
How would I go about doing this? I know how to include a program at start up after X starts but I'm not sure before. At least I haven't researched this yet. 

>  Sounds goofy to me to want to stream those through a SSH link to your laptop.
Well, the reason I thought this would be a good idea is because my home computer has lots and lots of music and movies. I thought instead of trying to decide what I will copy and what I wont, this would be a better idea. No? Do you suggest I just copy them over and erase them as needed?

---

### Post by krunge on 2011-04-20
> 
I feel vnc may not be the best solution for my situation.

It might not be, I'm not sure.  I find it ideal for accessing my workstation's display at home when I am travelling or at work.

Note that VNC doesn't do sound, and watching a video through it will be choppy except over a LAN.  So you will at least need to stream the music and video files to your laptop and run the player locally on your laptop. Long ago, I used to stream mpg's through an ssh link and play them locally via mpg123.  This works OK as long as the link is not intermittant.

> 
How would I go about doing this? I know how to include a program at start up after X starts but I'm not sure before. At least I haven't researched this yet.

There are two modes to consider. 1) Your X session is already up and running and 2) the system rebooted and you have no X session (i.e. the physical display is at the login window.)

If you want to use the physical display in both of those I can show you how to run x11vnc to attach to it.  For 2) you will need to use sudo to access the login panel via x11vnc.

It is possible to have x11vnc automatically attach to the X server for both 1) and 2). BUT you said you want the solution to be failsafe, so you'll need to know how to run x11vnc manually for both cases.

If you do not want to use the physical display, you probably should use the vncserver program (which is a wrapper script that launches Xvnc)

So for example if the VNC server (either x11vnc or vncserver) is running on port 5905 (note you get to choose and specify this value) the ssh command would look something like:
```

laptop>  ssh -C -L 5905:localhost:5905 you@your.home.ip

```
Then, for simplicity, in another terminal on laptop:
```

laptop>  vncviewer localhost:5

```
Of course all of this can be scripted, including starting x11vnc or vncserver if needed.


BTW, another option for a non-physical display would be nx, but I don't know how to set that up or use it.  I believe it sets up a special nx user that gets logged in via SSH and then attached to an X login panel for a nx  virtual X session.

> 
Well, the reason I thought this would be a good idea is because my home computer has lots and lots of music and movies. I thought instead of trying to decide what I will copy and what I wont, this would be a better idea. No? Do you suggest I just copy them over and erase them as needed?

Yes, what I would do when remote is scp the media files to the laptop, play them as much as you want and then delete them if you run out of space.  Streaming them live out of your home via broadband will work, but will probably have some glitches is my guess, but you would have to try it and see.

---

### Post by lmcfadden on 2011-04-20
> **winchendonsprings said:**
> 
  [SIZE=2]I need something failsafe. That's priority one. I won't be around to  fix it if it breaks. I can set the computer to come on in the BIOS at a  certain time if the power went out. But if I can get in remotely the  whole setup is useless.[/SIZE]

Perhaps a program like TeamViewer would work for what you want??  I have used it to provide remote support to friends with PCs and Macs, as well as tested it with my Ubuntu installs.

[http://www.teamviewer.com/en/download/index.aspx]("http://www.teamviewer.com/en/download/index.aspx")

---

