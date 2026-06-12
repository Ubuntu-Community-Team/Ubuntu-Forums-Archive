---
title: "Pidgin sys tray icon missing"
date: 2009-12-11
forum: General Help
---

### Post by syn4k on 2009-12-11
I noticed that my Pidgin sys tray icon is not showing up and now, if I close the buddy list, Pidgin closes completely and I have to sign back in. 

I need to know how to restore the Pidgin system tray icon so that my messenger will work properly.

BTW, in the preferences, the sys tray is checked to show always.

---

### Post by akakingess on 2009-12-11
Have you done a thorough search here on the forums, because I could have sworn that I just saw a similar issue brought up within the last couple of weeks, sorry, but I don't quite have the time to do the search for you right now, but searching here on the forums and googling it would be a great start if you haven't done so already.

---

### Post by syn4k on 2009-12-14
[http://forums.opensuse.org/applications/396406-pidgin-system-tray-issue.html](http://forums.opensuse.org/applications/396406-pidgin-system-tray-issue.html)

---

### Post by akakingess on 2009-12-14
I didn't read all of the link that you sent, but does that mean that a bug report has been already reported via Launchpad.net, and if so, have you gone in to "vote" for it as affecting you, because the more people that say it is affecting them, the more "priority" it starts to get, just a suggestion though.

---

### Post by syn4k on 2009-12-14
I don't think a bug was entered. Thanks for your assist.

---

### Post by cwhisperer on 2010-01-06
> **syn4k said:**
> I noticed that my Pidgin sys tray icon is not showing up and now, if I close the buddy list, Pidgin closes completely and I have to sign back in. 

I need to know how to restore the Pidgin system tray icon so that my messenger will work properly.

BTW, in the preferences, the sys tray is checked to show always.

Hi, did you solved your problem? I have the same issue on 9.10...

---

### Post by mcduck on 2010-01-06
Have you actually enabled the notification icon in Pidgin's preferences? It defaults to being disabled because the Indicator applet already provides some level of functionality with Pidgin..

---

### Post by syn4k on 2010-01-06
> **cwhisperer said:**
> Hi, did you solved your problem? I have the same issue on 9.10...
Yeah, I solved it...I'm trying to remember but I'm almost certain that I enabled the notification area by right clicking the systray and going to Add on the menu. Sorry...I'm in Windows at the moment and can't be sure. If you have further issues, I'll sign into Linux and get it right for you.

---

### Post by stanwang on 2010-01-06
The solution is simple, 
Click on "Tools" and go to "Preference" then Select the choice "System Tray Icon" as "Always" then click on "Close".

I am sure it may solve your problem.:guitar:

---

### Post by syn4k on 2010-01-06
> **stanwang said:**
> The solution is simple, 
Click on "Tools" and go to "Preference" then Select the choice "System Tray Icon" as "Always" then click on "Close".

I am sure it may solve your problem.:guitar:

Actually, that doesn't solve this particular issue. It only solves it if that is the problem and in my case it wasn't

---

### Post by cwhisperer on 2010-01-06
> **stanwang said:**
> The solution is simple, 
Click on "Tools" and go to "Preference" then Select the choice "System Tray Icon" as "Always" then click on "Close".

I am sure it may solve your problem.:guitar:

You're right, this solved the problem. Now I can close the buddy list without completely closing pidgin and the online status notification can be seen on the sysem tray. thank you a lot ;)

---

### Post by dirtyblanket on 2013-03-18
This 'fix' is not working for me. I can't get the Pidgin icon to appear in my system tray. I used Dconf editor and set my whitelist to 'all' and I set my pidgin settings to set the icon in the status bar 'always'. I also tried various themes of Ubuntu precise, but it's clear it's not a contrast issue -- the icon simply isn't there.

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

---

### Post by oldos2er on 2013-03-18
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

