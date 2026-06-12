---
title: "Samba - GAdmin Samba screwed up."
date: 2009-09-26
forum: General Help
---

### Post by Roasted on 2009-09-26
So, I've been checking out other GUI frontends available for Samba. I was using "Samba" (system-config-samba) but I figured I'd check out something with more features, so I fired up gadmin-samba. Right away, I began to have issues. Now, I have permissions issues left and right. Everything was running great for the last 6 months till just now when I ran gadmin-samba.

Well, I have no idea what happened, but here's the scoop.

Samba works. I have 4 users on Samba. 3 of them work. Guess which one doesn't work? Me.

I have deleted my user about 7 times, rebooted, re-added it, tried again, etc. My user just flat out does not work. Period.

When I log in to my share from an XP computer, it just continually asks me for my log in credentials. From my mac, it just says failed.

I added a new user, a completely bogus one and gave that account the same rights as my original account had. Bam. Worked. Perfectly.

So it's obvious it's something with my actual user. What could it be?

---

### Post by Roasted on 2009-09-26
I've tried everything. I've googled everything I've come across and asked several people in IRC. No leads.

Is it possible there's something stuck in between my Linux account and Samba account? If I delete my Linux account, and re-add it, do you think that might solve anything?

If that's the case, would it delete my home directory or ANYTHING by removing/re-adding my Linux account?

---

### Post by Roasted on 2009-09-27
Okay. It's fixed. Here's the scoop...

I had "Samba" (system-config-samba) open from an earlier change and didn't realize it. Then I fired up gadmin to check it out and sure enough it must have tried to edit the smb.conf file while system-config-samba was still tied to it. Anyway, it goofed up my account, while leaving the other accounts okay.

I had no clue how to fix it, so I just uninstalled every trace of samba I found in synaptic with a complete removal. Of course, I backed up the smb.conf from /etc/samba before I did. ;) Then I reinstalled samba, added the smb.conf, but wait! Still didn't work. Ahh yes, I had to assign passwords to the users really quick and bam - I was good to go.

Moral of the story - don't screw around with two GUI control panels that will try to edit 1 configuration file at a time. Bad things happen.

EDIT - Is anybody here a Samba expert? Can anybody tell me exactly what happened when I was using two Samba GUI's to edit that config file? I'm just trying to understand what I did wrong and what happened beyond the "oh dont use two guis to make changes in samba" thing I learned.

---

### Post by swerdna on 2009-09-28
These GUIs are just fancy text editors. They mostly edit the file smb.conf. So you've essentially got smb.conf hung between two text editors. And really, anything can happen if you edit a file with two text editors simultaneously. It is only that and nothing more.

---

