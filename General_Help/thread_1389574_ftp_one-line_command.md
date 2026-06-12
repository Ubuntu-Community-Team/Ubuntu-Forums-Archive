---
title: "ftp one-line command"
date: 2010-01-24
forum: General Help
---

### Post by Muscovy on 2010-01-24
I'm trying to script a program to download a log from my server. I've chmodded the log to protect it, so I need to download it via ftp. However, I'm unable to find a way to pass the information needed all in one line (includes user/password).

---

### Post by .nedberg on 2010-01-24
Use wget

```

wget --ftp-user=your_username --ftp-password=your_password ftp://example.com/path/to/file

```

---

