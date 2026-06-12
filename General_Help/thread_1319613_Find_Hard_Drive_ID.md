---
title: "Find Hard Drive ID"
date: 2009-11-08
forum: General Help
---

### Post by william91 on 2009-11-08
Hi there!

Could anyone tell me how to find the a Hard Drive ID in terminal?

I want to automount my drives, so I need the HD ID.

Thanks a lot!

---

### Post by howefield on 2009-11-08
Try opening a terminal and typing

```
sudo fdisk -l
```

Type your password when prompted and press enter. Does this give you what you want ?

---

### Post by coffeecat on 2009-11-08
If you mean the UUID, then open a terminal, and:

```
sudo blkid
```By automount, I suppose you mean add entries to /etc/fstab. Although using UUIDs has some distinct advantages, do you know that you can also use partition device descriptors, such as "/dev/sda3"?

---

### Post by william91 on 2009-11-08
Hmm.. Not exactly. Thanks for quick reply though!

EDIT: I think I found what I'm looking for. It was: "sudo blkid"

Thanks anyway though!

---

### Post by coffeecat on 2009-11-08
> **coffeecat said:**
> if you mean the uuid, then open a terminal, and:

```
sudo blkid
```

> **william91 said:**
> hmm.. Not exactly.

Edit: I think i found what i'm looking for. It was: "sudo blkid"

 ](*,) ](*,) ](*,)    

:(

---

