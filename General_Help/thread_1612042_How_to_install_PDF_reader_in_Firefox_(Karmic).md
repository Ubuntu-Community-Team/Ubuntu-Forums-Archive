---
title: "How to install PDF reader in Firefox (Karmic)?"
date: 2010-11-02
forum: General Help
---

### Post by PerfectReign on 2010-11-02
I'm running 9.1 - Karmic - with GNOME.  I run Firefox as my browser 99% of the time and am on 3.6.12 as of the time I write.  On a regular basis I want to view PDF files on the web. In all cases I have to download the file then open it in the reader.   I don't really care which reader I use, but I'd like to open the file in the browser like I can on Wintendo and used to be able to do here.  I googled and see instructions for installing:  [http://ubuntuforums.org/showthread.php?t=666122&highlight=acrobat+plugin](http://ubuntuforums.org/showthread.php?t=666122&highlight=acrobat+plugin)  [http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html](http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html)  and  [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Adobe_Acrobat_Reader_for_Firefox_Plug-in](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Adobe_Acrobat_Reader_for_Firefox_Plug-in)  Trying each of these I get an error. There's also no acroread in Synaptec.   kai@kai-laptop:~$ sudo apt-get install acroread mozilla-acroread acroread-plugins Reading package lists... Done Building dependency tree        Reading state information... Done Package acroread is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source E: Package acroread has no installation candidate   Looking at the medibuntu repository for Karmic, I see there's no Acrobat at all.  [http://packages.medibuntu.org/karmic/index.html](http://packages.medibuntu.org/karmic/index.html)  What gives?  How does one actually get the plugin working??

---

### Post by gandaran on 2010-11-02
I don't remember exactly but I think in Ubuntu Karmic the acroread (adobe reader) is in the archive.canonical partner repository, enable the repo in software sources and update the package list then you can find acroread in ubuntu software center or synaptic.
if it is not in archive.canonical repo then it must be in medibuntu repository

---

### Post by PerfectReign on 2010-12-27
By the way, I found it, thanks.  I'm up and have Acroread running.

Now, if only I could have Acrobat Pro.  I love the UI on that application.

---

