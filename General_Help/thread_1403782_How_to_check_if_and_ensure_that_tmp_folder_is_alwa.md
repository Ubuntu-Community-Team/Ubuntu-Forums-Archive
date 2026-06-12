---
title: "How to check if and ensure that /tmp folder is always deleted at shutdown?"
date: 2010-02-10
forum: General Help
---

### Post by pstein on 2010-02-10
How can I check if Ubuntu deletes all the content in /tmp folder at each shutdown
(without trial and error)?
 
How can I tell Ubuntu to delete it?
 
What about the deletion of other tracks like swapfile at shutdown?
 
Peter

---

### Post by colobix on 2010-02-10
Why would you do that?
If you want to save some space, then open ubuntu recovery mode from Grub and from there you choose "try to free space".
Browser tracks can be deleted from the tools menu.
HOpe this helped you.

---

### Post by AntonioPT on 2010-02-10
Ubuntu deletes /tmp folder at shutdown. PERIOD. Always deletes it. Don't worry. It will be deleted. PERIOD. (:D)

---

### Post by FearfulJesuit on 2010-02-10
Hi Peter,
my solution to this would be to generate a script that deletes those folders on startup/login and put it into your binary folder. I understand you want to do this on shutdown. But I am not sure how to execute the command on shutdown. 

You could always just shutdown through terminal and delete at the same time

Pseudo-code

shutdown -h now && rm -r /tmp /usr/tmp && rm -r swapfile folders

Anyone want to comment on the pseudo code. I wonder if you could make this into a binary script and link it to the shutdown button.

---

### Post by Richard1979 on 2010-02-10
> **FearfulJesuit said:**
> Hi Peter,
my solution to this would be to generate a script that deletes those folders on startup/login and put it into your binary folder. I understand you want to do this on shutdown. But I am not sure how to execute the command on shutdown. 

You could always just shutdown through terminal and delete at the same time

Pseudo-code

shutdown -h now && rm -r /tmp /usr/tmp && rm -r swapfile folders

Anyone want to comment on the pseudo code. I wonder if you could make this into a binary script and link it to the shutdown button.

What's the point?
Just mount it as tmpfs.

```

/etc/fstab
tmpfs      /tmp      tmpfs      defaults       0   0
```

---

### Post by colobix on 2010-02-10
OR just never mind since ubuntu deletes tmp anyway.

---

### Post by Richard1979 on 2010-02-10
> **colobix said:**
> OR just never mind since ubuntu deletes tmp anyway.

Or that.

---

