---
title: "There is no side applications panel in 11.04"
date: 2011-06-11
forum: General Help
---

### Post by RichardC400 on 2011-06-11
I installed Ubuntu 11.04 on my laptop and was looking to do the same onto my desktop.
However, when I installed the 11.04 download and put it onto a disk and booted my Desktop from the disk, I went into try and the side panel that is on my laptop isn't on this one. It has the Applications, Places and System menus on the top as it was in 10.10

Is this just in the try version side of things, or how can i change it to the new side panel.....thing?

---

### Post by cpmman on 2011-06-11
Have you tried to install your graphics card driver? (it would need doing again once you install it to hard drive)

---

### Post by wojox on 2011-06-11
Sounds like you have Intel on your laptop and nvidia or ati on your desktop, which needs the driver installed.

---

### Post by RichardC400 on 2011-06-12
So how would I install the driver for it?
I just don't want to mess it up completely mess it up

---

### Post by wojox on 2011-06-12
> **RichardC400 said:**
> So how would I install the driver for it?
I just don't want to mess it up completely mess it up

Go into System > Admin. > Additional Drivers and see if you driver is there.

---

### Post by RichardC400 on 2011-06-12
Checked there and it isn't showing any drivers. Would this be because I'm only in Try or something different?

---

### Post by wildmanne39 on 2011-06-12
> **RichardC400 said:**
> Checked there and it isn't showing any drivers. Would this be because I'm only in Try or something different?
Hi, if you are running a livecd and it shows the old desktop as you described then that system is not able to run unity if you install you can still log into ubuntu classic that is the same basically as gnome in 10.10.

---

### Post by RichardC400 on 2011-06-13
I see, so should I just run the 10.10 instead? or would 11.04 be better installed and just run classic?

---

### Post by wildmanne39 on 2011-06-14
> **RichardC400 said:**
> I see, so should I just run the 10.10 instead? or would 11.04 be better installed and just run classic?
Hi, actually 10.04 is the release that has longer support so I suggest 10.04. You could also install 11.04 and then in synaptic install unity 2d and run that, it is almost like unity but it does not have the 3d support, like for the cube. So it really depends on what you want.

---

### Post by sikander3786 on 2011-06-14
> **RichardC400 said:**
> I see, so should I just run the 10.10 instead? or would 11.04 be better installed and just run classic?
You might still be able to run Unity. Actually, it is the default behavior for Unity that if the open source drivers for your graphics are not available, or don't support Unity, you need to install the drivers and then, Unity should be able to run.

First, make sure you are connected to the Internet in Live environment. Then go to Applications > Accessories > Terminal and run:

```
sudo apt-get update
```

Now, go to System > Administration > Additional Drivers and once again take a look if any drivers are available. If still there aren't any, from Terminal, post the output of this command to let us see which graphics card is there and which drivers should be installed.

```
lshw -c video
```

---

### Post by RichardC400 on 2011-12-28
After much deliberation, I left the OS at 10.10
Its easier for my parents I believe

---

