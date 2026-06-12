---
title: "VBox Question"
date: 2010-01-03
forum: General Help
---

### Post by borneseller on 2010-01-03
I've loaded Virtual Box on my laptop - - and would like find a way to read my C drive in Windows XP - - can anyone provide assistance?

---

### Post by howefield on 2010-01-03
> **borneseller said:**
> I've loaded Virtual Box on my laptop - - and would like find a way to read my C drive in Windows XP - - can anyone provide assistance?

Too much info ;)

Is Windows XP the host and the guest is what ?

You could enable shared folders, (you'd need guest additions installed) or use bridged networking option in the VM network settings.

---

### Post by borneseller on 2010-01-03
Sorry - - I've been working with XP on my laptop and loaded Ubuntu last week. I'm trying to migrate to Ubuntu and am using Ubuntu as the host and trying to get access XP (and more specifically my ACT database program) and wanted to access my Windows C drive. Any thoughts?

---

### Post by bootsofjoy on 2010-01-03
As howefield said, to access the files on your C drive you'll need to install Guest Additions (last item in Devices menu) and then set up a shared folder. (See [http://www.virtualbox.org/manual/UserManual.html#sharedfolders](http://www.virtualbox.org/manual/UserManual.html#sharedfolders) and [http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868))

Hope that helps.

Cheers,
Chiara

---

