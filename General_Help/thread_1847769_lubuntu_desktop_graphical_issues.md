---
title: "lubuntu desktop graphical issues"
date: 2011-09-21
forum: General Help
---

### Post by Chiel92 on 2011-09-21
Hi all,

I'm experiencing graphical problems with several things on my Lubuntu installation. For example, 'partial-transparent' windows on my desktop. Have a look at the attachment. You see a youtube video right through the terminal window. These things happen e.g. with the xfce-terminal, but also with other programs. (The default LXterminal worked even worse, so I istalled xfce-terminal.) I also get black rectangles in the left-upper-corner of my screen.

I'm running Lubuntu 11.04, Lxde desktop, Nvidia drivers, graphics processor: GeForce G210M.

A good thing to mention is the following:
When I go to system tools->additional drivers, it says:
"No proprietary drivers are used on this system.", though I installed an nvidia driver as far as I know.
See also the attachment for further info.

Any help is appreciated.

---

### Post by amjjawad on 2011-09-21
Hi again,

Perhaps I need to change my glasses :P
It seems I can't see anything wrong. Is it possible for you to upload another screenshots when the case is even worse as you mentioned?

---

### Post by Chiel92 on 2011-09-21
Hey, that's weird:confused::confused::confused:
Sorry :) It seems that a screenshot filters the bug.
Sorry, I can't help. I really see windows through other windows right now!

---

### Post by amjjawad on 2011-09-21
> **Chiel92 said:**
> Hey, that's weird:confused::confused::confused:
Sorry :) It seems that a screenshot filters the bug.
Sorry, I can't help. I really see windows through other windows right now!

LOL, then I guess it's not a bug ;)

I believe you but I guess I need to imagine and in that case, I'll help you blindly.
Have you changed any settings?
Forget the Terminal. Try to open for example PCManFM and place the Window above your Browser or vice-versa ... see if the same will happen?

---

### Post by whatthefunk on 2011-09-21
That is weird, especially since LXDE doesnt offer true transparency on its own.

---

### Post by amjjawad on 2011-09-21
@OP: Wait, how did you install Lubuntu 11.04? could you please explain?


> **whatthefunk said:**
> That is weird, especially since LXDE doesnt offer true transparency on its own.
Indeed.

---

### Post by ajgreeny on 2011-09-21
Have you added compiz to your lubuntu installation?

That is the only way I can imagine transparency managing to show itself.  I know compiz will work with LXDE, but it is not in the default Lubuntu.

---

### Post by amjjawad on 2011-09-21
> **ajgreeny said:**
> I know compiz will work with LXDE, but it is not in the default Lubuntu.

Hello ajgreeny,

Are you positive that **compiz** will work with LXDE? I'm up to try that on my PC (haven't installed it in LXDE before) but just to make sure someone can fix a possible mess :)

Edit: Well, after watching [this]("http://youtu.be/BeuDBJ6IY5M"), I guess I'll go for it :)
I have never been so interested about these stuff. I just want my machine to work without any extra headache or steps. I'll do it this time for testing because I need to understand more about LXDE and Lubuntu.

---

### Post by Chiel92 on 2011-09-21
> **amjjawad said:**
> @OP: Wait, how did you install Lubuntu 11.04? could you please explain?


Downloaded an installation file on a bootable usb and just followed the instructions. I didn't do special things.

---

### Post by Chiel92 on 2011-09-21
> **ajgreeny said:**
> Have you added compiz to your lubuntu installation?

That is the only way I can imagine transparency managing to show itself.  I know compiz will work with LXDE, but it is not in the default Lubuntu.

No, I didn't.

---

### Post by Chiel92 on 2011-09-21
> **amjjawad said:**
> LOL, then I guess it's not a bug ;)

I believe you but I guess I need to imagine and in that case, I'll help you blindly.
Have you changed any settings?
Forget the Terminal. Try to open for example PCManFM and place the Window above your Browser or vice-versa ... see if the same will happen?

PCManFM doesn't get partially transparent. But mtPaint does, for example. It is even more weird. When the browser is minimalized, and the terminal or mtPaint not, then I can watch the video!! Right through some parts of their windows.:-s

Because a screenshot does not catch it, I would suspect the drivers or some hardware things. I don't know how exactly screenshots are taken, but I guess it is done via software that gets info from the OS or from the desktop environment. That would indeed mean that these issues are not chaught by a screenshot, just because it could be caused by the driver or hardware.

Does this sound plausible?

