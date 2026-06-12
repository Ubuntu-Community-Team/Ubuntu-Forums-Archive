---
title: "k3b and kdebase-runtime"
date: 2009-12-20
forum: General Help
---

### Post by Eugene_ on 2009-12-20
Hi.

On 9.04 jaunty I always used "k3b" for CD/DVD writing but on 9.10 karmik "k3b" package depends on kdebase-runtime.

Can I safely install it on Ubuntu?
I don't mind if it will occupy hundred or so MB on HDD but don't want any KDE-related services in autostart.

---

### Post by efflandt on 2009-12-20
Don't worry about it.  It is just that KDE programs or games need KDE hooks to work properly.  That does not mean that you will end up with KDE instead of gnome or extra programs loading (other than what is needed to run the KDE programs).

I just installed k3b last night.  Although, I never had trouble at all writing CD-R disks in Brasero @ 16x, I seem to have difficulty with CD-RW disks @ 4x with Brasero or k3b.  It took 3 tries to get one disk to burn without errors.  And when I tried to full erase a different disk that failed 1st write attempt, I gave up after 1hr 40min, but k3b would not cancel or close, I could not kill it from the terminal, and the disk kept churning, so I had to reboot.  I don't know if temperature is more critical for CD-RW (maybe my room is too cool), if the disks are substandard (from Staples), or my drive has issues, because this is the first time I ever used CD-RW on my PC from 2004.

---

### Post by Eugene_ on 2009-12-21
Thanks for the answer. Thought that my only option would be to use growisofs and wodim in command line.

Not sure that to tell about CD-RW. According to [http://www.cdrinfo.com/Sections/Glossary/Details.aspx?TermId=711](http://www.cdrinfo.com/Sections/Glossary/Details.aspx?TermId=711) temperature shouldn't be a problem unless discs are too substandard.

Tried to fast erase and write data CD-RW (Verbatim CD-RW, 10x) on 9.04 k3b 1.05 and everything went fine.
If it'll help there's a couple of successful lastlog.log's. May be you can compare them with yours for some glimpse.

---

