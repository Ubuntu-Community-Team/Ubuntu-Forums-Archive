---
title: "Ubuntu File Transfer Problems"
date: 2010-05-13
forum: General Help
---

### Post by semberton on 2010-05-13
Hi,

My company is trying to get an SVN dump file off our Ubuntu server. This has proven surprisingly difficult. 

We first tried to scp the file onto a local machine, but this seemed to be searching for the destination folder on the server instead of the local machine.

We tried setting up an ftp server on a local machine and using ftp to transfer the file, but although the Ubuntu server could ping the ftp server, it would not connect. 

We tried using a Flash drive or CD-R on the server to copy the file directly, but the drivers for both hardware solutions were not installed on the server. 

Any suggestions? I'm relatively inexperienced with Unix, so if anything's unclear or if I need to provide some more details, please let me know. Thanks,

-Steve

---

### Post by blazemore on 2010-05-13
> **semberton said:**
> Hi,
 We first tried to scp the file onto a local machine, but this seemed to be searching for the destination folder on the server instead of the local machine.

-Steve

That sticks out like a sore thumb.
Here's the correct usage for scp, are you sure you're doing it right?
```

scp *user*@*host*:*/*directory*/*SourceFile TargetFile

```

---

