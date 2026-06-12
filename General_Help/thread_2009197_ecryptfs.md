---
title: "ecryptfs"
date: 2012-06-24
forum: General Help
---

### Post by stuarta99 on 2012-06-24
Possible stupid question from a newbie here but I'm trying to get to grips with ecryptfs.

My query is that I have a Synology NAS which appears to do it's encryption in the ecryptfs system.  I also have a backup running to AmazonS3 which also shows the files as encryptfs.  I want to be able to check that I can manage these files should the NAS fail or need to recover via S3.

I've installed a ubuntu image in vmware and the ecryptfs tools, but can't work out how to decrypt a file that I have copied.

Hope someone can please advise

---

### Post by stuarta99 on 2012-07-13
Following on from this I've done the following and got a bit further.

[LIST]
[*]Copied 2 test files to memory stick and renamed folder to .private
[*]Fired up Ubuntu vm
[*]Opened Terminal
[*]sudo ecryptfs-recover-private
[*]entered my passphrase
[*]files extracted
[*]sudo nautilus
[*]I can then browse the files in the temp folder but they have retained their ecrypts_fnek_encrypted filenames
[/LIST]

Not sure if this is right or wrong as potentially I could have a whole volume or folders with subfolders to restore.  Not sure if it would work the same way.  

Is there a way to retain the filenames, or maybe it can't recognise them because they have gone via Amazon S3 backup.

Many thanks

---

