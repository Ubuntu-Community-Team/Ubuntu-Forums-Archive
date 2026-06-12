---
title: "Newbie with a few questions. Using 12.04 Desktop as a &quot;personal&quot; home server"
date: 2012-08-19
forum: General Help
---

### Post by Aerbax on 2012-08-19
**Disclaimer: **
I have played around with Ubuntu Desktop in the past, but am still very unfamiliar with the whole Linux scene. So with that out of the way... :redface:

**A tidbit of background of my situation:**
I recently inherited an older PC that I have decided to use as a home server. Up until today I was using Windows XP Home on it for a simple Teamspeak & Minecraft server. I have no monitor, and prefer to just have the case sitting here and connect to it via remote desktop or VNC (was using UltraVNC in XP). I plan on adding a bit more functionality to the server which XP Home just can't provide. I have installed 12.04 desktop (I'm not comfortable enough with linux to try without a GUI) today and managed to get the teamspeak and no-ip DUC working thus far.

**On to the questions:**
[LIST=1]
[*]During one of the tutorials to get teamspeak running on startup, I created a new user just for teamspeak. This may sound silly, but is there a way to do something similar to connect to a google talk account without logging in or entering a password? (Mainly used to see if the server is online via my desktop or other devices at a quick glance)

[*]Do I need to be/should I be using another user for my no-ip DUC service? Will This even work the way I have it installed/configured without logging on? (see tutorial I used below)

[*]I had another question but seems to have slipped my mind while trying to word this post.
[/LIST]

Here are the two tutorials I followed:
[no-ip tutorial]("http://ubuntu-for-humans.blogspot.com/2010/02/install-no-ip-client-from-source-on.html")
[TS3 tutorial]("http://robert.penz.name/296/howto-install-teamspeak-3-server-on-ubuntu-10-04-lucid/")

Thanks muchly in advance for any help!

---

### Post by cariboo on 2012-08-19
If you are running an older system, running a full gui desktop, especially Unity, may be to resource hungry to allow for proper game play. I'd suggest using the server version and install webmin:

[http://webmin.com](http://webmin.com)

To administer it remotely. If I remember there are modules to set up teamspeak and ip aliasing service.

---

### Post by Aerbax on 2012-08-19
Thanks muchly, I've bookmarked it for the future. Haven't been so much into minecraft as of late, so not too worried about that. This is turning into more of a getting my feet wet and learn some linux project. I'm a bit more comfortable learning with a gui behind me (sigh windows), and being able to remote in and "play" with ubuntu without a dual boot is a decent place for me to start.

Is there a way to get Pidgin or Empathy to start with the system and not require any user logins? It is a throw away google talk account/password so security isn't really a concern. Sending and receiving messages also isn't a concern. Would really like a contact on my messenger list on all my devices to see if the server is running.

---

### Post by mastablasta on 2012-08-20
you really didn't check the link did you?
you said the server has no monitor, yet you insist on having a desktop on it. why? 
 
as suggested install server and webmin (check their demo) or similar. then you can access the server from any computer in the network using a broswer. webmin provides you with a gui to administer the server.
 
there are also distributions that provide GUI server interface out of the box such as zentyal OS (there is a community -"testing edition" that is free) or Red hat based Clear OS: [http://distrowatch.com/table.php?distribution=clearos](http://distrowatch.com/table.php?distribution=clearos)
 
 
another nice and easy option for server is TurnKey Linux
 
if you need to only see if server is online you can just ping it. if you want it faster you can create a batch file (script) for ping if computers are windows maschines.
 
and if you really want to learn then do some exploring and reading rathern than making obscure work arrounds to your problem.
[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)
or PDF: [https://help.ubuntu.com/12.04/serverguide/serverguide.pdf](https://help.ubuntu.com/12.04/serverguide/serverguide.pdf)
 
good luck.
 
and as mentioned above. server willl use much much less system resouces than desktop environment (especially unity)

---

### Post by Aerbax on 2012-08-20
> **mastablasta said:**
> you really didn't check the link did you?
you said the server has no monitor, yet you insist on having a desktop on it. why?

I understand what webmin does. But webmin won't allow me to learn my way around ubuntu while getting my feet wet with linux. Being able to remote in to this machine allows me to do that. Being able to fall back onto the GUI when I didn't completely understand what I was doing in the terminal has already helped. 

Yes I know there are other options to "play" with ubuntu before I take the time to dual boot or even migrate on my other machine(s), but for now I'm using this spare machine while getting some simple personal server functionality with it.
 
> **mastablasta said:**
> if you need to only see if server is online you can just ping it. if you want it faster you can create a batch file (script) for ping if computers are windows maschines. 

It's more of a want than a need. Messengers are always in use on my PCs and mobile phone. I just thought it would be fun to have.
 
> **mastablasta said:**
> if you really want to learn then do some exploring and reading rathern than making obscure work arrounds to your problem.

The gtalk "problem" may be obscure, sure. But it would be handy, and again, "fun" for me to have. I never said this was a be all end all to learn everything linux/ubuntu. A simple response to my question(s) with a shove in the right direction if it's possible, would be great.

Cariboo had already mentioned the potential resource issue and solution. While I appreciate your suggestions for other software to be using, I won't be swapping away from ubuntu desktop on the machine just yet for the aforementioned reasons.

I guess at this point what I'm mainly concerned about is the noip service running properly.

---

