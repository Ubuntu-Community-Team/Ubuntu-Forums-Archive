---
title: "I have installed Ubuntu 9.04 next to windows."
date: 2009-10-11
forum: General Help
---

### Post by mobilrond on 2009-10-11
But i did not previous enough space (partition) on the disk...May i resize it and how can i do that?

---

### Post by dyous87 on 2009-10-11
You don't have enough space for Windows or Linux? If you want to add more space for windows you use use gparted from Ubuntu:

```
sudo apt-get install gparted
```If you want to make the Linux partition bigger it wil be a problem because while you can boot with a live cd and free up soe hard drive space, you cannot simply make the root (/) or home (/home) partition bigger as far as I know.

In windows however you can just free up space and add a new drive like f: or g: 

By the way if you need more in-depth help you can feel free to IM me on AIM at juveyank87 or on gmail at [email]dyous87@gmail.com[/email]

David

---

### Post by fela on 2009-10-11
I'm pretty sure you can resize, as in make smaller or bigger, ext3 partitions (the default with Ubuntu up to and including Jaunty). Not so sure about ext4.

---

