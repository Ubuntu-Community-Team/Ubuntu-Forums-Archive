---
title: "How can I remove the PDFStudio demo in Ubuntu 9.04?"
date: 2009-10-13
forum: General Help
---

### Post by BETATEST on 2009-10-13
It was installed using Qoppa's setup.sh from their website.  It doesn't show up in Add/Remove under Applications or Synaptic Package Manager.  sudo apt-get autoremove  doesn't work and errors it cannot find the package.   Any help would be nice to get rid of this thing.

---

### Post by BQAggie2006 on 2009-10-13
If you just accepted the defaults during installation, it looks like the default installation path of the program is /home/<username>/PDFStudio and it looks like it installed symlinks in /usr/local/bin. All you'll have to do is remove the PDFStudio directory from your home folder and the symlinks from the /usr/local/bin folder.

---

### Post by wojox on 2009-10-13
Try:

```
dpkg --remove --force-remove-reinstreq <APPLICATION>
```

---

### Post by mcduck on 2009-10-13
> **wojox said:**
> Try:

```
dpkg --remove --force-remove-reinstreq <APPLICATION>
```

That won't work, since the program wasn't installed from a .deb package (so Ubuntu's package management wasn't used, and it's not aware of the program)

---

### Post by BETATEST on 2009-10-13
Well, PDFStudio got back to me.

You delete   /home/<username>/PDFStudio 

Supposedly it installed symlinks in /usr/local/bin that you can delete ... but I didn't find any in there and the Qoppa's tech support didn't mention it for the 6.1 version.

You still have to manually remove it's entry from the APPLICATIONS menu.

Thanks BQAggie2006, your solution was right since this is a JAVA application and not a DEB package (which is why Wojox's dpkg force remove terminal command won't work in this particular case).

You'd think Qoppa would just include an uninstall script for it.  Especially for a DEMO.

---

### Post by zeddock on 2011-02-14
> **BETATEST said:**
> Well, PDFStudio got back to me.

You delete   /home/<username>/PDFStudio 

Supposedly it installed symlinks in /usr/local/bin that you can delete ... but I didn't find any in there and the Qoppa's tech support didn't mention it for the 6.1 version.

You still have to manually remove it's entry from the APPLICATIONS menu.

Thanks BQAggie2006, your solution was right since this is a JAVA application and not a DEB package (which is why Wojox's dpkg force remove terminal command won't work in this particular case).

You'd think Qoppa would just include an uninstall script for it.  Especially for a DEMO.

I doubt this is all since it also must install JRE or Java, right?

---

