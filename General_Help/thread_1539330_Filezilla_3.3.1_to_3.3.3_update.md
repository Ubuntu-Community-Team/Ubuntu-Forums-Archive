---
title: "Filezilla 3.3.1 to 3.3.3 update"
date: 2010-07-26
forum: General Help
---

### Post by FreedomOverdose on 2010-07-26
Hello

I'm on Ubuntu 10.04 Lucid. At the moment, the current version of filezilla in the software center is 3.3.1. That version has some known bugs, and the current version of filezilla at their website is 3.3.3 (released more than a month ago). How can i update filezilla? FIlezilla tells me to use software manager, but 3.3.3 isn't there yet. Moreover, they only release the source code without a deb package...

Thanks in advance

---

### Post by P4man on 2010-07-26
Generally its best to just wait until the new version makes its appearance in the ubuntu repo. If there are any showstopper bugs in that version; grab 3.3.3 here:
[http://www.getdeb.net/updates/Ubuntu/10.04/?q=filezilla](http://www.getdeb.net/updates/Ubuntu/10.04/?q=filezilla)

---

### Post by FreedomOverdose on 2010-07-26
Thanks! But when i try to install it says that filezilla is already installed. How can I update it?

Thanks

---

### Post by P4man on 2010-07-26
uninstall the one you have first? Wouldnt have thought youd need to; but sounds like the sensible thing to try.

---

### Post by FreedomOverdose on 2010-07-26
I'll try that, thanks :)

---

### Post by luigi_mb on 2010-07-26
> **FreedomOverdose said:**
> I'll try that, thanks :)

...but select "Mark for removal", not "Mark for complete removal". Doing so will keep the ~/.filezilla folder, which contains your settings. 

/luigi

---

### Post by FreedomOverdose on 2010-07-26
strangely, when I try to install the deb package from [http://www.getdeb.net/updates/Ubuntu/10.04/?q=filezilla](http://www.getdeb.net/updates/Ubuntu/10.04/?q=filezilla) (after removing the original version) I still get filezilla 3.3.1 instead of 3.3.3! Maybe it's just a wrong version shown in there... :S

---

### Post by P4man on 2010-07-27
Not sure why that is. But I got filezilla 3.3.3 doing this:

```
wget -q -O - http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu lucid-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'
```

That adds getdeb repository to your software sources and imports the key. Then update the sources:
```

sudo apt-get update
```

Then install filezilla (if its already installed it will upgrade it):
```

sudo apt-get install filezilla
```

You can do all of the above in the GUI if you prefer; just add the getdeb repo; reload your sources in synaptic and install filezilla.

---

