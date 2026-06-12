---
title: "All Thunderbird windows are tiny and blank"
date: 2010-10-30
forum: General Help
---

### Post by hughh on 2010-10-30
All of sudden, as of yesterday, I can't read any windows that Thunderbird displays.  First of all they are hard to find, because they're a couple of pixels wide and may two dozen pixels tall.  Once I find and enlarge them, they have no content—they're blank.  Everything worked fine until yesterday.  I haven't found any other application misbehaving.

Here's an image of one such window in the foreground, with a terminal window in the background (it's to the right of the *-jsconsole* option in the terminal):

[IMG]http://img.photobucket.com/albums/v280/hughh/screen%20captures/Screenshot-1.png[/IMG]

And here's an image of one such window after I've expanded it:

[IMG]http://img.photobucket.com/albums/v280/hughh/screen%20captures/Screenshot-2.png[/IMG]

I get the same tiny blank window if I start with *-safe-mode*.  The same happens with the *-ProfileManager* option too.  

Also, I found what seems to be [related thread]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/615779?comments=all") on Launchpad. I tried a suggestion there to use 3.1rc2 and I got exactly the same results.  I also posted a [MozillaZine thread]("http://forums.mozillazine.org/viewtopic.php?f=39&t=2022467&p=10073747#p10073747").

Thunderbird is version 3.0.10 and I'm running Ubuntu 10.04 (Lucid Lynx), which I installed a week or so ago.  Yesterday morning I performed a routine security update to Lucid as suggested by Update Manager, which may or may not have had anything to do with this failure.

Needless to say, this makes Thunderbird completely useless to me.  Please help!

---

### Post by ajgreeny on 2010-10-30
For the moment try renaming your /home/user/.thunderbird folder as a backup and then restart thunderbird again.  If you use pop mail protocol, all your emails will be in the old profile folder you have renamed, so don't delete it, just rename it, then you can get all the emails back again if the new profile works.

If that is not successful, I suggest you attempt a purge of thunderbird; don't worry all your folders in /home will still be there, and after purging, reinstall, perhaps with a shutdown in between, just to make sure there is nothing remaining in ram.

---

### Post by pfein on 2010-11-01
The problem seems to be caused by already-running thunderbird processes.  In a terminal, do:

pkill thunderbird

And then restart it.

---

### Post by hughh on 2010-11-03
'pkill thunderbird' solved the problem.  Thanks!

---

