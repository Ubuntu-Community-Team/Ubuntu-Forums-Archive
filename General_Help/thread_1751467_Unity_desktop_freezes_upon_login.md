---
title: "Unity desktop freezes upon login"
date: 2011-05-06
forum: General Help
---

### Post by Thecoolguru on 2011-05-06
Hello everyone.

So I finally managed to install a copy of Natty on my old laptop, but when I logged in, the desktop was frozen. I could move my mouse, but I couldn't click anything. I didn't know if it had to do with packages not being up to date or something (though I doubt it is) so I ran sudo apt-get update, and then tried to run sudo apt-get upgrade, but I got an error saying "E: Unable to locate package upgrade". Apparently I'm not the first to have this problem. I found a similar question asked at [http://superuser.com/questions/280028/ubuntu-natty-desktop-freezes-after-login]("http://superuser.com/questions/280028/ubuntu-natty-desktop-freezes-after-login"). However, there was no answer. I thought that maybe an Ubuntu-specific forum would have an answer.

Any suggestions would be useful. Thanks in advance,
thecoolguru

EDIT: It's not just Unity. I tried Ubuntu Classic, and that froze too. However, safe mode seems to work.

---

### Post by mikewhatever on 2011-05-06
Do you also have an nvidia card like the guy from the link you posted?
Unity/Compiz doesn't work with some Nvidia cards + proprietary drivers. It's a known bug with no fix for now.

---

### Post by Thecoolguru on 2011-05-06
That would be correct. Is there any way that I can use something besides Compiz? I think I remember having issues with it a while ago.

---

### Post by Thecoolguru on 2011-05-06
Sorry, I lied. I was thinking about a different machine. I have an ATI Radeon card.

---

### Post by bkuberek on 2011-06-21
In my case, everything worked fine after upgrade from 10.04 LTS to 10.10 to 11.04. 

It was then that I noticed at the task manager (top right) there was a "drivers" icon. I click on it and it shows me 2 options for the nVidia driver. I clicked the "recommended" one and activate.

After reboot I was stuck. Could not do anything. Read many posts and forums. Nothing.

In my mind I know it was that driver change. So after trying different things what worked for me was to login to session "Ubuntu Classic (no effects)" (not sure the effects matter here), then I went to System/Administration/Drivers and changed to the older driver Nvidia173.

It works fine now. Hope it will help someone.

---

### Post by orsula on 2011-08-24
I had freezes issues with Unity on Natty on a  Dell Latitude D630 with Nvidia Quadro NVS 135M. On login, screen would show only desktop icons but nothing else. Mouse was working but no menus were showing. Only way out was to reboot and then login with 'Ubuntu Classic' option.

What fixed it was:
In CCSM, go to Preferences and choose profile: 'Unity' and then UNCHECK 'Enable Integration into the desktop environment'.

Got this from here:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion ]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

I am using the 'NVIDIA accelerated graphics driver (version current) [recommended]' in the 'Additional Drivers'.

---

