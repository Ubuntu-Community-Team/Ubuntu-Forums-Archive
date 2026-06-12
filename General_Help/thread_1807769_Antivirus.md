---
title: "Antivirus"
date: 2011-07-19
forum: General Help
---

### Post by brad1138 on 2011-07-19
I want an antivirus solution to check Windows files I DL (I dual boot) I tried clamav w/clamtk but I couldn't figure out how to update the virus definitions (or get any for that matter).

I want an AV that I can just click on a button (if that) to update and not have to spend hours of searching just to do that.

Aside from that, what is the best AV for Linux.

Thanks,
Brad

---

### Post by srisharan on 2011-07-19
Well you can try avast antivirus for linux.It is supported

---

### Post by howefield on 2011-07-19
Try running clam from the terminal command and go to the Help menu and select Check for Updates.

```
gksudo clamtk
```

PS. (seems to work without using gksudo)

My preference is for Bitdefender. Not sure there is a definitive "best", only likes and preferences. :)

---

### Post by raja.genupula on 2011-07-19
have a look at this
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by ajgreeny on 2011-07-19
Clamav also installs freshclam as a dependency, and it is freshclam that checks and makes sure that the virus signatures are up-to-date automatically, at boot time, if I remember correctly.  You should be fine with what you already have, though I can't comment on efficacy of different applications.

---

### Post by dandnsmith on 2011-07-19
I used to run AVGfree, but haven't checked it's availability for a while (it was redundant in my operating context)

---

### Post by brad1138 on 2011-07-19
> **howefield said:**
> Try running clam from the terminal command and go to the Help menu and select Check for Updates.

```
gksudo clamtk
```

PS. (seems to work without using gksudo)

My preference is for Bitdefender. Not sure there is a definitive "best", only likes and preferences. :)

Thanks, I tried that and it did update the definitions, but not the Antivirus engine or GUI version (both show newer versions available on main screen). It warns that it shouldn't be run with gksudo. But if you dont, it doesn't update anything, only shows engine and GUI need updating.

I don't care about the GUI version, but I would think the engine should be current.

---

### Post by lisati on 2011-07-19
> **dandnsmith said:**
> I used to run AVGfree, but haven't checked it's availability for a while (it was redundant in my operating context)

I used to use the Linux version of AVG Free as well, and found that it was largely redundant as well. Recent versions seem to require the command-line for use, which has been covered in the forums before. AVG also provide a rescue CD, which works like a Live CD: [http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)

---

### Post by howefield on 2011-07-20
> **brad1138 said:**
> Thanks, I tried that and it did update the definitions, but not the Antivirus engine or GUI version (both show newer versions available on main screen).

I'd guess you are stuck with the version that you install from the repository in terms of engine and gui. Given the important bit is having up to date definitions you probably aren't suffering much from not having the latest "improvements" in engine or gui, at least regarding detection usefulness.

In any event, as stated above, there are many free linux alternatives.

---

### Post by PCaddicted on 2011-07-20
> **howefield said:**
> My preference is for Bitdefender.
Bitdefender Antivirus Scannner for Unices has my vote too :). It is rated 9/10 by the [TuxRadar]("http://www.tuxradar.com/content/get-best-virus-scanner-linux") website.

---

