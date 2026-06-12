---
title: "how can I restore my /etc/apt/sources.list with the back up?"
date: 2009-09-27
forum: General Help
---

### Post by honey toast on 2009-09-27
I know that this is probably a super dooper easy task, but I have tried a few different approaches...rename the file to the backup, and overwriting the current file without any avail. My dilemma comes from trying to update my repository, and instead of updating it, I actually back peddled into only having access to medibuntu, which is not all that I had initially.Fortunately, I made a backup of the file before tampering with it.   So my question is, how can I restore the back up from nano? or just plain restore the source.list PERIOD!

---

### Post by akakingess on 2009-09-27
I may be the only one, but I am not quite sure what you did and what you are trying to get back to.  Could you possibly clarify just a little more for the slow people out there (me).

---

### Post by astrakhan on 2009-09-27
if you already made a backup you shouldn't need nano to restore it. have you tried this

sudo mv /absolute_path_to_backup_file /etc/apt/sources.list

---

### Post by honey toast on 2009-09-27
Thank you AstraKhan. You have good perception, and your solution worked. I could have sworn I tried to do that though.

---

### Post by wilee-nilee on 2009-09-27
I am glad you fixed the problem, I just cut and paste it into a text program and save it to save time, and then I have a copy of the list to use on another computer that is running the same OS. Another thing some people know is that if you need to reinstall your whole system you can save the synaptic files and just have the new install read that and install.

---

### Post by akakingess on 2009-09-27
> **honey toast said:**
> Thank you AstraKhan. You have good perception, and your solution worked. I could have sworn I tried to do that though.

Thanks for the jab at my "perception", i was only trying to help.

---

