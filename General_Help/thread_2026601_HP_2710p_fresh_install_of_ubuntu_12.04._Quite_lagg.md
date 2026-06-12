---
title: "HP 2710p fresh install of ubuntu 12.04. Quite laggy."
date: 2012-07-15
forum: General Help
---

### Post by skeetwood-mac on 2012-07-15
So I recently got an old HP 2710p laptop/tablet. Was I was shopping for a laptop I was specifically looking for something that would work well with linux. This one seemed to fit the bill. I used the WUBI installer and things went smoothly and pretty much everything works as it should. The problem I'm having is with the speed of the system. On my old laptop (Acer travelmate from at least 4 or 5 years ago) I was running XP and it ran like crap. I installed Linux Mint and it was like a brand new computer. This was running decently on windows 7 so I thought it would be great with Ubuntu. Not the case. Sometimes the dash takes forever to open. And the software center is very slow as well. Even trying to write this is kind of a pain as it keeps lagging for 5 or 10 seconds making it hard to type. I tried installing gnome and things seem to run significantly better. I would like to play around a bit with Unity though if possible, but I can't deal with this laggyness.

One other thing that's working but incredibly slow is the rotation for the tablet mode which I got to work with magick rotation. Sometimes it can take over a minute to rotate or sometimes it just doesn't rotate at all. I have also had this happen where the screen will rotate but the digitizer doesn't so the cursor is in the wrong place when using the stylus. This isn't really a huge deal for me though. I just really need to get things running more smoothly.

Here are some specs if it helps

Memory: 1.9gb
Processor Intel Core 2 duo U7600
Graphics: Intel 965GM
OS type: 64bit (I didn't choose this it just happened automatically)

Im still pretty green when it comes to Ubuntu and I haven't used it much in years (been using a mac), but I much prefer it over Windows so I would really like to get this sorted. 

Thanks in advance!

---

### Post by ranger1021994 on 2012-07-15
You can install LXDE instead of GNOME/KDE etc. to boost your lappy or you can try reinstalling 12.04

---

### Post by Favux on 2012-07-15
Try running 'top' in a terminal and see if there is something chewing up your CPU cycles.

---

### Post by skeetwood-mac on 2012-07-17
So I ran top in the terminal and the biggest users of the CPU were Compiz up to around 30 or 40% then mount.ntsf which went up to around 95% then just now I tried opening the software center because that usually causes some problems and update-software went up to 100% CPU usage. It seems though that mount.ntsf is the most common cause of excessive cpu usage though. Any ideas why?

Thanks

---

### Post by Favux on 2012-07-17
Since you are running Compiz I'll guess you are using Precise Unity 3D.

At the log in screen click the gear and select Unity 2D and log in with that.  That doesn't use the Unity Compiz plug-in.  See if that fixes things.

I'm thinking the problem may be with the Intel 965GM video chipset.

---

### Post by kmsalex on 2012-07-17
Unity is no speed demand, the dash can stutter for me as well, and the software center has been slows since 9.10... for me anyway.

Keep in mind even though it is a C2D processor its only running at 1.2 ghz, i think your best bet hear is to go for something more lite weight, i personally use Lubuntu on 2 of desktop in my house, find it to be a solid "power user" environment. Don't wright it off as something only for old/crappy machines.

---

### Post by skeetwood-mac on 2012-07-22
So I couldn't take it any more. It was just sooo slow. Even slower than windows 7. Switching to classing gnome helped but still it was unbearably slow at times. So I've switched over to Mint and everything is working fine now. Much much faster. Wish I could have figured out what was going on, because I really did enjoy Ubuntu. Mint will do me for now though. Thanks for all the help.

---

### Post by kmsalex on 2012-07-23
> **skeetwood-mac said:**
> So I couldn't take it any more. It was just sooo slow. Even slower than windows 7. Switching to classing gnome helped but still it was unbearably slow at times. So I've switched over to Mint and everything is working fine now. Much much faster. Wish I could have figured out what was going on, because I really did enjoy Ubuntu. Mint will do me for now though. Thanks for all the help.

You didn't listen to a Darn word we said did you? 

About the using lxde, trying unity 2D or explaining to you its slow becuase your cpu is running at a slow clock speed.... 

Well if mint floats your boat fine by me. :popcorn:

---

### Post by skeetwood-mac on 2012-07-24
Actually I tried all of those things. Like I said about gnome classic they made a bit of a difference but something was definitely wrong. I tried installing skype and it took over 30 min. Installing anything took forever. Sometimes unlocking the screen would take 5 minutes just for the password box to come up. Programs took forever to launch. After spending hours trying to figure out what was wrong I had to give up because I'm on the road now and I wanted a working computer. So I tried openSuse and mint and decided to go for mint. Now things are running perfectly. Much faster than windows 7.

THANKS!

---

