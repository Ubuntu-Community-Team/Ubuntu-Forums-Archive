---
title: "Migrate filesystem from JSF to BTRFS"
date: 2012-01-21
forum: General Help
---

### Post by lodopidolo on 2012-01-21
Hello, I've installed JFS as filesystem in my computer, but I'm not satisfied with it. It is in general too slow despite having changed the scheduler.

So I want to migrate it to BTRS (or EXT4).

Is there any way to do it without reinstall all? Something like dd or any Ghost, Clonezilla, etc.

Thanks.

---

### Post by BC59 on 2012-01-21
First of all, DON'T use Btrfs. It has a bug making it extremely slow. It's unusable.
To migrate to ext4 there is no easy solution. You can use Remastersys or Clonezilla, but in that case you have to compare the time and effort consumed. When I tried to do a magic movement, I spent 10 times more effort than a new fresh installation.

---

### Post by lodopidolo on 2012-01-22
> **BC59 said:**
> First of all, DON'T use Btrfs. It has a bug making it extremely slow. It's unusable.

Ok, thank you for the notice. I didn't know.

Well, I'm going to try to migrate to ext4 using Clonezilla.
I have very software and configurations installed and I don't want to install it again.

---