---

### Post by amjjawad on 2011-09-21
> **Chiel92 said:**
> PCManFM doesn't get partially transparent. But mtPaint does, for example. It is even more weird. When the browser is minimalized, and the terminal or mtPaint not, then I can watch the video!! Right through some parts of their windows.:-s

O_o

> Because a screenshot does not catch it, I would suspect the drivers or some hardware things. I don't know how exactly screenshots are taken, but I guess it is done via software that gets info from the OS or from the desktop environment. That would indeed mean that these issues are not chaught by a screenshot, just because it could be caused by the driver or hardware.I know a Screenshot would be great but it's ok if you can't make it, I mean it can't catch that weird thing which is actually another weird thing.
[http://en.wikipedia.org/wiki/Print_screen](http://en.wikipedia.org/wiki/Print_screen)

> Does this sound plausible?Not for me :(

I'm sorry but I'm not sure what is going on. Lubuntu **by default** doesn't do that.

Edit: Try to search here, perhaps you'll find similar cases: [www.googlubuntu.com](www.googlubuntu.com)
It could be your driver but I'm not 100% sure about that.

---

### Post by Dennis N on 2011-09-21
For what it's worth, 

I've seen the same thing happen as the O.P. describes, but only a few times in the four months I have used Lubuntu 11.04. Nvidia graphics on that machine. Another Lubuntu 11.04 machine has never done this - it has AMD graphics.

Example: Firefox open on desktop 1. Terminal open (not minimized) on desktop 2. Switch from desktop 1 to desktop 2, and the terminal window would show the corresponding part of desktop 1 inside the terminal window. Closed the terminal, reopened it, and all was normal.  

Only happened with the terminal. Also, I could not reproduce the behavior at will - it might take weeks for it to happen again. Last time I saw this was several weeks ago.

---

### Post by amjjawad on 2011-09-22
I now remember that LXTerminal was acting somehow like that with Lubuntu 10.04. First thing I checked with Lubuntu 11.04 was that issue and it got fixed.

I'll keep an eye on this issue and hope we could find a solution.

Thank you :)

---

### Post by amjjawad on 2011-10-01
Hello Chiel92,

Is there any update? you still have the same issue?
Have you played around with Lubuntu 11.10? it's still Beta Version but was just wondering if you have done that from LiveUSB for example? just curious how that would work on your machine?!


> **Chiel92 said:**
> Downloaded an installation file on a bootable usb and just followed the instructions. I didn't do special things.
Have you downloaded it from: [https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A11.04](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A11.04)

I have come across some cases that users have installed "lubuntu-desktop" package on their Ubuntu installation (GNOME or Unity) and that created lots of troubles. I just want to make sure and double check that your case is different and you have installed Lubuntu 11.04 normally on a new formatted partition.

Thanks :)

---

### Post by Chiel92 on 2011-10-01
Sorry for my inactivity in this issue. I'm really busy with things concerning my study. I will dive right into this as soon as I've got any time again.;)

It takes time to reconstruct the bug... In the beginning the bug appeared more consequently.

---

### Post by amjjawad on 2011-10-01
> **Chiel92 said:**
> Sorry for my inactivity in this issue. I'm really busy with things concerning my study. I will dive right into this as soon as I've got any time again.;)

Take your time, focus on your study and everything else can wait :)

Good Luck!

---

### Post by Chiel92 on 2011-11-14
I tried a little bit around recently, but unfortunately I could not reconstruct the original hanging problems. So that won't help us any further in this thread.

I'm besides switching to ubuntu studio, for audio recording reasons. So I will deinstall Lubuntu, as I won't use it anymore.
Thanks all for your willingness to help me in these things!

Cheers

---

### Post by makitso on 2011-11-14
You can get some basic transparency by installing xcompmgr and running it.  I use this for the Cairo dock and it work perfectly.

---

### Post by amjjawad on 2011-11-14
> **Chiel92 said:**
> I tried a little bit around recently, but unfortunately I could not reconstruct the original hanging problems. So that won't help us any further in this thread.

I'm besides switching to ubuntu studio, for audio recording reasons. So I will deinstall Lubuntu, as I won't use it anymore.
Thanks all for your willingness to help me in these things!

Cheers

Whenever you want to go back to Lubuntu (and I'm sure you'll ;) ), just PM me in case you need anything, ok?

Before you un-install, have a look at Lubuntu One Stop Thread in my signature. There are many threads and you might find the same issue over there. Just have a look :)

---

