---
title: "Backup software for Ubuntu - which one?"
date: 2010-07-25
forum: General Help
---

### Post by theindustry on 2010-07-25
Hi everybody,

I have spent some time testing out different backup solutions for my small home office during the last weeks, but still haven't found anything that have been working out too well yet. We can definitely work with a non-GUI script if that's what it takes, if only the requirements are fulfilled:

- Upload to Amazon S3 Europe. We get unbelievable slow uploading speed to US, so uploading 400+ GB of data will not be happening anytime this year...

- Incremental backups - only changed files shall be uploaded or we will have a big bill from Amazon in the end of each month..

- Files should not be uploaded in one big per-folder archive. This is not efficient at all, since if we change one file in a subfolder, a huge two-digit GB sized file would have to be uploaded during next backup. Not good for economy again, or traffic overhead on our internet connection.

What options are available to us?

Thanks!

---

### Post by rubylaser on 2010-07-25
You could just use something like rsnapshot, or incremental rsync backups like this...
[http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")

Either way, you'll only have to push the bulk of your data to Amazon once, after that, it either method will just send incremental changes.

If you have any questions, or these aren't what you're looking for, let me know.

---

