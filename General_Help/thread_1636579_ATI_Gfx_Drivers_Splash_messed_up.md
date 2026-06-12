---
title: "ATI Gfx Drivers: Splash messed up"
date: 2010-12-03
forum: General Help
---

### Post by madmax.santana on 2010-12-03
I have an ATI Radeon 5730 HD graphics card. I know the open source drivers for ATI cards do not do well with the Plymouth splash. So now I am having a text based splash and a really horrible tty resolution. A few months back, I was running Lucid on a Laptop with nVidia card. I had the same problem then and I posted in Ubuntu forums and was directed to a page where some method was given to fix up the issue. I don't remember exactly but it had something to do with grub, probably explicitly telling it the graphics card parameters and forcing it to load graphical splash.

However, shortly after that I installed Maverick on the same laptop and tried to hack it with the same method... It didn't work with Maverick and my system refused to boot and kept going dark right after the grub menu. I posted in Ubuntu but the reply was a little bit late and I had to sell my laptop.

Then I bought a new one, with the mentioned ATI card... Now I have the same problem and I want to fix it but I don't want to try that method which caused me trouble last time. I know it doesn't work with Maverick and I don't wanna go there. But I am sure a workaround exists. I googled it and found the same old thread which I am weary of. Does anyone know of such a method which works with both ATI and Maverick? Please direct me or mention here...

---

### Post by Frogs Hair on 2010-12-03
There are some (use at your own risk) scripts and instructions available for 10.04 and 10.10 , but I can't find anything for the development release . Trying methods for other releases may end badly.

---

### Post by madmax.santana on 2010-12-04
Yeah, since I am using 10.110 (Maverick), I would like to have a look at those options. I am not using a development release.

---

### Post by madmax.santana on 2010-12-04
But you gotta give me options so I can try them...

---

### Post by madmax.santana on 2010-12-04
*Furious*
C'mon guys! It's been more than 7 months and still there is not a single proper fix for this bug! This is outrageous!
Third release is coming up with a lot of consistent problems. I guess the dev team should try and fix the previous releases before going for next release...

-- Empathy, Evolution and Gwibber don't work and I have tried everything to fix them. But no! They are still stuck. So I don't use any mail clients, instant messengers or social networking applets. Fine!
-- With Jaunty, I was deprived of the right to have a nice proper way to change the look of GNOME login screen. I tried a lot of fixes but all I can do is change the wallpaper and be happy! Good enough.
-- Since Lucid, there is this nasty problem with resolutions and graphics hardware. I cannot install the ones provided by ATI, rather I have to install the "open source" ones (fglrx), and they mess up with my splash. I try to fix them but it doesn't work. And when I uninstall fglrx, I cannot. And even if I manage to uninstall them, bye bye GNOME!

Alright... Linux is about freedom. But guys, everyone doesn't have enough time on their hands to keep fixing the issue with freedom. Hell yeah, that's why most of the general public is comfortable with paying a few hundred bucks for an operating system and anti-virus software, then sit back and relax... They don't have to fix-up the software problems for hours and days so they can use the hardware they paid an enormous amount for.

Ubuntu isn't for everyone. Please change the slogan... It is not for guys who are behind proxy servers. It is not for guys who have graphics cards in their PCs. It is not for guys who don't know programming. It is just for the people with enough wits (compliment) and time to "play".

EDIT: Oh and by the way, I tried installing startupmanager... It appears that the startupmanager doesn't "start" itself... I removed fglrx and now I don't have display... Thank God I had installed Windows as well... And thank God the grub still loads...

---

### Post by Zookalicious on 2010-12-05
> **madmax.santana said:**
> *Furious*
C'mon guys! It's been more than 7 months and still there is not a single proper fix for this bug! This is outrageous!
Third release is coming up with a lot of consistent problems. I guess the dev team should try and fix the previous releases before going for next release...

-- Empathy, Evolution and Gwibber don't work and I have tried everything to fix them. But no! They are still stuck. So I don't use any mail clients, instant messengers or social networking applets. Fine!
-- With Jaunty, I was deprived of the right to have a nice proper way to change the look of GNOME login screen. I tried a lot of fixes but all I can do is change the wallpaper and be happy! Good enough.
-- Since Lucid, there is this nasty problem with resolutions and graphics hardware. I cannot install the ones provided by ATI, rather I have to install the "open source" ones (fglrx), and they mess up with my splash. I try to fix them but it doesn't work. And when I uninstall fglrx, I cannot. And even if I manage to uninstall them, bye bye GNOME!

Alright... Linux is about freedom. But guys, everyone doesn't have enough time on their hands to keep fixing the issue with freedom. Hell yeah, that's why most of the general public is comfortable with paying a few hundred bucks for an operating system and anti-virus software, then sit back and relax... They don't have to fix-up the software problems for hours and days so they can use the hardware they paid an enormous amount for.

