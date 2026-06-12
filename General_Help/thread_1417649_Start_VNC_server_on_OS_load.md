---
title: "Start VNC server on OS load"
date: 2010-02-27
forum: General Help
---

### Post by e24ohm on 2010-02-27
Folks:
Not sure how to do this, but how do I get the vnc server to load automatically when the OS loads? Right now – I have to log into the system first, before I can vnc into the box; however, I want to be able to vnc into the machine without having to login locally at the system.

The goal is to build a simple web server, with no keyboard or mouse attached and place the box in the corner of my office.

---

### Post by hwttdz on 2010-02-28
I think the route would be to add it to the runlevel before a userlogin, perhaps the rc.local is the place it should go.  I'm not quite sure, but searching for runlevel, and startup applications should get you going the right way.  Just be careful that it starts up running under the user that you want it to (i.e. vncuser or root or billyjoe).

---

### Post by MJBoa on 2010-02-28
You would basically make a script called /etc/init.d/vncserver
write whatever you want run
make it executable and run this:

```
update-rc.d vncserver enable
```

What this does is add your script to a directory where it will be run on startup

Now, what you put in this script is another issue.
I personally like x11vnc as a vnc server because it's desktop independent.

To connect to X as root, you need a special file which is usually called Xauth. But the way this works seems to change with every god damn release of gnome. So I honestly am not sure anymore.

