---
title: "Firefox Won't Open While Connected to the Internet !!!"
date: 2010-09-12
forum: General Help
---

### Post by linuxyogi on 2010-09-12
Hi, 

The problem is Firefox won't open while the network manager has already established an adsl connection.

When I click on the FF icon it says starting FF & then nothing happens.
Now, just as soon as I disconnect my adsl connection FF opens instantly.

Note: I only clicked it once while connected to the internet. I didn't click it again after disconnecting the adsl connection.

Now that FF is already running I can easily redial my ISP & start browsing.

Typing firefox at the terminal prints nothing.

OS:Lucid 64
FF Ver. 3.6.9
apparmor for firefox is enabled.

**_Addons_**

[IMG]http://i851.photobucket.com/albums/ab73/img2010_album/Screenshot.png[/IMG]

---

### Post by cgroza on 2010-09-12
Very strange... never heard of this. Try the latest FF 4.0 just to check if it works.

---

### Post by Lukas666 on 2010-09-12
try the safe mode:

firefox -safe-mode

I bet it has something to do with autoupdating.

---

### Post by scouser73 on 2010-09-12
Go to **Administration** [COLOR="Red"]>[/COLOR] **System Monitor** and see if Firefox is running, if so right click on the Firefox entry and select **End Process**.

It's just a shot in the dark but it may sort it.

---

### Post by linuxyogi on 2010-09-13
> **Lukas666 said:**
> try the safe mode:

firefox -safe-mode

I bet it has something to do with autoupdating.

Actually this problem doesn't happen on every boot.
Its not exactly within my control.
So, the next time it happens I'll try firefox -safe-mode & tell you what happens.  

> **scouser73 said:**
> Go to **Administration** [COLOR="Red"]>[/COLOR] **System Monitor** and see if Firefox is running, if so right click on the Firefox entry and select **End Process**.

It's just a shot in the dark but it may sort it.

Already did that.
After ending the processes when I try to start firefox, as usual it fails to start.

---

### Post by linuxyogi on 2010-09-14
> **Lukas666 said:**
> try the safe mode:
firefox -safe-mode


Tried   firefox -safe-mode.
Didn't work.

> **Lukas666 said:**
> 
I bet it has something to do with autoupdating.

I searched the processes list in System Monitor didn't find "apt" there.

---

### Post by linuxyogi on 2010-09-21
No one?:confused:

---

### Post by linuxyogi on 2010-10-05
Guys, I am facing this problem every time I boot.

Tried uninstalling FF and reinstalling it.
Disabled the apparmor profile for firefox.

None helped.

Do I have to install Lucid all over again ?

---

