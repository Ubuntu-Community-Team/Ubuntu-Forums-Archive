---
title: "The optimal family computer - QNAP TS-119"
date: 2010-07-09
forum: General Help
---

### Post by chattanoga on 2010-07-09
I have bought a QNAP TS-119, and when going from 9.10 to 10.04 I want to create a failproof family computer that can be used by both computer noobs and small kids.
I want the normal user (FAMILY) to automatically be able to use all files on the NAS, but not be able to destroy anything (ie edit or delete files).
The administrator (DADDY) should be the only user being able to make changes on the NAS.

In which end shoud I start?
Shall I configure the NAS first and create all folders (music, videos, pictures, documents etc,)
Or shall I start by installing (fresh) 10.04 first?
Where do I set the user restrictions - in Ubuntu or the NAS (or both)?

Anyone with experience of QNAP; how did you configure yours, does it work as expected?

Thank you in advance

---

### Post by audiomick on 2010-07-09
Hallo.
I don't know this stuff all that well, so wait for some more advice, but here is my 2 cents worth anyway.

You need to set the permissions on the files on the NAS to be owned by DADDY, and with read only permission for others.

I think it effectively doesn't make a difference whether you install the computer first, or set up the NAS. They are two different entities in the network, and what you do to one should not make any difference to the other.

As far as I know, you need to set the permissions in the file system of the NAS (is it a linux based NAS?) and not on the Ubuntu machine.

---

### Post by nothingspecial on 2010-07-09
You need to set the permissions on all files and folders to 755

```
sudo chown -R daddy:daddy /path/to/NAS
chmod -R 755 /path/to/NAS
```

This will only work on a file system that support linux file permissions. If not you have to set the permissions at mount time. To do that read this

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

