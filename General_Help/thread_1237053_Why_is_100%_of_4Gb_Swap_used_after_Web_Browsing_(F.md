---
title: "Why is 100% of 4Gb Swap used after Web Browsing (Furious Disk Activity, System Halts)"
date: 2009-08-10
forum: General Help
---

### Post by OzzyFrank on 2009-08-10
OK, I noticed this a little while back, but diregarded it as one of those days (a few times). But now after testing this and that, I can say I definitely have something whacky happening with the Swap use after browsing a bunch of web pages, or more correctly doing lots of right-click saving of stuff.

Basically, when I have the free time to do some searching for clipart or royalty-free photos, etc, I like to spend as much of that constructively. Right-clicking and saving hundreds of pics, or saving the target if clicking a thumbnail, was never an issue (the only issue would be bandwidth if I had stuff downloading in the background). But now, once I get past about 150-300 (which is easy to do in a fairly short time if you're a quick draw on the right-click!), I start to notice an increase in hard drive activity, then after a bit more surfing/downloading/saving things like dialog boxes will not appear instantly, then it eventually gets to the point the mouse will barely move (and only after many seconds of pause) and hard drive activity is noticeably furious and without break.

After finally managing to get a terminal up and starting **top** one time, I could see swap use was at 100%, which I've never seen before (even with things like video conversion, etc). I mean, I rarely get anything chewing up my 4Gb of RAM let alone use the swap past 10%. Once the system gets to the point nothing is happening but over the top disk activity, it can be like that for over 2 hours before it stops and I can use other programs. I mean, what on earth could all that activity be when all I am doing is opening a bunch of pages and saving some files?? (Seriously, it's worse than doing a defrag while backing up your hard drive at the same time, hehe!)

Even when it's still at the point that the mouse cursor can move and things happen after a few minutes, I cannot open even things like the text editor, as all I get is:

[B]Could not launch application
Failed to fork (Cannot allocate memory)[/B]

Now, I have a Quad Core with 4Gb of RAM, not a 1st model Pentium with 4Mb RAM and running Internet Explorer, so things like this shouldn't be happening. And of course, if i go into Windows, it doesn't. So something has changed in the past few months, which I suspect was after one update or another.

And I've also ruled out the browser, as it **happens with either Opera or Firefox**. One time I managed to get System Monitor up (after half an hour) to see what was using the CPU(s), and a Wine logger was using 100% (Mailwasher Pro had crashed), but I've ruled that out too, since it happens without any Windows programs loaded. I've even tried disabling the swap just to see what happens, and of course it happens all over again, just a lot quicker (and I'm already used to furious disk activity and the system hanging from not having your swap activated).

So basically, it _is_ the web browsing and saving a couple hundred pics that is for some reason causing this. If someone can explain why downloading a few dozen pics each just a few Kb can fill up a 4Gb swap within an hour and keep it at overflowing, I'd appreciate it. Of course, if you have any suggestions on how to fix this, I'd be very happy. Cheers.

---

### Post by Mister.Vash on 2009-08-11
Sounds like something may be eating all your memory.  Try starting system monitor before you do anything else- you'll probably have to go into the preferences and add the resident memory columns and the Virtual Memory columns, set it to sort by either, leave it up in the background, and see what starts taking up the memory.  It could be something like nautilus taking more and more cpu while it does thumbnails or something - but the best bet is to be able to try and find out what starts to hog your resources, and then figure out what the app is doing.

---

### Post by JohnLau on 2009-08-11
According to top, can you see any process eating up your memory?

---

### Post by lavinog on 2009-08-11
how are you saving your pics? are you using a plugin to download them?
Are you viewing them after download?

Something is not freeing memory.

Does it happen if you disable all plugins in firefox?

Do you manage the pictures with nautilus or any other program?

---

### Post by OzzyFrank on 2009-08-11
Hi. I'll try an answer all your questions at once, as well as add new info.

With **top**, I mainly just used that to see what was happening with the swap. Watching all the rest bouncing around beneath that bit can get confusing without another coffee, so it was good to get the info about the extra columns in System Monitor. I never actually looked in the Preferences, though I'm the sort who usually hunts down all those cool features disabled by default in programs new to me (though this isn't new to me - I just hadn't thought to look for any other features like that).

Now, I thought I had also already eliminated Nautilus's thumbnailing, but did it again just to be sure. This time I had no windows open at all, let alone the one to the download folder. So when it happened again I managed to see some relevent info in the two new columns in System Monitor, being that Opera (web browser) was using 2.9 Gb of Resident Memory, and had taken up a whopping 7.7 Gb of Virtual Memory!

Now, I usually have 10-15 tabs open with Opera each time, and until recently opening another 10 or so on top of that and madly right-clicking and saving/downloading did nothing but maybe affect bandwidth. I mean, web browsing has up until now not been much of a drain on memory whatsoever (on an older PC running Windows and IE, that was another story, but in Ubuntu all has been fine). OK, I've actually had some issues with Opera, it has had bugs, but I can't single it out here since this has happened with Firefox too. The first thing I assumed was it was another Opera issue, so started using Firefox for the task... and it ended up happening there too, and that was without any other tabs open but a few image galleries and font sites.

Anyway, after force quitting Opera and waiting a few minutes before it gave me my system back, I restarted it and the memory usage (with a whole bunch of tabs open from last time) is 250Mb Resident and 680Mb Virtual. I'm sure that would be less if I had less tabs open, but as I said, in the past it wasn't an issue, and even in Firefox with only a few tabs open it will eventually get to the same meltdown point where every right-click and mouse movement adds to the load (imagine 15 seconds of furious disk activity every time you right-click before the menu comes up).

