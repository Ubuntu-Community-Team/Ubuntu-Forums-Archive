---
title: "Can't Connect to Wireless Network(WIFI)---!"
date: 2011-04-19
forum: General Help
---

### Post by El3mentGamer on 2011-04-19
When i click the networks icon on the toolbar, these options popup:

[B]Wired Network - (disconnected)
Wireless Networks (*[COLOR="Red"]device not ready--firmware missing[/COLOR]*)
VPN Connections[/B]

I can click VPN connections and that's it. How do i get the firmware needed to connect to a wireless network?

It's tooken me this long to get Ubuntu and now I can't connect T_T

---

### Post by matt_symes on 2011-04-19
Hi

Open a terminal and copy and paste

```
sudo lshw -C network
lspci -nnk | grep -iA3 network
```

Enter your password. It will not be echoed to the screen. This is normal.

Post the results back here between code tags.

Kind regards

---

### Post by El3mentGamer on 2011-04-19
Can't really post results considering im not connected to the interent, im currently working on Ubuntu but on this forum on a completely different computer.

So, i did what u said. But now is just says:

**Wireless Networks (*[COLOR="Red"]Wireless is Disabled[/COLOR]*)**

---

### Post by matt_symes on 2011-04-19
Hi

> **El3mentGamer said:**
> Can't really post results considering im not connected to the interent, im currently working on Ubuntu but on this forum on a completely different computer.

So, i did what u said. But now is just says:

**Wireless Networks (*[COLOR="Red"]Wireless is Disabled[/COLOR]*)**

```
sudo lshw -C network
lspci -nnk | grep -iA3 network
```

What the two commands above will do is tell me about you network hardware and what drivers you have loaded at the moment.

Do you not have an Ethernet connection ? Without that information i will be working blind. 

Is it possible for you to redirect it to a file, copy the file onto a USB stick and then upload it from a different computer ? To do this you will need to type this.

```
sudo lshw -C network > wireless.txt
lspci -nnk | grep -iA3 network >> wireless.txt
```

That will produce a file called wireless.txt that you can upload.

Kind regards

---

