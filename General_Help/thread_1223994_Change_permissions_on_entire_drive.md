---
title: "Change permissions on entire drive?"
date: 2009-07-26
forum: General Help
---

### Post by ubuntu1sttimer on 2009-07-26
I have a second hard drive that is used for file storage. There are no linux executables on it. 

My question, how do I change the permissions on the entire drive to allow users to read, write, and obtain full directory listings? That includes file/directory name, size, and when created.

Yes, I understand that is not something most would want to do but in this case, it needed to be able to work with the files on this drive.

---

### Post by credobyte on 2009-07-26
```
sudo chown -R user:user /media/mountpoint

```

Replace user:user with your actual username and set a proper mount point ( path to your HDD ).

---

