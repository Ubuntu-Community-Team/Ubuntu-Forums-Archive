---
title: "How do I link 2 ubuntu computers via crossover cable"
date: 2009-09-06
forum: General Help
---

### Post by t0p on 2009-09-06
I have 2 computers - a desktop pc running hardy and a netbook running jaunty.  I want to connect them with a crossover cable.  I need a howto for newbies to networking.

Please note, it *must* be suitable for newbies.  I emphasise this because so-called newbie guides that I've found on the internet contain sentences like "Assign ip addresses to the computers, ensuring they are on the same sub-net."  Completely useless to the newbie who doesn't know *how* to assign ip addresses.

Any help gratefully received.

---

### Post by falconindy on 2009-09-06
Wait, like a serial crossover cable? Those still exist? 

If you're attempting to use a network crossover cable, you're still going to need to assign IP addresses. There's no way around it. I'm on OS X right now, so I can't check my facts, but going from memory....

System > Preferences > Network Connections

Under the first tab, you should see a connection such as eth0. Edit that connection and go to the IPv4 settings tab. Assign an IP address like 10.0.1.1 with a subnet of 255.255.255.0.

Go to the second computer, do the same thing except use 10.0.1.2. Same subnet.

---

### Post by makariolewis on 2009-09-06
> **falconindy said:**
> Wait, like a serial crossover cable? Those still exist? 

If you're attempting to use a network crossover cable, you're still going to need to assign IP addresses. There's no way around it. I'm on OS X right now, so I can't check my facts, but going from memory....

System > Preferences > Network Connections

Under the first tab, you should see a connection such as eth0. Edit that connection and go to the IPv4 settings tab. Assign an IP address like 10.0.1.1 with a subnet of 255.255.255.0.

Go to the second computer, do the same thing except use 10.0.1.2. Same subnet.
If you're using the latest version of Ubuntu, the location for network settings has changed. Now, you have to right-click the network icon in your notification area (top right), and choose "Edit Connections..." to find the network settings.

---

### Post by spiderbatdad on 2009-09-06
not really a simple way of connecting 2 linux computers via crossover cable for any practical reason. Perhaps you could clarify your goal. Are you interested in file sharing, or sharing a network connection?

---

### Post by t0p on 2009-09-06
> **spiderbatdad said:**
> not really a simple way of connecting 2 linux computers via crossover cable for any practical reason. Perhaps you could clarify your goal. Are you interested in file sharing, or sharing a network connection?

I want to do several things with the connection.  The desktop machine has a large hard drive and the netbook has very little storage capacity, so I want to be able to access files from one to the other.  I may want to share internet connection.  I'm interested in playing with apache.  I'll probably want to do other stuff.

When I get home I will try out the suggestions that have already been made.  Thanks to all.

---

### Post by falconindy on 2009-09-06
> **makariolewis said:**
> If you're using the latest version of Ubuntu, the location for network settings has changed. Now, you have to right-click the network icon in your notification area (top right), and choose "Edit Connections..." to find the network settings.

That's an alternative method, yes. You're still able to access the connection manager from the main menu, though.

> not really a simple way of connecting 2 linux computers via crossover cable for any practical reason. Perhaps you could clarify your goal. Are you interested in file sharing, or sharing a network connection?
Agreed. A lot of times, questions are a LOT easier to answer when people describe their ultimate goal, and not just their problem.

---

### Post by makariolewis on 2009-09-06
> **falconindy said:**
> That's an alternative method, yes. You're still able to access the connection manager from the main menu, though.


Ah, yes. I see it now; I just remember it being in Administration. Now it's in Preferences. Good to know.

---

### Post by scouser73 on 2009-09-06
I know that you are looking to connect two Ubuntu computers together, but I thought I'd share my experience with you nonetheless.

I recently linked my Ubuntu PC to my brothers Windows XP machine, this was done with an Cat5e Patch Lead via a router.

