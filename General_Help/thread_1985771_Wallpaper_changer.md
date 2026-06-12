---
title: "Wallpaper changer"
date: 2012-05-23
forum: General Help
---

### Post by mdialogo on 2012-05-23
What is your recommended wallpaper changer for Ubuntu 12.04? I used Wallch but it affects my running apps (e.g. videos, games) when changing wallpapers. Thanks in advance!

---

### Post by Rodney9 on 2012-05-23
I like [DesktopNova]("http://sites.google.com/site/haliner/desktopnova") it is available in the Software Centre.

Rodney

---

### Post by hakermania on 2012-05-24
Hello mdialogo, I am one of the developers of Wallch. Can you please make clear what is the exact problem with Wallch, so as to help you fix it?

---

### Post by mdialogo on 2012-05-24
> **hakermania said:**
> Hello mdialogo, I am one of the developers of Wallch. Can you please make clear what is the exact problem with Wallch, so as to help you fix it?

Thank you for the response!  Wallch is great especially the picture of the day from Wikipedia and the live wallpaper earth, it's awesome!  The only problem I have with Wallch was when it changes the wallpaper it slows down my running apps like movies (e.g. totem), games (e.g. supertuxkart) for about 1-2 sec then they return back to normal.  So what I'm doing was I just turn off Wallch when I'm watching movies or playing games.  Not sure what is causing this.  I really want Wallch change my Wallpaper smoothly.  Is this because I'm using an open source video driver from NOVEAU?  
My system are AMD dual core, onboard GeForce 6150SE nForce 430, Ubuntu 12.04 32bit.  Please help...

---

### Post by hakermania on 2012-05-25
> **mdialogo said:**
> Thank you for the response!  Wallch is great especially the picture of the day from Wikipedia and the live wallpaper earth, it's awesome!  The only problem I have with Wallch was when it changes the wallpaper it slows down my running apps like movies (e.g. totem), games (e.g. supertuxkart) for about 1-2 sec then they return back to normal.  So what I'm doing was I just turn off Wallch when I'm watching movies or playing games.  Not sure what is causing this.  I really want Wallch change my Wallpaper smoothly.  Is this because I'm using an open source video driver from NOVEAU?  
My system are AMD dual core, onboard GeForce 6150SE nForce 430, Ubuntu 12.04 32bit.  Please help...
I seriously cannot reproduce this. Are you sure that it is Wallch to blame?
Let me explain that isn't Wallch that handles **how** the background will change; Wallch just sends the message to the system (via the gsettings command) so as to change the desktop background. So, Wallch only indirectly changes the desktop background. I'm not really sure what causes your problem because as I explained you Wallch just waits the timeout and sends the corresponding command, but you could try other Wallpaper Changers as well.
I really doubt whether the problem will be gone.

PS: A thought: Are you using images with very high resolution? That is maybe a reason that causes the lag. But it's physical, you can understand why.

---

### Post by mdialogo on 2012-05-25
> **hakermania said:**
> I seriously cannot reproduce this. Are you sure that it is Wallch to blame?
Let me explain that isn't Wallch that handles **how** the background will change; Wallch just sends the message to the system (via the gsettings command) so as to change the desktop background. So, Wallch only indirectly changes the desktop background. I'm not really sure what causes your problem because as I explained you Wallch just waits the timeout and sends the corresponding command, but you could try other Wallpaper Changers as well.
I really doubt whether the problem will be gone.

PS: A thought: Are you using images with very high resolution? That is maybe a reason that causes the lag. But it's physical, you can understand why.


Ok, I'll just try with other wallpaper changer, DesktopNova I think, and see if I will encounter the same issue.  I used the images I downloaded from Wallch 1000 wallpapers and they all have high resolution.  You're right, maybe it's my system that causes the lag.  Also, my video memory is only 512.  I'll keep you posted.  Thank you all!

---

### Post by IcyValmy on 2012-05-26
Hey guys! There's something I really hate about Wallch.. I can't select all my pics collection. Actually i'm alloed to select very few pics... that's sad

---

### Post by malspa on 2012-05-26
I have all my wallpapers in one directory and just select the directory, no problem.

Wallch works good here, whether in Unity or GNOME Shell. I didn't even know Desktopnova worked with those two, but I read that Wallch did so I went with that instead. I've been using Desktopnova with Xfce, though.

---

### Post by hakermania on 2012-05-26
> **IcyValmy said:**
> Hey guys! There's something I really hate about Wallch.. I can't select all my pics collection. Actually i'm alloed to select very few pics... that's sad

If you have a top folder e.g. Pictures, just click add folder and select that folder, all subfolders will be added. I don't understand where the problem is :)

---

### Post by honeyman on 2012-05-26
I think the problem is not in Wallch itself
Yes when i used background of lesser resloution the slow time decrease but i think the problem is the computer slows while detecting the main color of the picture and choosing it as a transparent color for unity as when i had chosen a fixed color the slow is gone...
So how to fix this anyway ??

---

### Post by john77eipe on 2012-05-26
Does Wallch work fine with gnome 3?

---

### Post by hakermania on 2012-05-26
> **honeyman said:**
> I think the problem is not in Wallch itself
Yes when i used background of lesser resloution the slow time decrease but i think the problem is the computer slows while detecting the main color of the picture and choosing it as a transparent color for unity as when i had chosen a fixed color the slow is gone...
So how to fix this anyway ??
Hmmm... I don't know whether there is a solution with this. It is called unity chameleon effect.


PS** Wallch works fine with GNOME 2 & 3 and is currently being developed so as to work with many many other desktop environments!**

---

### Post by Zvlwab on 2012-05-26
The Compiz wallpaper plugin has a cycle function for this.

---

