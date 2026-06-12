---
title: "Not allowed to create folders on my pendrive. Why not?"
date: 2009-06-29
forum: General Help
---

### Post by funky_uncle on 2009-06-29
Running Intrepid Ibex.

I tried copying some files to the pendrive, but I'm not allowed to write to it. So I (re)format it (with Partition Editor, as usual) and try again, but I get the same error. How can I be allowed to format a drive but not copy stuff onto it?

---

### Post by credobyte on 2009-06-29
```
sudo chown -R user:user /media/pendrive

```
Replace pendrive with what it's currently using ( mountpoint ).

---

### Post by pytheas22 on 2009-06-29
Partition Editor is always run as root; that's why you can format the drive but not write files to it as a regular user.

Ordinarily the system should let you write to the device, provided you just plugged it in and had it auto-mounted by Gnome.  I'm not sure what's wrong, but in any case the command in the post above should set it straight.

---

### Post by funky_uncle on 2009-06-29
Thanks, I'll try that. I hope I won't have to use the chown command every time I format the pendrive, though.

---

