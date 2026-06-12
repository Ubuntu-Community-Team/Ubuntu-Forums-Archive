---
title: "Delete folders and files from main Ubuntu installation from when booted from live cd?"
date: 2010-09-29
forum: General Help
---

### Post by Quackers on 2010-09-29
Can someone tell me how please? I'm getting permission errors.
Thanks.

---

### Post by linux-hack on 2010-09-29
So if I understand your problem, you want to delete file and folders from you installed ubuntu system from a live CD ?

---

### Post by Quackers on 2010-09-29
Yes Sir :-)

---

### Post by linux-hack on 2010-09-29
Can you give the commands that you tried and may be the full error message that you get ?

---

### Post by Quackers on 2010-09-29
I haven't tried any commands yet. All I've done is use the search function in Nautilus to find the files (which doesn't give paths) and tried to delete them from within nautilus.

---

### Post by linux-hack on 2010-09-29
whell you shoud do it on the terminal ... 

log in as root and delete the files or folders that you want .

If you get Permission Errors is because you'r not root. And you don't have the right on all the files and dirs that you search for or want to delete.

---

### Post by Quackers on 2010-09-29
I don't have the file paths to do that. Nor the commands.

---

### Post by linux-hack on 2010-09-29
Ok explain exactly wha you want to do and what you want to find and I'll give you the commands an a way to find the paths ...

---

### Post by Quackers on 2010-09-29
I want to delete several grub files from my Ubuntu installation. I installed them on the linux partition by mistake.

---

### Post by linux-hack on 2010-09-29
If you delete grub files you'll not be able to boot correctly any more.Do you have dual boot ? you rely need to give more precise infos if you want me to help you faster. What partitions do you have ? are you in dual boot ? what files do you want to delete ? why delete them ? do you have grub installed in another partition ?

---

### Post by Quackers on 2010-09-29
I have a dual boot system. Vista is on sda, Ubuntu is on sdb. Grub is installed on sda and sdb. It is also installed in sdb2 (by mistake). I want to delete all the grub files on sdb2. I have purged grub (using drs305's tutorial) and intend to re-install grub after I have deleted the grub files on sdb2.
Maybe I should just re-install grub, boot into my normal system and delete the files from within.
Thanks for your assistance :-)

---

### Post by linux-hack on 2010-09-29
Glad to help :D

If your problem is resolved please put a RESOLVED in the title.

---

### Post by Quackers on 2010-09-29
I've got OCD and want to tidy up :-) and was wondering if I could do what I want to from within the live cd.

---

