---
title: "Tbird will not start after upgrading to 3.1 using Ubuntuzilla"
date: 2010-07-04
forum: General Help
---

### Post by grr51 on 2010-07-04
Hi,

Today I received a pop-up from Ubuntuzilla indicating that version 3.1 of Thunderbird was available.  So I started Ubuntuzilla and updated Thunderbird to version 3.1, as I did successfully before with previous version updates.  The update proceeded normally, without any error.

However, now Thunderbird does start.  I get the "Starting Thunderbird" in the bottom status bar for a few seconds, then nothing!

I checked with Synaptic Package Manager, but it only indicates version 3.0.4

Any suggestions of how to fix this strange problem.

Thanks,

grr51

---

### Post by nanotube on 2010-07-05
Hi
it is possible you're being bitten by this bug:
[http://ubuntuforums.org/showpost.php?p=9538228&postcount=25](http://ubuntuforums.org/showpost.php?p=9538228&postcount=25)

(especially since it looks like you're using the ubuntuzilla script, rather than the repository, it is likely you have .thunderbird symlinked to .mozilla-thunderbird, which triggers the bug in tb3.1)

---

### Post by grr51 on 2010-07-05
Hi,

Thanks for the reply.

This might have been the case, but I managed to fix the problem in a more convoluted way before I had your reply.

I did the following steps:

[LIST=1]
[*]Removed Thunderbird using ubuntuzilla as follows:
ubuntuzilla.py -a remove -p thunderbird
[*]I ended up with Thunderbird 3.0.4, but in Synaptic Package Manager, I was seeing a "Thunderbird-Mozilla-Build" with version 3.0.4 in addition to the straight "Thunderbird" version 3.0.4
[*]So, I decided to remove the "Thunderbird-Mozilla-Build" with version 3.0.4
[*]After that, no more Thunderbird, although Synaptic Package Manager still indicates that Thunderbird 3.0.4 is installed!
[*]I went to the ubuntuzilla site:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)
[*]Added the repository for Jaunty or later
[*]Added package signing key
[*]Install the "Thunderbird-Mozilla-Build" version 3.1
[*]It works now!
[/LIST]
In the future in will no longer use the 'ubuntuzilla' script, since this seems to cause problem.  I will use the repository for now on.

Thanks,

grr51

---

### Post by nanotube on 2010-07-06
glad it worked out :)

---

### Post by kwalker on 2010-07-07
I have been using the ordinary ubuntu repositories.  I just did an update and now I seem to have this same problem.

Synaptic says the version I have is 3.0.5+build2+nobin.  

The bug description refers to an upstream directory which I don't have.  Is this the circular link:

kgw@kgw-desktop:~$ ls -ld ~/.*thunderbird*
lrwxrwxrwx 1 kgw kgw   22 2010-04-22 20:48 /home/kgw/.mozilla-thunderbird -> /home/kgw/.thunderbird
drwx------ 3 kgw kgw 4096 2009-12-08 14:34 /home/kgw/.thunderbird

PS
Interesting, I just asked firefox to send a link forgetting that thunderbird wasn't running and it popped up the usual box to send an email and let me send it.  The main screen of thunderbird still won't start. No idea what to make of that?

---

### Post by nanotube on 2010-07-07
well, 'ordinary ubuntu repositories' version probably looks for the profile in ~/.mozilla-thunderbird
which you have as a link to just ~/.thunderbird

if you're being affected by the bug... try un-symlinking that, and instead place your profile directly into a ~/.mozilla-thunderbird directory...

EDIT: ah, ignore that, i see more discussion has taken place on [http://ubuntuforums.org/showthread.php?t=1525651](http://ubuntuforums.org/showthread.php?t=1525651)

---

