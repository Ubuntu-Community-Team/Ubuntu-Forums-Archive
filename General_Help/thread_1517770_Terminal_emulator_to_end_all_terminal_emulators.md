---
title: "Terminal emulator to end all terminal emulators"
date: 2010-06-25
forum: General Help
---

### Post by MSPdwalt on 2010-06-25
Hey all,

I'm looking for the "Holy Grail" of terminal emulators  for my Ubuntu laptop.  I'm a network/server/desktop support engineer for  a managed service provider here in Minneapolis.  I've been running  Ubuntu for almost 6 months now (9.10 then 10.0.4) as my primary OS and  use vmware for my windows only apps.

During this time I have  managed to find open source equivalents that are as good or better than a  lot of the tools I used to use in Windows.  There is one exception....a  terminal emulator.  Under Windows I used putty, then SecureCRT.  

Putty  in Linux has all of the features that the windows implementation has,  except copy and paste is weird  (involves the middle mouse button) and I  have yet to figure out how to turn on text capture (session output  logging) on-the-fly. I can do it before I start the session, but I can't  turn it on/off mid-stream.

Here's the features I'm looking for:

-Session  storage with folders (putty-style storage is great for a handful of  devices, but I manage many across several sites for multiple clients)

-On-the-fly  text capture/session logging

-Telnet, SSH, and serial support

-Runs  natively in Linux (no wine)

Any Cisco guys out there? what do  you use?

Any feedback is greatly appreciated,

DW

---

### Post by lsutiger on 2010-06-25
I just want to follow this thread because I am in need of the same thing. I need an emulator that uses SCO-ANSI, which I have yet to find one that works correctly.

---

### Post by MSPdwalt on 2010-07-26
*bump*

---

### Post by MSPdwalt on 2010-08-11
*bump* again

---

### Post by bab1 on 2010-08-11
> **MSPdwalt said:**
> Hey all,

I'm looking for the "Holy Grail" of terminal emulators  for my Ubuntu laptop.  I'm a network/server/desktop support engineer for  a managed service provider here in Minneapolis.  I've been running  Ubuntu for almost 6 months now (9.10 then 10.0.4) as my primary OS and  use vmware for my windows only apps.

During this time I have  managed to find open source equivalents that are as good or better than a  lot of the tools I used to use in Windows.  There is one exception....a  terminal emulator.  Under Windows I used putty, then SecureCRT.  

Putty  in Linux has all of the features that the windows implementation has,  except copy and paste is weird  (involves the middle mouse button) and I  have yet to figure out how to turn on text capture (session output  logging) on-the-fly. I can do it before I start the session, but I can't  turn it on/off mid-stream.

Here's the features I'm looking for:

-Session  storage with folders (putty-style storage is great for a handful of  devices, but I manage many across several sites for multiple clients)

-On-the-fly  text capture/session logging

-Telnet, SSH, and serial support

-Runs  natively in Linux (no wine)

Any Cisco guys out there? what do  you use?

Any feedback is greatly appreciated,

DW

It appears you can log sessions in the Gnome Terminal.  I didn't know that.  :-)  See [**_here_**]("https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/7131").

---

### Post by MSPdwalt on 2010-08-24
@BAB1  Those options listed in your link are a little over complicated and still don't really do on-the-fly text capture.  If you have a windows box/vm I encourage you to download a trial of [secure CRT]("http://www.vandyke.com/products/securecrt/") then you'll get a better grasp of what I'm looking for.

Thanks for the response though, there's gotta be something out there, I just have to get the right person's attention.

---

### Post by MSPdwalt on 2010-10-29
*bump*

---

### Post by thinkinhurtz on 2010-10-29
Perhaps installing Terminator as the emulator which has some great features. Then installing "Screen" which is a terminal multiplexer, I believe it does some session logging among other things. 
sudo apt-get install screen

I'm not sure if that is exactly what you were looking for but screen can do a lot of things that most people wouldn't even know about. You may want to check the official documentation to see if it fits your requirements. 

Try looking for terminal plugins for different emulators if you still have problems. I hope that was some help......
Good Luck

---

### Post by cmcx_linux on 2010-10-29
As thinkinghurtz stated you would actually need a combo:
ssh & screen:
Ssh or telnet if you will to login remotely to a machine, and afterwards screen to keep the session alive on the targeted machine( even if the ssh connection drops or is disconnected). You just relog in your screen session and that's it.
Screen support writing to files. If you want to log the whole output of the application localy you can try ssh -p 12345 userid@server | tee -a logfile, meaning loginto the machine and copy the terminal output in the file.
In this way you can achieve what you did with rdp in a windows domain envir but for terminal.
If you want XWindows, study how to forward X11 apps through ssh. Unlike rdp/vpn, you can have windows of apps running on the targeted machine in your local desktop. ( Run the processing remotely but render the output locally in your desktop).

---

### Post by MSPdwalt on 2010-10-29
Thanks for the response guys, but I think you're both missing what I'm looking for.  It could be my fault, maybe terminal emulator isn't the right term...so let me try to describe it a different way...


