---
title: "still no firewall GUI???"
date: 2009-07-16
forum: General Help
---

### Post by browny_amiga on 2009-07-16
Hi

I have just setup ubuntu on my Netbook and have seen the progress of Ubuntu on and off. I is promising where it is going, yet, still, when I see some stuff, my hairs stand on end and it becomes clear why "Linux for Human beings" is yet far away from that slogan.

Example?

My netbook automatically received a firewall, I found that all ports are blocked from outside. It think this is a good thing. BUT:
Where is the possibility to configure it? Turn it off or open selected ports (ssh for example).

Where is the GUI for this so "uncomplicated firewall"????? I myself have no trouble going down into the command line, but how is a newbie going to cope?
Isn't "Linux for Human beings" supposed to preclude the command line, especially for dumb and trivial tasks like configuring a simple firewall?
I mean, it really does not make sense to use the CLI for that. Configure Iptables, yes. Scripting and automating, yes.
But simple configuration? When looking in the Ubuntu help, I find no mention of a GUI or how to install it. The repositories seem to not have it.
I am just wondering, since this is release 8.04 that I am talking about and it is pretty new, it seems to be that there are people at the wheel at Canonical that really love the CLI, which is fine if this would be Debian. I am a true Debian lover, since it gives you so much power. But Ubuntu should be for casual users too, making things AS SIMPLE AS POSSIBLE, and that is just not the CLI. An user will go look in Administration and Preferences for that firewall tool, which he will not find. 

It is probably the same people that still advocates getting down to the CLI even for grandma and grandpa, as well as joe mechanic, that surely doesn't like to memorize command line options of the ufw command. They are probably the same people that are responsible that the most terrible antiquated VI version is included in Ubuntu, STILL. Where use of the cursor keys in edit mode does not work, because when that tool was written, there were probably no cursor key, not invented yet ;-)

I am just asking all these questions, because I believe that I raise a valid point. 

Isn't Ubuntu supposed to be easy to use for beginners?

Markus

---

### Post by Sub101 on 2009-07-16
You can edit the firewall with a GUI program like Firestarter. 

Yeh you have to install it first, but 1 line on terminal and thats done, or you can use synaptic. So fairly simple.

---

### Post by michy99 on 2009-07-16
What's wrong with Firestarter?

Edit: Someone beat me to it!

---

### Post by t4thfavor on 2009-07-16
Plenty of firewall gui's for Ubuntu, it just doesn't ship with one (yet?). I think it should, but then again it may be just a PITA. 

On a side note:

Why does stock Ubuntu need any firewall (besides a blank iptables chain) when it has 0 open ports on plain install?

I never understood that rationale...

---

### Post by Mighty_Joe on 2009-07-16
```
sudo apt-get install gufw
```

---

### Post by CatKiller on 2009-07-16
> **browny_amiga said:**
>  Where is the GUI for this so "uncomplicated firewall"????? 

The firewall is iptables, included in the kernel. By default, all ports are open, actually, it's just that no services are listening on any ports.

The "uncomplicated firewall" that you mention would be ufw. The graphical equivalent would be the Graphical UFW, gufw.

If you've got a question that you'd like answered it's generally more productive to avoid using a hostile tone.

EDIT: Why would they remove vi? It's not like it's the only text editor that's included, and it's not like someone is holding a gun to your head to use it.

---

### Post by browny_amiga on 2009-07-16
It is not about that VI should be removed, no, I am talking about the ANCIENT version of VI, one that is so dumb that if you enter and press I for insert, pushing the cursor buttons will cause stuff like:
[D
[D
[D
but the cursor will not move downwards.

I guess what I mean is VIM (VI improved), which is still totally aweful, BUT has no shortcomings compared to plain old VI, so no reason not to chose that, especially for Ubuntu.

And no, Firestarter is no alternative. I know the tool and love it. BUT, we are talking about a very very simple Firewall GUI that is standard in Ubuntu. Of course the user can install any tool he wants. Question is, WHICH ONE? Must I remind you that Ubuntu has always chosen to install one or two tools in stead of the 15 that exist (like Debian does)? In Debian this is ok, because it is a professional oriented Distro, for people like me that want choice, but to a normal newbie user it is just confusing. 

What I am talking about is that Ubuntu should have a simple tool to switch on/off or  open a simple port or two on the firewall, which is active, as said, in 8.04, as standard install. So as it is active, if I want to access ssh on the machine, I want to open that port. How an average user (coming from Windows) is supposed to 
a) find out that the firewall is running
b) have any clue which tool to use to deactivate or open a port there
is beyond me.

He will just decide that Ubuntu has not managed, even in the almost newest version to have a rudimentary SIMPLE gui for firewall config install and accessible in the system menu, where it belongs.

And this critisizm (does not even have a firewall) we would have to swallow and accept as correct. Because if there is no way to deactivate a preset firewall intuitively, i.e. without buying a Ubuntu book and/or going to the command line, well....

If I can get GUFW, that is great, but why do I have to install it in the first place? Why isn't it included as standard?
Thing are moving too slow here, that is why I am so harsh. I care greatly about Linux and Ubuntu (and Debian) and want to move and better it. 

I applaud UFW, since it really is a simple and pragmatic little tool, switching off the firewall in my case was as simple as ufw deactivate, which the help file told me.
So why not just make the gui standard to it? Really simple and no work at all.

Markus

---

### Post by c0mput3r_n3rD on 2009-07-16
> **browny_amiga said:**
> It is not about that VI should be removed, no, I am talking about the ANCIENT version of VI, one that is so dumb that if you enter and press I for insert, pushing the cursor buttons will cause stuff like:
[D
[D
[D
but the cursor will not move downwards.

Yep, I had that same problem with the VI that came installed on my machine, and was very very upset because I learned on a CUI and VI was my text editor of choice.  A simple upgrade/re-installation of VI solved all my issues :D
.... And to make this post relevant to the thread.... I suggest Firestarter ;)

---

