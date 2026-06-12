---
title: "32 and 64 bit living together"
date: 2009-12-29
forum: General Help
---

### Post by operative.terminus on 2009-12-29
Would I be able to dual-boot two distros, one 32 bit, and one 64 bit, and have them share the same home partition?

I would of course have different user names for each distro and they would use different window managers.

---

### Post by 73ckn797 on 2009-12-29
> **operative.terminus said:**
> Would I be able to dual-boot two distros, one 32 bit, and one 64 bit, and have them share the same home partition?

I would of course have different user names for each distro and they would use different window managers.


If one is formatted as ext3 you likely will not be able to read a ext4 formatted partition. That has been my experience. I do not now have 2 Ubuntu systems installed. Ext4 will read ext3. Matching both will always work.

---

### Post by operative.terminus on 2009-12-29
> **73ckn797 said:**
> If one is formatted as ext3 you likely will not be able to read a ext4 formatted partition. That has been my experience. I do not now have 2 Ubuntu systems installed. Ext4 will read ext3. Matching both will always work.

That's fine, I don't use ext4. So, there wouldn't be any problem with one being 32 bit and one being 64 bit? Maybe a problem with them sharing grub?

---

### Post by falconindy on 2009-12-29
> **73ckn797 said:**
> If one is formatted as ext3 you likely will not be able to read a ext4 formatted partition. That has been my experience. I do not now have 2 Ubuntu systems installed. Ext4 will read ext3. Matching both will always work.
If your kernel supports Ext4 (true since 8.10), you can mount and read Ext4 partitions.

---

### Post by Strongman332 on 2009-12-29
it should work fine. you should try it then post results. but it should work. you could try it in virtual box first if you like

---

### Post by operative.terminus on 2009-12-30
> **falconindy said:**
> If your kernel supports Ext4 (true since 8.10), you can mount and read Ext4 partitions.

Thanks. But I have had problems with ext4. The last time I used it my file system was severely corrupted twice.

---

### Post by operative.terminus on 2009-12-30
> **Strongman332 said:**
> it should work fine. you should try it then post results. but it should work. you could try it in virtual box first if you like

Thanks for your reply. I will probably try it in virtualbox. The 64 bit system I want to try is 64 Studio, but I'm not going to install it to my HD until it is out of beta.

---

