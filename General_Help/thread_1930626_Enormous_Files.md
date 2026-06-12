---
title: "Enormous Files"
date: 2012-02-24
forum: General Help
---

### Post by guthriearmstrong on 2012-02-24
Hey guys, I need a little input on what's going on...

So earlier today, I logged on to my system, and after opening Firefox I got a warning. It said, "disk space low: 300mb left." Or some number like that. I was completely shocked (because my disk is brand new... one of them pesky sudo rm rf's again... but that's another story).

Anyways, I looked deeper into the files to find that it was in the /proc/kcore. The file was 149 terrabytes. I looked up what that was, and calmed down after finding out it was a Virtual Machine, that was normal, and I just ignored it. 149TB is the limit to how big a file can be on a 64x like mine. I removed that folder from my backup list, and I went on with my day.

I woke up just now to write this. I can't get it out of my mind! I have 300mb left, on a brand new computer! Could it be some strange virus that sits in a text file and does absolutely nothing?

~Ubuntu newb

P.S. my /home/.cache/checkbox file is nearly 300gb...

---

### Post by Paqman on 2012-02-24
> **guthriearmstrong said:**
> 
P.S. my /home/.cache/checkbox file is nearly 300gb...

That ain't right. Checkbox is (IIRC) the system testing app, so you can dump that cache if you want. You might want to consider filing a bug before you do though, leaving a 300GB cache file on your system can't be what the devs intended (and if it is they need a slap).

Additionally, run the Disk Usage Analyser as root by hitting Alt-F2 and entering:
```
gksu baobab
```
Look out for things like backups that have been dumped onto your hard drive instead of a remote location (this happens if you're not connected to the remote and you backup solution isn't smart enough to notice this).

Bleachbit is a good tool that you can use to clean out caches, although the kind of space you're lacking is more likely to be something going wrong rather than normal caching.

How big is your drive anyway?

---

### Post by guthriearmstrong on 2012-02-24
I can't even remember after the hard drive wipe.
System Info says it's 300.6 GB though.

Edit: yeah, gksu baobab is what I used to find the /proc/kcore. That's the only insanely large file I could find, and 149 terrabytes is preeeetyyyy large.

Oh, I'm sorry. I understand now. I should ignore proc, and focus on the checkbox. Alright. So, I'll just trash it then?

Haha, thank you! I know have 290 GB more hard drive space :lolflag:
Then again, that's what I would have said when I did "sudo rm -rf", if my computer hadn't started deteriorating...

---

### Post by Paqman on 2012-02-24
> **guthriearmstrong said:**
> 
Oh, I'm sorry. I understand now. I should ignore proc, and focus on the checkbox. Alright. So, I'll just trash it then?

Yep, /proc is kernel stuff, just ignore it. 

> 
Haha, thank you! I know have 290 GB more hard drive space :lolflag:
Then again, that's what I would have said when I did "sudo rm -rf", if my computer hadn't started deteriorating...

No worries. Sounds like Checkbox has been flipping out. Btw, anything in your own folder in /home can be deleted without using sudo, so it won't risk trashing your system (just your personal data!)

---

