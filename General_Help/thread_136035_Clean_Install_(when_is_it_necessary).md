---
title: "Clean Install (when is it necessary?)"
date: 2006-02-25
forum: General Help
---

### Post by melat0nin on 2006-02-25
Hi all,

I've been running Ubuntu for a couple of weeks now, but last night I ran into a seemingly grave problem ([http://www.ubuntuforums.org/showpost.php?p=768130&postcount=174](http://www.ubuntuforums.org/showpost.php?p=768130&postcount=174)) and it's got me wondering how easy it is to reinstall, and whether there is any need.

I remember reading a post on this forum by someone who said that one of the beauties of linux is that you almost never have to re-install.  I'm intrigued by that statement.

Since I've installed Ubuntu, I've also installed all manner of packages and at the moment I'm not exactly sure what state my installation is in (notwithstanding the problem referred to above).  FOr instance, I tried to install Amarok but the install never finished, so I don't know how much of the KDE stuff that was downloaded is floating about my Ubuntu cluttering it up, or worse.

One of the fundamentals that I'm yet to get my head around with Linux is how to be 'aware' of the condition of your system, when there are so many packages and dependencies and settings etc co-existing.

So, that said, how easy is a re-install and is it ever necessary except in the most grave cases?  Does Ubuntu 'degrade' over time in the same way that Windows does?  Given my problem above, is it fixable or should I reinstall?

Thanks for your help!

---

### Post by narnian99 on 2006-02-25
Having used Linux for over 13 years now (and still using WIndows quite) a bit, I have had much less need to reinstall Linux afresh. I have updated Linux systems through various generations many times and not reached the same of "wading thorugh molasses" that Windows suffers here.

The Ubuntu/Debian packaging database is quite robust - probably better than Redhat's IMHO.

For your amarok problem you can do things like 

"sudo apt-get check amarok" to check for broken dependencies
"sudo apt-get remove amarok" to remove it
"sudo apt-get install amarok" to try reinstalling it

you can even try things like :-
 "sudo apt-get -s remove kde" which will simulate (without doing anything dangerous) removing kde. You would then see what packages would be removed (and of course are dependant on kde)

There is also a "-f" option which will fix broken dependencies. 

Basically I wouldn't fret too much - a lot of thought has gone into the Ubuntu packaging system - precisely to make it very robust

---

### Post by z_diver on 2006-02-25
On Windows reinstallation becomes necessary if the registry gets big and bloated or corrupted.  This happens little by little when installing and removing programs.  The older and more heavily used the system, the more likely the need becomes.  Other reasons are when protected files (that the adminstrator cannot even change) get corrupted.

Linux doesn't have a registry so that takes care of most of the reasons a user would want to reinstall(in windows).  Second, the root user(or sudo) can update any file on the system!  So that narrows it down even further.

That whittles down the reinstalls to 10% of what windows users are used to but there are still a couple of reasons (some easily avoidable) for reinstall.

a) running out of room on / partition
b) permissions issues(don't use 'sudo chmod with wildcard' to avoid this)
c) corrupt file system(but that's possible on any OS)
d) user wants to upgrade to a whole new system(more likely than the others unless you are running a server.)
You can certainly upgrade linux without reinstalling but since you are probably upgrading most of the programs on the system at the same time(unlike in Windows) your old program settings may be useless in the new desktop environment.

---

### Post by melat0nin on 2006-02-26
Okay thanks for your replies.  If (and when) I decide to upgrade to Dapper Drake, would a re-install make more sense than an upgrade?  I've spent time customising Breezy, so I don't really want to go through all that again.  At the same time I want all the benefits of the new OS.

---

### Post by ronmarley1 on 2006-02-26
Hi melat0nin,
Here's how things worked for me.  I first installed Hoary around October-ish (I got the disk at a LinuxFest).  This was my first experience with Ubuntu and Linux.  I bonked around with that for about a month and then did an upgrade to Hoary (without a reformat).  At some point along the way, I discovered the difference between the EXT2 and EXT3 files systems (I originally formatted as EXT2, not knowing the difference) and decided that I should make that change also.  So, after about 3 months of installing/uninstalling/reinstalling apps. (as a noob, I eventually discovered I had installed OpenOffice.org twice, in two different places!), learning the command line, changing settings back and forth, I realized that a fresh install might clean up a bunch of "junk" I had accumulated.  So, I reformatted as EXT3, reloaded Breezy, installed all the stuff I really wanted/needed and my laptop runs smoother and feels more snappy.  In hindsight, I should have loaded Ubuntu on one of my old classroom PCs (I teach high school) and played with that before I loaded it on my laptop.  
Good luck!
Sorry for the long post, I just had a cappuccino.

---

### Post by melat0nin on 2006-02-28
So how do you know when it's necessary, in the same way that with Windows you can 'feel' it (lots of random registry entries, lots of folders you can't remember being there, random settings, crap files in the windows folder etc., and of course a speed reduction).

Because Linux doesn't have an equivalent of the Add/Remove Programs applet, it seems to me to be difficult to really have a complete understanding of what state your machine is in (of course I'm open to correction on that.  I say that as a newbie.  And I also know that the Add/Remove programs applet doesn't give a Windows user a complete picture of the state of their machine, by a long way).

Cheers guys!

---

### Post by queenorych on 2006-02-28
If you only install applications/drivers/etc. using the package manager it is pretty much impossible to bonk your system.  If you feel you bonked your system, you can dump your package list using dpkg, and reinstall those same packages in a new install.

Though if you say installed nvidia drivers using the nvidia installation, you're asking for trouble, as this overwrites necissary files.

Installed programs only in your user directory should be ok.

---

### Post by ronmarley1 on 2006-02-28
[QUOTE=melat0nin]So how do you know when it's necessary, in the same way that with Windows you can 'feel' it (lots of random registry entries, lots of folders you can't remember being there, random settings, crap files in the windows folder etc., and of course a speed reduction).

Hi melat0nin,
I'm not sure if I've used Linux long enough to be able to "feel" something similar to what I call "Winrot" (I didn't invent that term).  Maybe some of the longer uses could share their experiences?  But, I can tell you that after I reformatted and reinstalled Breezy, things seemed quicker.  However, I may have deluded myself into thinking things were quciker.  Sorry for the non-answer.

---

