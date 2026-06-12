---
title: "Cannot Uninstall aMSN"
date: 2012-09-04
forum: General Help
---

### Post by khanorak on 2012-09-04
Hello

I have installed Ubuntu 12.04 LTS. 

I then installed aMSN old version and removed it from software center. 

Then I came across this site [http://ubuntuforums.org/showthread.php?p=11926077](http://ubuntuforums.org/showthread.php?p=11926077) and followed it to install aMSN. Now it doesn't appear in Software center and I can't uninstall it via synaptic too. 

Please bear in mind that I am using Ubuntu for the very first time.

Please help

---

### Post by Bachstelze on 2012-09-04
Try going back to the source folder and do

```
sudo make uninstall
```

If that doesn't work you are basically out of luck. It's not a very big problem, though, the files just take up (a probably small amount of) space on your disk. If any file bothers you, just remove it with a good ol' [font=monospace]rm[/font].

---

### Post by khanorak on 2012-09-04
> **Bachstelze said:**
> Try going back to the source folder and do

```
sudo make uninstall
```

If that doesn't work you are basically out of luck. It's not a very big problem, though, the files just take up (a probably small amount of) space on your disk. If any file bothers you, just remove it with a good ol' [font=monospace]rm[/font].

Actually the aMSN folder is in root drive. It's somewhere in this path: /usr/share/amsn

And I think I can't remove it from there.

---

### Post by Bachstelze on 2012-09-04
Yes you can, just remove it as root (from the command-line with [font=monospace]sudo[/font], or in nautilus run with [font=monospace]gksudo nautilus[/font]).

---

### Post by Linux_junkie on 2012-09-04
> **khanorak said:**
> ...I then installed aMSN old version and removed it from software center. 

Removed from software centre? You don't have permission to remove  software from software centre.

Unless your  talking about adding (or removing) the ppa for aMSN from the software centre.

---

### Post by khanorak on 2012-09-04
> **Bachstelze said:**
> Yes you can, just remove it as root (from the command-line with [font=monospace]sudo[/font], or in nautilus run with [font=monospace]gksudo nautilus[/font]).

Thanks.

Although a bit tedious removing each file from the terminal, yet it did the job.

Thank you

---

### Post by khanorak on 2012-09-04
> **Linux_junkie said:**
> Removed from software centre? You don't have permission to remove  software from software centre.

Unless your  talking about adding (or removing) the ppa for aMSN from the software centre.

Well that's pretty Literary English :S of yours... 

I have written in my first post that it's the first time I am using Ubuntu. Don't quite understand what PPA is.. sorry for the n00bness

---

