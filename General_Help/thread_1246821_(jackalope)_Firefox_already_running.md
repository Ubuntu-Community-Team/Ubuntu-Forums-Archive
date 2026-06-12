---
title: "(jackalope) Firefox already running"
date: 2009-08-22
forum: General Help
---

### Post by jbeukema on 2009-08-22
So, I'm getting this error now, although firefox doesn't appear in running processes. A few relevant(?) details:

-running jackalope
-sharing profile with Windows XP Media Center

No problems starting Firefox in XP, suggesting no lock files present(?)

Tried:
uninstalling and -reinstalling Firefox in ubuntu

restarting

(both failed)

I tried installing Geck through synoptic for the time being, and i can't find it, so I'm having to post this from inside XP (in, Firefox...)

---

### Post by HiImTye on 2009-08-22
did you try
```
killall firefox
```
in a terminal?

[LIST=1]
[*]accessories
[*]terminal
[/LIST]

---

### Post by jbeukema on 2009-08-22
> **HiImTye said:**
> did you try
```
killall firefox
```
in a terminal?

[LIST=1]
[*]accessories
[*]terminal
[/LIST]

Yes. It said nothing was killed. 

The computer seems confused and i am too

---

### Post by jbeukema on 2009-08-24
am I screwed, then?

killall -firefox and killall -firefox -bin just brings up a list of switches for kill

---

### Post by jbeukema on 2009-08-24
> jtb@jtb-desktop:~$ ps ax | grep firefox
 4998 pts/0    R+     0:00 grep firefox
jtb@jtb-desktop:~$ sudo kill 7998
[sudo] password for jtb: 
kill: No such process
jtb@jtb-desktop:~$ 


and no lock or .parenlock in the profile folder :/

I uninstaklled completely and reinstalled (in Ubuntu) and zstill get the same error

---

### Post by michy99 on 2009-08-24
> **jbeukema said:**
> -sharing profile with Windows XP Media Center

I'm not sure what you mean by this.

---

### Post by jbeukema on 2009-08-24
> **michy99 said:**
> I'm not sure what you mean by this.

I went into the profile manager for firefox and pointed to the folder for my firefox profile in windows so that changes to bookmarks or settings in one are reflected in the other. That was prior, of course, to the uninstallation and re-installation during attempts to get thisd thing working.

---

### Post by P4man on 2009-08-24
> **jbeukema said:**
> am I screwed, then?

killal_l [COLOR="Red"]**-**[/COLOR]f_irefox and killal_l [COLOR="Red"]**-**[/COLOR]fi_refox -bin just brings up a list of switches for kill


No dash there!

sudo killall firefox*

---

### Post by michy99 on 2009-08-24
What error do you get when starting firefox from a terminal?

---

### Post by jbeukema on 2009-08-24
> **P4man said:**
> No dash there!

sudo killall firefox*
jtb@jtb-desktop:~$ sudo killall firefox
[sudo] password for jtb: 
firefox: no process killed

> **michy99 said:**
> What error do you get when starting firefox from a terminal?

What's the command to start a program from the terminal? You're talking to a total noob here

---

### Post by jheaton5 on 2009-08-24
> **P4man said:**
> No dash there!

sudo killall firefox*

P4man is correct.  There should not be a "-" in front of firefox.  If you have installed Firefox 3.5 then ```
killall firefox-3.5
```

---

### Post by jbeukema on 2009-08-24
I think it's 3.1, but I tried the 3.5 too and got the same result

> jtb@jtb-desktop:~$ sudo killall firefox
[sudo] password for jtb: 
firefox: no process killed


---

### Post by michy99 on 2009-08-24
To start firefox from a terminal, enter the command```
firefox
```

---

### Post by P4man on 2009-08-24
> **jbeukema said:**
> jtb@jtb-desktop:~$ sudo killall firefox
[sudo] password for jtb: 
firefox: no process killed

I put a * behind firefox, I should have been more clear. Type in ```
sudo killall firefox
``` then press **tab** to see if there is an "autocomplete" match, like firefox-3.5. You could also just check in "top" if ff is running.

---

### Post by jbeukema on 2009-08-24
> **michy99 said:**
> To start firefox from a terminal, enter the command```
firefox
```

same error

> Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

I don't get it.. if there are no lock files, it's not running, and it's been un- nd reinstalled....

---

### Post by jbeukema on 2009-08-24
> **P4man said:**
> I put a * behind firefox, I should have been more clear. Type in ```
sudo killall firefox
``` then press **tab** to see if there is an "autocomplete" match, like firefox-3.5. You could also just check in "top" if ff is running.

What is 'top'? Is that the system monitor? I don't see it in there

hitting tab just makes the computer beep

---

### Post by michy99 on 2009-08-24
Have you tried re-booting?

---

### Post by jbeukema on 2009-08-24
> **michy99 said:**
> Have you tried re-booting?

several times. I even tried running computor janitor

I can't think of anything short of *ugh* a complete reinstallation :( I nonly use the computer for three programs, really, and Firefox is one of them

thid is really frustrating :(

---

### Post by P4man on 2009-08-24
> **jbeukema said:**
> What is 'top'? Is that the system monitor? I don't see it in there

top is just like system monitor, but it shows all processes by default, unlike gnome system monitor, which only shows your own processes by default.

Anyway, if FF is not running, and there is indeed no lock (which I think is in the profile folder, you sure you looked there?), I guess you'll need to stop sharing profiles, and consider using x-marks to keep your bookmarks and passwords synchronized between installs:

[http://www.xmarks.com/](http://www.xmarks.com/)

---

### Post by jbeukema on 2009-08-24
> **P4man said:**
> 

Anyway, if FF is not running, and there is indeed no lock (which I think is in the profile folder, you sure you looked there?)

I have.


> , I guess you'll need to stop sharing profiles, and consider using x-marks to keep your bookmarks and passwords synchronized between installs:

I can't do that until Firefox is running. Trying to start the profile manager starts firefox and gets us right back to nowhere.:(

---

### Post by P4man on 2009-08-24
> **jbeukema said:**
> Trying to start the profile manager starts firefox and gets us right back to nowhere.:(

Heh, good point. I googled a bit for you, and found this:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)
> 
Check access rights

This problem can also occur if you don't have the rights to edit the files in the profile (or create the lock file in the first place). Please note that this can happen if you try to use a profile from a filesystem mounted with read-only (e.g. a remote Windows share which doesn't have "allow network users to change my files" checked). This can be pretty tricky to diagnose because there is no lock file in the profile, yet the same message appears (profile in use). Incidentally, Linux users may have ~/.thunderbird and/or ~/.mozilla-thunderbird in their home directories if they have had more than one version of Thunderbird installed. 

---

### Post by jbeukema on 2009-08-24
but... it was working at first...


*sigh* I'll go into Windows and check file sharing permissions

---

### Post by P4man on 2009-08-24
> **jbeukema said:**
> 
*sigh* I'll go into Windows and check file sharing permissions

Are you sharing the profile folder over the network, or is it dual boot? Either way, simply check if you have write permissions on the profile folder.

---

### Post by gldearman on 2009-08-24
A quick way to check to see if the problem is within the profile is to launch Firefox with a new profile.

```
firefox -CreateProfile test 
```

If that works, then the problem is somewhere within that shared profile, not with Firefox itself.  So, no amount of uninstalling and reinstalling will help.

But, if that same profile works for Windows, then the profile itself cannot be corrupt.  Therefore, it must be the way Ubuntu accesses the profile.  So, I would start trying to track down the access rights, like P4man said.

---

