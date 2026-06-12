---
title: "Have lost some priveleges?"
date: 2009-12-27
forum: General Help
---

### Post by hakimoerton on 2009-12-27
I am first user with admin privileges but, after some alterations with xorg (update with xorg-edgers, remove and reinstall because of repeated crashes), I seem to have lost some privileges. I can still sudo but am unable to edit users' rights or load a partition on a second hdd that I normally have access to.

Any suggestions as to where I can start looking? I don't know which log files or other info that would be useful to upload.

I am on Karmic on an intel based pc. Was working fine until xorg-edgers was installed to enable yWriter5 under mono (problem displaying fonts).

Hakim, with thanks.

---

### Post by hakimoerton on 2009-12-28
Surely somone can offer some words of wisdom?

Hakim

---

### Post by reiki on 2009-12-28
I think my ability to manage users and groups through the system->Administrative->Users and Groups app stopped working after I installed the fglrx drivers. 

That made no sense to me so I dismissed it as being coincidental. YOU have changed xorg "drivers" and now experience the same issue.

There are a LOT of permissions problem in Karmic, apparently, and they seem to manifest in different ways. The inabilty to manage users and groups seems a common manifestation. 

I still haven't figured out how to manage groups in the users-admin app. Even as root.

---

### Post by drdanielfc on 2009-12-28
can you change read/write privelages in system files (gksudo nautilus)?

---

### Post by hakimoerton on 2009-12-28
hakim@hakim-desktop:~$ gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:1821): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1821): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1821): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Error: Bad annotation destination
Error: Bad annotation destination
Error: Bad annotation destination
Error: Bad annotation destination
Error: Bad annotation destination
Error: Bad annotation destination
Error: Bad annotation destination
Error: Bad annotation destination
Error: Bad annotation destination
Error: Corrupted memory profile
Error: read ICCBased color space profile error

** (process:1910): WARNING **: Couldn't change nice value of process.
Error: Couldn't open file '/home/hakim/Documents/ubuntupocketguide-v1-1.pdf': Permission denied.
Error (0): Unknown filter 'Crypt'

--- Hash table keys for warning below:
--> hakim
--> root
--> inode/directory
--> l2051
--> Hakim Oerton
--> l2049

(nautilus:1821): Eel-WARNING **: "unique eel_ref_str" hash table still has 6 elements at quit time (keys above)

(nautilus:1821): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 7 elements at quit time
Shutting down nautilus-gdu extension
hakim@hakim-desktop:~$

Thanks for your interest
Hakim

---

### Post by hakimoerton on 2009-12-30
Come on guys and gals, surely someone can make sense of the message above?

Any help appreciated, and yes I know it is still the silly season. :)

All the best
Hakim

---

