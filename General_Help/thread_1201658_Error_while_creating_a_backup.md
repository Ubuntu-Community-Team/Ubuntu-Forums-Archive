---
title: "Error while creating a backup"
date: 2009-07-01
forum: General Help
---

### Post by HuBaghdadi on 2009-07-01
Hey,
I use this command to backup:
sudo tar cvpzf hubaghdadi-1-7-09.tgz /home/hubaghdadi/
But I'm getting this error:
tar: Error exit delayed from previous errors
What is going wrong?
Thanks.

---

### Post by colau on 2009-07-01
> **HuBaghdadi said:**
> Hey,
I use this command to backup:
sudo tar cvpzf hubaghdadi-1-7-09.tgz /home/hubaghdadi/
But I'm getting this error:
tar: Error exit delayed from previous errors
What is going wrong?
Thanks.
Where did you put this *hubaghdadi-1-7-09.tgz?*

---

### Post by upbeat.linux on 2009-07-01
After running the command you don't see errors?  If you scroll up?  Was the tar created?

This usually just means that tar hit an error but kept going.

Try piping the output to a file and then grep for errors:

```
tar cvpzf hubaghdadi-1-7-09.tgz /home/hubaghdadi/ > results.txt
```

You may need to exclude the files it errors on.

---

### Post by WRDN on 2009-07-01
To create a Gzip archive of your home folder, use the command:

```
tar czf backup.tar.gz ~
```

Add the "-v" option to make it verbose (print files processed).

Try looking in the system logs (at /var/log) to find the "previous errors".

---

