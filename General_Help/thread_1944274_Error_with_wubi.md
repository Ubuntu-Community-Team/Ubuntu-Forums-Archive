---
title: "Error with wubi"
date: 2012-03-21
forum: General Help
---

### Post by aoidenyx on 2012-03-21
I get an error message that looks like this:

pyrun.exe - No Disk

There is no disk in the drive. Please insert a disk into drive \Device\Harddisk2\DR2.

I'm trying to run wubi. I get this error no matter how I try to run it. Any suggestions?

---

### Post by Mark Phelps on 2012-03-21
You need to have the Ubuntu ISO file in the same directory as the Wubi.exe file.  It's acting like Wubi is looking for a file that is in that ISO and it can't find it.

---

### Post by aoidenyx on 2012-03-23
So I have to download the ISO file as well?

---

### Post by kdane4 on 2012-03-23
> **aoidenyx said:**
> So I have to download the ISO file as well?

its much more recommended.. If you only got the wubi.exe file, its going to download most of the ISO components anyway to complete installation.

---

### Post by bcbc on 2012-03-23
This is bug [lpbug]365881[/lpbug]. You can review this for the proposed workarounds. I'd personally just click ignore 20times or whatever it takes.

---

