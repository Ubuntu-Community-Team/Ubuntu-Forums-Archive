---
title: "troubleshoot Flash?"
date: 2012-02-11
forum: General Help
---

### Post by watgrad on 2012-02-11
Hi - 
I was wondering how to troubleshoot flash problems.  Most websites work well with my ubuntu, flash 11, chrome or firefox setup.  

However, some video sites won't play streamed flash content on ubuntu machines.  (I have three different computers in my house set up with 11.10 - none of them can place certain sites - like the streamed video content from local tv stations [www.citytv.com](www.citytv.com)).  If I boot into the windows side of the same machines, I can play the streamed flash videos no problem - so I don't think this is a problem with my network.

I was wondering if there is some way for me to find out what the problem is - error logs, something else...?

---

### Post by wolfen69 on 2012-02-11
CityTV flash videos won't play for me either. (all other flash sites are fine though) It could be that there is something else going on behind the scenes that won't allow linux users to view content.

---

### Post by Námo Mandos on 2012-05-30
Hi.

Bumping this thread.  Does anyone know why citytv.com videos won't play on Linux?  CTV and other streaming video sites do.

---

### Post by tich on 2012-12-14
bump, again.

---

### Post by gedakc on 2013-01-09
**TITLE:**
Streaming City TV shows not working with Firefox on Linux

**PROBLEM:**
When trying to stream City TV shows, the advertisements display
properly, but only a blank (black) screen is displayed for the actual
TV show.

Note:  City TV is a Canadian television station that limits web site
viewing to IP addresses in Canada.


**ROOT CAUSE:**
The reason this occurs is because the Flash Player fails to properly
load the Adobe protected content module.  Since City TV uses
Brightcove.com to stream TV shows, and since these use Adobe Digital
Rights Management, the TV shows will only display when the Adobe DRM
content protection module is working properly.


**SOLUTION:**
On Linux the Flash Player requires the Hardware Abstraction Layer (HAL) to
be able to properly load the Adobe protected content module.

The fix to the problem requires the installation of HAL and the
directory ~/.adobe/Flash_Player/APSPrivateData2 to be removed.

The steps to fix this problem on Debian/Ubuntu are as follows:

**1) ** Open a terminal window

**2)**  Remove the broken protected content module directory with the
    following command:

    > rm -rf ~/.adobe/Flash_Player/APSPrivateData2

**3)**  Install HAL with the following command:

    > sudo apt-get install hal

    NOTE:  To install HAL requires root privilege.  Hence the need to
           prefix the command with "sudo" to request root privileges.

Now try to play TV shows from the City TV web site in your browser.
These shows should now display properly.

If you still experience difficulty you might need to upgrade to a more
recent version of the Adobe Flash Player.  To do this try the
following command in a terminal window:

    > sudo apt-get install --reinstall flashplugin-installer

You should now be able to watch City TV shows from Linux in Canada. :-)


**BACKGROUND INFORMATION:**
Starting with Ubuntu 11.04 and higher (e.g., Ubuntu 11.10, 12.04,
12.10), HAL is no longer installed by default.  As such fresh installs
of these distributions will fail to play TV shows from City TV.

For me, diagnosing this City TV streaming problem was a drawn out and
complicated process.  While diagnosing the problem I found information
in the following links to be valuable:


***DEBUGGINGS LINKS:***
Brightcove Video Playback Troubleshooting
[http://support.brightcove.com/en/video-cloud/docs/troubleshooting-why-a-video-wont-play](http://support.brightcove.com/en/video-cloud/docs/troubleshooting-why-a-video-wont-play)

Brightcove Debugger
[https://sadmin.brightcove.com/viewer/BrightcoveDebugger.html](https://sadmin.brightcove.com/viewer/BrightcoveDebugger.html)

    In the debugger, the relevant two lines that led me to the root cause
    were:

       Handling DRM Metadata
       Error: Error #3344 [3344] dispatched

Adobe Community: Unable to install the adobe protected content module
[http://forums.adobe.com/message/4893329](http://forums.adobe.com/message/4893329)

Adobe Community: Flash access support on linux (ubuntu)
[http://forums.adobe.com/message/4797322](http://forums.adobe.com/message/4797322)


***REPORTS OF PROBLEM LINKS:***
troubleshoot Flash?
[http://ubuntuforums.org/showthread.php?t=1923986](http://ubuntuforums.org/showthread.php?t=1923986)

[#BOXEE-11347] citytv - black screen after commercials
[http://jira.boxee.tv/browse/BOXEE-11347](http://jira.boxee.tv/browse/BOXEE-11347)

[Extreme] Streaming CityTV on Rogers
[https://secure.dslreports.com/forum/r26380071-Extreme-Streaming-CityTV-on-Rogers](https://secure.dslreports.com/forum/r26380071-Extreme-Streaming-CityTV-on-Rogers)

Ads play, content does not
[http://forums.boxee.tv/showthread.php?t=43653](http://forums.boxee.tv/showthread.php?t=43653)

CITYTV won't work on Boxee Box?
[http://forums.boxee.tv/showthread.php?t=44349](http://forums.boxee.tv/showthread.php?t=44349)

[Cable] Citytv streaming?
[https://secure.dslreports.com/forum/r27127225-Cable-Citytv-streaming-](https://secure.dslreports.com/forum/r27127225-Cable-Citytv-streaming-)

CityTV not working
[http://forums.plexapp.com/index.php/topic/40703-citytv-not-working/](http://forums.plexapp.com/index.php/topic/40703-citytv-not-working/)

Streaming **City TV** shows not working with Firefox on Linux
[http://gedakc.users.sourceforge.net/display-doc.php?name=streaming-city-tv-shows](http://gedakc.users.sourceforge.net/display-doc.php?name=streaming-city-tv-shows)

Streaming **CTV** shows not working with Firefox on Linux
[http://gedakc.users.sourceforge.net/display-doc.php?name=streaming-ctv-shows](http://gedakc.users.sourceforge.net/display-doc.php?name=streaming-ctv-shows)

---

### Post by watgrad on 2013-03-10
Thanks for this - at the time I switched the offending PC to joli OS and flash worked.
I've reinstalled Ubuntu 12.10 and your fix solved the problem!
Thanks again for your help.

---