**Step 1** - Place one end of the Cat5e Patch Lead into a Router or Switch
**step 2 **- Place the other end of the Cat5e Patch Lead into the other computer/netbook

I was immediately able to access the internet/email etc. on both computers.

I didn't encounter any problems with "assigning IP addresses", it was a simple plug in and surf.

As for sharing your files between the two PC's I have no experience in this field but I'm sure someone will give you the help you're after.

---

### Post by lswb on 2009-09-06
Actually, it is simpler than you think. hardy and jaunty both have avahi installed and working by default. This is an implementation of the "zero config" or "link local" protocol which largely developed by apple; I beleive on a mac it is called "bonjour"

Plug your crossover cable into the 2 systems and in a moment or so they will self-assign ip addresses in the 169.254.x.x range. They will also be accessible by using the name "hostname.local" where "hostname" is replaced by the name of your system. If the 2 boxes are named hardy and jaunty, you should be able to "ping jaunty.local" from hardy when the crossover cable is connected.

You will still have set up some way to transfer files, all avahi does is provide the connectivity. I suggest for linux or unix boxes, install open-ssh on both boxes, then you can connect by using Main Menu/Places/Connect to Server, select SSH for server type, fill in the other fields, hit connect, and a file browser window will open for the remote system.

---

### Post by t0p on 2009-09-08
> **lswb said:**
> Actually, it is simpler than you think. hardy and jaunty both have avahi installed and working by default. This is an implementation of the "zero config" or "link local" protocol which largely developed by apple; I beleive on a mac it is called "bonjour"

Plug your crossover cable into the 2 systems and in a moment or so they will self-assign ip addresses in the 169.254.x.x range. They will also be accessible by using the name "hostname.local" where "hostname" is replaced by the name of your system. If the 2 boxes are named hardy and jaunty, you should be able to "ping jaunty.local" from hardy when the crossover cable is connected.


Thanks for the tip.  But it didn't work.  I get the network manager's "connecting" icon on both computers when I plug in the crossover cable.  After a while, I get the "connected" icon on the hardy machine - but Connection Info claims the ip address is 0.0.0.0, DNS server is 0.0.0.0 etc.  The jaunty machine doesn't even pretend to be connected - after watching the "connecting" icon go round and round for a while, the "disconnected" icon appears.  I have no idea how to fix this.

As for the other suggestions made in this thread: I shall explore them now.  Unfortunately, the GUIs on my computers are not the same as some of yours.  My desktop computer is running Xubuntu Hardy.  The netbook is running Eeebuntu (Gnome) Jaunty.  So some of the instructions don't fit what I can see.  Nevertheless, I shall see what I can do.  In the meantime, can anyone suggest how I fix the avahi/"link local" problem?

---

### Post by t0p on 2009-09-08
Okay, I got the zeroconf/link local link apparently working, by selecting the "zeroconf" or "link local" options in the Properties of the eth0 connection.  By "apparently", I mean that the network manager icon indicated a successful connection, and network manager reported a "wired connection" over eth0.

Unfortunately, there doesn't seem to actually *be* a connection.  Checking the properties of eth0 told me its ip address was 169.254.2.163.  So, I tried 

```
ssh 169.254.2.163
```

but the response was

```
ssh: connect to host 169.254.2.163 port 22: Network is unreachable
```

And eth0 on the desktop computer doesn't seem to have an ip address.  Which doesn't make much sense to me...

---

### Post by t0p on 2009-09-08
> **falconindy said:**
> 
System > Preferences > Network Connections

Under the first tab, you should see a connection such as eth0. Edit that connection and go to the IPv4 settings tab. Assign an IP address like 10.0.1.1 with a subnet of 255.255.255.0.

Go to the second computer, do the same thing except use 10.0.1.2. Same subnet.

This doesn't work.  On jaunty, there are 3 fields to be filled in: ip address, mask, and *gateway*.  The Apply button is greyed-out, which I assume is because the gateway field needs to be filled in.  Can anyone tell me what I should put in the gateway field?

