---
title: "I can't get VNC via SSH to work"
date: 2009-09-17
forum: General Help
---

### Post by clevertomato on 2009-09-17
I'll just start this out with an apology and request for forgiveness. I apologize for whining and request your forgiveness for the same., <begin-whine> e v e r y   l i t t l e   t h i n g   requires so much research and command lining to get to work. I'm amazed when I still come across discussions where Linux users are dumbfounded as to why Windows users don't flock to Linux in droves. I've had years of experience with computers--yes almost entirely Microsoft OSes along with OS/2--and I find myself having the urge that I get every now and then to become a Linux user. But, honestly, in Windows I would have already had this done hours ago and using it for WHAT I NEED TO DO simply by pointing and clicking. <end-whine src=mostly>

I've googled. I've read forums. I've read tutorials. I want to remotely control an Ubuntu 9.04 desktop... from a local network AND from the internet. It should be MY choice right? So why did the option to access remote desktop from internet exist in 8 but get removed in 9? It's beyond me. I thought Linux was about choice. Now I have to spend oodles of time wading through posts about the topic, many several years old, trying to hack at the command line and edit files. (sorry, my frustration got the better of me again.) Well, I threw VNC via SSH over the internet onto the back burner. I started simple, trying to get VNC without SSH to work on my LAN from XP to Ubuntu Jaunty. Finally I got it to let me login, but then I only see a low res grey window with NOTHING in it. I tried putting "gnome-session &" in the you-know-what file. I tried commenting out the twm at the end. Nothing. Obviously if I can't even make plain VNC work on my LAN without SSH, I'm nowhere close to doing it successfully over the internet via SSH. I installed vnc4server and openssh on Ubuntu. I've tried both VNCviewer and tightvncviewer on the XP remote machine. No dice.

I'm probably going to piss some of you off with my frustration, and I'm sorry. It's nothing personal. It's just that I WANT to be a Linux fan, but this is ridiculous. Everything is so painful to figure out. Can anyone provide a straightforward answer as to how I can securely gain remote access to an Ubuntu Jaunty machine? I can follow directions if they are up-to-date, detailed, and accurate (yes, even if they involve CLI).

Shawn

P.S. The current reason I need to do this is to take control of my nephew's fresh Jaunty installation to try to get Flash working in his Firefox. I'm trying to turn him into a Linux fan, too, but it's a little tough when he can't get anything to work and his uncle can't either. Ugh. I'm so frustrated. I'm going to step away from the PC now, waiting to see if I receive hate or help from the post (or maybe just get ignored).

---

### Post by clevertomato on 2009-09-18
Got it working on my own. I was reading so many posts and tutorials that my commented vs uncommented lines in start file were apparently messed up. I needed to uncomment the unset line, leave the line after it (against the instructions in the file, I might add), add "exec gnome-session &", and comment out the "twm &". Again, reading a half dozen different posts about it, each with a small piece of the puzzle, and the misleading instructions in the commented file resulted in my not having all the lines commented and uncommented correctly.

It's working now, VNC through SSH tunnel over the internet. Dang. I still say it shouldn't be this difficult. I can't imagine why the GUI for this was removed going from Ubuntu 8 to 9 and why config files for everything always have to be messed with manually. What is a GUI for if you always have to be dropping into CLI to "really" get things done?

---

### Post by andr983 on 2009-09-19
I'm glad for you that you were able to solve your problem. But it would be more interesting for the rest of the Ubuntu community to get to know HOW you did it.
I'm also looking for something like that, so please describe the steps you've done.

Thanks!

PS: one day you'll be able to manage any Linux distro better then any MS-OS!

---

### Post by clevertomato on 2009-10-05
I kind of assumed that I my experiences (at least so far) with Linux/Ubuntu couldn't possibly help anyone else. I'd be glad to post how I got it working...

I'm not sure whether it matters if the built-in Ubuntu remote desktop settings matter for this (System/Preferences/Remote Desktop), but I enabled access and control of the desktop just to make sure.

