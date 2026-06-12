---
title: "help needed uninstalling a package"
date: 2010-06-30
forum: General Help
---

### Post by peetee1979 on 2010-06-30
Hi All

i downloaded a printer driver called snx-100 which was installed correctly, i now need to uninstall it, i ran it's uninstall.sh script which it said it's done correctly, but now to every package i want to install i get the following message which i have attached

any help to remove this message would be much appreciated.

---

### Post by justleen on 2010-06-30
you could try manually purging it with dpkg:
```

dpkg --purge  pips-snx100
```

---

### Post by peetee1979 on 2010-06-30
hi
thanks for your reply, i tried that and am now getting this message (see attached)

---

### Post by justleen on 2010-06-30
for some reason it keeps looking for cupsys, which isn't installed anymore.
I think I would just force the purge at this stage, or reinstall cupsys (only to remove it again).
```
sudo dpkg --purge --force-all pips-snx100
```
or
```
sudo apt-get -y install cupsys && apt-get remove --purge   pips-snx100
```

---

### Post by peetee1979 on 2010-06-30
still the same error message, any other thoughts, I even re-installed the snx-100 package then did the purge command but no go, even uninstalling it through synaptic caused an error.

---

### Post by justleen on 2010-06-30
from [http://ubuntuforums.org/showthread.php?t=1254621](http://ubuntuforums.org/showthread.php?t=1254621)
> 
go to /var/lib/dpkg/info and remove any entries about pips-snx100


---

