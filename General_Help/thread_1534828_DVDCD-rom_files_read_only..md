---
title: "DVD/CD-rom files read only."
date: 2010-07-20
forum: General Help
---

### Post by lostcub on 2010-07-20
Not sure if anyone will answer this one, but here goes.

I am not really new to linux, but I am with Ubuntu since Debian appears to be abounded now. The only issue I am having is accessing files on CDs and DVDs burned from another OS such as Windows and Debian. The files I cannot access are labeled as "read only" What is kind of ironic is the "read only" under the same name, but still they can not be viewed. I even tried using root, but even root and sudo users are blocked from seeing/executing them.

Is there a command I can use to "force" it to be read/write? the standard way does not work.

Why would viewing be blocked when even others are allowed to "read"?... Not to mention the files are owned but the same name as my account. In both Debian and Windows, read only means can not be modified, in Ubuntu it's blocked.

I've googled this in many paraphrases, even this forum had no mention of accessing "read only" files on DVD/CDs.

all I'm trying to do is, copy my back up files (mostly media and photos) onto the hard drive.

Rodney

---

### Post by robsoles on 2010-07-20
Should be pretty much the same as accessing in any other OS so I'm going to ask you the questions that occurred to me when I read your post:

Have you allowed your newly installed Ubuntu OS to do all of it's updates?

Was this disc finalised as closed session or was it a windows open session?

Have you checked out other data discs from your collection - do all discs do this or just this one?

---

### Post by varunendra on 2010-07-20
This....
> **robsoles said:**
> Have you allowed your newly installed Ubuntu OS to do all of it's updates?

Was this disc finalised as closed session or was it a windows open session?

Have you checked out other data discs from your collection - do all discs do this or just this one?
....plus....
Are you able to successfully create an iso image of the CD/DVD (using brasero or a similar tool)?

If even root is unable to copy the files, then most probably the CD/DVD has some technical or physical defect and hence should behave the same way on other OSes as well.

To try its behavior on other OSes, you may try VirtualBox to install them & access the CD from within them.

---

