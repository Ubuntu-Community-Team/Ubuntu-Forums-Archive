---
title: "tar errors: Not sure the cause/solution... help?"
date: 2012-03-11
forum: General Help
---

### Post by daweefolk on 2012-03-11
I downloaded a .tar.gz file and while trying to tar xzvf it, I ran across a slew of errors. I ran it with 2> to save it to a file and copied it into a pastebin. 
It can be found at [http://pastebin.com/bry9M3FM](http://pastebin.com/bry9M3FM). If someone could check it to see what the problem may be, I'd greatly appreciate it. 
I saw the "permission denied" and ran sudo chown -R /home/jordan jordan to make myself the owner of all my files, and still got the same errors.
I am running debian, but I don't think that would make a difference

---

### Post by Dreamer Fithp Apprentice on 2012-03-11
What type of file system was it on when you tried to extract it, etc.? Sometimes they need to be on an extN file system to work correctly because the FAT and NTFS systems do not have the same sort of permission system.

---

### Post by daweefolk on 2012-03-11
If I remember right it's an ext3

---

### Post by Dreamer Fithp Apprentice on 2012-03-12
If you don't have any FATs or NTFSs or some exotic file system on the system and are certain you extracted on some common linux file system, say an ExtN where N is > or = 2, I think you can dismiss my suggestion. Good luck. I'm not geek enough to help in that case.

---

### Post by daweefolk on 2012-03-12
If I run gunzip I get the plain .tar file...
then when i try to extract the tar file i get the errors. 
It happens with any tar file, I replicated it with 5 or so compressed files from different locations

---

