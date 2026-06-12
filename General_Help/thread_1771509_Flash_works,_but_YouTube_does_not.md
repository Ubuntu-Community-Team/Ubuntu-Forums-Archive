---
title: "Flash works, but YouTube does not"
date: 2011-05-30
forum: General Help
---

### Post by jbandlow on 2011-05-30
The problem: When I try to play YouTube video with Firefox, there is just a black box where the video should be.

What does work: Any other flash site I can find. In particular [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) and [http://www.mozilla.com/en-US/plugincheck/](http://www.mozilla.com/en-US/plugincheck/) both show that I have Flash player version 10.3.181.14 correctly installed. Furthermore, YouTube works fine in Chrome.

Embedded videos (for example, the ones here: [http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=56115](http://www.google.com/support/youtube/bin/answer.py?hl=en&answer=56115) ) also work. It is only when I am on the main video page (for example, [http://www.youtube.com/watch?v=uCeXNzI_i9g](http://www.youtube.com/watch?v=uCeXNzI_i9g) ) that nothing happens.

My setup: 32-bit Ubuntu 10.10 on a System 76 laptop, Firefox 3.6.17.

I've tried disabling all extensions, and all plugins (except for Flash) without success. Restarting the browser and rebooting the computer don't help. I'm now out of ideas. Can anyone help?

---

### Post by linuxinstalledfromhdd on 2011-05-30
Try Flash Aid Plugin for Firefox over here:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Install it..  From inside Firefox click Tools, then Add-ons.. Look in Extensions. Open Flash Aid. And hit "execute".

---

### Post by jbandlow on 2011-05-30
Thanks [linuxinstalledfromhdd]("http://ubuntuforums.org/member.php?u=1050936"),

I installed FlashAid, and when I go to Tools->Add-ons->Extensions, I see Flash Aid 2.1.1 and three buttons: Preferences, Disable, Uninstall. If I click on Preferences, I see a check box 'Check for flash updates' (which is checked) and the terminal path (/usr/bin/gnome-terminal which is correct). I don't see an 'execute' button anywhere.

Restarting firefox still does not fix the problem.

---

### Post by linuxinstalledfromhdd on 2011-05-30
It looks like the developer has changed the way the interface works last night, or they are in the process of making some changes to the way it functions.  Uninstall it for now. 

Here is a walkthrough for new users to Ubuntu 11.04. It's possible that you are missing other plugins that might make a difference to the quality of flash playback. 

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by hari1986 on 2011-07-01
I had the same issue -

you have to uninstall flashblock.

go to system>preferences>synaptic package manager 
search for "flash" or "flashblock" and uninstall it.

---

### Post by alfu on 2011-07-05
Do NOT install FlashAid!

I am 'still' running 9.1, and this exact symptom started when I opened up a YouTube account (still not sure why I made THAT harebrained move).  According to YouTube, many people are having this problem.

At any rate, after doing all of the above, plus 'installing' the latest Adobe flash (which is claimed to be compatible with 9.1) even the Flash graphics like satellite weather loops claim to be running not only show up blank, but slow the computer to a crawl.  I have 'installed' 10.3.181.34 many times from 
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) but it still reports I have 10.2.159.1 installed.  Getting file 'properties' in Ubuntu does not report version numbers (and I always have to enlarge the dialog box to see the complete path -- that needs to be fixed some day ...)

If I ever get this fixed without having to upgrade Ubuntu (and the attendant loss of all my user settings) I will report back how to fix this here.

I went to [http://apod.nasa.gov/apod/ap110307.html](http://apod.nasa.gov/apod/ap110307.html) and tried playing the movie -- it actually had controls.  It gave a message (after a bit of fiddling with the controls to try to get it to play) that I needed more stuff, then installed 29MB of crap which did not improve the situation, I suppose because it said it couldn't get all the crap it needed.  I can get it to show a few frames by moving the slider, but it is very broken.

With Synaptic, I removed swfdec-gnome and swfdec-mozilla: no improvement.

---

### Post by Swagman on 2011-07-05
Kewl Link

Btw.. I'm using Flash-aid in Firefox 5

[[IMG]http://img691.imageshack.us/img691/6929/ubuntu208.th.jpg[/IMG]](http://img691.imageshack.us/i/ubuntu208.jpg/)

---

### Post by nomko on 2011-07-05
> **alfu said:**
> Do NOT install FlashAid!
 
Hmmm....... For some reason alfu migth be rigth. After trying Flash-aid and removing it, i noticed that my system is crawling like a snail, certain games i play are running on crawling speed. I've got the idea that Flash-aid indeed did something to my well running 10.04.1 LTS system... 
 
@ alfu: let me know if you find some fix or solution!

---

### Post by alfu on 2011-07-05
I pulled all the swf and flash items off with Synaptic, then re-installed the 'flashplugin-installer' that Synaptic finds, but that only installs the older version (10.21591  -- developers please note: no decimals are needed to the right of the first one ...).

Started working again, despite the report from the Adobe website that I still only have 10.21591 installed.  YouTube (even in HD), weather loops all going-- not sure I did anything good; maybe someone at YouTube coincidentally pulled a switch, since I had complained to them about the situation.

It works now, so I am not fooling with it any more.:confused:

Update 1107052100: ... and suddenly, now YouTube videos are NOT playing.:mad:

---

### Post by lovinglinux on 2011-07-07
> **jbandlow said:**
> Thanks [linuxinstalledfromhdd]("http://ubuntuforums.org/member.php?u=1050936"),

I installed FlashAid, and when I go to Tools->Add-ons->Extensions, I see Flash Aid 2.1.1 and three buttons: Preferences, Disable, Uninstall. If I click on Preferences, I see a check box 'Check for flash updates' (which is checked) and the terminal path (/usr/bin/gnome-terminal which is correct). I don't see an 'execute' button anywhere.

Restarting firefox still does not fix the problem.

Since version 2.1.0, the Flash-Aid functions are no longer packed in the Preferences dialog. Now there is a menu in the toolbar icon. If you don't see the toolbar icon, then right-click on a toolbar, select *Customize* and drag the icon to the toolbar.

---

### Post by childe joseph on 2011-07-07
I'll be checking back here. I'm a Mint user with a similar problem. I can't get YouTube on either browser, Firefox or Chromium, not off the main YouTube page or YouTube's posted on any site i.e. facebook. Here's a link to my thread in the Mint forum

[http://forums.linuxmint.com/viewtopic.php?f=47&t=76613](http://forums.linuxmint.com/viewtopic.php?f=47&t=76613)

---

### Post by lovinglinux on 2011-07-07
> **alfu said:**
> Do NOT install FlashAid!

I am 'still' running 9.1, and this exact symptom started when I opened up a YouTube account (still not sure why I made THAT harebrained move).  According to YouTube, many people are having this problem.

At any rate, after doing all of the above, plus 'installing' the latest Adobe flash (which is claimed to be compatible with 9.1) even the Flash graphics like satellite weather loops claim to be running not only show up blank, but slow the computer to a crawl.  I have 'installed' 10.3.181.34 many times from 
[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) but it still reports I have 10.2.159.1 installed.  Getting file 'properties' in Ubuntu does not report version numbers (and I always have to enlarge the dialog box to see the complete path -- that needs to be fixed some day ...)

If I ever get this fixed without having to upgrade Ubuntu (and the attendant loss of all my user settings) I will report back how to fix this here.

I went to [http://apod.nasa.gov/apod/ap110307.html](http://apod.nasa.gov/apod/ap110307.html) and tried playing the movie -- it actually had controls.  It gave a message (after a bit of fiddling with the controls to try to get it to play) that I needed more stuff, then installed 29MB of crap which did not improve the situation, I suppose because it said it couldn't get all the crap it needed.  I can get it to show a few frames by moving the slider, but it is very broken.

With Synaptic, I removed swfdec-gnome and swfdec-mozilla: no improvement.

> **alfu said:**
> I pulled all the swf and flash items off with Synaptic, then re-installed the 'flashplugin-installer' that Synaptic finds, but that only installs the older version (10.21591  -- developers please note: no decimals are needed to the right of the first one ...).

Started working again, despite the report from the Adobe website that I still only have 10.21591 installed.  YouTube (even in HD), weather loops all going-- not sure I did anything good; maybe someone at YouTube coincidentally pulled a switch, since I had complained to them about the situation.

It works now, so I am not fooling with it any more.:confused:

Update 1107052100: ... and suddenly, now YouTube videos are NOT playing.:mad:

Hi,

I am the developer of Flash-Aid and I am here to help you. 

First of all, I think I deserve the right to defend my application, saying that it has more than 21.000 happy users. Cases like yours are extremely rare. In fact, this is the first time I see someone blaming Flash-Aid for their flash problems.

Most likely that your problem is due to the fact that you are using a unsupported version of Ubuntu. Flash sucks in Linux and the fact that you are using an old Ubuntu version only contributes to the problem.

The reason why your Flash stopped working in Firefox is due to some weird YouTube issue. Is not the first time this happens and it is affecting many users. To fix the problem, see [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

About the fact that you have version 10.2 instead of 10.3, is probably because that Karmic Koala repositories are no longer updated.

You need to upgrade. Using Ubuntu 9.10 any longer is a security risk. You don't loose your personal stuff by doing an upgrade. However, I would recommend a clean install instead. If you want to preserve you personal files and settings when doing a clean install, you can create a separate partition for home. This can save you a lot of time and trouble, since you can install  clean Ubuntu any time, preserving your personal settings and files. I never created a separate partition for home after installation. That is usually accomplished during install. However, there are some tutorials on how to do it.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Always make backups of your important stuff when doing such things like partitioning.

---

### Post by lovinglinux on 2011-07-07
> **childe joseph said:**
> I'll be checking back here. I'm a Mint user with a similar problem. I can't get YouTube on either browser, Firefox or Chromium, not off the main YouTube page or YouTube's posted on any site i.e. facebook. Here's a link to my thread in the Mint forum

[http://forums.linuxmint.com/viewtopic.php?f=47&t=76613](http://forums.linuxmint.com/viewtopic.php?f=47&t=76613)

See [YouTube Problems Mega Thread]("http://ubuntuforums.org/showthread.php?t=1799217")

---

