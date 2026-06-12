---
title: "sudo fsck wiped my Thunderbird folder"
date: 2011-07-19
forum: General Help
---

### Post by dragonfly41 on 2011-07-19
I had to run **[COLOR=Navy]sudo fsck /dev/sda8 [/COLOR]** on a partition through ubuntu liveCD since ubuntu 10.10 would not start up.

I ran sudo fsck (without arguments) and I must have erased something in error (there was a stream of errors) because when I rebooted ubuntu .. my Thunderbird inbox had been cleared .. erased.

I've still got inbound emails archived on my pop server so I can download those again .. but I've lost outgoing emails sent from my Thunderbird client.

Where did I go wrong using fsck?

Can Thunderbird files wiped by fsck be recovered?

---

### Post by blind2314 on 2011-07-19
If data has been written to that drive since this happened (which it sounds like it has), your chances of recovery are slim.

---

### Post by dragonfly41 on 2011-07-19
No data written .. this was recent .. so do I use liveCD .. testdisk?

and I would like to know what I did wrong .. what args to use?

---

### Post by psusi on 2011-07-19
The damage happened before you ran fsck.  If data is important to you, then you need to regularly back it up.

You should check the drive SMART status in the disk utility to see if it is physically failing, which would have caused the error.

---

### Post by dragonfly41 on 2011-07-19
disk is healthy .. self-tests completed o.k. .. disk is o.k.

my earlier freeze occurred as /home started to become full .. 

on forced (power down/up) rebooting "check disk" came up and I then did a manual fsck using liveCD

I'll be a bit more wary in future.

---

### Post by SeijiSensei on 2011-07-20
Look in the lost+found directory on the partition where your home folder resides.  You might find the missing files in there.

---

### Post by bodhi.zazen on 2011-07-20
> **SeijiSensei said:**
> Look in the lost+found directory on the partition where your home folder resides.  You might find the missing files in there.

And if not, use testdisk and photorec, from a live CD, to see what if any data recovery you are looking at.

---