Ubuntu isn't for everyone. Please change the slogan... It is not for guys who are behind proxy servers. It is not for guys who have graphics cards in their PCs. It is not for guys who don't know programming. It is just for the people with enough wits (compliment) and time to "play".

EDIT: Oh and by the way, I tried installing startupmanager... It appears that the startupmanager doesn't "start" itself... I removed fglrx and now I don't have display... Thank God I had installed Windows as well... And thank God the grub still loads...



If we put aside the fact that you haven't tried any IM or Email clients aside from the stock ones (which is more than a little silly), we can safely say that you're infuriated because you are unable to customise the appearance of your splash and login screen to your desire? That seems a bit.... hypocritical to say the least. You're more than welcome to go and try to modify the Windows splash and login screen and you can let us know if you get as far as changing the wallpaper...;)

---

### Post by madmax.santana on 2010-12-06
I have tried Pigeon and Thunderbird as well... Same problem... Thunderbird works charm in Windows. But fails in Ubuntu. After a lot of searching over thee internet I found out that apparently everybody at the developer side of Linux hates everybody on the user side of Linux who is behind a proxy server. Hence, due to some bugs (several of them filed several times), the IM and e-mail applications in Ubuntu fail to connect to my proxy server. So, I guess we are back at the same point as my previous post...

It's not that I hate Linux... Oh I love it... Despite everything I am still trying to install Ubuntu 10.04 in hopes of getting fglrx working. My frustration is NOT because Linux has problems... My frustrations, please note, lie with the fact that the last few releases of Ubuntu have not been given the care that should have been given. And I know many Ubuntu users will agree with me, although I dunno why they don't they say it out loud.

And, just to remain in the "game", I know Windows Splash is not customizable... Although back hen I used Windows XP, I had found ways to change the Login screen as well the screen which says "Windows is shutting down"... It was simple, changing some registry values. And yeah, the video drivers worked very well.

As far as Windows 7 is concerned, there is a software which can change your login screen background. I haven't found any way to change the splash, though. But whatever, I don't wanna change it because at least the splash "appears"...

Whatsoever, I don't mean to offend anyone. I am a fan of Linux and Ubuntu. I don't even want to imply that Windows is better or more secure than Linux. But Windows definitely is easier. (Although less customizable)... But behaves good with graphics drivers and proxy servers and IM/email clients etc.

Still, if instead of concentrating on pointing out the contextual mistakes that I have made, if you would give some thought to the problem that started this thread, that would be more Ubuntu.

---

### Post by Zookalicious on 2010-12-06
> **madmax.santana said:**
> 

Still, if instead of concentrating on pointing out the contextual mistakes that I have made, if you would give some thought to the problem that started this thread, that would be more Ubuntu.

Since the open source drivers are not working well for you, consider installing the proprietary AMD drivers from their support website. I've only ever used nvidia cards but the proprietary drivers worked well on my friends computer.

---

### Post by madmax.santana on 2010-12-07
Ok... Good. Sincere thanks...
That's a solution.
Will definitely try once I manage to install the new system above the broken one. Thank you very much indeed.

---

### Post by Zookalicious on 2010-12-07
No problem. Hopefully that works better for you.

---

### Post by madmax.santana on 2010-12-07
:( NO!
That doesn't... Same... Even worse. Now the graphics performance is like 0. My desktop loads frame-by-frame. Splash is still creepy text Ubuntu Logo! And the "Additional Drivers" applet keeps bugging me to install the driver it proposes!

---

### Post by Zookalicious on 2010-12-07
It keeps bugging you as in that pops up even if you enable the driver? If you haven't taken it's advice and installed that driver yet, I would suggest that since it sounds like you have not enabled the new driver you just downloaded yet.

---

### Post by madmax.santana on 2010-12-08
Installing it enables it... :\
But the drivers applet doesn't recognize that it has been enabled and keeps bugging me to re-install it...

---

### Post by mastablasta on 2010-12-08
what graphics card are you using? how did you install the drivers?
 
Note that for 10.10 AMD made drivers in time for this Ubuntu release. And they have plenty fixes for newer cards. So maybe it would be better to try to go with 10.10 and then install proprietary AMD drivers through hardware drivers/additional drivers menu applet.
 
i use open source ones because i can't use the proprietary (graphics card is too old). i don't get the splash screen at all (only cursor blinkig), but i don't really care as long as everyhting else works ok.
 
also as i know fglrx is proprietary driver: [http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx)
 
to remove them you will also need to purge them after removal and do some rebooting. dont' knwo exactly how as i said i use the opensoruce ones.

---

### Post by madmax.santana on 2010-12-08
I am using Radeon HD 5730.
I installed propriety drivers in both ways. By downloading and running ATI script and by the Additional Drivers applet...
And it's too late to purge now. Because the system is down.
And that is the exact same situation with me. I know how to remove splash altogether. That would fix the issue. But the issue is I WANT SPLASH, WORKING.

---

