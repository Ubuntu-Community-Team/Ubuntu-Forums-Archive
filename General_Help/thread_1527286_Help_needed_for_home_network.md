---
title: "Help needed for home network"
date: 2010-07-09
forum: General Help
---

### Post by xhaggotx on 2010-07-09
I am looking for a solution to make my home network run easily.
This is the set up I have:
PC downstairs by a tv, with 3TB of storage containing my media, connected to the tv too.
HTPC upstairs by another tv and connected to it.
A few laptops and other desktops around the house which are windows based

I want the downstairs pc to act as a file server and to run my torrent client, it is running Ubuntu desktop version and has xbmc installed too for use with the tv. The upstairs htpc has xbmc live on and will access the media from the file server.
What I am looking to do is to be able to log into my ubuntu machine remotely from a laptop running windows so I can manage the files and add torrents for download etc, but for this to be a complete remote session, rather than taking control over what is already being shown on the downstairs pc, like VNC does in windows.

What is the best way to do this?
I have two user accounts set up on the main ubuntu machine, the admin account and a media user account which is set to go straight to xbmc after log in. Also how can I make sure that the media drives are automatically mounted to allow access if the admin user is not logged in?

---

### Post by CharlesA on 2010-07-09
You can add the media drives to /etc/fstab so that they are mounted automatically on boot.

---

### Post by VeeDubb on 2010-07-09
Adding the media drives to /etc/fstab is definitely the way to go for getting those mounted consistently.

For other administration tasks, do you need a GUI for your remote session or are you only doing things that you could do easily from a command line?

If a command line is good enough, then you could just install ssh on the server, and install Putty on the windows machine.  That would be straight forward and not very resource intensive, which may be important depending on what kind of hardware your HTPC/media server is running.

---

### Post by xhaggotx on 2010-07-09
Thanks for the info on mounting the drives, I will look how to do that (new to linux)

The media server is a full pc running some dual core intel processor (can't remember exactly, am at work not home) with 4GB of ram. The htpc would just be accessing the file shares not the actual system.

All I would be doing would be moving files around and adding torrent links for downloading or even just adding RSS feeds to the BT client. Would SSH be fine for doing that? I'm not used to command lines coz of using windows for many years now but I am not "scared" of them

---

### Post by Darkness Des on 2010-07-09
SSH with X11 forwarding would be good for that, if the PC downstairs is a Linux PC. I'm not quite sure if SSH (much less with X forwarding) could even work on Windows.

---

### Post by xhaggotx on 2010-07-09
Yes the downstairs pc is linux. Would that be fine to forward to a windows machine then?
If so, what would I have to install on both machines?

---

### Post by CharlesA on 2010-07-09
> **Darkness Des said:**
> SSH with X11 forwarding would be good for that, if the PC downstairs is a Linux PC. I'm not quite sure if SSH (much less with X forwarding) could even work on Windows.

I use Putty and XMing to forward X over SSH on Windows.

> **xhaggotx said:**
> Yes the downstairs pc is linux. Would that be fine to forward to a windows machine then?
If so, what would I have to install on both machines?

You don't need to "install" Putty, you can just download it [here]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") and run it.

There are a few X servers for Windows but I've been using [XMing]("http://www.straightrunning.com/XmingNotes/") which you can download and install. The public domain one is the free version. :-)

Note: XMing comes up a version of putty called portableputty.

---

### Post by xhaggotx on 2010-07-09
Ok thanks for the info.
Tomorrow I shall be trying to work all this out. 
Wish me luck!

---

### Post by xhaggotx on 2010-07-10
Ok so its not going as well as I can have hoped
Can someone walk me through the best way to do this please!?

---

### Post by CharlesA on 2010-07-10
What do you need help with?

If you are running Windows and Putty, make sure that XMing is running and then select SSH > X11 > Enable X11 Forwarding in Putty then create the connection. After you do that, you should be able to run a graphical app on your local machine.

---

### Post by xhaggotx on 2010-07-10
ok so I've now got the terminal through putty, what command do I use to launch a desktop?
I tried launching xterm but it says the display is not set

---

### Post by CharlesA on 2010-07-10
That I am not sure of. I usually just launch applications from the terminal when I need them.

What's the exact error message you are getting?

---

### Post by Darkness Des on 2010-07-10
I remember something about this, long ago when I was messing with SSH. I think you have to give it the command DISPLAY 0:0 or something around those lines.

---

