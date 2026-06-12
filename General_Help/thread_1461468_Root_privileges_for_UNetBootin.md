---
title: "Root privileges for UNetBootin?"
date: 2010-04-24
forum: General Help
---

### Post by Rubi1200 on 2010-04-24
Hi,
I installed UNetBootin and everything went well on the first run. However, now when I start it to create a Live USB it wants to use root privileges; asks for the admin password. Is this normal and if not how can I change this behavior?
Thanks in advance.

---

### Post by Rubi1200 on 2010-04-24
Quick update: I have not found anything yet searching Google or on the website of the software about this matter.
Thanks

---

### Post by snowpine on 2010-04-24
As Ubuntu does not have a root password by default, I recommend:

```
gksu unetbootin
```

Enter your user password when prompted. 'gksu' is basically 'sudo' for graphical applications. Hope it works for you! :)

---

### Post by Rubi1200 on 2010-04-24
Thanks for responding but I am at fault for not explaining myself clearly. I can run the program no problem. What bothers me is that it wants to run with elevated privileges and I was asking if that is normal for this program.
Hope that clears things up. 
Thanks

---

### Post by snowpine on 2010-04-24
> **Rubi1200 said:**
> Thanks for responding but I am at fault for not explaining myself clearly. I can run the program no problem. What bothers me is that it wants to run with elevated privileges and I was asking if that is normal for this program.
Hope that clears things up. 
Thanks

Yes, it is normal to require root/sudo privileges, because you could seriously mess up your system with Unetbootin gone wild. :)

Basically Ubuntu will ask for your password any time you make changes outside your /home folder. This is totally normal and a good thing.

---

### Post by Rubi1200 on 2010-04-24
Thanks snowpine! This makes sense.
I suppose it also logical in the context since I am formatting a USB drive and installing a bootloader.

---

### Post by DonVla on 2010-11-02
I know this is an old thread. Sry for this.
But unetbootin does not need root privileges when you build an image for common usb sticks. When it asks for root password, it is sufficirnt to hit "ignore". The boot image still builds fine.

---