The GUI differences (different version of ubuntu, different window manager) is making this more complicated than it needs to be, I'm sure.  Can someone please tell me what I need to use *in the terminal* to set up this connection?  That will be a lot more simple.

---

### Post by t0p on 2009-09-08
Okay, I found out how to connect the computers, from [this thread]("http://ubuntuforums.org/archive/index.php/t-50825.html").

Basically, I type into the terminal on my desktop machine:

```
sudo ifconfig eth0 192.168.0.1
```

and on the netbook:

```
sudo ifconfig eth0 192.168.0.2
```.

Now, if I go to **Places > Connect to Server** and set up a ssh connection, I can transfer files through sftp in Nautilus. I can type the ip address of the desktop machine into the browser on the netbook and access the web pages on the Apache server.

2 simple lines of code.  Sweet!  :)

---

### Post by lswb on 2009-09-08
I think that some of the settings you have changed are interfering with avahi working on the jaunty box. It is possible to connect the systems by more than one method, it will be easier to help if you choose one and we can step through that method. If you try to do it 2 or more different ways at the same time, well, "that way lies madness" I think Shakespeare said.

By far (IMHO) the easiest way is to just use avahi/zerconf. If you have configured a system to use a static IP address as some of the others in this thread have suggested, it will likely prevent avahi assigning a 169.254.x.x address. 

The more complicated method is to assign a static ip address in the same subnet to both systems. This method is also not too difficult, but IIRC, the version of Network Manager shipped with hardy has a problem with static ips and you will have to use the /etc/network/interfaces file to set this up. (I'm not certain about this recollection, though, maybe someone else can verify)

Anyway, I think it will be easiest to start from a clean slate on both machines, choose one method, and step through it. I would suggest, if you have edited the /etc/network/interfaces file on either system, change it back to the original version, i.e. the only contents are 
```

auto lo
iface lo inet loopback

```

If you have changed settings using the Network Manager/Edit Connections dialog in jaunty, open it again, select wired network; it will probably have a selection "auto eth0" Select that, click on edit, click on the IPv4 tab, and set it to the first selection in the drop down list, "Automatic (DHCP)"

I don't have a running hardy system available at the moment so I can't say for sure what the steps are, but set hardy NM settings back to the premodified, vifgin state also.

Likewise if you have modified any network settings from Main_Menu/System/Network or whatever, set them back to default.

At this point, avahi/zero-conf should work as advertised. If you decide you'd rather use the static ip address method, post again and we'll walk through it. Before you post again, install open-ssh server on both systems, and if you do post, include your system names the the output of the terminal command "ifconfig" from both systems.

EDIT: I posted the above before I saw your last post. Can't argue with success. Glad you got it working, it always feels better when you do it on your own, doesn't it?  :)

---

### Post by t0p on 2009-09-09
Okay, I had marked this thread as 'Solved'.  But then I realized, I haven't tackled sharing internet connection yet.  And that's something I want to do.  So I'm back.  I've marked the thread unsolved again, and I'm here soliciting for advice.

I do *not* have a router, nor do I wish to use one.  I don't have 2 ethernet cards either.  I connect to the internet using a 3G/HSDPA modem.  So: what do I need to do in order to share an internet connection?  When the modem is connected to my netbook, I can share that connection with the desktop machine by starting a command-line ssh session and running w3m, eg with the command

```
w3m www.google.co.uk
```

Unfortunately, w3m is a pretty dull browser.  So how do I get my desktop pc to get Firefox on the interwebs, via the ethernet 'crossover' connection to the netbook and its 3G modem?

---

### Post by croissont on 2009-09-09
I have a Windows OS installed on my netbook and a dualboot of Windows/Jaunty on my PC. I could not access the net from my PC because of lack of a wired/wireless connection and the modem was pretty far off to consider a wired connection. I had the same problem that you had so I connected a RJ45 cable from the laptop to my PC and configured the internet client (this is in Windows) and I could access the internet. Ubuntu did not give me a problem when I tried to access the net, which felt good, 'cause Windows pretty much sucks. 

