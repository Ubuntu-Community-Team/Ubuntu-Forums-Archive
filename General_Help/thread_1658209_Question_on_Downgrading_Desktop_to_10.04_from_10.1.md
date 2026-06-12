---
title: "Question on Downgrading Desktop to 10.04 from 10.10!"
date: 2011-01-02
forum: General Help
---

### Post by Rytron on 2011-01-02
Hi.

Would there be any possible problem with installing Ubuntu 10.04 over 10.10 on a manually partitioned PC?

I am using Ubuntu 10.10 and am considering going back to Lucid. I have 2 partitions ~ home and root. I presume there would be no problems with installing 10.04 over the 10.10 root partition? Will configuration files created by 10.10 in my home folder be usable by Ubuntu 10.04?

---

### Post by Topsiho on 2011-01-02
No problem at all.
You say you have two partitions: / and /home (why not a swap?)
/ contains your previous ***system*** installation, and will contain the pristine new Ubuntu. /home contains all the personal data of the users of your computer, and the personal configurations.

So while manually installing the new (or rather: other) version of Ubuntu you carefully reformat only the partition that contains the / mountpoint, and NOT that partition that contains /home (both mountpoints will have to be set again however, if I remember well, as well as the filesystems, be sure you ***know*** the filesystem of the present /home partition).

After the installing you'll have to update, and install the packages that you want, but are not included in the basic install.

:)

Topsiho

---

### Post by Vaphell on 2011-01-02
yup, make sure that you don't reformat /home and everything will be just fine.

Config files should work just fine, but if the newer version of some app was not backwards compatible, you may be forced to wipe related dotfiles.

---

### Post by Rytron on 2011-01-03
> **Topsiho said:**
> No problem at all.
You say you have two partitions: / and /home (why not a swap?)


Thanks Topsiho.

I decided not to use a swap partition because I have 3GB of Ram and read somewhere that swap is not really needed on computers with 2GB or more. Or am I wrong?

---

### Post by Rytron on 2011-01-03
> **Vaphell said:**
> Config files should work just fine, but if the newer version of some app was not backwards compatible, you may be forced to wipe related dotfiles.

Yes, I was thinking something along those lines. ):P

---

### Post by Bucky Ball on 2011-01-03
Right if you never suspend or hibernate. Wrong if you do. 2Gb /swap required for suspend.

---

### Post by Topsiho on 2011-01-03
Bucky Ball just said it already: you may need a swap. My idea is always to better be safe than sorry. I use the rule of thumb to have a swap that is twice my RAM, but I probably will agree with Bucky Ball :)

Topsiho

---

