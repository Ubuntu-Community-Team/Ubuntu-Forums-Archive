---
title: "UUIDs"
date: 2010-05-05
forum: General Help
---

### Post by Tux118 on 2010-05-05
Is there a way I can change those long and ugly UUIDs to something I type in? Thanks!

---

### Post by bab1 on 2010-05-05
> **Tux118 said:**
> Is there a way I can change those long and ugly UUIDs to something I type in? Thanks!

You can label the partition with either *e2lable* or *tune2fs*.

See [**_here _**]("http://www.cyberciti.biz/faq/linux-partition-howto-set-labels/#more-3175")for details.

This will give you both: Labels and UUID's for your partitions.

---

### Post by pqwoerituytrueiwoq on 2010-05-05
gparted also works

---

### Post by quadproc on 2010-05-05
> **Tux118 said:**
> Is there a way I can change those long and ugly UUIDs to something I type in? Thanks!
Those long and ugly strings are necessarily that way but there are a couple of things that can make life easier.

One, if you need to copy a UUID from one place to another, highlight it by dragging the cursor over it with the left mouse button pushed.  Then locate the cursor at the destination, click the left mouse button, and then press the middle mouse button.

Two, if you need a new UUID (perhaphs for some new hardware) then the uuidgen program will create one for you.  Just type uuidgen in a terminal window.

quadproc

---

### Post by capscrew on 2010-05-05
> **quadproc said:**
> Those long and ugly strings are necessarily that way but there are a couple of things that can make life easier...


The thing that is necessary is that the partition is uniquely identifiable to the O/S and that the ID stays the same.  This can be done with either UUID's or Partition Labels.  The only difference is the user is responsible for the uniqueness when using Labels.

---

