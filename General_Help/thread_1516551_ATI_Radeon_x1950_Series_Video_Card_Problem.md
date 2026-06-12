---
title: "ATI Radeon x1950 Series Video Card Problem"
date: 2010-06-23
forum: General Help
---

### Post by youngcondor12 on 2010-06-23
First off I'd like to say I am new to the whole world of Linux OS. I just installed Ubuntu 10.04 on my computer the other day. It proved a challenge at first but I managed to work my way through some problems. Firstly I managed to install World of Warcraft, and it works, well sort of works lol, thats part of the problem. 

After I had installed WoW I ran the program, I was able to log in, but I found that a lot of objects in the game weren't being rendered, i.e. characters, mounts, etc. all of the terrain was rendering though. Also the fps was extremely low, like 3-4 fps, in the past this computer ran 60-70 fps with no problem, but with Windows XP. 

First off I tried restarting the computer to see if that work, no luck. So I started to do a little research...

I found that I should see if my video card was rendering so I tried:
glxinfo | grep rendering

[FONT=Verdana]and received the response:[/FONT]

direct rendering: Yes

[FONT=Verdana]I also did a:[/FONT]

 lspci | grep VGA    

[FONT=Verdana]to make sure the video card was being recognized, and it was being seen as a Radeon x1900, in reality it is a x1950, but I dont if thats an issue.

I also found some forums mentioning Envy, but soon found it was no longer being supported by Ubuntu, and I am not sure if the ATI Catalyst drivers provided for Linux will work either.

Any help in the matter would be much appreciated, I have other problems but this is on top of the stack at the moment.

Thank You[/FONT]

---

### Post by dcstar on 2010-06-24
> **youngcondor12 said:**
> 
........  
to make sure the video card was being recognized, and it was being seen as a Radeon x1900, in reality it is a x1950, but I dont if thats an issue.

I also found some forums mentioning Envy, but soon found it was no longer being supported by Ubuntu, and I am not sure if the ATI Catalyst drivers provided for Linux will work either.

Any help in the matter would be much appreciated, I have other problems but this is on top of the stack at the moment.

Thank You

If your card is supported by the Ubuntu ATI driver then the system will offer to install the Hardware Driver, otherwise you have to use the open source driver.

---

### Post by youngcondor12 on 2010-06-24
> **dcstar said:**
> If your card is supported by the Ubuntu ATI driver then the system will offer to install the Hardware Driver, otherwise you have to use the open source driver.
  Thanks for the reply. Which open source provider is still available? All the ones I've found are no longer supported.

Thanks

---

### Post by coldraven on 2010-06-24
I'm reasonably certain that your card is in the "Legacy" section of ATI, see:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

If you want fast 3D speed your best bet is to install Ubuntu 8.04 which will use the proprietary driver.
Ubuntu 10.04 will only work with the open source (slow) driver.

---

### Post by cbrunhaver on 2010-06-24
The problem is that ATI has dropped support for your video card in their (proprietary) driver.  They (amd / ati) are only supporting thier "radeon HD" models, on the consumer side.  You can install and older version of ubuntu (I believe 8.04) and install their driver, as it doesn't support the newer version of xorg (in later version of ubuntu). 

The open source drivers are getting better and are fine for desktop effects (compiz) but are still very slow, incomplete and buggy for gaming. This should improve a bit in a couple of releases with the switch over to the gallium3d framework.  They OSS community has been working a long time to get useable 3D accelerated drivers and it is finally beginning to happen but it is sort of like what happened with the sound stack (pulse audio etc.) a couple of years ago.  

I would buy an nvidia card if you want to game in linux or dual boot into windows.

---

### Post by cbrunhaver on 2010-06-24
coldraven beat me to it

---

### Post by QIII on 2010-06-24
nVidia is neither a panacea nor a silver bullet.  nVidia also has "legacy" cards that require the legacy drivers or the open source driver.  Try running a GeForce2 MX400 on a recent release of Ubuntu.

The continuing FUD is frustrating.  A currently supported AMD/ATI card is fine.

Just a bit of history I like to point out every time I hear the "nVidia is the answer" surrounding the continuing AMD/ATI FUD.

In 2007, AMD bought ATI which, admittedly, provided poor Linux support.

