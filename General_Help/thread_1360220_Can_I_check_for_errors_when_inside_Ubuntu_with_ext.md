---
title: "Can I check for errors when inside Ubuntu with ext4?"
date: 2009-12-20
forum: General Help
---

### Post by feedmecereal on 2009-12-20
I suspect errors on my hard drive so I want to check for errors. I am using ext4. I was just in a chatroom and someone told me that even though I am using ext4, I still need to have my partition unmounted and I should check my hard drive with a LiveCD. But I though the one of the major advantages of ext4 was that it would allow checking for errors while it was mounted!

So, can I check it for errors while I'm using it? I Googled around and I couldn't figure out how even though I thought I read how to do it before.

---

### Post by dcstar on 2009-12-20
> **feedmecereal said:**
> I suspect errors on my hard drive so I want to check for errors. I am using ext4. I was just in a chatroom and someone told me that even though I am using ext4, I still need to have my partition unmounted and I should check my hard drive with a LiveCD. But I though the one of the major advantages of ext4 was that it would allow checking for errors while it was mounted!

So, can I check it for errors while I'm using it? I Googled around and I couldn't figure out how even though I thought I read how to do it before.

fsck checks for **filesystem** errors not **disk** errors.

Disk errors are where the underlying hardware has a problem and are unrelated to the filesystem structure that tools like fsck checks.

---

### Post by feedmecereal on 2009-12-20
I think you misunderstood me. I don't suspect physical errors on my hard drive, I suspect logical errors on some files that I was copying from an external hard drive. Maybe I wasn't clear about that.

How do I check for these errors?

---

### Post by dcstar on 2009-12-20
> **feedmecereal said:**
> I think you misunderstood me. I don't suspect physical errors on my hard drive, I suspect logical errors on some files that I was copying from an external hard drive. Maybe I wasn't clear about that.

How do I check for these errors?

Safest way is to boot off a CD/USB (with an ext4 compatible OS) and then do a fsck on it.

---

