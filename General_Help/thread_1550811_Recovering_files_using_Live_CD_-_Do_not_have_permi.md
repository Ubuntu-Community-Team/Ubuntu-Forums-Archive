---
title: "Recovering files using Live CD - Do not have permission?"
date: 2010-08-11
forum: General Help
---

### Post by Haruki-kun on 2010-08-11
Hi!

So my old computer died. I was Dual-Booting Jaunty and Windows XP. Now I'm trying to recover my files from the hard drive, but of course, you can't do it from Windows 7. I could recover everything from the Windows Partition, but Windows doesn't even see the Ubuntu Partition.

So I popped in a Lucid Lynx live CD to recover my files, only to find out that several seemingly random folders within the Documents folder have a cross on them. When trying to access them I get a message saying I "Do not have the permissions necessary to view the contents."

What should I do now? I really need to recover those files!

---

### Post by gsgleason on 2010-08-11
use sudo

if you are using the graphical file manager, open a terminal and type sudo nautilus

---

### Post by snowpine on 2010-08-11
Actually you want:

```
gksu nautilus
```

as Nautilus is a graphical application.

---

### Post by Haruki-kun on 2010-08-11
sudo nautilus

Seems to have done the trick.

So... for the future... Why does this happen? What'd those folders have that made them inaccessible?

---

### Post by switch10 on 2010-08-11
It is good practice to use gksudo instead of sudo when using a graphical application, like nautilus.  

You will have to use sudo/gksudo to mv or cp directories and files that are not in your home directory (/home/username/).

---

### Post by techunit on 2010-08-11
This was a past topic on my [Blog]("http://ubuntuvideotutorials.wordpress.com") I talked about gaining administrative privileges in the file manager, something that has plaged me in the past trying to figure out how to do it. The best way to do it is hit alt-f2 and type ```
gksu nautilus
``` and hit run. It then opens a root file manager. When your finished and close the window it loses administrative privileges.

---

