---
title: "MS Office in Ubuntu"
date: 2010-09-14
forum: General Help
---

### Post by thundaraptor on 2010-09-14
What do people think is the best way to get MS Office working in Ubuntu?  I haven't yet tried but thinking to use WINE, how is it?  I really like ubuntu but from a work perspective, it is totally impossible not to have to be able to quickly deal with .docx in the way that ms office handles them.  The internal office management stuff is ok but really doesn't handle the advanced functions well.  Advice?  This is the final step in my linux journey.

---

### Post by snowpine on 2010-09-14
OpenOffice can read/write .docx just fine; can you articulate your concerns more clearly?

But, to answer your specific question, I know of 3 options:

1. dual boot ubuntu/windows. this is 100% guaranteed to work flawlessly

2. run windows in virtualbox (or other virtualization option) within Ubuntu. this will probably work OK assuming your hardware is powerful enough

3. run office in wine. be sure to check [http://winehq.org](http://winehq.org) to see what they have to say!

---

### Post by rcayea on 2010-09-14
I believe the software available through the repo, Play On Linux supports one of the versions of MS Office. It might be 03.

---

### Post by 3Miro on 2010-09-14
For MS Office I recommend Virtual Box. Dual-booting is clumsy if all you want to do is edit a file and wine can be iffy especially with MS specific apps. Wine is also often hard to setup. Virtual Box does, however, require some powerful hardware. For smooth performance you should have at least 2GB of RAM (1.5 or 1 may work, but not very smooth) and at least Athlon X2 or Pentium Dual Core CPU.

---

### Post by thundaraptor on 2010-09-14
> **rcayea said:**
> I believe the software available through the repo, Play On Linux supports one of the versions of MS Office. It might be 03.

I find that much of the advanced formatting tools of MS Office don't carry over well.  Things like table of contents, track changes, table formatting and alignment.  Also embedding pdfs and anything that uses macros is out and in my industry, i can't get away from the inundation of MS Office centric documents that people send.  Consider, if someone sends me a document and says edit it, once I make the edits and return there can be no question of interruption of format or style and in my past experiences, open office was not robust enough to satisfy this.

---

### Post by snowpine on 2010-09-14
> **thundaraptor said:**
> I find that much of the advanced formatting tools of MS Office don't carry over well.  Things like table of contents, track changes, table formatting and alignment.  Also embedding pdfs and anything that uses macros is out and in my industry, i can't get away from the inundation of MS Office centric documents that people send.  Consider, if someone sends me a document and says edit it, once I make the edits and return there can be no question of interruption of format or style and in my past experiences, open office was not robust enough to satisfy this.

If your career depends on it, there is no substitute for the real deal: Microsoft Office running on Windows (either dual boot or in a virtual machine).

I prefer to use Linux as much as possible, but if a client needs me to use a Windows app, I do not hesitate.

---

### Post by thundaraptor on 2010-09-14
> **3Miro said:**
> For MS Office I recommend Virtual Box. Dual-booting is clumsy if all you want to do is edit a file and wine can be iffy especially with MS specific apps. Wine is also often hard to setup. Virtual Box does, however, require some powerful hardware. For smooth performance you should have at least 2GB of RAM (1.5 or 1 may work, but not very smooth) and at least Athlon X2 or Pentium Dual Core CPU.

I have a pretty strong system that I built myself, 4gb 1066hz ram, AMD 64 X4 but I have to say I don't really know what virtual box is.  I would def like to learn more about how to handle this though.

---

### Post by snowpine on 2010-09-14
> **thundaraptor said:**
> I have a pretty strong system that I built myself, 4gb 1066hz ram, AMD 64 X4 but I have to say I don't really know what virtual box is.  I would def like to learn more about how to handle this though.

You are in for a treat! Virtualization allows you to run Windows (or any other operating system) inside a "virtual machine" or in other words, as an application on your Ubuntu desktop. (For that matter, you could run Ubuntu as a virtual machine inside of Windows... your choice.)

We have a whole sub forum on the topic, I recommend reading the "Sticky" threads to get started.

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

Please note you will need to install Windows and Office in the virtual machine, which "counts" as an additional license as far as MS is concerned.

I think your system specs are more than capable, good luck! :)

---

### Post by e79 on 2010-09-14
> ...but I have to say I don't really know what virtual box is.  I would def like to learn more about how to handle this though.VirtualBox is a Virtualization Software (like VMware), allowing you build 'Virtual Machines' that would run from your desktop and could be accessible like any other machine. To do so, you need a working and valid copy of MS Windows to install it into VirtualBox.

If you really want to run MS Office on Ubuntu, either use Wine (free version) or CrossOver (WINE enhanced paid version) to set it up. Crossover is one of them company specializing into tweaking WINE for an easiest and better way to use Windows Apps under Linux/MAC. 

[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

Hope this helps.

---

### Post by cloyd on 2010-09-14
I think problems with formatting in MS office documents is the reason my wife won't switch. _[COLOR=black]If[/COLOR]_[COLOR=black] people would just stick to PDF's on those highly formatted documents, we'd be ok. Personally, if I must send someone a highly formatted document, I'll send a PDF. If I get one that doesn't work in open office, I'll ask for a format that will. But hey, I'm close to retirement, anyway. Some people may not get away with this.  One day, _I_ may not get away with it.  

However, problems with highly formatted open office documents is an issue. Text comes across fine, and documents where formatting is not highly developed work fine. But lots of tables, or forms just do not work. I know, lack of access to MS's spec's is an issue. I guess more of a reason to like open source and dislike proprietary more. 
[/COLOR]

---

