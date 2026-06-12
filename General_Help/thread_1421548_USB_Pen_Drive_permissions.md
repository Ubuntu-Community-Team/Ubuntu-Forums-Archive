---
title: "USB Pen Drive permissions"
date: 2010-03-04
forum: General Help
---

### Post by colintivy on 2010-03-04
Hi folks,

I have been trying to get my USB Pen Drive 16GB Datatraveller working. It all mounts automatically OK but clicking on properties it says "Permissions cannot be determined". I have tried to set them to me as user but nothing seems to alter this situation. Of course I cannot use the drive which is disturbing. All the posts that I have read do not exactly mimic my problem and books don't either!! Must be something simple but I am foxed. Any ideas out there?

colintivy :confused:

---

### Post by wilee-nilee on 2010-03-04
Use gparted to reformat the drive to whatever partition type suits you. I have a 16 gig digital traveler that I use for full installs of linux and other things.

---

### Post by colintivy on 2010-03-05
Hi wilee-nilee,

Thanks for that. I should have mentioned that I had formatted the drive to ext3 already but not having any permission appears to prevent me from using it. All the advice seem to avoid my problem in detail or is it uneccessary?

colintivy

---

### Post by cong06 on 2010-03-05
When I formatted mine, I had to set permissions for the root folder on the drive..
So if the folder (mounted) was:
/media/disk

I did:
```

sudo chown 1000:1000 /media/disk

```
and I could then make folders on the base folder...

Did you try this already?

Edit: This will give permissions to the first user installed on the system...

---

### Post by wilee-nilee on 2010-03-05
> **colintivy said:**
> Hi wilee-nilee,

Thanks for that. I should have mentioned that I had formatted the drive to ext3 already but not having any permission appears to prevent me from using it. All the advice seem to avoid my problem in detail or is it uneccessary?

colintivy

The thumb I have with a fully installed lucid OS says in the permission not determined. I was under the impression that the thumb is not usable with the format to ext3, personally I format all my thumbs to fat32 unless it is a full install then I use the native format.

A reformat should leave the thumb as read and write. So you can't drag anything into it?

---

### Post by colintivy on 2010-03-25
Hi wilee-nilee,

I have not got any further with this problem due to other matters. I used ext3 because I will be storing my Home directory prior to doing a clean instal of 10.04 when it finally appears. Never heard of any difficulty with ext3, would not have thought that fat32 was more of a Windows/MSDOS thing. Now I hear that ext4 might be needed for 10.04, is this right?

Being an ex-Gates-bloat person, how do I transfer files/directories from my HD to the thumb anyway? I thought that my unsuccessful attempts to do this was due to my failure to get permission to write to the thumb. Your views will be appreciated.

colintivy

---

### Post by 3rdalbum on 2010-03-25
> **cong06 said:**
> When I formatted mine, I had to set permissions for the root folder on the drive..
So if the folder (mounted) was:
/media/disk

I did:
```

sudo chown 1000:1000 /media/disk

```
and I could then make folders on the base folder...

Did you try this already?

Edit: This will give permissions to the first user installed on the system...

+1

Looks like this particular post has been dismissed or ignored; but I'm pretty sure it's the right set of steps.

---

