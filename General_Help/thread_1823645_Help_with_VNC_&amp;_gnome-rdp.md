---
title: "Help with VNC &amp; gnome-rdp"
date: 2011-08-12
forum: General Help
---

### Post by Ant01 on 2011-08-12
Please can someone help me. I am running a ubuntu desktop machine as a server and use VNC from my windows machine to login via a LAN to the ubuntu machine.

The login session is very sluggish and frustrating. I installed gnome-rdp to see if it would be better but I don't know how it works or what to do and if there is something else I can do to improve the performance. I have 3 gig of ram and the server is a dual celeron machine

Thanks

---

### Post by Kira_Belka on 2011-08-12
gnome rdp is a tool that can connect from ubuntu machine to any vnc and rdp host (linux /win not important).. you can use not only vnc.. you can use tightvnc also..mmm.. other way is X forwarding + ssh -X or Xming ( on windows host)

---

### Post by doas777 on 2011-08-12
well, my advice is to use FreeNX instead of VNC (Vino/Vinagre), but if you are interested in sticking with VNC, then experiment with other vnc viewers and settings (the encoding setting is key.) Vinagre has great integration into ubuntu and has a nice ui, but isn't the fastest I have found. I've not used the gnome-rdp client for vnc before, but last time I looked into it, x4vncviewer was the best one for remoting into my 1080p media box (less laggy, and decent scroll bars since host res is so high), whereas vinagre was best for my server console. 

if you do look into FreeNX, there are clients for all major OSes, and the install is a snap. here are some instructions: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)
since freenx is ssh based, you can even extend it to the wan, if you take some solid precations with your ssh config (non-default port, keys, fail2ban/denyhosts, etc).

---

### Post by Ant01 on 2011-08-12
I've installed tightvnc but its still the same.

I'm trying to setup FreeNX but excuse my ignorance as I'm still new to this. I want to connect my windows machine to the ubuntu machine. I've installed lamp on the ubuntu machine and the help file says i need to install FreeNX server. Do I need to or can I set up the lamp server.

Once the server is setup how do I connect from my Windows PC. Also not sure about SSH

---

### Post by doas777 on 2011-08-12
to install freenx, you only need ssh and a desktop environment (no need for full lamp stack).

Edit: 
Wow, FreeNX install has gotten a lot more complicated in this last month. 

what version of ubuntu do you run? I can whip up a quicke install script if you like.

---

### Post by Ant01 on 2011-08-12
I;ve already installed LAMP as I am attempting to host a webserver on the ubuntu desktop but at this stage still learning my way around. Please help with SSH and once setup how do I access from my windows machine

---

### Post by doas777 on 2011-08-12
to install ssh server on ubuntu, all you need to do is:
```
sudo apt-get install openssh-server
```


On the **windows** machine, download [PuTTY]("http://the.earth.li/%7Esgtatham/putty/latest/x86/putty.exe"), and run it either with a doubleclick or from a command terminal/powershell. 
here is the cli:
```

putty <hostname or IP>

```

putty is great for command line access to your server, but for when you need to work with files or transfer them over ssh, then [WinSCP]("http://winscp.net/download/winscp434setup.exe") is a good tool. 



If you wish to connect to your server from an **ubuntu** machine, you can invoke the ssh client with:
```
ssh <hostname or ip>
```

and if you want filetransfer over ssh, just open nautilus (the gnome window manager), and hit Ctrl + L so you can type an address in. then enter:
```
ssh://hostnameOrIP
``` to open a window to the servers / partition.

---

### Post by Ant01 on 2011-08-12
Thanks for all the help, managed to get access via putty but it takes me to bcommand line, is there a way I can bring up the GUI

---

### Post by doas777 on 2011-08-12
> **Ant01 said:**
> Thanks for all the help, managed to get access via putty but it takes me to bcommand line, is there a way I can bring up the GUI
yes and no. the GUI is where FreeNX comes in. Freenx connects to your server via ssh and then presents the desktop to you. 

instead of using FreeNX, you can look into X-Forwarding applications over ssh (many people swear by it), but i've generally found that to be a bit of a pain. check [this link]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding") under "Forward Gui Programs"

 otherwise let me know what version of ubuntu you are running (lucid/mavrick/natty/oneric) and I'll give you some more specific instructions on FreeNX install.

---

### Post by Ant01 on 2011-08-12
Shooo let me try FreeNX setup. I am running Ubuntu 11.04 I've checked [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) should I follow this or is there a easier way. Once I've loaded FreeNX how does it work then.

I think the Nautilus GUI has something to do with the slow connection because it wasn't this slow with 10.04

---

### Post by doas777 on 2011-08-12
yeah, unity may account for it, as it is all 3da. 

as for an install script, this is just the commands from the support doc for your build. each line is its own command.
```

sudo add-apt-repository ppa:freenx-team
sudo apt-get install python-software-properties
sudo sed -i 's/natty/lucid/g' /etc/apt/sources.list.d/freenx-team-ppa-natty.list
sudo apt-get update && sudo apt-get install freenx
wget https://bugs.launchpad.net/freenx-server/+bug/576359/+attachment/1378450/+files/nxsetup.tar.gz
tar -xvf nxsetup.tar.gz
sudo cp nxsetup /usr/lib/nx/nxsetup
sudo /usr/lib/nx/nxsetup --install
rm nxsetup

```

---

### Post by Ant01 on 2011-08-13
I think i've installed FreeNX what now?
How do I connect from the windows pc to the ubuntu desktop using GUI

---

### Post by doas777 on 2011-08-13
ok!

now all you haave to do is go to [http://www.nomachine.com/](http://www.nomachine.com/), and download the client that is right for your windows system. install it, and launch teh NX client. supply the name or ip of your nx server and connect.

---

### Post by Ant01 on 2011-08-14
> **doas777 said:**
> ok!

now all you haave to do is go to [http://www.nomachine.com/](http://www.nomachine.com/), and download the client that is right for your windows system. install it, and launch teh NX client. supply the name or ip of your nx server and connect.

I've download the nx client but there still seems to be a problem. I get error Authentication failed for use ....

I think its something I have to do on the server side, maybe the nx server is not running, please advise

---

