---
title: "chromium segmentation fault"
date: 2011-12-07
forum: General Help
---

### Post by Gitanes on 2011-12-07
I'm using Ubuntu 10.4 on a desktop and I'm getting constant crashes from Fire Fox tonight and so I went to my Chromium browser instead.  When I attempted to open it, all I got was an hour glass.  I tried running it from a terminal window and I got "segmentation fault".  Any idea what's going on here?  I saw a lot of old results for "Chromium and segmentation fault" in Google but nothing recent.  My suspicion regarding the FF crashes is that it's related to Adobe Flash of which (I seem to recall) I received a recent update of.

---

### Post by jaimeaux on 2011-12-07
have you attempted to reinstall chromium?

---

### Post by Gitanes on 2011-12-07
> **jaimeaux said:**
> have you attempted to reinstall chromium?

Not yet.  I'm worried about losing information in my browser.

---

### Post by jaimeaux on 2011-12-07
Losing information in it? You shouldn't have to worry about losing any information... especially if you have the google sync option set up. What type of information are you worried about losing?

---

### Post by Gitanes on 2011-12-07
> **jaimeaux said:**
> Losing information in it? You shouldn't have to worry about losing any information... especially if you have the google sync option set up. What type of information are you worried about losing?

webpages that I've visited and the like.  I don't have sync set up that I can recall.  If reinstalling wouldn't wipe out all my settings and history, etc., I'd give it a try.  Perhaps I could save pertinent files, like in FF, that are stored in a profile folder and overwrite the new folder with the old after reinstalling?  Does Chromium have such a folder and where is it located?

---

### Post by jaimeaux on 2011-12-07
If it does have that folder, it should be under your home directory...  probably hidden, so use "ls -a" in your home dir, and look for .google  or .chromium.... anything along the lines of that. Lemme know if this  helps!

---

### Post by nothingspecial on 2011-12-07
~/.config/chromium/ is the one you are looking for.

---

### Post by WorMzy on 2011-12-07
Config files created in a users home directory aren't tracked by the package manager, and are therefore unaffected by program removals/re-installations/purges/updates/etc.

Re-install chromium, and if that doesn't fix it, check your disk's SMART data, it may be beginning to fail.

---

### Post by Gitanes on 2011-12-07
> **WorMzy said:**
> Config files created in a users home directory aren't tracked by the package manager, and are therefore unaffected by program removals/re-installations/purges/updates/etc.

Re-install chromium, and if that doesn't fix it, check your disk's SMART data, it may be beginning to fail.

Didn't work.  When I attempt to run GSmartControl, both the extended and short test stop with an error message (I know I've run this program successfully on this computer in the past):

Error 168 occurred at disk power-on lifetime: 23088 hours (962 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 20 17 29 60 e0  Error: UNC 32 sectors at LBA = 0x00602917 = 6301975

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 17 29 60 e0 00      03:12:29.688  READ DMA
  ec 00 00 00 00 00 a0 00      03:12:29.688  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      03:12:29.688  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      03:12:29.688  IDENTIFY DEVICE

Incidentally, I just installed Google Chrome and it has the exact same problem.

---

### Post by WorMzy on 2011-12-07
It's probably not a good sign when you start getting errors from self-tests. I couldn't tell you what the error means though, check the program's man page/web site and see if it can explain what it's trying to tell you.

Does the SMART Attributes List list any fails/high raw values for any error counts?

---

### Post by Gitanes on 2011-12-07
> **WorMzy said:**
> It's probably not a good sign when you start getting errors from self-tests. I couldn't tell you what the error means though, check the program's man page/web site and see if it can explain what it's trying to tell you.

Does the SMART Attributes List list any fails/high raw values for any error counts?

It does indeed:

197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       2

I'll start taking stuff of this HDD.  If I get a new disk or computer and reinstall Ubuntu, do I just need to save my home directory and copy that over to the new install to get all my program settings back?

I still wonder though if the problem with the Chromes are coincidental or related to this?  What made you think that the error "segmentation fault" was related to a disk failure?

BTW, am I being helped by a cute kitty?

---

### Post by WorMzy on 2011-12-07
> What made you think that the error "segmentation fault" was related to a disk failure?

It seems to regularly be a common cause, especially with officially packaged applications. If you'd written an application yourself, and were getting a segfault, I'd be less inclined to assume it's because of a disk failure. ;)

> 197 Current_Pending_Sector 0x0012 100 100 000 Old_age Always - 2

That value by itself isn't too much to worry about. What does 196 (Reallocated_Event_Count) and 5 (Reallocated_Sector_Ct) say?

> If I get a new disk or computer and reinstall Ubuntu, do I just need to save my home directory and copy that over to the new install to get all my program settings back?

That will cover all your personal settings. If you've edited any daemon/system config files in /etc, you might want to make a copy of those too. If you've got any websites kicking about in /var/www (I think that's where Ubuntu defaults to), don't forget about those.

> BTW, am I being helped by a cute kitty?
Yes. Yes you are. :)

---

### Post by Gitanes on 2011-12-07
> **WorMzy said:**
> That value by itself isn't too much to worry about. What does 196 (Reallocated_Event_Count) and 5 (Reallocated_Sector_Ct) say?


 5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always

196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always

Thanks for your help.

---

### Post by WorMzy on 2011-12-07
You're missing the last two columns from that output, which are the most important part. :P

If they're both "-" and "0", then there's no need to panic just yet. Try forcing a fsck, then reinstalling chromium, and seeing if the problem persists.

```
sudo touch /forcefsck
sudo shutdown -r now
```

---

### Post by Gitanes on 2011-12-07
> **WorMzy said:**
> You're missing the last two columns from that output, which are the most important part. :P

If they're both "-" and "0", then there's no need to panic just yet. Try forcing a fsck, then reinstalling chromium, and seeing if the problem persists.

```
sudo touch /forcefsck
sudo shutdown -r now
```

That is the case, they're both "-" and "0".  I actually tried that command earlier today and the problem is, I've got a fully encrypted installation and when I restarted, entered my passphrase it just continued to load and didn't do a disk check and I'm under the impression that the encryption setup had something to do with the command not running.  Nevertheless, I get the periodic disk check when I start up sometimes so I don't see why the command didn't work.  I'll try it one more time.

---

### Post by Gitanes on 2011-12-07
I take that all back.  Your command worked.  The earlier command I found online may have been slightly different or something.  Does fsck automatically fix any errors it finds or does that have to be part of the command?

No joy with reinstall of Chromium.

---

### Post by WorMzy on 2011-12-08
I'm not sure how encryption affects fsck. You can't repair a mounted partition with fsck, and you (presumably) can't check the filesystem without it being decrypted.

fsck should automatically fix any small problems with the filesystem automatically; but if there's anything terribly wrong, it will prompt you to decide the best course of action.

I'm not sure what else to tell you. The self-tests suggest that there's a problem, but the SMART data suggests otherwise and the partition seems to be passing the fsck.

I doubt it's the application's fault that it's segfaulting, there'd be a lot more than one topic about it if it was. It may or may not be the harddrive's fault. You could check your RAM with a [memory test]("https://help.ubuntu.com/community/MemoryTest"), but if your RAM was bad, I'd expect to see a lot more than one or two specific applications segfaulting. You could check the cables connecting the harddrive to the motherboard too, but again, if they were loose, I'd expect to see a more widescale problem.

---

