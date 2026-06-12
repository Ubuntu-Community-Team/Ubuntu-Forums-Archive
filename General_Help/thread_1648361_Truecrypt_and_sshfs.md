---
title: "Truecrypt and sshfs"
date: 2010-12-18
forum: General Help
---

### Post by anathema415 on 2010-12-18
Hi all,
I'm in the process of setting up a truecrypt container on a remote host for secure backups. I've setup sshfs to mount it, Truecrypt to open the container, it's all good. Now comes the really stupid question part. Do I just add the files I want to backup to the mounted folder and they'll be transfered? Is it that simple?

Thanks!

---

### Post by noah++ on 2010-12-18
It's that simple. But why not test it yourself? Add a file to the folder, unmount and disconnect. If the file is there next time you connect and mount, ...

---

### Post by anathema415 on 2010-12-18
> **noah++ said:**
> It's that simple. But why not test it yourself? Add a file to the folder, unmount and disconnect. If the file is there next time you connect and mount, ...

Thanks! I agree with you on the testing thing, I'm just the kind of person who feels much better knowing things ahead of time.

---

### Post by noah++ on 2010-12-18
Understood! Both ways of knowing are important.

---

### Post by anathema415 on 2010-12-18
Okay, I cannot open the container file. I attempt to mount
it through truecrypt, I enter the containers password, I get a second
password prompt for admin or user  and no matter what I put in I get a
'Permission Denied' error. I am a member of the fuse group...I'm really confused.
Any help appreciated please.

---

### Post by noah++ on 2010-12-19
Any luck with this yet? If not, I am curious to know whether you have the same problem mounting a locally stored TC container.

---

### Post by anathema415 on 2010-12-20
> **noah++ said:**
> Any luck with this yet? If not, I am curious to know whether you have the same problem mounting a locally stored TC container.

Yes. It was out of my control. The service I'm using (datastorageunit) had to manually give me ownership of the container. He does this so that we don't have to upload the container and then our files. Changing this to solved.

---

