---
title: "Chrome Hangs/Freezes"
date: 2012-07-12
forum: General Help
---

### Post by svtguy88 on 2012-07-12
I've been using Chrome for some time now, and it's been pretty good.  I was amazed at the speed difference from Firefox when I initially switched - the start up times for Chrome was much faster.

Anyway, I've noticed that Chrome has been hanging more often than usual lately.  I get the "warning, this page is unresponsive" message, followed by "He's dead Jim" or "Aww..snap" if I kill the page.  If I don't kill it, sometimes it will come back, but usually not.

Usually this seems to happen on more complex sites.  Using Stumble, for example, will freeze Chrome every few pages.  Facebook seems to behave, but Best Buy's site froze it.

Ideas?  I did a little bit of searching, but most of the stuff that I see relating to Chrome freezes is from a long time ago.

---

### Post by vasa1 on 2012-07-12
Sometimes it could a problem with the profile: [http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059](http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059)

---

### Post by mwk88 on 2012-07-12
I have the same problem. I'm running 12.04 LTS and Chrome began freezing a couple days ago when I installed the latest update. It works for a while then completely locks up, sometimes reporting the pages as unresponsive. (The sites are not the problem, I'm writing this in FireFox and all sites work fine.)

I think a bug was introduced. I have wondered if it is related to having multiple users signed in on the computer all running Chrome as that has always been the situation here when it freezes up, but that could be a coincidence.

---

### Post by vasa1 on 2012-07-12
> **mwk88 said:**
> I have the same problem. I'm running 12.04 LTS and Chrome began freezing a couple days ago when I installed the latest update. It works for a while then completely locks up, sometimes reporting the pages as unresponsive. (The sites are not the problem, I'm writing this in FireFox and all sites work fine.)

I think a bug was introduced. I have wondered if it is related to having multiple users signed in on the computer all running Chrome as that has always been the situation here when it freezes up, but that could be a coincidence.

I'm using the latest Chrome on 12.04 fully updated. I'm not seeing any freeze. But I'm just the one user.

---

### Post by Jeffa on 2012-07-12
I'm also noticing that chrome is freezing a lot lately. Was working fine, now it hangs up a lot. I'm running 12.04. This is happening in chrome and chromium. 

There also seems to be a minor increase in pop ups. I'm wondering if there is some sort of malware infesting my machine. I've searched the repositories for alternatives to programs like spybot or malwarebytes but I don't see anything. could this be a possibility?

---

### Post by montego95 on 2012-07-14
Chrome started freezing up for me two updates ago.  Same issue being expressed by the others on this thread.  Just saw another update yesterday to Chrome and I let it update.  Still having the same issue.  Seems to really break a lot on heavy javascript sites such as Yahoo! mail and gmail.

---

