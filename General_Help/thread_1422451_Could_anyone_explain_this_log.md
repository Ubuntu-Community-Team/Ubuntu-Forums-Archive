---
title: "Could anyone explain this log?"
date: 2010-03-05
forum: General Help
---

### Post by bungtrader on 2010-03-05
Hello,

I have a friend who's worried his computer is being hacked into based on this log, he's taken a screenshot of it and doesn't quite understand what it means.

If anyone could explain to me what is going in this picture, it would be greatly appreciated.

He was particularly concerned about the "using root" bit

Thankyou for your time, apologies if I've posted this in the wrong section.

---

### Post by jmichelsen on 2010-03-05
Where was this log located and what initiated it? It looks to me like this was written on initial system install and the installation of packages was using root to create the groups it needed to operate. 

There isn't anything there that would suggest outside intrusion in my opinion.

---

### Post by audiomick on 2010-03-05
Without being able to say for sure, I would agree with jmichelsen. It looks like a system  install log, and all the "using root" entries come before the entries regarding installing things like the filesystem.

There are date/time stamps all the way down. Do they show the date on which your friend did  his installation?
I don't think he needs to be worrying.

---

### Post by Kevbert on 2010-03-05
Have to agree with the previous poster. It looks like the log was generated while installing openSuse and the files are just CD system install files. The timestamp should be when the system was installed on the PC. The numbers at the end of each line look like checksum values to check the integrity of the respective files.

---

### Post by doas777 on 2010-03-05
yeah, no need to fear. when you install certian services, they look for predefined account names in case the admin wishes to run the service as a specific service user (good for security but harder to deploy).  thus the service looks for a user named 'news' but uses root if the admin has not seen fit to create or configure a 'news' account.

---

