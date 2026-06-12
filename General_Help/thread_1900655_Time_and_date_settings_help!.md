---
title: "Time and date settings help!"
date: 2011-12-26
forum: General Help
---

### Post by Drewberg on 2011-12-26
Hello,

I'm using a student version of Tecplot 360 on Ubuntu 11.10.  Because it's a student version, my license file is one provided by my university, which expires Dec. 31.  Rather than looking for next year's license file, I lazily tried to change the time and date via "Time & Date Settings...".  I specifically tried manually changing the month.  It didn't seem like I could actually change anything, however the next time I ran Tecplot, I got an "old license error" along with "Details: System clock has been set back (-40)".  I understand this means that something is seeing a weird date in some file, but I'm not sure how to fix it.  Can someone please help me?  I've tried rebooting, and I've found the new 2012 license file, however I'm still getting this error.

Thank you in advance for your help,
Drew

---

### Post by Drewberg on 2011-12-27
Quick (easy) question: how can you search in Ubuntu 11.10 to see what files have been modified with a date in the future?

Thanks!

---

### Post by Lars Noodén on 2011-12-27
Use [touch](http://manpages.ubuntu.com/manpages/oneiric/en/man1/touch.1.html) and [find](http://manpages.ubuntu.com/manpages/oneiric/en/man1/find.1.html)

```

touch -t 201204231200 /tmp/x
find / -newer /tmp/x -print

```

---

### Post by Drewberg on 2011-12-27
Thank you for your help.  I'm getting a lot of results using the find command, especially from the /proc/ folder with "Permission denied."  Maybe a better question would be, are there particular files whose modification dates would be affected solely by changing the time and date settings?  If so, do you know where I might find them?  I'm just trying to figure out what files with weird dates my license manager might be looking at.

Thanks again!

---

### Post by Lars Noodén on 2011-12-27
You can skip /proc, /dev, /sys, and /run:

```

find / -path /proc -prune -o -path /sys -prune -o -path /dev -prune -o -path /run -prune -o -newer /tmp/x -print

```

---

### Post by grahammechanical on 2011-12-27
It seems to me that the licence file not only checks the date but records it so that it knows that the date has been put back some 40 days.

Do you know how to use the File Manager to find hidden files? With the File Manager active click Edit>Show hidden files. Now search your home folder for a file or folder that relates to this licence. It will have a dot ( . ) at the beginning of the name. That is what makes it a hidden file.

Regards.

---

### Post by Drewberg on 2011-12-27
Thank you very much for your help, Lars and Graham.  I received an email from Tecplot product support, and they said to first check if my clock is set correctly and to reboot.  Since the problem persisted for me, they said I should look in my /etc, /var/adm, and /var/log folders for future-dated files.  In these folders (I only had to fix my /etc folder), I sorted the files in order of last access time and by last write time using the following code, respectively: 

```
ls -ult
ls -clt
```There were a few files dated January 2012 (I have no idea why), and after copying a backup of them, I used the touch command (-touch xfilenamex) on each file, and Tecplot opened sans error.  Thanks again for your help!

---

