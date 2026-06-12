---
title: "Is it possible to change permissions on a mac-formatted hd using ubuntu?"
date: 2010-08-31
forum: General Help
---

### Post by user1397 on 2010-08-31
I have an external hard drive which has the mac os filesystem (hfs+) and it is read-only.  I was trying things like 'sudo chmod 777 /path/to/my/drive' or 'sudo chmod -R u+w /path' but it wasn't working.

I just want to be able to have write permissions, anyone know how?

---

### Post by Bachstelze on 2010-08-31
Is your drive HFS or HFS+? Journaled or non-journaled?

---

### Post by user1397 on 2010-08-31
> **bachstelze said:**
> is your drive hfs or hfs+? Journaled or non-journaled?

hfs+

---

### Post by Bachstelze on 2010-08-31
> **ubuntuman001 said:**
> hfs+

Then it's probably journaled, and Linux mounted it read-only. You can mount it read-write with --force, but it will ignore the journal.

---

### Post by user1397 on 2010-08-31
> **Bachstelze said:**
> Then it's probably journaled, and Linux mounted it read-only. You can mount it read-write with --force, but it will ignore the journal.
i'm having the darndest time trying to figure out how to mount it with the force option... any specific examples?

let's say my path is /media/Passport250

---

### Post by user1397 on 2010-08-31
well not that i solved anything, but i just made enough space on my desktop to copy all the files from the hfs+ drive, and then i formatted the hfs+ drive in ubuntu to fat32, then moved back all the files.

i don't really think i should mark this as solved since my original question is still unanswered, but o well what the heck :)

---