Under windows I used a program called SecureCRT, what it did was store connection information for my different network devices in a nice little folder structure Client > Site > Devices. (routers, firewalls, switches, ect..) So if I needed to make a change to my Cisco PIX 515, I would double click the entry for that and the program would ssh into it for me.

Our SOP for confing changes is to capture the running to a text file before and after a change.  So now that I'm SSHed into the device I turn on text capture...issue my show run command, once the config has scrolled by (and been captured) I tun off the text capture, save the config to flash, and make my changes.  When I've finished I save the config to flash, then I turn on text capture, issue my show run command again, (config gets captured) and I end the session.

Does that help?

---

### Post by MSPdwalt on 2011-01-17
I've settled on screen for now, biggest thing it's missing for me is the ability to store session settings.

What I do is open a terminal and issue a screen command (or screen /dev/ttyS0 if I'm consoling directly into something)

once I'm in my screen session and get to the point that I want to capture something I hit Ctrl-a then H (make sure it's a capital H) then that creates a screenlog.0 text file in my home directory and copies output to it until I close the file with another Ctrl-a H.

Makes my captures a lot cleaner than capturing the whole session with putty.  Still not ideal though.

Maybe I'll make a shell script for each session or something...

---

### Post by theDaveTheRave on 2011-01-17
have you thought about NX ??

I know that it has a 'session admin' screen. I believe that you can have multiple connections, but I've only ever needed a single connection.

Don't know if you can set it up to automatically record session output though, but as it uses SSH I'm sure it can be somehow set up to do so.

David

edit: Just thought, with ssh you can also X-forward, then create simple shell scripts for the different locations you SSH to (as you previously mentioned) with the correct SSH command to record output to a local file.

---

### Post by MSPdwalt on 2011-01-17
> **theDaveTheRave said:**
> have you thought about NX ??

I know that it has a 'session admin' screen. I believe that you can have multiple connections, but I've only ever needed a single connection.

Don't know if you can set it up to automatically record session output though, but as it uses SSH I'm sure it can be somehow set up to do so.

David

edit: Just thought, with ssh you can also X-forward, then create simple shell scripts for the different locations you SSH to (as you previously mentioned) with the correct SSH command to record output to a local file.

Thanks for the reply, but I'm dealing with network devices, specifically Cisco network devices.  NX requires an NX client to connect to an NX server, then the NX server will give you an X11 session (KDE/GNOME/XDMC), RDP session, or VNC session to a server.

You can capture a standard SSH session from gnome terminal using the script command **before** you start the session capturing everything, but as I've stated earlier there's only certian parts of my ssh/telnet/console sessions I'd like to capture, not the whole thing.

---

### Post by theDaveTheRave on 2011-01-18
sorry I didn't twig that you are logging into network devices, well I did, but didn't realise they where CLI only. Sorry for that.

If you can SSH into the devices can you not set the logging level much higher on them, so as they catch what you are looking for?

Or am I off base??

you'll have to excuse me, as I don' know that much about networking devices (apart from the fact that my pc plugs into one!). But my experience is that sometimes the 'stupid' and 'semingly bloody obvious' aren't always the first thing people think off, and bouncing the ideas around can soemtimes lead to a bright idea.

David

---

### Post by MSPdwalt on 2011-01-20
> **theDaveTheRave said:**
> But my experience is that sometimes the 'stupid' and 'semingly bloody obvious' aren't always the first thing people think off, and bouncing the ideas around can soemtimes lead to a bright idea.

David,

On this we completely agree.  You are a little off base as far as what I'm looking for though.

I'm not looking to grab logs (there's syslogging for that).  Cisco devices keep their active configuration in RAM, and their boot up configuration in NVRAM.  The active configuration isn't saved to NVRAM unless you give it a command to do so.

They have the ability to output both configurations to the screen in a format that can be pasted into the device in the event of a hardware failure or the need to revert to a previous config. It's also nice to have a few revisions around for comparisons.

So lots of people will turn on text capture before they run that command.  It makes comparison and review a lot easier if you don't have the entire session captured.

Thanks for the attempt though, and let me know if there's anything obvious I've skipped over. ;)

---

### Post by djeikyb on 2011-01-20
Check out the script command. It'll copy everything you do on the terminal until it encounters EOF (ie control+d).

---

### Post by coldraven on 2011-01-21
I'm not sure if this is what you want...
[http://fileforum.betanews.com/detail/Telconi-Terminal-for-Linux/1101837624/3](http://fileforum.betanews.com/detail/Telconi-Terminal-for-Linux/1101837624/3)

---

### Post by theDaveTheRave on 2011-01-24
I hate to be a bother but I like this thread as I'm learning stuff.

MSPdwalt

you are logging into networking devices, I guess that these don't have a output device as such attached to them (and no input mechanism either) so you must have to log into them remotely?

Why is grabbing the logs a 'non starter' for you though? surely you could catch them somehow then grep through them with perl / awk (or your favorite other scripting language)?

Or is capturing the logs (and the size of them) the issue?

David.

---

