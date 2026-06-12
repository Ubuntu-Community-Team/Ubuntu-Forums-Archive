---
title: "How to log into an Ubuntu PC over LAN?"
date: 2010-02-05
forum: General Help
---

### Post by mahela007 on 2010-02-05
I've been reading up about Ubuntu and Linux. I'm impressed / interested in this whole 'multiuser OS' thing and X sever which is 'network transparent'. So, I was wandering if there was some way to log into a computer running ubuntu using another PC running Ubuntu.. The two PCs are linked via a simple LAN network with a router. I haven't done any configuring of things like firewalls in Ubuntu. At the moment, both PCs run more or less out-of-the-box Ubuntus.

---

### Post by CharlesA on 2010-02-05
SSH or VNC. If I needed a GUI, I'd tunnel VNC over SSH myself.

---

### Post by mahela007 on 2010-02-05
> **CharlesA said:**
> SSH or VNC. If I needed a GUI, I'd tunnel VNC over SSH myself.
Umm... I think I'll need a few noob friendly instructions...

---

### Post by sanderj on 2010-02-05
See instruction for Vinagre (VNC on Gnome) here: [https://help.ubuntu.com/community/Vinagre](https://help.ubuntu.com/community/Vinagre)

---

### Post by mahela007 on 2010-02-05
Can't Xwindows do this on it's own? I though that was the idea behind the Xserver and X clients..

---

### Post by sanderj on 2010-02-05
> **mahela007 said:**
> Can't Xwindows do this on it's own? I though that was the idea behind the Xserver and X clients..

Yes, you can: "xterm" is your friend.

Start by using 

```
xterm -display localhost:0.0

```

If I remember correctly, you have to 'ssh' to the other machine, and then 'xterm' back to your originating machine.

Some googleing on Ubuntu, SSH and Xterm will certainly help you.

---

### Post by mahela007 on 2010-02-05
Hmm... I'll try to do that and post back.
In the mean time, i'd really appreciate a link to a detailed how to.. I've been googling but haven't found any good sites.

---

### Post by Grenage on 2010-02-05
I'd use *NX*, it's fast and secure.  Plenty of guides out there for that.

---

### Post by sanderj on 2010-02-05
> **mahela007 said:**
> Hmm... I'll try to do that and post back.
In the mean time, i'd really appreciate a link to a detailed how to.. I've been googling but haven't found any good sites.

Probably because it's not used very much; other methods (Vinagre/VNC, and maybe NX) are more user friendly.

---

### Post by Zack McCool on 2010-02-05
I'd highly recommend using NX.  It is a terminal server type of environment, designed to provide independent graphical login sessions to multiple users.  It is quite efficient at it's task.

---

### Post by stinkeye on 2010-02-05
> **mahela007 said:**
> Hmm... I'll try to do that and post back.
In the mean time, i'd really appreciate a link to a detailed how to.. I've been googling but haven't found any good sites.

[**_[COLOR="DarkRed"]Connect to a remote Linux desktop with x11vnc and Gtk VNC[/COLOR]_**]("http://www.ghacks.net/2010/01/24/connect-to-a-remote-linux-desktop-with-x11vnc-and-gtk-vnc/#more-22555")

---

### Post by mahela007 on 2010-02-05
> **sanderj said:**
> Probably because it's not used very much; other methods (Vinagre/VNC, and maybe NX) are more user friendly.

Vinagre (the default out of the box one in Ubuntu) seems to provide remote desktop functionality. I was able to set that up after a little fiddling. However, what I want is to be able to log in as *another user.* For examples, let's say PC1 has two users called A and B. While A is working on PC1 , I want to be able to log into B's account using another computer.

EDIT
> **Zack McCool said:**
> I'd highly recommend using NX. It is a terminal server type of environment, designed to provide independent graphical login sessions to multiple users. It is quite efficient at it's task.
I'll check out NX..  Is it able to do what I want?
PS: I'm not a professional or anything.. just a linux fan with too much free time.

---

### Post by Grenage on 2010-02-05
> I'll check out NX.. Is it able to do what I want?

Yes, it's a fast and secure way to remote desktop.

---

### Post by mahela007 on 2010-02-05
Now I'm getting curious.. ;-)
If X is based on a client - server model, then why should the user have to install other program in order to use X window system from another PC? I'm getting a bit confused... Could someone explain why this is?

---

### Post by Grenage on 2010-02-05
We could bat questions and answers all day, or you could read the information on the [website]("http://nomachine.com"). :)

