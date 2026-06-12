---
title: "ssd - delete lots of files = hang"
date: 2012-05-10
forum: General Help
---

### Post by SlugSlug on 2012-05-10
I have a ssd for / and gameserver,

If I delete a folder with 
31,075 items, totalling 332.9 MB

The system hangs for a while (until the bin or rm command has finished)

Pretty sure this didn't happen on HDD

am using discard in fstab


Is this a bug?

Linux drunkenslug 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by idoitprone on 2012-05-10
> **SlugSlug said:**
> I have a ssd for / and gameserver,

If I delete a folder with 
31,075 items, totalling 332.9 MB

The system hangs for a while (until the bin or rm command has finished)

Pretty sure this didn't happen on HDD

am using discard in fstab


Is this a bug?

Linux drunkenslug 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

ssd brand because most ssd on the market have really awful random io performance and latency problems

---

### Post by SlugSlug on 2012-05-10
ocz agility 3

---

### Post by HermanAB on 2012-05-10
Try the ionice command.

---

### Post by idoitprone on 2012-05-10
> **SlugSlug said:**
> ocz agility 3

I have nothing it supposely is a fast drive but the sandforce controller will obscure the numbers. I guess i cannot help other than suggest changing your fstab to noatime to reduce writes

maybe run top while doing heavy io

I have reason to belive the sandforce controllers are eating your resources such as ram and cpu

---

### Post by SlugSlug on 2012-05-10
io is fantastic, its just when deleting a mass amount of files, not sure if discard has a negitive effect, guess I could remove discard and test 

just seems wrong

---

### Post by idoitprone on 2012-05-11
> **SlugSlug said:**
> io is fantastic, its just when deleting a mass amount of files, not sure if discard has a negitive effect, guess I could remove discard and test 

just seems wrong

Oh this seems like a known issue 
with sandforce 2000

there are threads about the freezing issues with those controllers 
I dont know what to say?
Maybe update firmware?
[http://forums.overclockers.co.uk/showthread.php?p=19193882](http://forums.overclockers.co.uk/showthread.php?p=19193882)

---

### Post by SlugSlug on 2012-05-11
am not sure that's the case, am on the latest firmware, mine doesn't just drop out, it hangs when deleting lots (like loads!) of files. So I have like a min system freeze then back to normal.

---

### Post by SlugSlug on 2012-05-15
Just tried deleting the same folder on a windows machine and it was fine :(
 
If anyone wants to try, then this is the folder am talking about
 
[ftp://drunkenslug.com/tmp/Build.tar](ftp://drunkenslug.com/tmp/Build.tar)
 
just untar it, its full on png files (minecraft webserver map)

---

### Post by SlugSlug on 2012-06-22
removing discard from fstab solved(?) it

---

### Post by idoitprone on 2012-06-22
> **SlugSlug said:**
> removing discard from fstab solved(?) it

strange?

discard just enable trim in the ssd

weird. i dont get it either. I guess i wonder if someone who know ssd in detail might give a reason on this issue

---

