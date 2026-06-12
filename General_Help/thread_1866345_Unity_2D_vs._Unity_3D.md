---
title: "Unity 2D vs. Unity 3D"
date: 2011-10-21
forum: General Help
---

### Post by eklikeroomys on 2011-10-21
Halo,

Since Unity 3D feels a bit laggy on my laptop, and I dont like its color (cant find how to edit the color??!!), I've decided to switch to Unity 2D, since I like the dark look more.

Now, for some reason, I have to maximize the dash every single time that I open it, which gets quite frustrating.. Is there a way to make Unity 2D maximize by default? 

If not, is there a way to make Unity 3D open up a bit faster? (the delay is not that bad but I would like it to be faster) And, can I change the color of the dash?

My laptop has 2 GB RAM and a dual core CPU which should be sufficient for running Unity.
I'm concerned about the direction in which Ubuntu is heading. Sure it looks a bit more sleek and everything, but IMO they are trading off productivity to achieve this.:(

---

### Post by beew on 2011-10-21
There seems to be only one desktop in Unity 2D, also the icons for customized launchers on the Unity bar become a square box with a question mark,--they still work though,--at least that is how it is on my 11.10 install. Unity3D is better despite the superficial similarity in appearance.

---

### Post by Frogs Hair on 2011-10-21
This should point out some differences .[http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d](http://askubuntu.com/questions/62001/am-i-using-unity-or-unity-2d)

---

### Post by mc4man on 2011-10-21
> **beew said:**
> There seems to be only one desktop in Unity 2D, also the icons for customized launchers on the Unity bar become a square box with a question mark,--they still work though,--at least that is how it is on my 11.10 install. Unity3D is better despite the superficial similarity in appearance.

If you have used gnome-shell then when logging into unity-2d there will usually be only 1 workspace available
This is because Gs writes a value to gconf upon exiting changing num_workspaces to however many where open in Gs when logging out

Can be adjusted thru gconf-editor or a small start up script

apps > metacity > general > num_workspaces

---

### Post by Gatemaze on 2011-10-21
Have you installed the drivers of your graphics card for 3d acceleration? This should make unity3d faster... Regarding your issue with unity2d I dont understand what you mean by saying that "you have to maximise the dash every time". When I tried unity2d the dash autoappears when mouse hovers on the left side of the screen....

---

### Post by 3rdalbum on 2011-10-21
> **eklikeroomys said:**
> Halo,

Since Unity 3D feels a bit laggy on my laptop, and I dont like its color (cant find how to edit the color??!!)

If you're talking about the colour of the dash, it's actually governed by the colour of your wallpaper.

> Now, for some reason, I have to maximize the dash every single time that I open it, which gets quite frustrating.. Is there a way to make Unity 2D maximize by default?

I can't remember if it's in gconf-editor or in dconf-editor, but there's a key in either gconf or dconf that tells Unity "This is a desktop, don't use all the space for the dash" or "This is a netbook, fill up the screen". If you tell Unity that you're on a netbook, the dash will maximise and fill up the screen.

> If not, is there a way to make Unity 3D open up a bit faster? (the delay is not that bad but I would like it to be faster)

ccsm (or Compizconfig Settings Manager, to use its full name) has some Unity settings as well. Some of these govern how quickly things will appear. Go into CCSM and click on Ubuntu Unity Plugin, then change the "Edge Reveal Timeout" to a lower value. The Launcher will appear quicker now.

---