So, while the size of things downloaded shouldn't affect memory, and everything downloaded is quite small anyway, and while the pages I go to only weigh in at the Kbs, rarely even in the Mbs, for some reason my web browsing in Ubuntu is actually taking around 11Gb in combined resident/virtual memory!! Is there any way to fix this or get around this? Surely I don't need in the vicinity of 10Gb to surf some frakking web pages! What has changed in Ubuntu that this could come about with either web browser? Is this a known bug that will be addressed?

Anyway, if you can shed any light on this, it would be appreciated. Oh, and no, did not have Firefox extensions disabled, but don't have many of those anyway, and they've never been a problem. And in case you're wondering why I prefer Opera, I actually use Firefox quite a bit too, but with Opera not only have I come to love the Wand password management feature, and the Speed Dial page, I depend on its ability to save web pages complete with images (all in the one file) in the MHT "archive" format that Internet Explorer has and Firefox hasn't. Thanks.

---

### Post by OzzyFrank on 2009-08-11
I also should add, just in case it makes any difference, that this doesn't seem to happen when just opening a bunch of pages over and over - it really seems to be tied into how many times I right-click and either save what is there in front of me or choose to download the target of the thumbnail or font link or whatever. When I do some media hunting and saving/downloading, I may sometimes have over 10 extra tabs open at any given time, though it is usually more like 5. But when I am madly Goggling some info, I will have usually more than 10 open in the background, and when I've looked through those, I'll keep doing the same for hours without this memory disaster happening.

EDIT: Some more info, being that with the very first right-click and save-as, both virtual and resident memory went up by 40Mb, and on the 2nd resident went up another 15, while virtual climbed another 65Mb!!! You can see where this is going, hehe. Soon it has my RAM and wants double the swap I have, hahaha!

I just downloaded 15 pics and my virtual memory usage is now 912Mb and resident has climbed to 471Mb. Something is definitely wrong with this picture, methinks!

---

### Post by lavinog on 2009-08-11
where are you saving the images to?

> did not have Firefox extensions disabled, but don't have many of those anyway, and they've never been a problem.
whenever there is an update to firefox, any extension can become incompatible with the new version, and can have this type of behaviour.

The problem could be that the browsers are not flushing out old pages. Normally they do this to improve render speeds.
You might be pushing limits that have not been tested in this way.

---

### Post by Tuvok41 on 2009-08-13
I am having somewhat the same problem I have 4 programs using each around 2.6 GB of virtual memory:

[LIST=1]
[*]services.exe
[*]winedevice.exe
[*]winewrapper.exe
[*]uTorrent.exe
[/LIST]

When I restart uTorrent it fixes it, but it comes back once I launch uTorrent again, and the Memory colon will grow from 80MB at about 100MB for every GB uploaded, it is constant so if I upload 10GB the memory used will show 1.0Gb or a little more and if i ever let it go beyond 1.4GB uTorrent becomes unresponsive and ends up crashing.
I also use FF and I do download some files from Megauploads, and I have many tabs open as well but I find it hard to believe FF would make uTorrent mis-managed the memory, no expert so it is only my opinion based on logic.
BTW uTorrent is running through CrossOverLinux Pro and it has been behaving this way since I upgraded to the new release of COLinux Pro.
How can I fix this problem?

---

### Post by lavinog on 2009-08-13
> **Tuvok41 said:**
> 
BTW uTorrent is running through CrossOverLinux Pro and it has been behaving this way since I upgraded to the new release of COLinux Pro.
How can I fix this problem?

It looks like you should address this issue to uTorrent, and CrossOverLinux.
The problem is most likely a bug, and the only thing you can do is report the bug to the appropriate developers.

---

### Post by Tuvok41 on 2009-08-14
I forgot to mention I did post on the CrossOverLinux about it, and after I posted here I received this email from them, I am sharing this as it may be doing the same thing for anyone who updated to the new release of CrossOverLinux recently, seems it is not due to uTorrent at all :

> 
Hi Rxxxx,
 
We just noticed your post in the forums regarding your memory leak issue.  I apologize that we're not always able to respond to forum posts - please note that the ticket system is the only "official" support system.
 
Anyway, this problem with memory leaking seemingly resembles a regression bug that crept into Crossover 8.0, whereby IE6, accessing https (secure) websites, would "run away" with CPU and and memory, eventually freezing a user's computer.  One of our devs has just finished a patch which should fix this issue.
 
We'd like to see if you're suffering from this bug, as well.  The upcoming "nightly builds" of Crossover will contain this patch (i.e. those available tomorrow, 8/14/09).  To download a "nightly build", login to your account and head to the Nightly Build Downloads section in the My Account menu.  You'll want the 20091814 builds, either .deb or .sh (depending on how your normally install).  Please remove your current version of Crossover, first ($ sudo ~/cxoffice/bin/cxuninstall, choose to keep your bottles when prompted), and then install the nightly and try running uTorrent, checking to see if the memory leak is still present.  You *may* need to reinstall utorrent with the nightly, but first try with your pre-existing bottle.
 
Please let me know if this build has any affect on the error you're seeing.
 
Best regards,
Jack


---

### Post by lavinog on 2009-08-14
Back to the OP:
Are the pictures that you are saving very large?
Can you reproduce this on another computer?

---

