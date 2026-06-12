---
title: "Firefox error &quot;firefox is already running&quot; ALMOST fixed..."
date: 2011-01-07
forum: General Help
---

### Post by martin1205 on 2011-01-07
Hello.

I've experienced the fairly annoying firefox error where it refuses to start the GUI.

If there were no active firefox processes, nothing happened when I started it, but it did "start", meaning that I got the "firefox is already running" when I tried again.

I found a fix to this, which was to delete some or all files in the ~/.mozilla/firefox directory.

I now have 2 different problems. Number one is that the problem keeps reoccurring and I'd like to know what's causing it.

The second problem is that even when I've "fixed" the issue, I still can't run firefox from scripts or click links. I get the "firefox is already running" error instead of a new tab or window. 

Regards,

Martin

---

### Post by sikander3786 on 2011-01-07
Welcome to the forums :-)

Kill any running instances of Firefox.

Applications > Accessories > Terminal:

```
ps axjf | grep firefox
```

Start Firefox again and see if it is fixed (temporarily).

As for what is causing the problem, try starting Firefox in safe mode close it and re-open and see if any plug-ins were causing the problems or it is something else that needs to be addressed.

```
firefox -safe-mode
```

---

### Post by martin1205 on 2011-01-14
Thanks for your help.

Unfortunately, none of the above helped. When I try to start in safe mode, I get a dialogue with a list of things to disable, but after clicking past it, firefox still never starts up.

I'll try to reinstall it for the 4th time now...

Oh and another thing...When I did the "ps axjf | grep firefox"
it did give me a list of processes with firefox somewhere in the name/source, but I couldn't find the corresponding ID's to actually kill them. (I did kill them through top though).

And, after trying to start firefox and then rebooting, I get a popup saying that a process named "firefox.bin" isn't finished. 
So, I'm guessing firefox is "trying" to start up?

---

### Post by wojox on 2011-01-14
Have a look here [Firefox Tutorials]("http://www.webgapps.org/blogs/firefox-tutorials"). Maybe a bad profile.

---

### Post by yamaplos on 2011-01-17
Had the same problem today. 
After rebooting a couple times (that is the advice of the "firefox is already running" message), first I moved to a safe place my .default file where I have all my bookmarks, etc.
- Went to Synaptic, reinstalled Firefox - didn't help, even without retrying to put back my .default.  
- Installed "A Web Browser" (the non-branded Firefox), no dice.
- Followed this thread (using epiphany, since Firefox was out), Terminal ps axjf, didn't work, 
- *finally eliminated everything inside the .mozilla folder (made visible by going to my home folder, View, Show Hidden Files).*

Bingo!
Then I copied back my .default, edited profiles.ini so it points to it, inside firefox folder inside .mozilla, and all is fine - for now.

No idea what caused this - before turning in for the night everything was fine yesterday, and I do not remember installing something new - besides playing with a new video card earlier, which didn't work.

I will reboot now and hope all holds together...

edit a few minutes later:
it still works, yay!

---

### Post by martin1205 on 2011-01-18
I've also isolated the issue to the profile. Not sure what part, but my third reinstallation is working so far. Only thing I haven't done yet is get my bookmarks in order. So, it could be those that caused it.

---

### Post by horstkotte on 2012-03-12
I ran into the same issue today after having installed a second profile for an older firefox instance (3.6) on my ubuntu 10.10. There were two problems:
1. lock file in FF profile
2. created and deleted profile was not cleaned up in profiles.ini

The first issue is easy to resolve by checking you ~/.mozilla/firefox/[profile] folder for lock files and deleting them. But I was still getting the "firefox is already running" error message. I remembered that I had created a second profile but then decided to delete, but not via the profile manager but rather by deleting the directory. That left an artifact behind in profiles.ini. After deleting the profile artifact in the file (delete the lines after the name of your profile that has been removed) firefox started up as expected.

---

### Post by dhel4 on 2012-06-04
Hi everybody,

I have a very similar problem, but I couldn't fix it with your solutions.

I have a shared Firefox profile that is located in a NTFS partition, so that both Ubuntu and Windows 7 have access. 

Everything works just fine except the "already running" problem when launching Firefox in Ubuntu. The funny thing is: once I navigate into the ntfs partition (without even opening any folder), firefox will start. 

I have tried a lot of stuff, including deleting parent.lock. I'm lost at this point. Do you guys have any clue??

---

### Post by Cyanarchy on 2012-06-04
Usually when I get that message I just close the window, wait a few seconds and then it works. When that doesn't work, however, I go to System>Administration>System Monitor, then I select the processes tab, look for one with 'firefox' in its name and end that process, then Firefox works like a charm.

---

### Post by dhel4 on 2012-06-06
thanks for the advice, but that doesn't fix it.. there is no running firefox process. nevertheless it won't start. Clicking on the partition in nautilus and then launch firefox is a workaround, but it's kind of annoying.

---

### Post by zombifier25 on 2012-06-06
```
killall firefox
```
To get rid of all Firefox processes, if any. And then start Firefox is Safe Mode:
```
firefox -safe-mode
```
and see if any addons is causing the malfunctioning.

---

### Post by Marylouise on 2012-07-31
I have been having this same issue. A few minutes ago I closed the Firefox is already running window. I then the tried to open Browser from a different location. Alls well!! The Firefox already running did not open. 

For some unknown reason if I use the icons on the desk top it does it. And if I just the tab on top left above the desktop platform, it works just fine. Can anyone explain this to  me?

---

### Post by rich1842 on 2012-07-31
Sounds as if the desktop shortcut is broken. I would delete it and make a new one (go through the menus to applications - internet - rightclick on firefox and choose 'add to desktop').

---