Some of following was found at [http://imthi.com/blog/linux/ubuntu-904-remote-desktop-using-vncserver-without-monitor.php](http://imthi.com/blog/linux/ubuntu-904-remote-desktop-using-vncserver-without-monitor.php)

Install secure shell ssh.

```
$sudo aptitude install ssh
```Install vncserver.

```
$sudo aptitude install vnc4server
```After it is installed you should be logged as normal user and not root.

```
$vncserver :1 -geometry 1024x768 -depth 16
```Once you issue the above command it will prompt for password. This password will be used for connecting to the server. Once it is complete we can change the setting for the server. Before we do that we have to kill the server.

```
$vncserver -kill :1
```The configuration is kept in the file /home/userxx/.vnc/xstartup I edited this file so that I can start the server with gnome. My file is below with the following changes:
1. I uncommented the "unset SESSION_MANAGER" line
2. I added "exec gnome-session &"
3. I commented the "twm &" line at the end

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
exec gnome-session &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
# I commented out following line when I added the "exec gnome-session &" above
# twm &

```Now everything is done. All you have to do is to restart the system which is helpful for the setting to work properly. Once you have restarted please start the vnc server.

```
$vncserver
```If you want to use this on a machine that doesn't have a monitor and don't want it to bother starting a gnome session at every boot (why should it if you don't have a monitor hooked up to it?), you can (optionally) disable GDM in the services list.

So, to securely take control of the desktop via the internet, find out what the public IP is of the host machine that you're taking control of. Go into the router settings and forward port 22 to the private IP of that machine. So if you the private IP of the machine you want to control is 192.168.1.10, set your router to forward incoming traffic on port 22 (the ssh port) to port 22 on 192.168.1.10.

Now, get one of the available vncviewers available for your remote PC's OS and get Putty SSH (if you're using Windows). Open Putty, enter a new connection. In the IP box, put the public IP of the machine you want to control. Go to "Tunnels" and add one. In "source port," enter 59xx (where xx is the vnc display the server opens... more on this later. I don't currently know how to predict or control this) and in "destination" enter the PRIVATE IP address of the machine being controlled followed by a colon and the same port (i.e. 192.168.1.10:59xx). Make sure setting on this Putty SSH page is "local" not "remote." Click "Add." If you want this saved with this profile in Putty (you probably do), then go back to Session and click "save."

Now, connect via SSH with Putty. Login, then type:

```
$vnc4server
```to start the server if it's not already running. Pay attention to what it says afterward. It tells you which display number it opens (i.e. my-ubuntu:1). Leave this SSH session active.

Go to the vncviewer software on the remote machine and start it. For server, enter 127.0.0.1 or "localhost" followed by colon and the display number (i.e. 127.0.0.1:1). Hit connect. You'll be prompted for the password you set when you setup the vnc4server earlier. After you enter it, you'll see the desktop.

---

### Post by XCan on 2009-10-06
Actually, the default vncserver (Vino) worked just great for me out of the box in Jaunty by simply enabling it. After that, I just blocked it on the firewall to make it only accessible through SSH tunnel. 

But I agree with the OP, usually there are so many things to do it, a user can easily be confused. Just try and figure out how to enable VNCserver at login with Vino for example. There is a very easy way to do it, yet the net is flooded with posts on installing alternative vncservers (which of course have their advantages).

---

### Post by andr983 on 2009-10-06
@shawnboy: thanks for your explanation.
In the meantime I was also able to find out how to get a desktop sharing over the Internet via a SSH tunnel, as shown in the following picture.
[IMG]http://www.e-cattivi.com/blog/wp-content/uploads/2009/09/connessione2.png[/IMG]
**Situation**. Alice want to help Bob.
**Software**. With respect to a default installation of Ubuntu, you need to install openssh-server just on Bob's pc, using Synaptic or the command
```
sudo apt-get install openssh-server
```
**Preliminary setup**. On Bob's PC, connect to the router and make a port forwarding of the port 22 (for SSH). Enable remote connection under System/Preferences/Remote Desktop and give Alice the following data:
1. username and password of any Ubuntu account on Bob's PC
2. password of the remote connection
3. public IP address of Bob's connection
**Connection!** Open the terminal, type:
```
ssh -l usernameUbuntu -L 50000:localhost:5900 10.10.10.10
```
changing usernameUbuntu with the point 1 of the list and the ip address with the point 3. The password you've been asked for is the one of the Ubuntu account. Then open the remote desktop viewer and search for ```
localhost:50000
```. You'll find the desired PC, just connect and give the remote connection password.
Type exit to close the connection.
:popcorn:

---

