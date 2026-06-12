---
title: "how to veiw the result of last clamscan scan?"
date: 2011-01-02
forum: General Help
---

### Post by Abhijit Navale on 2011-01-02
I scanned pen drive using clamscan and I closed the terminal after scanning without reading the result. Now one of my folder is missing in pen drive. I wanted to know if clamav deleted it. So I want to view the last scan result.

---

### Post by cheapie on 2011-01-02
Have you checked /var/log/clamav?

---

### Post by Abhijit Navale on 2011-01-02
In /var/log/clamav there are two files.
freshclam.log and freshclam.log.1
and both dont have anything of that 'scanning' result.
both have something about updating clamav database.

---

### Post by gandaran on 2011-01-02
> **Abhijit Navale said:**
> I scanned pen drive using clamscan and I closed the terminal after scanning without reading the result. Now one of my folder is missing in pen drive. I wanted to know if clamav deleted it. So I want to view the last scan result.
there is no scan results unless you specify the output to a file while running clamscan in command line.

type 'clamscan --help' for options

---

