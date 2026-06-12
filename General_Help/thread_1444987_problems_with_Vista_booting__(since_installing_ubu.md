---
title: "problems with Vista booting  (since installing ubuntu)"
date: 2010-04-02
forum: General Help
---

### Post by CaptainWraith on 2010-04-02
since ive installed ubuntu on my laptop vista has failed to boot numerous times.  it gets part way through booting and then restarts.  is this a problem caused by installing ubuntu and how can i fix it? also when it does boot it takes forever it seems.

---

### Post by CaptainWraith on 2010-04-02
surely someone knows something about this

---

### Post by Mark Phelps on 2010-04-02
Did you use the Ubuntu installer to shrink the Vista partition, installing Ubuntu in side-by-side mode?

If so, you most probably corrupted your Vista OS partition in the process.  You will have to repair it before it will boot again.

Since you probably do NOT have a Vista repair CD, use the link below to download the proper Vista Repair CD image and burn that to CD.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Once you have that CD in hand, boot from it, and select Startup Repair.  You may have to do that as many as three times in order to completely repair Vista.

After you do that, GRUB will be removed from your MBR.  So, you will have to reinstall GRUB.

---

### Post by CaptainWraith on 2010-04-07
how would i go about reinstalling grub?

---

### Post by Calash on 2010-04-07
A good guide to follow for fixing GRUB

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You will need a LiveCD to do this.  I like to print out the instructions before hand as well...just incase I have issues getting out to the internet when in the LiveCD.

---

