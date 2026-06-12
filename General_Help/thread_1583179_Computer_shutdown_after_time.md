---
title: "Computer shutdown after time"
date: 2010-09-27
forum: General Help
---

### Post by jodlajodla on 2010-09-27
Hello!
Is in Ubuntu option, that can shutdown computer after time or at defined time?

I think: I have turned on my computer and I will need to automaticly shutdown computer after 4 hours or at 21.00 pm.

Is there option, if computer can automatically turn on at defined time?

Thanks for all replies! :)

---

### Post by andrewthomas on 2010-09-27
```
sudo shutdown -h +240
```

this will shutdown after 240 minutes

---

### Post by jodlajodla on 2010-09-27
> **andrewthomas said:**
> ```
sudo shutdown -h +240
```this will shutdown after 240 minutes

then i will need opened terminal?

---

### Post by andrewthomas on 2010-09-27
Yes.  Enter the command in the terminal and leave the terminal open.

---

### Post by jodlajodla on 2010-09-27
What about automatticaly turn on? 

Thanks! :)

---

### Post by The Cog on 2010-09-27
I don't think it's possible to automatically turn on. When powered off, the OS isn't running, not able to do anything.

---

### Post by ajgreeny on 2010-09-27
For a specific time of shutdown it is ```
sudo shutdown -h 23:30
``` which will shutdown at 11.30pm.

See ```
man shutdown
``` for all details.

---

### Post by othiena on 2010-09-27
In the bios there is usualy a setting that will start the computer on at a specific time. If you time ```
crontab -e
``` may be able to have to so it will exicute ```
sudo shutdown now
```

---

### Post by jodlajodla on 2010-09-28
But how can I do this if there is someone who is normally user?

Thanks! :)

---

### Post by ajgreeny on 2010-09-28
Users who are not in the **admin** group can not do this without making shutdown not require password entry.  You will need to change the system to make this possible, but I'm afraid I can't remember exactly how.

---

