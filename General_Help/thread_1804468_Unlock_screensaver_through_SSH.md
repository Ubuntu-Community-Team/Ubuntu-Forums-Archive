---
title: "Unlock screensaver through SSH"
date: 2011-07-14
forum: General Help
---

### Post by Teh_Messiah on 2011-07-14
Hi I have an Xubuntu 10.10 File server / Media centre which I have set up to automatically lock the screen at 1am so the teenagers dont stay up all night watching movie and then being tired for school.

My problem is I dont know how to automatically unlock it or how to unlock it through SSH.
Usually I just manually unlock it every morning as I walk out the door but sometimes I forget and then can't unlock it from home :(
Kids come home from school while I'm at work and then cant watch movies or shows.

[LIST=1]
[*]How do I get it to automatically unlock the screensaver / screen lock?

[*]How do I unlock it through SSH without using VNC?

[*]BTW I cant get VNC working anymore since I upgraded to 10.10 with a fresh install either. how do I fix that?
[/LIST]

---

### Post by Toz on 2011-07-15
> **Teh_Messiah said:**
> 
How do I get it to automatically unlock the screensaver / screen lock?

How do I unlock it through SSH without using VNC?
Although you can lock the screen remotely through ssh, I don't think you can unlock it remotely, because the password needs to be entered.

> BTW I cant get VNC working anymore since I upgraded to 10.10 with a fresh install either. how do I fix that?
[/LIST]
There appears to be some sort of bug in recent releases of vncserver in that it listens to connections on both ipv4 and ipv6 protocols, but only connects on ipv6. You can either:
[LIST=1]
[*]Connect via ipv6
[*]Disable ipv6 on the computer serving the connection (forcing it to use only ipv4)
[*]Use another product like nxserver
[/LIST]

---

### Post by Teh_Messiah on 2011-07-16
Thank you :)
Shame you cant do it through SSH.
It's a pain having to setup remote desktop through a secure ssh tunnel.
I can putty in from work in seconds.
But remote desktop is slower and laggy :(
VNC used to have the terminal setup which I was familiar with configuring.
Now it uses a GUI (shocking :P) and I'm confused.
I thought I had it set up but then it never worked since 10.10 :(
I'll check out nxserver if no one comes up with an easier solution, besides sending the  kids away ;)

---

### Post by Teh_Messiah on 2011-11-17
Can you please help me with setting up the config for NXServer so I can use it?

---

### Post by Toz on 2011-11-17
> **Teh_Messiah said:**
> Can you please help me with setting up the config for NXServer so I can use it?

I don't think FreeNX is being actively developed anymore. Have a look at; [http://mlepicki.com/?p=10]("http://mlepicki.com/?p=10") for information on getting x11vnc to work. It worked for me when I tested it.

---

