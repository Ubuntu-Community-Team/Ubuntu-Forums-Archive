---
title: "Nautilus - usr/share/doc"
date: 2011-01-14
forum: General Help
---

### Post by billio on 2011-01-14
Why would nautilus take several minutes to display the contents of usr/share/doc ?. There are 2783 items in the folder.

I am using dual-core 2.9MHz processor, 4G memory and 10.10, with no other applications running.

Any suggestions on how to improve the response ?.

Thanks.

---

### Post by Tamlynmac on 2011-01-14
Just a quick thought.

If your using "icon view" try switching to "list view" nautilus/view/list". I think you'll find that it performs much faster than opening an icon for each file.

Good Luck & Hope This Helps.

---

### Post by WorMzy on 2011-01-14
Nautilus is a rather.. slow file manager, especially if you have previews enabled. However, that particular directory should only contain directories, and definitely shouldn't take minutes to render..

You could try disabling the folder-item count by going to (in nautilus): Edit -> Preferences -> Preview, and changing the folders "Count number of items" to "Never".

[IMG]http://img203.imageshack.us/img203/361/20110114224931386x517sc.png[/IMG]

Might help, might not.

---

### Post by LewRockwellFAN on 2011-01-14
> **billio said:**
> Why would nautilus take several minutes to display the contents of usr/share/doc ?. There are 2783 items in the folder.

I am using dual-core 2.9MHz processor, 4G memory and 10.10, with no other applications running.

Any suggestions on how to improve the response ?.

Thanks.

Try checking your memory when it happens. (System-Administration-System_Monitor, Resources tab). I've seen this behavior occasionally also, but I haven't thought before to see if it was connected to the memory leak issue. For some people the Nautilus memory leak went away with some past upgrade apparently but I am experiencing it now in 11.04 Narwhal. Thunar and Roxy-filer have not had this slow-to-display-contents-of-a-directory problem since I began experimenting with them a week or so ago. If it IS the memory leak issue try either killing all the nautilus in the system monitor processes tab or type "killall nautilus" and hit enter in a terminal. If that works you could make it convenient with a launcher. And if that is the problem you might want to take a look at this thread [http://ubuntuforums.org/showthread.php?t=1489741](http://ubuntuforums.org/showthread.php?t=1489741) and in particular my post near the end of it. Until Nautilus is fixed the easiest thing seems to be to kill it and let it restart.

---

