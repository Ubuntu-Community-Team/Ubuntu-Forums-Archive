---
title: "xfig problem with ubuntu 11.04"
date: 2011-04-29
forum: General Help
---

### Post by liu4gre on 2011-04-29
I update to 11.04 from 10.10, then the worked xfig has problems now.
First one is "Can't find -*- times-medium-r-normal--13"; and so on. Looks like font problem. Installed psfont, still have problem there.
Second, when using "picture project" to insert a eps file, it does not give a preview, showing "EPS object read OK, but no preview bitmap not found/generated".

---

### Post by dino99 on 2011-04-29
its the second time today i've seen this problem. i suppose ghostscript is installed

is there errors logged into .xsession-errors or /var/log (system admin logviewer)

---

### Post by Sebastock on 2011-05-06
Same problem here. I've updated to ubuntu 11.04 and now when I open xfig  I have
```
Can't find -*-helvetica-medium-r-normal--16-*-*-*-*-*-ISO8859-*, using 6x13 
```Although, I still can edit and export xfig files to an eps files, but the EPS file is kind of weird (for example, on windows xp, the eps file appears empty...).

---

### Post by hennessy.matt on 2011-05-08
I had the same problem, but installing the gsfonts-x11 package seemed to fix it.

---

### Post by Sebastock on 2011-05-08
The gsfonts-x11 package has solved the problem for me as well. I did install this package before but it didn't seem to have any effect. I forgot that I had to restart the x server   for the changes to take effect...

---

### Post by Goober123 on 2011-06-15
Great info. The gsfonts-x11 package has solved the problem for me as well.

---

