---
title: "Teamviewer w/ Dual Screen. Any luck?"
date: 2010-05-17
forum: General Help
---

### Post by Roasted on 2010-05-17
I was messing around with Teamviewer today on my Ubuntu machines. This is an application I love on Windows, and was very happy to see Linux support for it (though it's still in beta).

When I remote to my desktop, which has two monitors: 19 @ 1440x900 + 24 @ 1920x1080, giving me a total resolution of 3360x1080, it comes back to my laptop I'm trying this from notifying me of the user having dual monitors. The screen is black, I see nothing, but I can move the mouse around.

Has anybody else seen that?

---

### Post by Timtro on 2010-05-17
Are there scroll bars? I've had it happen, when using dual monitors of different sizes/orientations that you get a segment of black, since the image stream must be a square.

I've never used teamview, however. I could also see it being a problem to mix different refresh rates or color depths.

Probably not very helpful, but something to think about maybe?

---

### Post by kurmudgeon79 on 2010-06-18
When the connection is established, you have to go to View -> Active monitor -> Show all monitors.

I'd also recommend going to View -> Show remote cursor.  It doesn't scale things right, so where you click isn't necessarily where the click is registering.

The problem is a bug in TeamViewer.  They recognize that you have 2 monitors, but don't separate them properly.  So it displays a black screen instead when you choose monitor 1 or monitor 2.  It could also be due to proprietary drivers.  I'm using Nvidia drivers, which is most likely the cause of this issue.

They definitely have some work to do, but hope this helps you.

---

### Post by DavidG24 on 2010-08-16
Hey guys,

I know this posting is a little late, but I just ran into this problem myself. I'm using Nvidia Drivers and am having the same issues connect from my laptop (windows xp) to my PC (Ubuntu 10.04) - as a trivial short term solution, I log into my PC, change the Nvidia settings to one monitor, do what I have to do, then change back before I log out. But am hoping there is a better way :)

Please let me know if there is!

Cheers,

David

---

### Post by pejoslav on 2011-05-14
Hello all,

i don't use dual screens, but i use multiple workspaces :)
teamviewer installed and running - host is ubuntu 10.04
when i connect to it, i get black screen and a cursor, no windows, no bars, nothing

but i am connected - i can move the cursor around (though i don't know where, its all black) nad host machine also says there is a connection.

anyone?
thanks

edit: above happens when i try to connect using teamviewer on my android phone (it does work when i connect to the windows host)

later i tried to connect to ubuntu host via windows pc and it worked - i got good image.

so problem is android phone connecting to ubuntu host.

---

