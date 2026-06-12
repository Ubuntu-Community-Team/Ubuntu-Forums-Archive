---
title: "Separate /home partition makes upgrading easier?"
date: 2010-10-12
forum: General Help
---

### Post by jcd29 on 2010-10-12
If I have a 20GB (or more, I dunno what's enough) root (/) partition, and a 200GB /home partition, would that make it easier for me to upgrade when a new version comes out?

I'm wondering if it'd be as easy as just formating the "/" partition and installing the new version there, while keeping the /home partition with the data, or would it be a little bit more complex, in that installing the new version would create its own /home too.

---

### Post by cek on 2010-10-12
Yes.

during the installation process you get the option to select how the disk should be formatted.  To use your separate /home partition, you have to select the disk partitions manually.  Then use your existing partitions, format the / partition, and select not to format your current /home partition and give it the mount point of /home.

It's really easy, especially when the partitioning application is in front of you.

---

### Post by ratcheer on 2010-10-12
> **jcd29 said:**
> If I have a 20GB (or more, I dunno what's enough) root (/) partition, and a 200GB /home partition, would that make it easier for me to upgrade when a new version comes out?

I'm wondering if it'd be as easy as just formating the "/" partition and installing the new version there, while keeping the /home partition with the data, or would it be a little bit more complex, in that installing the new version would create its own /home too.

It works better if you do NOT format /. Select manual partitioning and then select the existing / to use for /. Then deselect the check box that tells it to format /. Also, select /home if it is a separate partition and tell it to use it as /home, again without reformatting. It will install without touching /home, whether it is a separate partition or not. This is being referred to as a "dirty install" and I saw it in one of the Maverick testing threads. I did it, yesterday and it worked perfectly, all my configuration settings were carried over. Except, of course, for config info that is stored under /.

Tim

---

### Post by searchfgold6789 on 2010-10-12
I would say, not.
Remember that your home folder also contains all of your application settings and data...for this reason I don't think it would be worth it :)

---

### Post by cek on 2010-10-12
> **ratcheer said:**
> It works better if you do NOT format /. Select manual partitioning and then select the existing / to use for /. Then deselect the check box that tells it to format /. Also, select /home if it is a separate partition and tell it to use it as /home, again without reformatting. It will install without touching /home, whether it is a separate partition or not. This is being referred to as a "dirty install" and I saw it in one of the Maverick testing threads. I did it, yesterday and it worked perfectly, all my configuration settings were carried over. Except, of course, for config info that is stored under /.

Tim

If you properly select the mount points, then there is no benefit to not formatting the / partition.  In fact, this can leave directories out there that are left over from the previous install for applications and libraries that are no longer installed.

---

### Post by ShakeyJake on 2010-10-12
It definitely works, I have / on an SSD and /home on a HDD and have done the 'dirty install' a couple of times.

---

### Post by jcd29 on 2010-10-12
> **searchfgold6789 said:**
> I would say, not.
Remember that your home folder also contains all of your application settings and data...for this reason I don't think it would be worth it :)

Ah, true. Wouldn't be a clean install then.

---

### Post by Vaphell on 2010-10-12
but wiping dotfiles is not exactly a rocket science
ctrl+h, remove most if not all .*, log out/in -> all necessary dotfiles are recreated just as if it was a fresh account.

---

