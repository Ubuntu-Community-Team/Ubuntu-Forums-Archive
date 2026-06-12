---
title: "SSH Working but not SFTP"
date: 2009-08-04
forum: General Help
---

### Post by zzzBrett on 2009-08-04
SSH to my OpenSSH server works just fine, and a few weeks ago so did SFTP (if i recall correctly), but now, attempting to use filezilla to connect gives me the error:

```
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server
```

Why might this happen?

---

### Post by zzzBrett on 2009-08-04
I think it may be a filezilla problem actually.  In terminal, I CAN log in using:

```
sftp user@server
```

Maybe a wrong setting in filezilla?

---

### Post by zzzBrett on 2009-08-04
> **zzzBrett said:**
> I think it may be a filezilla problem actually.  In terminal, I CAN log in using:

```
sftp user@server
```

Maybe a wrong setting in filezilla?

Fixed it.  I deleted the stored 'site' settings, and recreated a connection.  I still do not know what happened, though.

---

