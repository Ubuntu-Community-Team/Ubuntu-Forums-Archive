---
title: "Slow response with Apache remotely, fast locally"
date: 2011-07-01
forum: General Help
---

### Post by zbuffered on 2011-07-01
I'm running Ubuntu 10.10 Desktop, 64-bit.

I've had this issue now for about a year; I recently rebuilt the machine and the issue actually persisted across a fresh install.  

On the local machine, requests are fast, but on remote machines (like the Windows machine on my desk here), requests are delayed (Firefox status tab says "Waiting for %hostname%") almost exactly 5 seconds.  It doesn't matter if it's a PHP page or a static HTML page.  Resources like images may be delayed another 5 or so seconds, and usually all the requests come in at once (for example if there are multiple images they'll usually appear at once).  If I request another page right away it will sometimes come up immediately, but if I wait a bit, there will be the delay again.

I've tried adding the DNS name to a hosts file and connecting by IP -- no change.

The web server is under basically no load, I use it for web development and I'm effectively the only person to ever access it.  

I've been getting by by testing on the server rather than on my Windows machine unless I need to look at some IE-specific issue.  It seems like a difficult issue to troubleshoot, so I haven't been interested in messing around with it before now.

Running [FONT="Courier New"][COLOR="DarkGreen"]top[/COLOR][/FONT], I can see that there is effectively no load on the server.

Running [FONT="Courier New"][COLOR="DarkGreen"]tail -f /var/log/apache2/access.log[/COLOR][/FONT], I can see that the requests get added to the log at about the same moment that the resources load on the page.

Googling around for other people having this issue, I came up with this unresolved thread which seems like an identical problem:
[http://ubuntuforums.org/showthread.php?t=1095387](http://ubuntuforums.org/showthread.php?t=1095387)

Accessing and updating files on the machine via Samba causes no delays.

Any suggestions on things to try?

Update: I did a capture on a Windows machine with wireshark, and the GET request happened 5.007846 seconds before the 200 response, and the 200 response is what gets added to the access.log.  It definitely seems like that 5 second number is not an accident.  

Here's a screenshot of the capture: [http://i.imgur.com/2CFfL.gif](http://i.imgur.com/2CFfL.gif) 
The "Time" column is time since capture began, in seconds.

---

### Post by zbuffered on 2011-07-01
I can't believe this but I have resolved my issue.

[http://www.hsuconsulting.com/2011/01/12/apache-and-the-5-second-delay/](http://www.hsuconsulting.com/2011/01/12/apache-and-the-5-second-delay/)

The issue was with my .htaccess file.  I renamed it (so that it wouldn't load) and the page loaded instantly.  I narrowed down the specific rules that, by deleting them, would remove the delays.  The rules were:

#Deny from 110.88.0.0/14
# chinese scrapers with faked UA 050911

Yes, literally two comments were causing the delay.  

.htaccess is a strange beast.

---

### Post by zbuffered on 2011-07-06
Upon having further problems with this issue, I began to remove lines from my .htaccess file again until it was working (waiting 30 seconds between each test because it would load right away if I didn't).  It turns out that the two lines above probably weren't causing the problem at all, but rather lines with comments after the rule like:

Deny from 10.89.214.48/24 # Contact form exploits on 10.89.214.48

So the lesson learned is, put comments in htaccess on their own line!  While the above works in many circumstances, I have had it break things in the past as well.  I started putting comments on their own lines after having some problems awhile back but still had a bunch left over that looked like the above.  After fixing all of those, things are once again working well.

While I now know the cause of the problem, I don't have a clue *why* it causes the five-second delay, or why it works fine for 30ish seconds and then delays by five seconds again.

---

### Post by Habitual on 2011-07-07
"So the lesson learned is, put comments in htaccess on their own line!" - interesting.

I've always used comments # in line on both apache[12] and never had an issue. But that was CentOS also.... curious.

+1 for fixing your own stuff however :D

---

