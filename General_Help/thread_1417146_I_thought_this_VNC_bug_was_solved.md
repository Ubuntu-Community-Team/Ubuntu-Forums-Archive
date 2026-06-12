---
title: "I thought this VNC bug was solved??"
date: 2010-02-26
forum: General Help
---

### Post by diablo75 on 2010-02-26
[https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/77442](https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/77442)

I just tried to VNC into one of my laptops as well as my own PC from my Nexus One and discovered a problem with the video feed not refreshing like it's supposed to.  At first I thought it might have been the apps I was using on the phone, because while I had remembered a problem with VNC and refreshing occurring in the past, I thought they had surely worked out a solution to this problem by now.

Basically what's happening (as described in the above link) is any time you try to VNC into a box that is running Compiz AND also uses an nVidia card, the video stream doesn't refresh properly... in fact, it doesn't refresh at all.  This problem doesn't occur with other video cards even if Compiz is enabled and effects are on full blast.

I've been out of the country for the last 6 months so I've been out of the loop for quite some time and any VNCing that I did was into a box that didn't have effects enabled solely to save on bandwidth.  But I could almost swear and bet money on the memory of this problem having been taken care of with the release of 9.04.  In fact I even remember it cropping back up for a week or two and then going away again after some updates to vino came out.  The problem seemed to come back up at the same time an advanced control panel for vino was added into System>Preferences>Remote Desktop and then went away after another update seemed to revert that control panel back to the way it used to be.

Here's a picture of the panel I saw come and go (notice the now-missing Advanced tab):

[IMG]http://www.techotopia.com/images/1/12/Ubuntu_advanced_remote_desktop_preferences2.jpg[/IMG]

The problem, once solved, came back with that new panel above.  Then the box reverted back to what it used to be, which used to look like this:

[IMG]http://www.pendrivelinux.com/wp-content/uploads/u_remote_set.png[/IMG]

And now looks like this:

[IMG]http://www.addictivetips.com/wp-content/uploads/2009/06/remote-login.png[/IMG]

I'm not sure when that particular change took place, but I just assumed that with it the same problem of refreshing didn't migrate back into the picture...

Anyway, I'm not trying to troll, but just wondering if anyone knows more about this particular issue because it has seemed to weave in and out of the scene for the last 3 years now.

---

### Post by KillaB7 on 2010-03-29
I just tested 10.04 beta 1 with all the latest updates and I'm sad to say this still doesn't work.

I didn't realize that it was nVidia specific until now.

Turning off Compiz is a terrible workaround, so if it's still not working by 10.04 final, I'll probably be testing x11vnc server, xvnc, etc. to find a decent alternative to vino.

I might be necessary to set up a profile for screen:1 (port 5901). I think I used that method with x11vnc in 8.04.

---

### Post by krunge on 2010-03-30
I don't have any clear thoughts on why this bug has not been fixed in so long, but I wonder whether it is related to the problem involving nvidia proprietary drivers.  Would nvidia need to change their drivers? Are people waiting for that instead of working around it?  I haven't read the bug reports in detail (and when I try they are often very unclear.)  Any thoughts?

---

### Post by KillaB7 on 2010-03-30
I was prompted to install the Restricted drivers for nVidia and chose "nvidia-current".
Is Nouveau the default driver prior to installing the Proprietary drivers?

[http://www.ubuntu.com/testing/lucid/beta1#New%20default%20open%20source%20driver%20for%20nVidia%20hardware](http://www.ubuntu.com/testing/lucid/beta1#New%20default%20open%20source%20driver%20for%20nVidia%20hardware)

---

### Post by bunny rabbit on 2010-04-28
I have it all working fine with an old NVIDIA driver. Perhaps, if you don't really need the new one, you can use an older driver...

When it _does_ work, I can give you this info about my driver:

System Information-
Operating System: Linux-x86
NVIDIA Driver Version: 173.14.12

X Server Information-
Server Version Number: 11.0
Server Vendor Version: 1.4.0.90 (10400090)

NV-Control Version: 1.16

Maybe I'm jumping to conclusions, but I guess, by means of deduction, that the driver's the culprit.

All the best,

[http://ubuntuforums.org/attachment.php?attachmentid=154621&stc=1&d=1272502580]("http://ubuntuforums.org/attachment.php?attachmentid=154621&stc=1&d=1272502580")

---

### Post by Redundant Username on 2010-04-28
It's not nVidia specific, I have an ATI card and I still had a VNC problem. Use the -noxdamage argument with vncviewer to fix it.

---

### Post by krunge on 2010-05-23
Note that it appears NVIDIA has specifically addressed and fixed this problem in its recent driver release:

[INDENT][http://www.nvnews.net/vbulletin/showthread.php?t=151186](http://www.nvnews.net/vbulletin/showthread.php?t=151186)[/INDENT]

---

### Post by bunny rabbit on 2010-05-27
Ah. I finally found some time to get into it.
I'm not so good at computer software that installing this driver is easy for me.
In hindsight it was pretty straight forward though.
I looked the readme over, the installer itself helped with messages and I checked some other threads on the forum too.
[This thread]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+NVIDIA+drivers+manually") in particular, I found very handy.

I haven't tested VNC just yet, though I trust it will be solved now.

Cheers!

edit: It looks like it's working :D Actually, I notice a lot of stuff works better with this driver. I'm very happy with it!

---

### Post by tealio on 2010-07-03
I am experiencing this problem also... I installed an nVidia card and now vino doesn't work... well not properly.  No updates on the client side, although events are being sent to the server.

The problem seems to only be with vino.  Is there any other way to VNC to an active X session?  

I need to get into an existing session because i use VNC on my laptop to start up movies, etc on my media machine.  Basically im using VNC instead of having another remote or wireless kb/mouse sitting around... 

Currently i use x2vnc, but sometimes its hard to click the right thing using the TV as a monitor.  If I could mirror the monitor on my laptop it would help things out tremendously...

---

### Post by KillaB7 on 2010-10-06
Working great using a fresh copy of 10.10-RC.
Thanks devs!

---

