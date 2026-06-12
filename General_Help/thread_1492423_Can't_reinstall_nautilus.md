---
title: "Can't reinstall nautilus"
date: 2010-05-24
forum: General Help
---

### Post by bobtfish on 2010-05-24
I'm still using 9.10, haven't had time to reinstall recently. Of course I will soon enough, so this will only be a temporary annoyance at worst, but still...

I installed Nautilus Elementary through the PPA, but decided I didn't really like it. So I removed the PPA from my sources and tried to update again, assuming it would realise the version of Nautilus I had wasn't the one listed in the sources, but nothing. So I went to Synaptic to try and reinstall Nautilus, but Mark for Reinstallation is greyed out. I also tried
"sudo aptitude reinstall nautilus" to see why that wouldn't work, and I got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages will be REINSTALLED:
  nautilus 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the nautilus package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the nautilus package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

```

So any suggestions how to get back to regular Nautilus? Thanks in advance.

---

### Post by -humanaut- on 2010-05-24
You'll have to purge the elementary version of nautilus I believe then reinstall it as a quick fix you could just download Thunar and replace it with that until you upgrade may be alot easier then trying to recover nautilus.


also did you update apt with sudo apt-get update??

---

### Post by bobtfish on 2010-05-24
> **-humanaut- said:**
> 
also did you update apt with sudo apt-get update??
I think I did it through update manager at the time, not that it should make any difference, but I've done it through the command line now and still nothing.
There's no point installing another file browser now, I still have Elementary working, I just didn't particularly prefer it to regular Nautilus, and wanted to go back.
If I try to mark Nautilus for uninstallation through Synaptic so I can reinstall it clean afterwards, it tells me I also have to uninstall gnome-session, nautilus-share and ubuntu-desktop, which I'm fairly sure will destroy a lot.

---

### Post by -humanaut- on 2010-05-24
Yeah, Nautilus is tightly integrated into Gnome thats why I recommended a different file manager as a stop-gap so to speak.

---

### Post by ammonkey on 2010-05-25
google ppa-purge it will fix easily this issue.

---

### Post by Donalb on 2010-05-29
Could you explain futher about ppa-purge?

I'm on 9,10, no plans to install Lucid, also tried installing nautilus elementary and it screwed my gnome-setting-demon (which I fixed) but I've lost my ability ot sync my Ubuntu One folder (though my U1 applet shows connected). Uninstalled Elementary (can't recall how) but a few othjer minor issues lead me to suspect Nautilus. 
I also have lost the Reinstall Nautilus option in Synaptic.

I've looked at that ppa-purge but not sure what I'm supposed to do with it.

---

