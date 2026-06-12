---
title: "wireless connection keeps dropping"
date: 2011-12-10
forum: General Help
---

### Post by pelee98 on 2011-12-10
hello all.

I have an Acer netbook with a dual boot ubuntu 11.10 and windows 7,  in ubuntu the wireless keeps dropping out. Ran great for months - no problems.  Then,for a couple of weeks, it would drop the connection and then reconnect on its own in a few seconds - annoying, but at least it reconnected. Now i need to tell it to reconnect, and to make matters worse, it will not save the access code to the wireless. So I have to keep the network password with me and type it in every time I reconnect (which is a lot).

And none of this happens when I've booted in to windows 7 - so it's not a hardware issue.

---

### Post by lechien73 on 2011-12-10
What model of wireless card do you have in your Acer? If you open a terminal window and run:

```
lspci
```

You should be able to find it listed as a Network Controller.

If you could post the output of:

```
dmesg | grep wlan0
```

(I'm assuming your card is wlan0) then that would be useful too.

If it's an Atheros card, then I've had issues with that before. It's likely that the card stopped working as a result of an update.

---

### Post by gandaran on 2011-12-10
>  and to make matters worse, it will not save the access code to the wireless. So I have to keep the network password with me and type it in every time I reconnect (which is a lot).

that is a keyring problem, delete the existing keyring profiles then set a new one.

---

### Post by pelee98 on 2011-12-11
> **lechien73 said:**
> What model of wireless card do you have in your Acer? If you open a terminal window and run:

```
lspci
```

You should be able to find it listed as a Network Controller.

If you could post the output of:

```
dmesg | grep wlan0
```

(I'm assuming your card is wlan0) then that would be useful too.

If it's an Atheros card, then I've had issues with that before. It's likely that the card stopped working as a result of an update.


It Is an Atheros card, but it still works fine in windows.  Is this a bug in recent updates.

---

### Post by pelee98 on 2011-12-11
> **gandaran said:**
> that is a keyring problem, delete the existing keyring profiles then set a new one.

OK, bit of a noob here. You may have to explain that one for me.  Got a link to an instructional?

---

