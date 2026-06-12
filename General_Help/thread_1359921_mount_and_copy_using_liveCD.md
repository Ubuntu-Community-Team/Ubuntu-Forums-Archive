---
title: "mount and copy using liveCD"
date: 2009-12-20
forum: General Help
---

### Post by booah on 2009-12-20
I can't boot into my ubuntu partition and was wondering if someone could please tell me how to copy my files onto a usb memory stick. I can log in on the liveCD and I can see the folders I want using explorer but I do not have the access rights to copy and paste (using the mouse).

the drive they are on is /dev/sda5
they are in:
 /home/booah/java programming 
/home/booah/shell programming

thanks alot for any help

---

### Post by dcstar on 2009-12-20
> **booah said:**
> I can't boot into my ubuntu partition and was wondering if someone could please tell me how to copy my files onto a usb memory stick. I can log in on the liveCD and I can see the folders I want using explorer but I do not have the access rights to copy and paste (using the mouse).

the drive they are on is /dev/sda5
they are in:
 /home/booah/java programming 
/home/booah/shell programming

thanks alot for any help

Open a command prompt, then:

```
sudo nautilus
```

And you should have rights to copy.

---