Check this out for more information about running x11vnc as root.
[http://www.karlrunge.com/x11vnc/faq.html#faq-xperms](http://www.karlrunge.com/x11vnc/faq.html#faq-xperms)

Even when I COULD run x11vnc as root and connect and see the login screen (in 9.04), GDM would always kill x11vnc and kick me back out after I logged in. There was apparently a KillInitClients option I could set to false but that never seemed to work and it looks like they've completely removed it anyway.

I'm gonna attempt tomorrow to make this work on my machine again, I recently installed 9.10.

---

### Post by krunge on 2010-02-28
It is possible to have x11vnc start at boot time by way of the display manager (e.g. GDM) Init/Default script.  More details at this link under the section "Continously":
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

BTW, starting with x11vnc version 0.9.9 (in some repos I think) x11vnc takes care to avoid being killed by GDM or any other display manager.  You don't even need to set KillInitClients=false (which is a good thing because that feature has been removed in recent GDM.)

---

### Post by MJBoa on 2010-02-28
Indeed, I just set it up myself.

I compiled x11vnc version 0.9.9 from source, which really isn't very difficult. ([http://www.karlrunge.com/x11vnc/#building](http://www.karlrunge.com/x11vnc/#building))

I did
```

nano /etc/gdm/Init/Default
```

and before the last line, "exit 0"

I added 

```
/usr/local/bin/x11vnc -auth guess -o /var/log/x11vnc.log -forever -bg
```

-auth guess tells x11vnc to find the xauthority cookie itself
-o /var/log/x11vnc.log tells it to send all output to /var/log/x11vnc.log
-forever keeps x11vnc alive connection after connection
-bg sends it to the background

This seems to work!

---

### Post by krunge on 2010-03-01
> **MJBoa said:**
> 
This seems to work!
That's great.

BTW, I believe you do not need the "-auth guess" option.  I say this because the nice thing about the /etc/gdm/Init/Default script is that GDM launches it with the correct DISPLAY and XAUTHORITY environment variables set and so no need to guess either one.

Why don't you try it without "-auth guess" and if it works for you, edit your previous post and remove it from the cmdline.  That way people reading this thread trying to solve the same problem won't think that option is required. Thanks.

---

### Post by e24ohm on 2010-03-01
thanks folks - i will try tomorrow at work to see if I can get my vnc deamon to load at start up.

---

### Post by e24ohm on 2010-03-03
I tried to login to my server again, but I still cannot VNC into the box until I locally login. Afterwards I am able to use the VNC client on another machine and log into the server remotely.

Do I need to load the VNC server daemon on boot?

---

### Post by asmoore82 on 2010-03-03
I did this exact same thing at work.
I had to see how a Fedora 12 box accomplished it first, then
I went back and perfected the method for Ubuntu.

The Fedora way uses the newly revamped "TigerVNC" software, which should be
coming to Ubuntu in the future, but for now...

This "perfect" method kills 2 bird with 1 stone.
1. You want the VNC enabled X session to load every time the box boots
2. You don't the X session attached to the physical console at all, for 2 reasons
2.1 Security, anyone who looks at the monitor on the box shouldn't be able to see your VNC session.
2.2 Graphics drivers, you don't want your VNC to fail because of problem with the VGA hardware
that you're not even using, be it the Video card or the Monitor.
There are intermittent issues with the desktop editions of Ubuntu
that prevent them from completing the boot process without a monitor
attached. This method will work around those as well...

[next post]

---

### Post by asmoore82 on 2010-03-03
**_[SIZE="2"]HOWTO: Perfect Headless Server Setup with Secure VNC and RDP.[/SIZE]_**

For this guide, we'll assume you are already comfortable with the text editor
of your choice and can edit and save system wide config files that require
root privilege without further instruction.

Also, We'll assume you are running the _Desktop_ Edition of Ubuntu _9.10 Karmic Koala_.
It should be easily adaptable to the Server Edition but I think it really needs to be Karmic or later.

Using the Desktop Edition makes it a little more difficult so we should cover all of the "Gotchas."

First of all, any server worth its salt has a static I.P. address and always brings up networking on boot.
In other words, we are about to go beyond the use case of NetworkManager,
so let's just turn it off! Edit "/etc/network/interfaces" to make it look like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.100.10
	netmask 255.255.255.0
	network 192.168.100.0
	broadcast 192.168.100.255
	gateway 192.168.100.1
```
^replacing all of the 192.168.*.* with suitable values for you network, of course.

Next edit "/etc/resolv.conf"
```
# /etc/resolv.conf
nameserver 192.168.100.1
nameserver 192.168.100.2
search example.com
```
^replacing with your network info as necessary

Starting with Karmic, certain lucky init scripts now live in "/etc/init/"
and are fully Upstart-able.
NetworkManager is one of these, so disabled it like so:
```
sudo mv /etc/init/network-manager.conf{,.disabled}
```

Now, Restart the machine and make sure networking is OK

Like the static IP, any good server also has SSH, this is important to us
because our VNC server will *only* accept local or SSH-tunnel connections, so
```
sudo apt-get install openssh-server
```

We need to turn off and disable gdm, so our VNC can be running on Display :0
Log in to the real console(Ctrl+Alt+F1) and do it Upstart style!
```
sudo stop gdm
sudo mv /etc/init/gdm.conf{,.disabled}
```

We need to install a standalone VNC server, tightvnc gave me trouble
by mangling remote keyboard input, so I'm using vnc4server:
```
sudo apt-get install vnc4server
```

We need to pick a user for autologin in VNC, for this, we'll assume it's the user "mark"

We need to set mark's VNC password, run `vnc4passwd` as mark

Now we will see the beauty in Upstart, we are going to write a 100% valid
initscript in less than 15 lines.
Create "/etc/init/vnc-mark.conf" like this:
```
# vnc-mark.conf

start on runlevel [2345]
stop on runlevel [016]

pre-start script
	su mark -c 'vnc4server :0 -geometry 1024x768 -localhost'
end script

post-stop script
	su mark -c 'vnc4server -kill :0'
end script

#End of File
```
^remember to replace "mark" with your username

Now we are ready to start the VNC service, Upstart style!
```
sudo start vnc-mark
```

That's it for the VNC portion, you can't stop here if you don't want RDP support.
RDP is "Remote Desktop Protocol" for [Gasp] Windows machines. Sometimes it's
convenient to be able to control your headless Linux box from a Windows PC without
having to install additional software in Windows, some people are touchy about that!
Life without Walls sure can make you paranoid! Cold and damp too I guess.

We're going to use a very narrow bit of the xrdp software's powers,
all we want it to do for us is be a translator for VNC and RDP.
So, install it and immediately stop it(not Upstart style :'[)
```
sudo apt-get install xrdp
sudo service xrdp stop
```

Edit/Demolish "/etc/xrdp/xrdp.ini" to this:
```
[globals]
bitmap_cache=yes
bitmap_compression=yes
port=3389
crypt_level=low
channel_code=1

[xrdp1]
name=mark@VNC
lib=libvnc.so
username=na
password=ask
ip=127.0.0.1
port=5900

[xrdp2]
name=disabled
#lib=libvnc.so
#ip=127.0.0.1
#port=5900
#username=na
#password=ask
#
[xrdp3]
name=disabled
#lib=libvnc.so
#ip=ask
#port=ask5900
#username=na
#password=ask
#
[xrdp4]
name=disabled
#lib=libvnc.so
#ip=ask
#port=-1
#username=ask
#password=ask
#
[xrdp5]
name=disabled
#lib=librdp.so
#ip=ask
#port=ask3389
#
[xrdp6]
name=disabled
#lib=libxup.so
#username=ask
#password=ask
#ip=127.0.0.1
#port=-1
```^again change "mark" to suit your needs, I was nice and used comments for Demolition.

Fire up xrdp again: ```
sudo service xrdp start
```

**_[SIZE="2"]That's all Folks![/SIZE]_**

Control your headless box from other Linux boxes with this:
```
vncviewer -via mark@192.168.100.10 localhost
```
^replace username@IP as needed
the `-via` option tells `vncviewer` to use the SSH tunnel
the "localhost" bit is tricky because you have to specify the
hostname from the point of view of the SSH tunnel :D

If you did the last bit you can also control from "Remote Desktop Viewer" on a PC.

---

### Post by t0lkman on 2010-04-15
Why do you use libvnc.so? instead libxup.so ?
I've noticed with libvnc.so it works slower, probbaly because it's kinda VNC over RDP

I tried to use libxup.so works well for me, except the keyboard mapping...
keyboard layout completely wrong with libxup.so

Evgeny.

---

### Post by HermanAB on 2010-04-15
Howdy,

Note that VNC is insecure and pretty much a guaranteed way to get your Ubuntu machine hacked.  These forums are full of tales of VNC woe - about one sucker per month.

VNC is supposed to be safe for use on a LAN, but due to some things it does with Plug and Play, it tends to open up an unsuspecting machine to the wild wild world if it is behind a garden variety router or firewall that supports PnP.

So, unless you are a masochist and actually want to get hacked and re-install all the machines on your LAN, please do consider removing VNC and using SSH instead.

This is why all the gray beards use SSH and not VNC...

---

### Post by asmoore82 on 2010-09-07
> **HermanAB said:**
> Howdy,

Note that VNC is insecure and pretty much a guaranteed way to get your Ubuntu machine hacked.  These forums are full of tales of VNC woe - about one sucker per month.

VNC is supposed to be safe for use on a LAN, but due to some things it does with Plug and Play, it tends to open up an unsuspecting machine to the wild wild world if it is behind a garden variety router or firewall that supports PnP.

So, unless you are a masochist and actually want to get hacked and re-install all the machines on your LAN, please do consider removing VNC and using SSH instead.

This is why all the gray beards use SSH and not VNC...

...Someone obviously didn't read my Howto...

SSH Tunneling!

---

### Post by lokutus25 on 2010-10-02
Thanks asmoore82 for the howto.
I followed the instruction but when i connect to my remote server using vncviewer -via XXX, I don't have a login or my user desktop. All I have is a grey window and a mouse pointer. I think I'm near the solution but can you point me in the right direction? :)

---

### Post by e24ohm on 2010-10-02
> **asmoore82 said:**
> ...Someone obviously didn't read my Howto...

SSH Tunneling!

Yeah, I saw a How-To in Linux Pro magazine, and it was really nice on how to tunnel vnc through SSH.

thanks

---

