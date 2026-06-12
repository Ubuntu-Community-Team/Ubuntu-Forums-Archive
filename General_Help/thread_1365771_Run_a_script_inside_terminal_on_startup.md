---
title: "Run a script inside terminal on startup"
date: 2009-12-27
forum: General Help
---

### Post by TiuTalk on 2009-12-27
Hi there!

I need to open the terminal and run a executable .sh script on my startup...

I just started the script on background, but I need the terminal window so I can see the log thing..

How can I do that?

Ps.: Ubuntu 9.10 - Karmic

---

### Post by lswb on 2009-12-27
We need to know more about the script, what it does, and what resources it needs to correctly answer your question. Are you referring to your user session startup under a DE like gnome or kde, or do you mean system startup at boot?

---

### Post by pastalavista on 2009-12-27
I'm no expert, but if I was doing it I'd use the [System--> Preferrences--> Startup Applications] tool and Add "gnome-terminal <script here>".

---

### Post by bodhi.zazen on 2009-12-27
> **pastalavista said:**
> I'm no expert, but if I was doing it I'd use the [System--> Preferrences--> Startup Applications] tool and Add "gnome-terminal <script here>".

Add in screen so you can detach from the terminal session if you wish =)

---

### Post by TiuTalk on 2009-12-27
> **pastalavista said:**
> I'm no expert, but if I was doing it I'd use the [System--> Preferrences--> Startup Applications] tool and Add "gnome-terminal <script here>".

That's what I need!

I mus use:
**gnome-terminal ./home/zzz/zzz.sh**

Or:
**gnome-terminal /home/zzz/zzz.sh**
(without the dot)

?

Obs.: zzz is my user :)

---

### Post by apmcd47 on 2009-12-27
There should be a startup folder in your $HOME/.kde or $HOME/.gnome directory tree, into which you put an executable file containing one of the following:

KDE:```
konsole --noclose -e **scriptname** *arguments*
```
Gnome:```
gnome-terminal -x **scriptname** *arguments*;read x
```

The read x bit is required for the gnome-terminal because I could not find an option like the --noclose in konsole.

Andrew

---

### Post by TiuTalk on 2009-12-27
Yeah... I got it:

**gnome-terminal -x scriptname**

It's done! :)

Thanks everybody!

---

### Post by efflandt on 2009-12-27
Why not simply log (append) all output to a log file:

**/bin/date >> /home/zzz/zzz.log && /home/zzz/zzz.sh &>> /home/zzz/zzz.log**

---