---

### Post by mahela007 on 2010-02-05
lol.. yes. I think I  bit off more than I could chew. I'll read that and post back.

---

### Post by mahela007 on 2010-02-05
Ok.. i read some of the documentation at the website you gave. So my question boils down to this. The X windowing system was designed to work 'network transparently'. So can it or can it not send it's messages (communications between the X server and X client)over the network by itself without the use of additional software?

---

### Post by ushills on 2010-02-05
have a look at this 

[http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu](http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu)

you should not need any additonal software.

---

### Post by Grenage on 2010-02-05
> Ok.. i read some of the documentation at the website you gave. So my question boils down to this. The X windowing system was designed to work 'network transparently'. So can it or can it not send it's messages (communications between the X server and X client)over the network by itself without the use of additional software?

NX has a client and a server.  You can pull GUI applications across the network using X transparently:

```
ssh -X -C user@machine gedit
```

---

### Post by mahela007 on 2010-02-05
Could you please  explain that command?

---

### Post by mahela007 on 2010-02-05
> **ushills said:**
> have a look at this 

[http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu](http://www.zolved.com/synapse/view_content/28158/Remote_Login_via_XDMCP_on_Ubuntu)

you should not need any additonal software.
Yes.. that's more like what I meant. Does this use the X systems capabilities?

---

### Post by Grenage on 2010-02-05
> **mahela007 said:**
> Could you please  explain that command?

That command runs gedit on the remote machine, and tunnels the graphical output to the local machine.

---

### Post by ratcheer on 2010-02-05
Install **putty** on Windows. It will make ssh'ing to your Linux host a breeze. While you're at it, if you want to transfer files to/from Linux on your Win host, also install **WinSCP**.

Tim

---

### Post by mahela007 on 2010-02-05
> **Grenage said:**
> That command runs gedit on the remote machine, and tunnels the graphical output to the local machine.
what does 'tunnel' mean? (yes .. another question ;-) )

---

### Post by Grenage on 2010-02-05
It's basically taking something and pushing it through a 'tunnel' (in this case SSH) to another system.

See [here]("http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html").

---

### Post by mahela007 on 2010-02-05
Thanks a lot for the link. By the way, before I start reading it... can you give my an example of usage of the previous command you gave me? I tried it on one of my two PCs. I replced username@machine with my own UN and machine. However, it didn't seem to work. It said ''Could not resolve hostname '

---

### Post by Grenage on 2010-02-05
If you can't resolve hostnames, you can use an IP address:

```
user@192.168.10.54
```

---

### Post by mahela007 on 2010-02-05
> **Grenage said:**
> If you can't resolve hostnames, you can use an IP address:

```
user@192.168.10.54
```
Well.. thanks for all your help. I'll get back tomorrow after reading you link.

---

### Post by mahela007 on 2010-02-05
Um... I seems I've made a mistake.:sad: What I actually wanted was to be able to log into a virtual terminal using another PC. I've somehow managed to confuse this up with X server.:confused: X doesn't necessarily run on a virtual terminal in Ubuntu.... I'm gonna mark this thread as solved and hopefull once I figure out exactly what I want I'll post another one. That's not to say this has been a complete waste of time. I did manage to learn a bit about X and ssh.. Thanks for all your help everyone..

---

### Post by sanderj on 2010-02-05
> **mahela007 said:**
> Could you please  explain that command?

This starts to look like a session with ELIZA (see [http://en.wikipedia.org/wiki/ELIZA](http://en.wikipedia.org/wiki/ELIZA))

Or start an interactive session with Eliza: [http://www.manifestation.com/neurotoys/eliza.php3](http://www.manifestation.com/neurotoys/eliza.php3)

;)

---

