---
title: "can't uninstall package?"
date: 2010-10-25
forum: General Help
---

### Post by garyed on 2010-10-25
I've been trying top get my Brother MFC-420CN printer working in 10.04
I had it working in 8.04 but I can't get the model to show up in the brother drivers. Anyways I tried uninstalling & reininstalling through synaptic but one thing got stuck with an error uninstalling. A package named
"brscan". It has an x by the package & I get an error no matter what I try to do. Now I can't install any of the Brother packages because I keep getting this error about the brscan package & I can't get rid of it. 
Any ideas how to clear this up?

---

### Post by katykat on 2010-10-25
If aptitude -remove brscan does not work (or else if it tries to remove half your system)...

Then it is one of those obstinate files that nothing seems capable of purging. 

The only solution I have found in these instances is to  to :
/var/lib/dpkg/status 
copy the status to status-backup
and edit the original status by searching for brscan and removing the ENTIRE entry. 

I do this stuff as root with a file manager, so there are alot of 'sudos' missing there. 

 




> **garyed said:**
> I've been trying top get my Brother MFC-420CN printer working in 10.04
I had it working in 8.04 but I can't get the model to show up in the brother drivers. Anyways I tried uninstalling & reininstalling through synaptic but one thing got stuck with an error uninstalling. A package named
"brscan". It has an x by the package & I get an error no matter what I try to do. Now I can't install any of the Brother packages because I keep getting this error about the brscan package & I can't get rid of it. 
Any ideas how to clear this up?

---

### Post by garyed on 2010-10-25
I found this on another thread. 
 ```
 sudo mv /var/lib/dpkg/info/brscan.postrm /var/lib/dpkg/info/brscan.postrm.backup 
```

then do:
```
sudo dpkg --purge brscan
```

That worked but to get rid of the errors & allow me to reinstall the cups drivers etc. I still haven't got my printer working but that's for another thread.

Thanks

---

