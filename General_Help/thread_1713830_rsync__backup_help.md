---
title: "rsync / backup help"
date: 2011-03-24
forum: General Help
---

### Post by mbeltoft on 2011-03-24
I'm trying to backup my pictures to my google storage cloud. I have mounted it via webdav using the smestorage service.

I can create files and folders without problem in the mounted cloud but when I'm trying to use rsync to backup some files I get an error and nothing gets stored.


the command im using, I've tried a bunch of options but always with the same result: 
```
rsync -crv --size-only ~/Random/ ~/webdrive/Google

```The error:
```
rsync: mkstemp "/home/beltoft/webdrive/Google/.IMG_2304.JPG.IXQYG9" failed: No such file or directory (2)
rsync: mkstemp "/home/beltoft/webdrive/Google/.IMG_2305.JPG.AeUsTM" failed: No such file or directory (2)
rsync: mkstemp "/home/beltoft/webdrive/Google/.IMG_2306.JPG.61RJQw" failed: No such file or directory (2)
rsync: mkstemp "/home/beltoft/webdrive/Google/.Thumbs.db.2CcAFn" failed: No such file or directory (2)

sent 64562785 bytes  received 468 bytes  855142.42 bytes/sec
total size is 64553094  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

```any ideas why this happens and what to do to fix it?

---

### Post by mbeltoft on 2011-03-28
No one who can help me with this?

---

### Post by MrEgg on 2011-03-28
Have you tried using full instead or relative pathnames?
Have you tried rsync options -uav?

---

### Post by deconstrained on 2011-03-28
It looks like rsync is trying to make temporary files for the transfer and the WebDav service won't let it because they start with "."

---

### Post by fan0o on 2011-03-28
this could be permission problem. that file that fails to copy might denying permission to copy the content.

---

### Post by MrEgg on 2011-03-28
> **deconstrained said:**
> It looks like rsync is trying to make temporary files for the transfer and the WebDav service won't let it because they start with "."

Yes, I also think this could be a permission issue with the temp directory, by default on the destination server.

You could try --temp-dir=/tmp or create a temp directory on your remote drive and point --temp-dir= to that directory.

I don't have a google storage account unfortunately, so I'm not able to play around with those options.

---

### Post by SeijiSensei on 2011-03-28
Try creating a "dot" file manually on the cloud server like this:

```
touch ~/webdrive/Google/.test
```

If that fails, then rsync will fail, too.  It creates a hidden file on the remote share during the copying process.  Once the file has been transferred intact, rsync renames the temporary file to its actual name.

---

### Post by mbeltoft on 2011-03-28
> **SeijiSensei said:**
> Try creating a "dot" file manually on the cloud server like this:

```
touch ~/webdrive/Google/.test
```

If that fails, then rsync will fail, too.  It creates a hidden file on the remote share during the copying process.  Once the file has been transferred intact, rsync renames the temporary file to its actual name.

it fails :/ - however i can make a folder named .test without a problm.

can rsync do the copy without making it hidden first?

or is there another tool I can use for my backup

---

### Post by mbeltoft on 2011-03-28
Bump

No one with an idea of how I can get it to work?

---

### Post by MrEgg on 2011-03-29
> **mbeltoft said:**
> it fails :/ - however i can make a folder named .test without a problm.

can rsync do the copy without making it hidden first?

or is there another tool I can use for my backup

Try to modify the --temp-dir option. From what I understand, rsync could be trying to create temp files in a default location it doesn't have access to on your cloud server.

---

### Post by mbeltoft on 2011-03-29
Tried to set the --temp-dir option to a folder in my home dir but rsync still comes with the same error...

this really bugs me as i had hoped to be able to use it as a backup solution

---

