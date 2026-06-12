---
title: "&quot;550 Failed to change directory.&quot;"
date: 2009-06-26
forum: General Help
---

### Post by Muscovy on 2009-06-26
I set up an ftp server using vsftpd, and started getting the error "550 Failed to change directory." right from the start. How can I solve this?

---

### Post by siryuhan on 2009-06-26
Sounds like you haven't properly configured the permissions (error 550 = permission denied). You may want to search online for "vsftpd configuration" or consult the man page (man vsftpd) for configuration info.

---

### Post by Muscovy on 2009-06-26
I looked through, but the onlt apparent cause I could see was that the default for listen is NO, but on mine it's already yes.

---

