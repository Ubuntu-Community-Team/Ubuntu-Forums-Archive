---
title: "Unix FTP from command line halts"
date: 2012-02-16
forum: General Help
---

### Post by CrusaderAD on 2012-02-16
I'm ftp'ing down files from a remote server from the command line. Once in a while the process just stops dead in its tracks during the download process and not all files get downloaded. Any idea on how to prevent this?

---

### Post by Khayyam on 2012-02-16
> **CerealCypher said:**
> I'm ftp'ing down files from a remote server from the command line. Once in a while the process just stops dead in its tracks during the download process and not all files get downloaded. Any idea on how to prevent this?

I'd suggest using a client that support resume. The standard 'ftp' client is .. to be polite .. wigglewonk. The client '[lftp](http://lftp.yar.ru/)' has support for resume, sftp, tab completion, parallel downloads, etc, etc. There are other CLI clients out there but in my experience lftp is the best.

HTH ... khay

---

### Post by Lars Noodén on 2012-02-16
ncftp is good too.

---

### Post by CrusaderAD on 2012-02-16
> **Lars Noodén said:**
> ncftp is good too.

I just checked this out, I didn't see an "mget" option. I need to research it more, thanks for the suggestions.

---

### Post by Khayyam on 2012-02-16
> **CerealCypher said:**
> I didn't see an "mget" option. I need to research it more, thanks for the suggestions.

Not to keep on plugging lftp but it supports mget (and 'get ""'), you can also 'mirror <directory>' for recursive downloads.

HTH ...

---

