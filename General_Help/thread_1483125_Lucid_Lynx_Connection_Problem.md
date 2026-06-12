---
title: "Lucid Lynx Connection Problem"
date: 2010-05-14
forum: General Help
---

### Post by giaschel on 2010-05-14
Hi!

I'm pretty new to Linux so please bear with me.

I've installed Lucid Lynx last week and all was going fine. Last night, there was a power failure in my neighbourhood and my laptop was left on standby mode at the time.

Now, when I power my laptop again, all works fine except I can't get a connection to my wired network, let alone internet. But I can get internet from my other computer (Windows) so my router and modem work fine. I've tried configuring a network connection manually but it's not working either. I've tried configuring a wifi connection without success.

Can anyone help? Thank you!

---

### Post by _0R10N on 2010-05-14
> **giaschel said:**
> Hi!

I'm pretty new to Linux so please bear with me.

I've installed Lucid Lynx last week and all was going fine. Last night, there was a power failure in my neighbourhood and my laptop was left on standby mode at the time.

Now, when I power my laptop again, all works fine except I can't get a connection to my wired network, let alone internet. But I can get internet from my other computer (Windows) so my router and modem work fine. I've tried configuring a network connection manually but it's not working either. I've tried configuring a wifi connection without success.

Can anyone help? Thank you!

Are you sure you're not even acquiring a network address? Check whether your ethernet adapter's led is on, when you're suppose to be connected to the Internet. It could be a hardware issue.

---

### Post by giaschel on 2010-05-15
Thanks Orion.

The led light is on next to the ethernet cable. When I unplug the cable, the light goes off and it goes on again after I replug it so it doesn't seem like this is the problem. I don't know how many times I rebooted after I changed some settings but still no connection.

I'm a little hopeless.

---

### Post by SabreWolfy on 2010-06-01
I am experiencing a similar problem with my desktop machine running Lucid Lynx. When I specifically (re)start the machine, Auto Eth0 connects automatically.

I have the BIOS set to return the machine to the previous state after a power failure. The location of this machine experiences a few power failures per month, ranging for a few minutes to a few days.

When the power returns after a power failure, the machine starts up again, but Auto Eth0 does NOT automatically reconnect. After logging in, I have to manually connect Eth0. It always connects successfully after I manually select it, but it means that I am not able to remotely connect to the machine after a power failure because Auto Eth0 is not "auto" anymore.

I've checked the settings on the actual connection in Network Manager and various conf. files (/etc/network something) and these are all set correctly, as is shown by the fact that Auto Eth0 connects automatically after a "normal" startup.

---

### Post by SabreWolfy on 2010-06-01
Post [here]("http://www.uluga.ubuntuforums.org/showpost.php?p=7061373&postcount=8") which may be relevant. The second line mentioned in that post (iface eth0 inet dhcp) was commented out in my /etc/network/interfaces file. I've uncommented it and will restart now and wait for a power failure :)

---

### Post by SabreWolfy on 2010-06-01
Uncommenting the line and restarting resulted in a connection (as expected) but the Network Manager Applet disappeared from the panel. Commenting the line out again and restarting restored the applet to the panel.

---

### Post by shai3421 on 2010-06-01
> **SabreWolfy said:**
> Uncommenting the line and restarting resulted in a connection (as expected) but the Network Manager Applet disappeared from the panel. Commenting the line out again and restarting restored the applet to the panel.

Sometimes after a restart things randomly disappear from the panel and re-appear if you restart again.

You should try just restarting again without uncommenting the line if the applet disappears. It might return after a restart.

(and you can add it yourself anyway with "Add to Panel...")

---

### Post by SabreWolfy on 2010-06-01
How do you add the network manager applet via "add to panel"? It's part of the notification section, which is present showing the speaker, but not NM.

---