Regarding your file sharing problem, I setup FileZilla between the PC and the laptop(in Windows; used the PC as server and lappy as Client) and it worked fine. Checked the ips using ipconfig and configured the server/client and it worked. You can use it in Ubuntu too:

[http://www.ubuntugeek.com/filezilla-ftp-client-software.html]("http://www.ubuntugeek.com/filezilla-ftp-client-software.html")

[http://ulyssesonline.com/2008/04/28/filezilla-in-ubuntu-804-linux/]("http://ulyssesonline.com/2008/04/28/filezilla-in-ubuntu-804-linux/")

I'm gonna try using it and let you know :)

Edit: The server application is only for Windows, but if you can map the drives I bet you can send files. Mount the devices and you'll be good to go.

---

### Post by t0p on 2009-09-11
> **croissont said:**
> I have a Windows OS installed on my netbook and a dualboot of Windows/Jaunty on my PC. I could not access the net from my PC because of lack of a wired/wireless connection and the modem was pretty far off to consider a wired connection. I had the same problem that you had so I connected a RJ45 cable from the laptop to my PC and configured the internet client (this is in Windows) and I could access the internet. Ubuntu did not give me a problem when I tried to access the net, which felt good, 'cause Windows pretty much sucks. 


That's what I want to do, but I don't know how.

Okay, I'll spell it all out:

I have 2 computers: **Computer A**, a desktop machine running Hardy (Xubuntu); and **Computer B** running Jaunty (Ubuntu).  They are connected via their *eth0* interfaces and a crossover cable.

**Computer B** is connected to the internet via a hsdpa modem - this uses interface *ppp0*.

I want to be able to access the internet on **Computer A**, using a web browser (firefox).  I mention firefox because I can access the internet on **Computer A** by opening a shell on **Computer B** via ssh and using w3m.  I don't want to use w3m.  I tried doing it by opening that shell then typing 'firefox', but I got an error 'no display specified'.

How do I do what I want to do?

---

### Post by spazzeri on 2010-07-12
> **lswb said:**
> I think that some of the settings you have changed are interfering with avahi working on the jaunty box. It is possible to connect the systems by more than one method, it will be easier to help if you choose one and we can step through that method. If you try to do it 2 or more different ways at the same time, well, "that way lies madness" I think Shakespeare said.

By far (IMHO) the easiest way is to just use avahi/zerconf. If you have configured a system to use a static IP address as some of the others in this thread have suggested, it will likely prevent avahi assigning a 169.254.x.x address. 

[...]



This was working fine for me in Ubuntu Karmic. The other machine is a Mac, and wicd was assigning a 169.254.* address to the Ubuntu machine, which was then reachable as hostname.local.

Unfortunately this stopped working after the upgrade to Ubuntu Lucid. Have you any idea how to fix this ?

---

### Post by felixq78 on 2010-08-04
> **scouser73 said:**
> I know that you are looking to connect two Ubuntu computers together, but I thought I'd share my experience with you nonetheless.

I recently linked my Ubuntu PC to my brothers Windows XP machine, this was done with an Cat5e Patch Lead via a router.

**Step 1** - Place one end of the Cat5e Patch Lead into a Router or Switch
**step 2 **- Place the other end of the Cat5e Patch Lead into the other computer/netbook

I was immediately able to access the internet/email etc. on both computers.

I didn't encounter any problems with "assigning IP addresses", it was a simple plug in and surf.

As for sharing your files between the two PC's I have no experience in this field but I'm sure someone will give you the help you're after.

He asked for advice on Networking 2 Ubuntu machines with a crossover cable and we get your post which describes a totally different setup. While I admire your motivation to help, it's not really what he was seeking. 
Of course you had no problems with IP addresses you're using Windows!

---

