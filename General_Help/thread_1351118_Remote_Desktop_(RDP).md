---
title: "Remote Desktop (RDP)"
date: 2009-12-10
forum: General Help
---

### Post by EdGy28376 on 2009-12-10
I have been able to us Microsoft Remote Desktop to my Ubuntu boxes. Recently Microsoft updated their Remote Desktop in which I would receive a connection error.

I have identified the Microsoft update that creates this problem as being KB9690874. To uninstall this update look in the Windows folder for $NtUninstallKB969084 it will be a hidden directory. Within that directory there is a spunist directory that contains spuninst.exe. Run that and it will back out the change. You should be able to once again use RDP.

Hope this helps someone!

---

### Post by EdGy28376 on 2009-12-26
Ok here it is better then using Microsoft Remote desktop. Use Neatx based on No Machine. Its simply to install really no configuration to speak of and just as good if not better. 

:popcorn:

---

### Post by NFblaze on 2009-12-26
Nice find.

---

