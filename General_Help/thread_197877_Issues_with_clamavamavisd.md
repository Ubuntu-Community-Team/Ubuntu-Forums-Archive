---
title: "Issues with clamav/amavisd"
date: 2006-06-16
forum: General Help
---

### Post by Vermyndax on 2006-06-16
I'm having some bizarre issues getting postfix/amavisd/clamd to work together.
 
Amavisd claims that the virus scans are happening (even writes it to the headers of the message) but tests with EICAR-infected messages coming into the system always fail - the messages pass through just fine.
 
I'm at a loss.  It seems to be something to do with the scanning of the message file itself as amavisd-debug indicates that the file size is 0 bytes... but clamav.log shows *nothing* is going on, even with verbose logging turned on.
 
Clamav is running under the user amavisd, the permissions are set on the necessary directories, amavis is finding clamd correctly in startup... I don't know what's going on here.
 
Anyone have any new tips?

---

