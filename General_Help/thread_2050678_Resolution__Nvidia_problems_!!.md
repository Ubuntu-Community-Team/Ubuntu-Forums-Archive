---
title: "Resolution / Nvidia problems !!"
date: 2012-08-31
forum: General Help
---

### Post by gman101 on 2012-08-31
Hey Ubuntu forums !  For about 5 months i have been having problems with Ubuntu and screen resolution, for a while i used these forums to help me fix the problem but the problem never remained permanently fixed so i have decided to make my own thread ! 

I'm a bit of a Ubuntu noob (still prefer GUI interface to pure text based) so go easy on me ! Basically the problem is that Ubuntu has given me a range of resolutions to choose from when looking at the display section of system settings (1024x768, 800x600, 1152x864, 1360x768) however any resolution above 1024x768 limits the movement of my mouse cursor, as in I wont be able to access half of the screen ! This should not be the case as i know my monitor can handle 1680x1050 @60hz (or 59.93hz) so what is causing this and why cant i choose 1680x1050 in display options !?

As mentioned earlier i have been trying to fix this problem for months, i have had to completely rebuild my xorg.conf files as well as install new nvidia drivers and reconfigure gdm. This solved the problem for a while but one day at boot i got no graphical interface and when pressing F7 i saw an error stating ubuntu was 'unable to load fallback graphic devices', to solve this i completely removed all xorg files and all nvidia drivers then  reinstalled the latest nvidia driver once i could access unity GUI.

So i am now using nvidia-current from xorg on ubuntu 12.04 and am using a bamboo tablet as a mouse (could this be the cause of the limited mouse cursor movement ?!) furthermore ubuntu routinely shuts down when running flashplayer intensively, this normally causes compiz settings to be reverted back to defaults, at first i thought this could be caused a faulty psu but since replacing my psu it still occurs so could it be caused by the same issue which is causing me to have limited resolution?

Please help !!

---

