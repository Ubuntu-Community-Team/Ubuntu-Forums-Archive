---
title: "Gimp and Inkscape crash after upgrade (broken dependencies?)"
date: 2011-04-29
forum: General Help
---

### Post by kaltv on 2011-04-29
Both programs were working just fine yesterday before the upgrade to Ubuntu 11.04.

Opening Gimp results in many error pop-ups on being unable to locate module gimp and module gimpfu. I tried to uninstall and reinstall, and the installation fails with this message:

The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (<= 2.6.11-z) but 2.7.3-2010072701~ll is to be installed
        Depends: gimp-data (<= 2.6.11-z) but 2.7.3-2010072701~ll is to be installed

This may be because of times in the past where I tried to compile Gimp. Do I need to clean up my repositories list? (in that case, any way to get a fresh one?)

Inkscape doesn't open at all, instead the terminal message says this:

inkscape: error while loading shared libraries: libwpg-0.1.so.1: cannot open shared object file: No such file or directory

I'm not sure what's wrong in the case of Inkscape though, although I did compile a few versions long ago I was using the "normal" version from the Ubuntu repositories afterwards. Any ideas?

Thanks very much in advance. :)

---

### Post by hwttdz on 2011-04-29
Try "sudo ldconfig" and then try inkscape again.  

Also "sudo aptitude reinstall packagename" might manage to sort dependencies.  

When you run "which gimp" or "which inkscape" where does it say it's living.  It's possible you've still got the old ones floating around.

---

### Post by kaltv on 2011-04-29
> **hwttdz said:**
> Try "sudo ldconfig" and then try inkscape again.  

Also "sudo aptitude reinstall packagename" might manage to sort dependencies.  

When you run "which gimp" or "which inkscape" where does it say it's living.  It's possible you've still got the old ones floating around.
Thank you very, very much! You were right about Inkscape, there was an extra one in:
/usr/local/bin/inkscape

Nothing showed up for Gimp though, and ldconfig + reinstall didn't work, it still shows:
gimp : Depends: libgimp2.0 (<= 2.6.11-z) but 2.7.3-2010072701~ll is to be installed
Depends: gimp-data (<= 2.6.11-z) but 2.7.3-2010072701~ll is to be installed

Weird. I must have added a ppa somewhere to get the development version. At least I know where the error is coming from now, so I'll mark this thread as resolve for now. Thanks for the help!

---

