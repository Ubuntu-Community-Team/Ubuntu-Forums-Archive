---
title: "Wubi for 10.10 - question"
date: 2010-10-10
forum: General Help
---

### Post by Prohibited on 2010-10-10
Waiting for the 10.10 release and I'm just wondering, will the wubi for 10.10 be released today as well?

Running XP at the moment and planned on burning it to CD then splitting the partition, I had a look and I have no unused CDs/DVDs to burn it to which is why I need it.

---

### Post by sendblink23 on 2010-10-10
> **Prohibited said:**
> Waiting for the 10.10 release and I'm just wondering, will the wubi for 10.10 be released today as well?

Running XP at the moment and planned on burning it to CD then splitting the partition, I had a look and I have no unused CDs/DVDs to burn it to which is why I need it.

I think if you simply download the final release 10.10 iso and place it in the same directory of the Wubi.exe file... it should install that iso instead of going online to download any other version

---

### Post by pbelfi on 2010-10-10
> **sendblink23 said:**
> I think if you simply download the final release 10.10 iso and place it in the same directory of the Wubi.exe file... it should install that iso instead of going online to download any other version
Nope by putting the iso in the same directory doesn't work...It still wants to get 10.04.....This has been an ongoing problem with the last two releases of Ubuntu....I think you may just have to wait for the Wubi 10.10 in order to install via Wubi.

---

### Post by ultranoize on 2010-10-10
I had 10.04 installed and did a release upgrade and now ubuntu is not bootable. Any ideas why this happened?

---

### Post by afroze9 on 2010-10-10
the way i installed it is that you use an image mounting tool such as daemon tools or alcohol 52% to mount the 10.10 image 
then open it and start wubi

---

### Post by WorMzy on 2010-10-10
Is there a reason why you can't just install to a partition? You wouldn't have to wait for a Wubi installer, and you'd get a much more stable operating system (that doesn't break every time there's a kernel update).

---

### Post by Mark Phelps on 2010-10-10
> **ultranoize said:**
> I had 10.04 installed and did a release upgrade and now ubuntu is not bootable. Any ideas why this happened?

Had you bothered to read the Release Notes, you would have seen the writeup that clearly indicated that upgrading Wubi would fail.

Rule of thumb .. NEVER upgrade before you read the Release Notes.  If you go to distrowatch.com to get your version upgrades, you will see that they always bundle the URLs into the same location. Makes it easy to find and read the Release Notes.

---

### Post by Mark Phelps on 2010-10-10
I would stay away from Wubi 10.10 for now ...

From the Release Notes (which, apparently, no one bothers to read!):

Known Issues:

> The Wubi Windows installer was reported to be unable to open Windows' boot configuration data store in some (but not all) cases. Investigation of the problems are ongoing (613288)

You cannot upgrade if wubi is installed to a partition other than Windows. (610898,653134) 

---

### Post by ultranoize on 2010-10-10
> **Mark Phelps said:**
> Had you bothered to read the Release Notes, you would have seen the writeup that clearly indicated that upgrading Wubi would fail.

Rule of thumb .. NEVER upgrade before you read the Release Notes.  If you go to distrowatch.com to get your version upgrades, you will see that they always bundle the URLs into the same location. Makes it easy to find and read the Release Notes.

Mark you are right, I didn't bother to read. I should know better...

---

### Post by ultranoize on 2010-10-10
WorMzy, I'llprobably give it a go... thing is I do not want to screw up my new computer....

---

