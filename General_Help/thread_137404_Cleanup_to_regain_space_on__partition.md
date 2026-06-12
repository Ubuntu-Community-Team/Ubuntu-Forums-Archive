---
title: "Cleanup to regain space on / partition"
date: 2006-02-27
forum: General Help
---

### Post by z_diver on 2006-02-27
I would like to get a little breathing room on my 3.5 gig root partition.  I think removing some of the 450mb in /var and some of the nearly 1 gig I have in /proc may be enough.  Is there any recommended procedure?

TIA

---

### Post by dcstar on 2006-02-28
[QUOTE=z_diver]I would like to get a little breathing room on my 3.5 gig root partition.  I think removing some of the 450mb in /var and some of the nearly 1 gig I have in /proc may be enough.  Is there any recommended procedure?

TIA[/QUOTE]
Start with you /tmp directory, then you may want to clear out your /var/cache/apt/archives directory (use Synaptic to do this).

A look at /var/log might also be useful.

---

### Post by RAOF on 2006-02-28
[QUOTE=z_diver]I would like to get a little breathing room on my 3.5 gig root partition.  I think removing some of the 450mb in /var and some of the nearly 1 gig I have in /proc may be enough.  Is there any recommended procedure?

TIA[/QUOTE]
/proc is a virtual filesystem - no space is taken up on your drive.  Also, since one of the "files" in /proc is the entire contents of your memory (if you're ever interested in seeing a whole bunch of binary garbage, you can sudo cat /proc/kcore ;)), it's bound to be quite big :)

---

### Post by z_diver on 2006-02-28
[QUOTE=RAOF]/proc is a virtual filesystem - no space is taken up on your drive.[/QUOTE]Thanks!  Makes sense.  I knew you never want to back up /proc ...just didn't realize it's virtual. ;) 

Now I have a question about removing unnecessary packages in /var/cache/apt/archives using Synaptic.  I have already removed orphaned files using the filters.  Ran that 3 times as more kept appearing.  That felt good but didn't make a huge dent. :D   I looked through the directory and there are certainly some packages in there that could(or should have been) removed but I don't see that option.

---

### Post by RAOF on 2006-02-28
The /var/cache/apt/archives directory contains downloaded .deb files, so you don't have to download them again if you remove & then reinstall the package.  It doesn't actually have anything to do with what packages you've got installed.

To clear the cache, you can run "sudo aptitude clean" from a console.

---

### Post by z_diver on 2006-02-28
[QUOTE=RAOF]
To clear the cache, you can run "sudo aptitude clean" from a console.[/QUOTE]
That handed back a clean 350 mb and I really appreciate it!!!  thank you.

is there an equally simple command to clear the logs?

---

### Post by soonindallas on 2006-02-28
you could look at deborphan and debfoster, both in repos.

deborphan finds orphan packages ie packages that were installed as dependencies and no longer have packages depending on them.

debfoster allows you to remove packages *and* dependencies since apt-get does not always do this.  apparently aptitude is better at this but I do not use it.

Yesterday I freed 195M using debfoster on my Breezy install.

Caution is advised.  For example I had to independently obtain and install libtiff3g to get my Canon printer to work, deborphan tells me it's an orphan, but if I get rid of it my printer will no longer work....

---

