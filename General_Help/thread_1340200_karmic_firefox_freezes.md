---
title: "karmic firefox freezes"
date: 2009-11-28
forum: General Help
---

### Post by bodhidharma on 2009-11-28
Folks,

Does anyone have this unpleasantness -- I just upgraded to karmic
koala (and don't like the new login very much!)... but now Firefox
frequently just freezes in the middle of something... seems to
be I/O related, since it always stops while the bottom window
frame status line indicates "waiting for data from www.google-analytics.com"
(or other sites).

Anyone else have this problem?  Anyone have a solution?  ...other
than switching to Opera... which I am sorely tempted to do since
Firefox is basically unusable...

Thanks in advance!

---

### Post by QLee on 2009-11-28
[QUOTE=bodhidharma]Does anyone have this unpleasantness -- I just upgraded to karmic
koala (and don't like the new login very much!)... but now Firefox
frequently just freezes in the middle of something... seems to
be I/O related, since it always stops while the bottom window
frame status line indicates "waiting for data from www.google-analytics.com"
(or other sites).

Anyone else have this problem?  Anyone have a solution?  ...other
than switching to Opera... which I am sorely tempted to do since
Firefox is basically unusable...[/QUOTE]
What you have detailed indicates that firefox is waiting for information from the site. Can you see any leds on your gateway/router or modem to see if there is any traffic at the time? If your bandwidth is limited or the site is slow to respond, switching to another browser is not going to help. Are you on a LAN where other systems might be using some of your bandwidth? ...or are you running any bandwidth intensive applications , like a p2p app or downloading something?

---

### Post by bodhidharma on 2009-11-28
Thanks for thinking about it QLee....

Typically, the netspeed applet shows OB/s up and down (and it is
usually at least approximately accurate).  I'm on DSL at home,
and I think the giveaway on this issue is that it never happened
before I upgraded to karmic koala (well, of course, sometimes
Firefox would slow way down for some slow internet site, but
this thing of completely freezing about once every fifteen minutes
of surfing is completely new), and now it happens so often.  I really
think there must be some issue with karmic...  if no one else has
had this, maybe it is some quirk of my software setup, if other
have had it, maybe it is more of an issue.

---

### Post by 23dornot23d on 2009-11-28
I have just had it happen to me twice tonight ..... but never before ........

but it was after I had two updated addons on firefox ......

and not sure what they were ...... firebug and cooliris I think .....

have just swapped desktops to XFCE and disabled greasemonkey

while I try to work out what is going on .....

but it may be a job for tomorrow as its 3:37 am here now .....

Am running on Karmic and have been running ok all day .......

The only other thing I was using was Facebook ...... on chat

It could be a memory thing with me ..... as that is the only time I have problems

when I run out ...... very strange for it to freeze completely though ........

---

### Post by pbhill on 2009-11-28
I've been having Firefox trouble for a few days now. As I was again attempting to use my favorite browser, it froze once again and I could see the memory usage slowly climbing to over 60%. The CPU usage was 128% (dual core). Nothing else running except System Monitor. Then I got this error message. Can anyone decode it for me? I have had to switch to Opera out of necessity. Not a bad browser...

---

### Post by claracc on 2009-11-29
I think it can be a problem with database.

I recommend you this thread from lovinglinux : [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567), go to the first page and follow the advise for database optimization.

I had a similar problem which has dissappeared since clean firefox database of junk.

I hope it can help

---

### Post by pbhill on 2009-11-29
> **claracc said:**
> I think it can be a problem with database.

I recommend you this thread from lovinglinux : [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567), go to the first page and follow the advise for database optimization.

I had a similar problem which has dissappeared since clean firefox database of junk.

I hope it can help

Thank You claracc, I will work on this when I get a free hour or two!
This morning I uninstalled Firefox and reinstalled from the repositories, but it did not help. I now seem to be having similar troubles outside of Firefox. Maybe it's a Karmic issue not just Firefox...

---

### Post by hb8 on 2009-12-09
I've solved the same problem by clearing my profile:
[html]mv ~/.mozilla ~/.mozilla-01[/html]Probably an issue with one of the addons (DownloadHelper was giving an error message).

---

### Post by bodhidharma on 2009-12-09
Thanks for that suggestions, hb8, I'll try it.

The previous idea of clearing out the database seems to help
instances of the problem but not prevent it in the future.
That is, I still have constant freezing, and when I kill
firefox and restart, usually it is in a totally messed up
state; then, "clearing the database" helps restore to (temporary!)
usability.

Often the recurring problem has to do with sound, I wonder if
that is a hint....

I'll post separately about the whole set of related karmic
woes.

Thanks to everyone who has posted on this thread.

---

### Post by pbhill on 2009-12-09
I solved most of my problems by going back to Jaunty 9.04. Karmic was just too buggy... Maybe I'll try it in VirtualBox in the future to see if it's cleaned up any.

---

### Post by bodhidharma on 2009-12-09
that's probably a good idea.

is there any easy way to roll back to jaunty?

---

### Post by pbhill on 2009-12-09
> **bodhidharma said:**
> that's probably a good idea.

is there any easy way to roll back to jaunty?

Not that I know of... I reinstalled, formatting my root partition but leaving my home partition intact.

---

### Post by emaydubya on 2009-12-14
I had this problem but now it's FIXED!

I read somewhere else:
Turn OFF : Edit menu > Preferences > Security >
Block reported Attack Site
Block reported Web Forgeries



Something has gone wrong with way it works, Firefox checks the lists and that's where it hangs, I can't remember the details and can't find the link again but OBVIOUSLY you may have to be more careful.
If you MUST search around pron, warez or other sus sites, use another browser.

---

### Post by bodhidharma on 2009-12-14
Thanks, I'll try that!

---

### Post by jwburnside on 2009-12-17
Firefox crashes for me almost every time while visiting resource intensive sites when I also have XP running in VirtualBox. I have my memory split up about 30/70 out of 3.5 GB (so I can run CS4). When I turn off VB, no more Firefox freeze.

JW

---

### Post by tom3k493 on 2009-12-18
Hi i have the same problem, -firefox hangs in karmic.. So i decided to switch to opera but im still having the same problem every so often :(

---

### Post by GeorgeOfTheBush on 2010-03-14
Any SOLUTION yet to this problem! 

Me too bitten by the same bug - "FREQUENT FREEZES".

I dont think its a browser issue as the problem is seen while using Firefox as well as Opera. I felt that Jaunty was better. The number of times it froze were comparitively less, but the problem still remains.

Hasn't anyone been able to find out the ROOT CAUSE yet?

---

### Post by seiyachan on 2010-06-10
Try this solution:

[http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/]("http://tombuntu.com/index.php/2008/05/07/firefox-3-excessive-disk-io-and-freezing/")

---