### Post by mwk88 on 2012-07-15
I also noticed this post [http://askubuntu.com/questions/163204/google-chrome-not-rendering-after-sleep](http://askubuntu.com/questions/163204/google-chrome-not-rendering-after-sleep) suggesting the trigger is when returning from sleep. That might be related in my case -- what I thought was a trigger of multiple people switching users might be the ubuntu session sleep

---

### Post by svtguy88 on 2012-07-15
I'm the only user that is on my machine, so the multi-user bug is not my problem.

I can confirm that heavy Java sites seem to be the worst offenders.

---

### Post by vasa1 on 2012-07-15
> **pkmgarf said:**
> I'm the only user that is on my machine, so the multi-user bug is not my problem.

I can confirm that **heavy Java sites** seem to be the worst offenders.

[LIST]
[*]Are you sure it's Java and not javascript?
[*]Have you tried a [new profile]("http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059") as I suggested earlier?
[/LIST]

---

### Post by svtguy88 on 2012-07-16
Sorry, my mind thought Javascript and my fingers typed Java.

No, I haven't had time to really test much yet.  I was out of town camping for the past three days.  I'm just getting caught back up in the "online world" now.  Chrome seems to be playing nice today though.  Some updates came through, but I didn't see anything that would relate to Chrome.

I'll see if I have some time to play with what exactly is causing the freezing later tonight while doing laundry.

---

### Post by Doughy on 2012-07-21
I tried creating a new profile and it did not solve this problem for me.

---

### Post by svtguy88 on 2012-08-21
Just weighing back in here.  I've kept up to date with all updates that come through, and I'm still having issues with sites that use a lot of Javascript.

I use Chrome for web development work too, and the site I'm working on uses some JS (nothing crazy, though), and even it will hang up in Chrome from time to time.  Firefox behaves fine, though.  

I'm the only user on my system, but I tried deleting and re-adding my account via the settings panel anyway.  We'll see if that helps at all...

---

### Post by irv on 2012-08-21
Another thing you can try is to completely remove the Chrome Browser and try re-installing it. I had to do this with other software and it fixed some problems.
Sometimes one need to step back to move forward.

---

### Post by RayDeCampo on 2012-09-12
I am experiencing the same problem.  When I was the only one using Chrome there were no issues.  When my wife starting using it Chrome does not work.  It loads one page and then will not load anything else.  Mousing over links in the one page does not change the mouse.  

The only solution I have found is a reboot.  I have tried uninstalling and re-installing Chrome but it still needs a reboot.  I would love to know if there is a work-around that does not involve rebooting the computer.

---

### Post by irv on 2012-09-13
> **RayDeCampo said:**
> I am experiencing the same problem.  When I was the only one using Chrome there were no issues.  When my wife starting using it Chrome does not work.  It loads one page and then will not load anything else.  Mousing over links in the one page does not change the mouse.  

The only solution I have found is a reboot.  I have tried uninstalling and re-installing Chrome but it still needs a reboot.  I would love to know if there is a work-around that does not involve rebooting the computer.

Chrome browser is different then other browser in that it stores all your extensions and setting online. So when you install it, it remembers all your setting and loads all your extensions. When I was having problems with it locking up I started by uninstalling all my extension and my problem went away. Now I have three extensions reinstalled and everything is still working OK. Here are the extensions I have installed. 
[ATTACH]224097[/ATTACH]

---

### Post by pjalegria on 2012-10-27
I start to have this problem after 12.10 upgrade, any fix???

Thanks

---

### Post by svtguy88 on 2012-11-16
I'm still having issues with Chrome on heavy JavaScript pages.  I've been using Firefox as necessary...

---

### Post by irv on 2012-11-16
> **pkmgarf said:**
> I'm still having issues with Chrome on heavy JavaScript pages.  I've been using Firefox as necessary...

I do switch back and forth from Chrome to Firefox also.

---

### Post by jockmullin on 2012-11-22
Unfortunately I can contribute little here except to report I am having the same problem under 12.10 (WUBI); it started on the second last Chrome update. I have uninstalled/reinstalled and tried another profile to no avail. Single user Dell Inspiron 9400 2 gig ram.

When it craps out the hard drive light goes on solid. Have tried waiting it out but it never stops; always have to hard boot.

The system is primarily used to concurrently monitor several servers using remote desktop viewer and Logmein within Chrome (which uses java).

PITA having to reinit everything when this happens, so have had to revert to FF, but the nice thing about Chrome was the cloud syncing to maintain settings over multiple machines.

This same setup used to work admirably; nothing changed except the ongoing flood of Ubuntu updates and the last 2 Chrome replacements.

Jock

---

### Post by RayDeCampo on 2012-11-22
> **jockmullin said:**
> 
PITA having to reinit everything when this happens, so have had to revert to FF, but the nice thing about Chrome was the cloud syncing to maintain settings over multiple machines.


I'm pretty sure there is a sync plug-in for FireFox, you'll need to install it so not as seamless as Chrome but it is something.

---

### Post by hank22077 on 2012-12-11
So... no real solution here?

---

### Post by svtguy88 on 2012-12-12
Not really...except stay way from heavy javascript pages.

I haven't noticed as many problems lately...

---

### Post by jockmullin on 2012-12-17
Further to my prev, I did in fact resolve my problem, though not likely a general solution ... it turned out my swap partition was clobbered. Happened to do a "free -m" and found to my amazement swap file size was zero.

Recreated it and no more problem with Chrome or anything else. I was short of virtual memory pure and simple.

Jock

---

### Post by rrich1974 on 2012-12-26
I have the same problem with chrome. today i have got my total freeze after one week of using ubuntu 12.04. i have had the same problem in the past with mint and fedora. 
the OS become completly blocked. i need to log in to tty and reboot from there.

---

### Post by irv on 2012-12-26
I have been keeping a eye on my memory and swap usage while running Chrome to see what it doing now that I am running 12.10. I do this by running 
```
top
``` at the command line.
Been up for 4 days + and it look good.
[ATTACH]229176[/ATTACH]
As you can see, I am a little heavy on memory usage, but my Swap is only using 104Mg. I also have about 93Mg buffered.
I am going to do a restart and re-post my top readings.

EDIT:  Here is my top reading after a reboot. It was without running Chrome. As you can see it wasn't much different on the swap, but I am using a lot less memory.
[ATTACH]229177[/ATTACH]
Running Top and using a little more memory
[ATTACH]229178[/ATTACH]

---

### Post by rrich1974 on 2012-12-26
here is mine, few minutes after starting chrome.

---

### Post by irv on 2012-12-26
> **rrich1974 said:**
> here is mine, few minutes after starting chrome.

I don't see chrome in the list of running programs. Sometimes you need to give top a little time to start picking up a started program.

---

### Post by irv on 2012-12-26
This is something not related to chrome directly, but a few years ago I was running Netflix in IE on a windows machine and I keep running out of memory. When I ran Netflix in firefox this didn't happen. IE had a problem releasing memory.
The point being not all browser are not equal. 
I think the more tabs you have open in chrome or any other browser the more memory it will use.

---

### Post by rrich1974 on 2012-12-27
here we go again....just a few minutes ago a experiences another freeze. 
i entered in tty and run top, see the picture. 
```
rich1974@rich1974-Inspiron-1521:~$ dmesg | tail
[   26.948078] composite sync not supported
[   29.096126] composite sync not supported
[   30.444102] composite sync not supported
[   31.620101] composite sync not supported
[   46.176740] PPP BSD Compression module registered
[   46.192762] PPP Deflate Compression module registered
[   49.200155] composite sync not supported
[   55.796487] mmc0: new SD card at address e624
[   55.819573] mmcblk0: mmc0:e624 SU064 59.5 MiB 
[   55.824354]  mmcblk0: p1
```

what is your take on this?

---

### Post by rrich1974 on 2012-12-30
so, after some searches, i tried two things:
in plugins i disabled embeded flash player 11.5 and let the ubuntu flash 11.2 to run.
i add in kernel boot option "pci=nomsi"
[https://bugs.launchpad.net/unity/+bug/946572](https://bugs.launchpad.net/unity/+bug/946572) comment #10

that is after, today i experienced a total freeze of unity during pdf reading with document-viewer. 

for now, the things seems to be okay. later, i will try to enable flash 11.5 back. 
i will update the behaviour in coming days. 

can someone tell what that "pci=nomsi" means? thanx.

---

### Post by gordintoronto on 2012-12-30
More than you want to know:
[http://www.mjmwired.net/kernel/Documentation/PCI/MSI-HOWTO.txt](http://www.mjmwired.net/kernel/Documentation/PCI/MSI-HOWTO.txt)

The key point is #4: "Not all machines support MSIs correctly..."

---

### Post by irv on 2012-12-31
> **rrich1974 said:**
> so, after some searches, i tried two things:
in plugins i disabled embeded flash player 11.5 and let the ubuntu flash 11.2 to run.
i add in kernel boot option "pci=nomsi"
[https://bugs.launchpad.net/unity/+bug/946572](https://bugs.launchpad.net/unity/+bug/946572) comment #10

that is after, today i experienced a total freeze of unity during pdf reading with document-viewer. 

for now, the things seems to be okay. later, i will try to enable flash 11.5 back. 
i will update the behaviour in coming days. 

can someone tell what that "pci=nomsi" means? thanx.

I had to disable-bundled-ppapi-flash to get Amazon videos to work because of a kernel update and my AMD CPU.
See this link: [http://askubuntu.com/questions/159379/have-to-run-chrome-from-google-chrome-disable-bundled-ppapi-flash-command-t]("http://askubuntu.com/questions/159379/have-to-run-chrome-from-google-chrome-disable-bundled-ppapi-flash-command-t")
How I did this was to start Chrome with this command.
```
google-chrome --disable-bundled-ppapi-flash %U
```
[ATTACH]229394[/ATTACH]

---

### Post by rrich1974 on 2013-01-01
happy new year guys! 

so, i have enabled back the pepper flash (11.5) and it seems to work ok so far. 
you can disable the flash in graphical mode, just type in the adress bar "chrome://plugins" 
but for me, it seems that "pci=nomsi" did the trick.

---

