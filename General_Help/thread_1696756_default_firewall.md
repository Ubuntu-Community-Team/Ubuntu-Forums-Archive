---
title: "default firewall"
date: 2011-02-27
forum: General Help
---

### Post by wog on 2011-02-27
Does Ubuntu come with a firewall in it?

I'm trying to set up a minecraft server, and something keeps me from connecting to it. So I was wondering if there's a firewall I need to get under control to allow the minecraft server to function properly.

Advice?

---

### Post by seawolf167 on 2011-02-27
The firewall is ufw by default. You can install a GUI for it to ensure that you have everything passed through

```
sudo apt-get install gufw
```

Make sure that you have your ports forwarded correctly to your machine from your router[s] and that your Ubuntu box is listening on the correct port 

```
netstat -al
```

---

### Post by wog on 2011-02-27
netstat's output is completely baffling.

What does it mean? Will minecraft be listed as minecraft?
There are a lot of identical entries, too.

What is /tmp/orbit-james/linc-704-0-638982b864415 ?
I mean, I'm james, but what's the rest of it?

---

### Post by seawolf167 on 2011-02-28
See if this link [here ]("http://www.minecraftwiki.net/wiki/Setting_up_a_server")helps at all for setting up the minecraft server.

As for [netstat]("http://linux.die.net/man/8/netstat"), the important part for you is to make sure that your computer is listening on the port specified that Minecraft uses

---

### Post by mcduck on 2011-02-28
> **wog said:**
> Does Ubuntu come with a firewall in it?

I'm trying to set up a minecraft server, and something keeps me from connecting to it. So I was wondering if there's a firewall I need to get under control to allow the minecraft server to function properly.

Advice?

Ubuntu doesn't have any firewall enabled by default.

All tools and features required for a firewall are included in the Linux kernel itself, and Ubuntu does come with a command-line tool (UFW) for setting up a firewall should you need one.

So, the default install doesn't have any services listening for incoming connections, so there's no need to run a firewall that would restrict such connections. If you install server software that you can't configure properly and thus need some external tool for limiting it's connectivity, you can of course activate the firewall using UFW, or install Gufw if you want a graphical tool.

However, your problem is likely to be elsewhere, like I said there's no firewall running unless you have set up one yourself, thus the problem with your Minecraft server must be caused by something else. Are you perhaps using a router? In that case you need to forward the correct ports to your server computer in the router's settings...

---

### Post by celldweller1591 on 2011-02-28
edit

---

### Post by celldweller1591 on 2011-02-28
i

---

### Post by celldweller1591 on 2011-02-28
i would suggest you to install Firestarter Firewalll :- 
> sudo apt-get isntall firestarter
It is a little more advanced and gives you full power to customize it to your needs like i have made an inbound traffic policy to keep my things safe !

---

### Post by wog on 2011-02-28
The new version of minecraft_server.jar fixed my problems.

I can connect to my server.

---

