---
title: "Do I Need A Firewall For Ubuntu"
date: 2010-12-26
forum: General Help
---

### Post by Mindswap1 on 2010-12-26
Hey Guys! I was wondering what does a firewall do and do I need one? And How can I get one? Thanks In advance I'm a noob at this stuff, and you guys always manage to help :).

---

### Post by TeoBigusGeekus on 2010-12-26
Just [one]("http://ubuntuforums.org/showthread.php?t=1652180") of the countless threads about this.

---

### Post by kgarbutt on 2010-12-26
Ubunutu comes with a command line firewall called ufw. There is a graphical front end for it called gufw.

To install it using the terminal:

sudo apt-get install gufw.

You will find it under System>Administration>Firewall Configuration

There is alway another one in the repos called firestarter. I like gufw.

---

### Post by Irony on 2010-12-26
There's also frontends;

[http://code.google.com/p/ufw-frontends/](http://code.google.com/p/ufw-frontends/)

---

### Post by SpotHT on 2010-12-26
Firestarter is a front-end for iptables.

---

### Post by karthick87 on 2010-12-26
Have a look at the following link,

[http://www.uluga.ubuntuforums.org/showthread.php?t=510812](http://www.uluga.ubuntuforums.org/showthread.php?t=510812)

---

### Post by mcduck on 2010-12-26
> **Mindswap1 said:**
> Hey Guys! I was wondering what does a firewall do and do I need one? And How can I get one? Thanks In advance I'm a noob at this stuff, and you guys always manage to help :).

The default install of Ubuntu has no running services that would listen for incoming network connections, which makes a firewall completely pointless.

You'll only need a firewall if you install some server application, and it doesn't suitable options for limiting who can connect to it. Linux already comes with all the tools required for setting up a firewall, so you'll only need a way to configure it and give it some filtering rules to work with. I recommend using UFW for this purpose (or Gufw if you prefer having a graphical tool).

edit: What comes to "what does a firewall do", I believe a wikipedia link might give a decent answer: [http://en.wikipedia.org/wiki/Firewall_%28computing%29]("http://en.wikipedia.org/wiki/Firewall_%28computing%29")

---

### Post by karthick87 on 2010-12-26
The default installation of Ubuntu will not listen to any incoming connections.So you dont need a firewall unless you server applications.If you need one you can use the default firewall UFW.
```

sudo ufw enable
```

---

### Post by karthick87 on 2010-12-26
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by tredegar on 2010-12-26
Do you need a firewall? 
Yes, you do. If you don't have one now, you'll probably start some service just to "test it", forget about it..... and then with no firewall, you'll perhaps regret it very badly.

Do you need to implement one?
Probably not: Most (A)DSL modems / routers from the last 5years come with one built-in, and set with sensible defaults (my netgear, after all, is running linux).

Check your modem / router's documentation. Your LAN is probably already protected, but it's a big, bad, world out there, and you certainly need to check right _now_.

---

