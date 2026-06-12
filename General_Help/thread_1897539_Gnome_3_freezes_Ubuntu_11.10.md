---
title: "Gnome 3 freezes Ubuntu 11.10"
date: 2011-12-19
forum: General Help
---

### Post by wethegreenpeople on 2011-12-19
So basically, I'm trying to get Ubuntu all set up, it installs no problem and works just fine. But I have a problem when it comes to using Gnome Shell. For some reason, every time I install Gnome Shell it messes everything up, I'll install it, and it'll run fine for about 5 minutes then everything freezes and I have to force shut down the computer.

And it's not a problem of using just Gnome Shell, if I install Gnome Shell, I can't even use Unity without the system crashing.

I have to re-install ubuntu all over again just so everything will work (I've re-installed 3 times now)

So, right now I don't have Gnome Shell installed, but I was just kind of wondering why it does this and if there is something that I can do to fix it? If not, that's okay, Unity is cool.. but I'd prefer to run Gnome.

I'm on a Mac, dualbooting with OSX.

---

### Post by wethegreenpeople on 2011-12-22
No help on this?

---

### Post by ubix on 2011-12-22
Have you tried using **Classic GNOME Desktop** instead of GNOME shell?

---

### Post by wethegreenpeople on 2011-12-22
> **ubix said:**
> Have you tried using **Classic GNOME Desktop** instead of GNOME shell?

You mean Gnome 2.whatever? It comes with the Gnome 3 install. And like I said, when I install it, it crashes everything, Unity, Gnome 3, Gnome classic.

---

### Post by ubix on 2011-12-23
> **wethegreenpeople said:**
> You mean Gnome 2.whatever? It comes with the Gnome 3 install. And like I said, when I install it, it crashes everything, Unity, Gnome 3, Gnome classic.

I think this is Ubuntu version, tailored to work in concert with Unity based DM or at least in Ubuntu GUI environment. And yes its touch-and-feel is like GNOME2, but I found it quite stable, and you can tweak it to have almost all the functionality it used to have before Unity.

You install it by running:

```
sudo apt-get install gnome-panel
```

or from _Ubuntu SW Centre_, by searching for **gnome-panel** and installing it.

---

### Post by jmadero on 2011-12-23
Sorry -- wrong thread ;)

---

### Post by wethegreenpeople on 2011-12-23
Okay, now I have a problem. I guess, that it's not actually Gnome that was causing this, it was just bad timing. Without having gnome installed, it crashed again, and I don't understand why it just happened now, it was working perfectly fine for a while.

I don't know if this makes any difference, but when I go into rEFIt, and select partition tool (I think? I don't know the name now...) It says "MBR table is invalid. Partitions overlap"

Could that have anything to do with this?

---

### Post by ubix on 2011-12-23
> **wethegreenpeople said:**
> Okay, now I have a problem. I guess, that it's not actually Gnome that was causing this, it was just bad timing. Without having gnome installed, it crashed again, and I don't understand why it just happened now, it was working perfectly fine for a while.

I don't know if this makes any difference, but when I go into rEFIt, and select partition tool (I think? I don't know the name now...) It says "MBR table is invalid. Partitions overlap"

Could that have anything to do with this?This looks to me as a major screw up, and I am surprised you are able to run anything at all:confused:

---

### Post by wethegreenpeople on 2011-12-23
Bleh. I was afraid you were going to say that...

OSX runs just fine thank goodness.

Is there anything I can do to fix the MBR?

---

### Post by ubix on 2011-12-23
> **wethegreenpeople said:**
> ...
Is there anything I can do to fix the MBR?I think this is one of those times you should hope you had payed for ApleCare or APP. I have no idea how could you have overlapped GPT amd MBR partitions. I think you will need to check things with ***»Applications->Utilities->Disk Utility«***. But you ain't gonna get any help ob this here, as far as I know. 

Though unlikely, perhaps you should pray you only have a problem with partitions in Ubuntu. Just a curiosity, have you created multiple partitions in Ubuntu? You know / (root), /boot, swap, /usr, /tmp, /var,...

---