AMD/ATI worked very hard to turn the situation around and provide solid Linux support.  So hard, in fact, that for the last several versions of Ubuntu, AMD/ATI has made sure that its latest driver was available in the Ubuntu repos at the time of the final release.  The other distros had to wait until it was released for public consumption.

Not only is AMD/ATI providing solid Linux support, they also seem to have a sweet spot for Ubuntu in particular.

Supported AMD/ATI and nVidia cards work fine.  The choice between them is just like the choice between Chevy and Ford -- one of preference.

Legacy AMD/ATI and nVidia cards are problematic.

---

### Post by avengerxp on 2010-10-06
well, i have the same issue. trying to switch from XP to ubuntu. as you said my X 1950 pro is no longer supported by amd/ati.

but i could still play games and get the most out of it on windows xp. why the heck i need to switch to 8.04 to get the best out of my VGA ??

if ubuntu will run on mostly old systems, it should support an old VGA for sure. BTW the driver in ubuntu that automatically gets with the card sucks. 

if i try to play a video it goes really slow (almost a slide show). and it renders artifacts under the cursor.

any fix for this??

---

### Post by Mark Phelps on 2010-10-06
> **avengerxp said:**
> well, i have the same issue. trying to switch from XP to ubuntu. as you said my X 1950 pro is no longer supported by amd/ati.

but i could still play games and get the most out of it on windows xp. why the heck i need to switch to 8.04 to get the best out of my VGA ??
Because ... AMD dropped proprietary driver support for you hardware long ago.  They write those drivers, not Canonical, not the Ubuntu community.

> if ubuntu will run on mostly old systems, it should support an old VGA for sure. 
Don't know about VGA, but the open-source drivers DO support older (now called "legacy") video cards.

> BTW the driver in ubuntu that automatically gets with the card sucks. 
Useless assessment.  I have a "legacy" ATI video card, use the open-source drivers in Ubuntu 10.04, and get full desktop effects.

> if i try to play a video it goes really slow (almost a slide show). and it renders artifacts under the cursor.
I play videos on my box, using both VLC and Mplayer, and I get no slowdown, no stuttering, no artifacts -- and as I said, I'm using the open-source driver.

> any fix for this??
If you do some forum searches, you'll find posts from folks who have used some ppas to get other drivers -- and then hacked around with settings to improve their video performance.

I don't have the links, since I have no problems with my video performance.

---

### Post by avengerxp on 2010-10-07
@ Mark Phelps,

thanks for your feed back, what i was trying to say is, (no matter ATI dropped support for my hardware long ago), i could still use what ever the old driver it has and squeeze out the power of my GPU.

well the driver offered by AMD for ubuntu works with ubuntu 8.04 (being legacy or what ever). and it does not it 10.04.

so a new user walking into linux will always expect some easy support for the hard ware. indeed it picks up my mobo n sound card drivers automatically.:)

even though you do not have any VGA probs (am happy to hear that),I do. and i have been googling, posting here for almost 2 weeks.

yesterday i was able to get a small fix n the video play back is now good. but still am unable to get ahead of any extra stuff.

---

### Post by Mark Phelps on 2010-10-07
> **avengerxp said:**
> @ Mark Phelps,

thanks for your feed back, what i was trying to say is, (no matter ATI dropped support for my hardware long ago), i could still use what ever the old driver it has and squeeze out the power of my GPU.
Understand what you want to do, but the problem here is that the X-Server in the newer Ubuntu versions has been updated since the 8.04 days, and since only AMD has the code for their proprietary drivers, no one can update that code to handle the newer versions of the X-Server.  So, once again, it's AMD's fault, not Canonical, and not the Ubuntu community's.

> so a new user walking into linux will always expect some easy support for the hard ware. indeed it picks up my mobo n sound card drivers automatically.:)
And generally, that's true -- as evidenced by open-source drivers STILL supporting the older video cards.  And, as time goes on, these drivers are getting better and better.

Case in point -- the radeon driver.  When I started in Ubuntu 7.04 days, the driver was really awful and only the fglrx driver gave decent performance and desktop effects.  Now, in 10.04, the open-source driver provides me real-time video with no slowdown or artifacts and I get full desktop effects.

> yesterday i was able to get a small fix n the video play back is now good. but still am unable to get ahead of any extra stuff.
Glad to hear you were able to fix some of it.

---

