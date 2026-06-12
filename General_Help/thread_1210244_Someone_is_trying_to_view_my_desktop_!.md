---
title: "Someone is trying to view my desktop !"
date: 2009-07-11
forum: General Help
---

### Post by chriskin on 2009-07-11
it actually happens to both my brother and my girlfriend , even though we don't share the same ip

what happens is that a window pops up saying that someone is trying to view my desktop, and it asks me to either refuse or accept it.

by checking the ip, it usually is from center or south america (by usually i mean all five times) , but from different countries each time.

is it a bug or is someone foolishly thinking that he can hack a computer by asking to remote control it?
in any case, how can i make those messages stop, allowing for example only IPs from Greece to ask for remote control?

---

### Post by 6205 on 2009-07-11
I have uninstalled all remote desktop related packages from my Jaunty... I think they are vino, vinagre, tsclient and other results from Synaptic when searching by keywords like 'vnc' Bud you must know what are you doing!

But propably is enough when you only disable those services from runnig in 'Startup applications' preferences..

---

### Post by chriskin on 2009-07-11
> **6205 said:**
> I have uninstalled all remote desktop related packages from my Jaunty... I think they are vino, vinagre, tsclient and other results from Synaptic when searching by keywords like 'vnc' Bud you must know what are you doing!

But propably is enough when you only disable those services from runnig in 'Startup applications' preferences..

i know how to remove them, but i need them 
i just want to block all non-greek ips if possible, so these messages will stop :) (or fix the bug in case i get notified that someone is trying to see my desktop while he doesn't know it)

---

### Post by The Cog on 2009-07-11
It's not a bug. You configure it to accept connections to the remote desktop, so it accepts connections. It's a good job you said to ask for permission first!

There are lots of compromised PCs out there that spend all day trying to connect to other peoples desktops. When they succeed, they automatically try to compromise that PC too, and so it goes on. You occasionally see posts in these forums where people complain about their PCs doing commands all on their own. It's normally trying to download and run windows executables.

I would suggest that you install a firewall and configure it to only allow connections to port 5900 from IP addresses that you know and trust. I think that gufw is the recommended firewall these days.

---

### Post by Johnny B on 2009-07-11
[block-whole-ip-range-with-iptables]("http://www.linuxquestions.org/questions/linux-security-4/block-whole-ip-range-with-iptables-469432/")

i used to get alot of ssh login attempts from Taiwan and china. i have since setup [denyhosts]("http://denyhosts.sourceforge.net/") to block any ip with 3 bad password attemps. however i don't think its compatible with remote desktop.

---

### Post by Liolikas on 2009-07-11
Configure you remonte desktop system to use not default ports, like 5901 not 5900. That will be most simple to do.

---

### Post by iponeverything on 2009-07-11
> **chriskin said:**
> it actually happens to both my brother and my girlfriend , even though we don't share the same ip

what happens is that a window pops up saying that someone is trying to view my desktop, and it asks me to either refuse or accept it.

by checking the ip, it usually is from center or south america (by usually i mean all five times) , but from different countries each time.

is it a bug or is someone foolishly thinking that he can hack a computer by asking to remote control it?
in any case, how can i make those messages stop, allowing for example only IPs from Greece to ask for remote control?

It's not a bug, that is what the program is for.

---

### Post by chriskin on 2009-07-11
i will try them, starting with the firewall way

thank you

---

### Post by Tony25 on 2009-07-11
> **The Cog said:**
> It's not a bug. You configure it to accept connections to the remote desktop, so it accepts connections. It's a good job you said to ask for permission first!

There are lots of compromised PCs out there that spend all day trying to connect to other peoples desktops. When they succeed, they automatically try to compromise that PC too, and so it goes on. You occasionally see posts in these forums where people complain about their PCs doing commands all on their own. It's normally trying to download and run windows executables.

I would suggest that you install a firewall and configure it to only allow connections to port 5900 from IP addresses that you know and trust. I think that gufw is the recommended firewall these days.

I agee.

Anyway try to install firestarter firewall and leave open only thoose ports you need.

---

### Post by The Cog on 2009-07-11
> **Liolikas said:**
> Configure you remonte desktop system to use not default ports, like 5901 not 5900. That will be most simple to do.

Very good ideea, but how? It doesn't seem possible in System->Preferences->Remote Desktop, and I couldn't see anything for vino in /etc/init.d or /etc/defaults.

---

### Post by 6205 on 2009-07-12
Maybe you could instal Gufw - it's graphical interface to ubuntu's default firewall 'ufw' which disabled by default..
[http://www.getdeb.net/app/gufw](http://www.getdeb.net/app/gufw)

After that, when you enable firewall and block all incomming connections you could propably open some specific port of your choice for VNC. But don't ask me how :/

---

