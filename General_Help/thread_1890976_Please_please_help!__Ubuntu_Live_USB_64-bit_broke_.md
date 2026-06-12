---
title: "Please please help!  Ubuntu Live USB 64-bit broke my wireless in Windows"
date: 2011-12-04
forum: General Help
---

### Post by peGGi on 2011-12-04
The problem:

After trying out Ubuntu 11.10 64-bit from a Live USB, when I logged back into Windows, my internet connectivity was completely screwed up.  

My network manager tells me I have internet connectivity, and utorrent and Skype both work, but my browsers (Opera, Chrome, Internet Explorer) can't connect to the internet.  At other times, since then, the network manager says I have no internet connectivity.  

Background to the Problem:

While in the Live USB session, I had trouble getting the wireless working.  This is a common problem for people like me who have a Broadcom 43xx card (mine is 4313).  After hooking up LAN and removing the Broadcom STA driver with the Software Centre, the wireless started working in Ubuntu.  

I logged out of the Ubuntu session, but couldn't log back in, as it was asking for a password and username, and nothing I tried worked.  So I eventually had to power down the laptop without being able to properly boot out of the live session.  I should also add that I created the Live USB using UNetBootIn.  I then booted up Windows and this wireless problem was there.  When I logged into Windows, my computer didn't log onto the home network as usual.  Instead, it automatically "re-found" it, created a new name for it, and asked me if it was a home/public/work network.   (My interent network is normally called upc 16, Windows now called it upc 16 2). It said I was conected to the internet, but none of my browsers worked on any websites.  

More worryingly, the following day (this was on Friday evening) my flatmate rang me and told me she was having the same problem! (no browser activity but internet connection).  She has a MacBook Pro.  I told her to power down the Mac and turn power down and disconnect the modem and router.  After 5 min, turn both back on, then after a further 5 min, turn the Mac on.  This solution worked for her, but didn't work for me. 

Similar thing happened with my Android phone and again this solution worked for it but not for my PC.

So it looks to me that somehow the Ubuntu live sesssion has messed up how my PC talks to the router.  Furthermore, it's going to keep doing this - her Mac's browsers were again unable to use the internet today until we did the modem/router off/on fix.  I had spent ages last night trying to fix my PC laptop.


Attempted Solutions:

[LIST]
[*]Ran the troubleshooter in Network and Sharing Centre.  It says "The DNS server isn't responding" and doesn't give me much help after that.  
[/LIST]

From searching internet for people with the same problem, I've tried the following fixes (all from within Windows).  However on all the forums and websites I've read with solutions for this problem, none of them mention or attribute it to problems with Ubuntu Live session or anything.  Most of them blame it on Norton Anti-virus.  This makes me think that my situation is quite unique, and therefore their solutions less likely to work.  I tried them anyway if I thought they weren't going to damage my computer.

[LIST]
[*]One was to reset the TCP/IP by entering the command " netsh int ip reset c:\resetlog.txt " and rebooting. This seemed to work - I had activity on my browsers for about 30 seconds (although very slow loading pages) but then it went back to nothing.
[/LIST]

[LIST]
[*]I "flushed the DNS".   I entered the command "ipconfig/flushdns" and rebooted.  Still had the wireless problem.
[/LIST]

[LIST]
[*]I reset winsock (no idea what that is, just going on the advice of forums...) by entering commands “netsh winsock reset catalog” and “netsh int ip reset reset.log hit” and re-booted.  The first time I did that, I had browser connection for about 1 minute, then it went back to not working.  I tried it again, and this time I didn't even get the 1 minute, it just didn't work at all.
[/LIST]

