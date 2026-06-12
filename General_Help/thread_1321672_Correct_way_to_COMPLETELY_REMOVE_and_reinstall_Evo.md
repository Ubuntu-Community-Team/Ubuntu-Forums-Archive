---
title: "Correct way to COMPLETELY REMOVE and reinstall Evolution ?"
date: 2009-11-10
forum: General Help
---

### Post by ozark_hillbilly on 2009-11-10
I have corrupted data in Evolution SMTP mail accounts area and cannot get help to correct it. So I want to wipe Evolution off and reinstall clean.

Synaptic Package Mgr does not do it! After removal and re-installation my old data is still there along with the request for password on a deleted mail account; this halts Send/Receive function.

I don't want to screw up the gnome -panel area as i see this is possible looking at other threads. Is sudo apt get -remove  evolution the correct way without causing other problems?

I just want a CLEAN copy of Evolution so that I can setup my SMTP mail accounts from scratch.

Ed

---

### Post by Giblet5 on 2009-11-10
Exit evolution.

Open a terminal window and enter: ```
mv .evolution .evolution-corrupt
```

Start evolution.

Ta da.

---

### Post by ozark_hillbilly on 2009-11-10
> **Giblet5 said:**
> Exit evolution.

Open a terminal window and enter: ```
mv .evolution .evolution-corrupt
```

Start evolution.

Ta da.

Giblet,

That's great info as it cleared up my SMTP problem! If I restore settings to get my old email back the corrupted data comes back. Can I restore just my mail folder without everything else?

Tks,

Ed

---

### Post by SirBismuth on 2009-11-10
I also had corrupted data in Evolution before, just complete removed that profile and data, and restored it from a clean backup.  Then it worked like new, just lost a few emails that had been sent/received after the backup, but that was minor.

But, it sounds like your backup is also corrupt.  Sorry, don't know what else to suggest.

B

---

### Post by Giblet5 on 2009-11-10
> **ozark_hillbilly said:**
> Giblet,

That's great info as it cleared up my SMTP problem! If I restore settings to get my old email back the corrupted data comes back. Can I restore just my mail folder without everything else?

Tks,

Ed

Yes you can. This is the best feature of Evolution, IMO.

Thunderbird is ... crankier.

---

### Post by ozark_hillbilly on 2009-11-10
I now have no Desktop after login!!!!!!!!!!! Just a blank orange screen.
Running under Windows 98 for now.

How do you selectively restore just your mail folder under Evolution? I would like to try this if I can get my Desktop back again.

Ed




> **Giblet5 said:**
> Yes you can. This is the best feature of Evolution, IMO.

Thunderbird is ... crankier.

---

