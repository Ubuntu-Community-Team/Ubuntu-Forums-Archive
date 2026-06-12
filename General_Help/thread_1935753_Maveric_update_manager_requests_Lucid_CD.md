---
title: "Maveric update manager requests Lucid CD"
date: 2012-03-04
forum: General Help
---

### Post by sea_dawg on 2012-03-04
I'm running Maverick yet update manager has asked for the Lucid CD? > CD/DVD 'Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release i386 (20110720.1)' is requiredThis happened when an exclamation mark icon appeared in the upper panel.  Clicking that icon told me to manually start Update Manager to see if any PPA were outdated.  

Two quest6ion:
1 - Is this a good idea to update Maverick with a Lucid disc?
2 - The request is specifically for Release i386 (20110720.1).  How do I know if the CD I have is that release?

---

### Post by plucky on 2012-03-05
> **sea_dawg said:**
> I'm running Maverick yet update manager has asked for the Lucid CD? This happened when an exclamation mark icon appeared in the upper panel.  Clicking that icon told me to manually start Update Manager to see if any PPA were outdated.  

Two quest6ion:
1 - Is this a good idea to update Maverick with a Lucid disc?
2 - The request is specifically for Release i386 (20110720.1).  How do I know if the CD I have is that release?



Answer 1:- No

Answer 2: Open Software Sources and disable the Lucid CDrom as a source.
          Then open a terminal and run ```
sudo apt-get update
``` and see if you get any more errors.

Good luck

---

### Post by sea_dawg on 2012-03-05
Deleting the lucid source and running update from terminal worked.  No errors.

However I am having other issues that in my ignroance I speculate may be related.

[http://ubuntuforums.org/showthread.php?t=1930875](http://ubuntuforums.org/showthread.php?t=1930875)

This all started approximately the time I began installing OSs in Virtual Box.  Among the ones that I tried were Lucid and Kbuntu, both were listed in Maverick's software sources.

With just over a month to Maverick's EOL I'm beginning to think it is time to make my decision and do a clean install.

---

### Post by raja.genupula on 2012-03-05
> **sea_dawg said:**
> Deleting the lucid source and running update from terminal worked.  No errors.

However I am having other issues that in my ignroance I speculate may be related.  [http://ubuntuforums.org/showthread.php?t=1930875]("http://http://ubuntuforums.org/showthread.php?t=1930875")  

This all started approximately the time I began installing OSs in Virtual Box.  Among the ones that I tried were Lucid and Kbuntu, both were listed in Maverick's software sources.

With just over a month to Maverick's EOL I'm beginning to think it is time to make my decision and do a clean install.

is that thread link is working ?

---

### Post by sea_dawg on 2012-03-05
No, the thread link is not working.  I probably did something wrong.

---