[LIST]
[*]Downloaded Norton Removal Tool (I've never had Norton – my computer came pre-installed with McAfee, which I never used, and it currently uses Bullguard – however, I read on a forum that this solution worked for someone even though they had never had Norton either)... and ran it.  After I re-booted, didn't fix the problem.  In fact seemed to be worse, because there was no internet activity at all – utorrent, Skype not connecting and network manager saying that there was no internet connection.   I reset winsock after this and back to square one (i.e. Internet connection but browsers won't work).
[/LIST]

[LIST]
[*]Turned off all security software, including Windows Firewall, but no fix.
[/LIST]

[LIST]
[*]I have tried various settings in internet options, in adapter settings, but nothing has worked.  I was careful to put all settings back to original.
[/LIST]

[LIST]
[*]I have uninstalled and re-installed the wireless drivers on my computer, but no joy.
[/LIST]

[LIST]
[*]I have just run a full scan with Malawarebytes.  It didn't find anything.  However I'd be amazed if this was down to malware due to the timing of it.  The problem began immediately after using the Ubuntu Live USB, and I had had problems with Wireless within the live session.
[/LIST]

As I have attempted all these fixes, etc., the network manager sometimes says connected to the internet (and other internet-based apps work) but browsers don't, and sometimes it says there is no internet connection, and those other apps don't work also.  At the minute, I have no internet connection at all.

I didn't have system restore set up, so I have no restore points to go back to....

I have tried to attach the diagnostic reports that the windows network troubleshooter created.  However this forum thing won't let me upload them, saying that they are invalid files..?

My computer is a Lenovo IdeaPad Z570, with Core i5-2410M, 6Gb RAM, NVIDIA GT520M Optimus graphics, Broadcom 802.11n wireless adapter, running Windows 7 64-bit.  The wireless router is Netgear WNR2200.

If anyone has any ideas, please let me know.  I just think that somehow the Ubuntu live session, messing around with wireless, somehow has knocked out the way my compter speaks to the router.  And furthermore, this is causing problems with the router as I try and fix it, as my flatmates mac and my android phone have both lost connectivity afterwards (although both have been successfully restored).  Has anyone else ever had this problem after using an Ubuntu Live USB/CD?  

I have backed up my Windows and should be able to recover it.  However I'd rather not have to  do this. I've a feeling that there is a solution without having to resort to that, as I do have some internet connectivity.

---

### Post by oldtimer7777 on 2011-12-04
What I recommend you do is first contact your ISP to have them walk you through restoring your internet connection on the Windows computer.  Then I would visit the web site for the manufacture of your wifi router (hopefully you have one) and look up the phone number for the router tech support phone number.   Both of these tech support help lines should be free of charge since you already have paid for both.  Try to reach someone in Level II tech support, preferably, since they tend to be knowledgeable in Linux OS.  Tell them you want to configure your router so it will also work on your Linux system.  Have them test the connection to make sure it is working, and to walk you through any steps to assure that the router is providing your Linux OS internet connectivity. These are exactly the steps any repair person would take if they came out to your flat for a housecall.   You would need to do the same thing if you want to get this resolved quickly, and painlessly.   Anything else would be a complete shot in the dark here, since this is a router/ISP issue. 

> **peGGi said:**
> The problem:

After trying out Ubuntu 11.10 64-bit from a Live USB, when I logged back into Windows, my internet connectivity was completely screwed up.  

My network manager tells me I have internet connectivity, and utorrent and Skype both work, but my browsers (Opera, Chrome, Internet Explorer) can't connect to the internet.  At other times, since then, the network manager says I have no internet connectivity.  

Background to the Problem:

While in the Live USB session, I had trouble getting the wireless working.  This is a common problem for people like me who have a Broadcom 43xx card (mine is 4313).  After hooking up LAN and removing the Broadcom STA driver with the Software Centre, the wireless started working in Ubuntu.  

I logged out of the Ubuntu session, but couldn't log back in, as it was asking for a password and username, and nothing I tried worked.  So I eventually had to power down the laptop without being able to properly boot out of the live session.  I should also add that I created the Live USB using UNetBootIn.  I then booted up Windows and this wireless problem was there.  When I logged into Windows, my computer didn't log onto the home network as usual.  Instead, it automatically "re-found" it, created a new name for it, and asked me if it was a home/public/work network.   (My interent network is normally called upc 16, Windows now called it upc 16 2). It said I was conected to the internet, but none of my browsers worked on any websites.  

More worryingly, the following day (this was on Friday evening) my flatmate rang me and told me she was having the same problem! (no browser activity but internet connection).  She has a MacBook Pro.  I told her to power down the Mac and turn power down and disconnect the modem and router.  After 5 min, turn both back on, then after a further 5 min, turn the Mac on.  This solution worked for her, but didn't work for me. 

Similar thing happened with my Android phone and again this solution worked for it but not for my PC.

So it looks to me that somehow the Ubuntu live sesssion has messed up how my PC talks to the router.  Furthermore, it's going to keep doing this - her Mac's browsers were again unable to use the internet today until we did the modem/router off/on fix.  I had spent ages last night trying to fix my PC laptop.


Attempted Solutions:

[LIST]
[*]Ran the troubleshooter in Network and Sharing Centre.  It says "The DNS server isn't responding" and doesn't give me much help after that.
[/LIST]

From searching internet for people with the same problem, I've tried the following fixes (all from within Windows).  However on all the forums and websites I've read with solutions for this problem, none of them mention or attribute it to problems with Ubuntu Live session or anything.  Most of them blame it on Norton Anti-virus.  This makes me think that my situation is quite unique, and therefore their solutions less likely to work.  I tried them anyway if I thought they weren't going to damage my computer.

[LIST]
[*]One was to reset the TCP/IP by entering the command " netsh int ip reset c:\resetlog.txt " and rebooting. This seemed to work - I had activity on my browsers for about 30 seconds (although very slow loading pages) but then it went back to nothing.
[/LIST]

[LIST]
[*]I "flushed the DNS".   I entered the command "ipconfig/flushdns" and rebooted.  Still had the wireless problem.
[/LIST]

[LIST]
[*]I reset winsock (no idea what that is, just going on the advice of forums...) by entering commands “netsh winsock reset catalog” and “netsh int ip reset reset.log hit” and re-booted.  The first time I did that, I had browser connection for about 1 minute, then it went back to not working.  I tried it again, and this time I didn't even get the 1 minute, it just didn't work at all.
[/LIST]

[LIST]
[*]Downloaded Norton Removal Tool (I've never had Norton – my computer came pre-installed with McAfee, which I never used, and it currently uses Bullguard – however, I read on a forum that this solution worked for someone even though they had never had Norton either)... and ran it.  After I re-booted, didn't fix the problem.  In fact seemed to be worse, because there was no internet activity at all – utorrent, Skype not connecting and network manager saying that there was no internet connection.   I reset winsock after this and back to square one (i.e. Internet connection but browsers won't work).
[/LIST]

[LIST]
[*]Turned off all security software, including Windows Firewall, but no fix.
[/LIST]

[LIST]
[*]I have tried various settings in internet options, in adapter settings, but nothing has worked.  I was careful to put all settings back to original.
[/LIST]

[LIST]
[*]I have uninstalled and re-installed the wireless drivers on my computer, but no joy.
[/LIST]

[LIST]
[*]I have just run a full scan with Malawarebytes.  It didn't find anything.  However I'd be amazed if this was down to malware due to the timing of it.  The problem began immediately after using the Ubuntu Live USB, and I had had problems with Wireless within the live session.
[/LIST]

As I have attempted all these fixes, etc., the network manager sometimes says connected to the internet (and other internet-based apps work) but browsers don't, and sometimes it says there is no internet connection, and those other apps don't work also.  At the minute, I have no internet connection at all.

I didn't have system restore set up, so I have no restore points to go back to....

I have tried to attach the diagnostic reports that the windows network troubleshooter created.  However this forum thing won't let me upload them, saying that they are invalid files..?

My computer is a Lenovo IdeaPad Z570, with Core i5-2410M, 6Gb RAM, NVIDIA GT520M Optimus graphics, Broadcom 802.11n wireless adapter, running Windows 7 64-bit.  The wireless router is Netgear WNR2200.

If anyone has any ideas, please let me know.  I just think that somehow the Ubuntu live session, messing around with wireless, somehow has knocked out the way my compter speaks to the router.  And furthermore, this is causing problems with the router as I try and fix it, as my flatmates mac and my android phone have both lost connectivity afterwards (although both have been successfully restored).  Has anyone else ever had this problem after using an Ubuntu Live USB/CD?  

I have backed up my Windows and should be able to recover it.  However I'd rather not have to  do this. I've a feeling that there is a solution without having to resort to that, as I do have some internet connectivity.

---

### Post by bluexrider on 2011-12-04
sounds like your ISP has a problem

---

