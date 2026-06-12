---
title: "FTP user limit the Permission"
date: 2011-04-11
forum: General Help
---

### Post by suresh_vandiyur on 2011-04-11
Hi All,

I need set the limit of the permission to the FTP users like they only do upload and download only dont delete any files. please help me. how to do this.

Thank you,

Regards,
Suresh

---

### Post by sam123 on 2011-04-11
It's not straightforward. If users have write permission, they can delete files as well. One option is running a cron job to run at intervals to chmod -w all files currently in the directory.

---

### Post by suresh_vandiyur on 2011-04-11
> **sam123 said:**
> It's not straightforward. If users have write permission, they can delete files as well. One option is running a cron job to run at intervals to chmod -w all files currently in the directory.

Thanks for your response.in cronjob file what are commands i need add how it works. please tell me.

Thank you,

Regards,
Suresh

---

