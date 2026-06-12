---
title: "How to schedule e2fsck"
date: 2010-10-09
forum: General Help
---

### Post by Emanuele_Z on 2010-10-09
Hi guys,

given that e2fsck can't run on mounted partition, how is it possible to schedule it with a customized command line?

Thanks again,
Cheers, :)

---

### Post by jv2112 on 2010-10-09
[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/]("http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/")


Try this.

---

### Post by Emanuele_Z on 2010-10-09
> **jv2112 said:**
> [http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/]("http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/")


Try this.

I'd like to specify the *-c* at command line...

Cheers,

---

### Post by Rubi1200 on 2010-10-09
Take a look through this thread (it is old but most of it should be relevant or can be changed to suit your needs):
[http://ubuntuforums.org/showthread.php?t=590123&highlight=change+fsck+frequency](http://ubuntuforums.org/showthread.php?t=590123&highlight=change+fsck+frequency)

Post # 6 has some good options in my opinion.

Hope this helps.

---

### Post by mcduck on 2010-10-09
> **Emanuele_Z said:**
> Hi guys,

given that e2fsck can't run on mounted partition, how is it possible to schedule it with a customized command line?

Thanks again,
Cheers, :)

The simplest way is to run "sudo touch /forcefsck". All drives configured in fstab will be checked during the next boot.

---

### Post by dcstar on 2010-10-09
> **mcduck said:**
> The simplest way is to run "sudo touch **/forsefck**". All drives configured in fstab will be checked during the next boot.

Even better if you SPELL it correctly when giving explicit instructions to someone:

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

---

### Post by Emanuele_Z on 2010-10-10
> **mcduck said:**
> The simplest way is to run "sudo touch /forcefsck". All drives configured in fstab will be checked during the next boot.

Apart spelling issue, with what option does that e2fsck get executed?
Does it get executed with *-c* as well?
That is my issue.

Cheers,

---

### Post by mcduck on 2010-10-10
> **Emanuele_Z said:**
> Apart spelling issue, with what option does that e2fsck get executed?
Does it get executed with *-c* as well?
That is my issue.

Cheers,

So you want to check for bad blocks?

I don't think the default automatic check would do that. You should probably just boot the machine with a live-CD (or USB drive) and run the fsck manually from there. :)

---

### Post by Emanuele_Z on 2010-10-10
> **mcduck said:**
> So you want to check for bad blocks?

I don't think the default automatic check would do that. You should probably just boot the machine with a live-CD (or USB drive) and run the fsck manually from there. :)

Any Ubuntu LiveCD/USB (i.e. Ubuntu 10.04) should do the trick, right?
Do I have to do something particular to run in order not to **** up my system?

Cheers!
Ema! :)

---

### Post by CharlesA on 2010-10-10
> **Emanuele_Z said:**
> Any Ubuntu LiveCD/USB (i.e. Ubuntu 10.04) should do the trick, right?
Do I have to do something particular to run in order not to **** up my system?

Cheers!
Ema! :)

Any livecd should work, however, I don't know if 8.04 supported ext4 or not.

You just need to have the drive you want to check unmounted.

---

### Post by dcstar on 2010-10-10
> **Emanuele_Z said:**
> Apart spelling issue, with what option does that e2fsck get executed?
Does it get executed with *-c* as well?


No way, that could take hours to run and is totally inappropriate for a mount-time function that is there to provide a little extra insurance of filesystem integrity whilst not impacting on availability time too much.

---

### Post by Emanuele_Z on 2010-10-10
> **dcstar said:**
> No way, that could take hours to run and is totally inappropriate for a mount-time function that is there to provide a little extra insurance of filesystem integrity whilst not impacting on availability time too much.

Indeed I know, it took 3 hours and 12 minutes to complete on a 750 GB disk.
Btw it wrote on the log *Updating bad sector list...* (or something similar).
How do I know how many bad sectors do I have?
Any idea?

Cheers,

---

### Post by CharlesA on 2010-10-10
You can use smartmontools to see if there are any badblocks found on the drive.

---

### Post by Emanuele_Z on 2010-10-10
> **CharlesA said:**
> You can use smartmontools to see if there are any badblocks found on the drive.

I guess I have to install them right? Those are not part of Ubuntu 10.04, am I correct?

Cheers,

---

### Post by CharlesA on 2010-10-10
> **Emanuele_Z said:**
> I guess I have to install them right? Those are not part of Ubuntu 10.04, am I correct?

Cheers,

It is in the repos.

```
sudo apt-get install smartmontools
```

---

