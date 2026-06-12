---
title: "Help for a Noob"
date: 2010-05-03
forum: General Help
---

### Post by Berzy on 2010-05-03
I'm just getting into the ubuntu/linux world. I know it's annoying to help noobs but I just need some help getting off the ground. 
I have installed ubuntu 9.10 and it works like magic on my laptop but my desktop is another story. I installed it no prob but there are issues after the install. 
one annoying one is the boot up time. I need someone to look at my boot log please and tell me how stop it from hanging on the beginning of the boot. another is my wifi works but for some reason it just stops after a while. not sure what causes it but it may be just a temp folder fills up, over heats or it seems to be when other usb devices are plugged in. It's not consistant enough for me to pin point it. 
Again I'm a noob and I know little of what i'm doing but I know enough to follow instructions and maneuver around the O/S.

Thanks in advance

B

---

### Post by crlang13 on 2010-05-03
Hey mate,

No one has any problems helping noobs round here, it's where everyone starts.  I don't think I'll be able to help you, but those who will will probably need to know the specs on your desktop - brand, model, etc, etc.

Goodluck.

---

### Post by DomesDKG on 2010-05-03
Updating is always a good place to start, see if there are any updates for 9 that you haven't installed yet, or you might even want to take the dive to lucid lynx (10) now that it's out.

---

### Post by TBABill on 2010-05-03
+1 on updating. Karmic had some issues with the first month or so and lots of updates corrected issues for users. Plus your system will look in the repositories to see if any proprietary drivers are available for your system. If there are you could find improvements in wireless, wired, video, sound, etc. 

Are you connected directly to your router? If able, connect by wire and let the updates run if you get better speed that way. You may be surprised like I was after updating Karmic. I couldn't connect via wireless until I updated and I found Lucid to be the same way for my laptop with a Broadcom adapter.

Good luck!

---

### Post by techunit on 2010-05-03
Wait I wan't to add one more thing about the update process... Don't try to update to Ubuntu 10.04 from it right now. You could have more problem than you want. I hope that this helps.

---

### Post by Berzy on 2010-05-05
thanks for the advice. Everything is up to date and I was not planning on upgrading to 10.04 right now. 
I am not connected directly to my router hence having a wifi problem. my router is a few rooms away. 

I'm wondering how I can view the boot process? all i get is a blank screen and I can't see what the boot process is hanging on. 

any other suggestions out there?

---

### Post by nitstorm on 2010-05-05
You can look for messages in /var/log folder or simple and nice GUI way is System->administration->log file viewer. Look for the messages tab. Even better thing to see how much time each boot process takes is [bootchart]("http://www.bootchart.org/") Once you get it and install it you'll find bar graphs and some other details on how much time the whole system is taking to boot along wit how much time each process of booting takes. Once you have installed bootchart you'll find the log files as images in /var/log/bootchart

---

### Post by techunit on 2010-05-10
I have never gotten much use out of the log viewer myself but it is useful if you post a log in a thead post to get help from more experienced people...

---

### Post by Mitchell Hale on 2010-05-10
When you do finally upgrade to 10.04, install fresh (don't just update) and set up a separate home partition. That way you can update in the future, without having to deal with your personal files.

It might sound complicated, but it's pretty easy, here's a guide-
[http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")

And speaking of noobs, I have a little story.

When I first started using Ubuntu, I installed it on a computer with no internet. I figured I would install software by MOVING DEB PACKAGES ON A FLASH DRIVE. I had no idea what dependencies were. When I tried to install, it said I needed libaudio. So I downloaded it to a flash drive. Took me forever to set up WINE.

P.S.
For anyone in this situation, use virtual Ubuntu on a connected computer, install your packages, and use [APTonCD]("aptoncd.sourceforge.net") (available in the repos), burn to a CD, and put it in the unconnected computer. From there, set it up a a source (there will be a dialogue box), and install from synaptic.

---

