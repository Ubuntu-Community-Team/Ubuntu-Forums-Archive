---
title: "Formated mount point!"
date: 2010-05-31
forum: General Help
---

### Post by anubis2814 on 2010-05-31
I accidentally formatted my mount point drive and nothing starts now.  Can someone help me fix this?
Thanks

---

### Post by ajgreeny on 2010-05-31
What on earth is your "mount point drive"?

I have no idea what you are asking about.

---

### Post by jerenept on 2010-05-31
> **ajgreeny said:**
> What on earth is your "mount point drive"?

I have no idea what you are asking about.

Maybe root filesystem...
this is impossible, Linux does not allow this to happen, unless you run some mad command (like sudo rm -rf /)

---

### Post by WinRiddance on 2010-05-31
> **anubis2814 said:**
> I accidentally formatted my mount point drive and nothing starts now.  Can someone help me fix this?
Thanks

Wow, that's a bit over my head too. Actually, Linux would allow for that to happen if you were using Gparted from a LiveCD while you were actually planning on resizing some partitions or whatever which would have to be unmounted first. Can you be a little bit more specific? Did you format the drive with your installed version of Ubuntu ... does this mean that you also formatted the space where your home/user folders would be located?

And if you did that, does this mean that you're using a LiveCD or someone elses computer to communicate on the forum here?

---

### Post by anubis2814 on 2010-05-31
@wowriddance
Yes it was a perfect storm. I was trying to resize two drives without realizing that one was my mount point drive.  After it refused to start I realized what I had done, but gparted wouldn't recover the mount point or let me reinstall one once I had resized the drive.



Wow, that's a bit over my head too. Actually, Linux would allow for that to happen if you were using Gparted from a LiveCD while you were actually planning on resizing some partitions or whatever which would have to be unmounted first. Can you be a little bit more specific? Did you format the drive with your installed version of Ubuntu ... does this mean that you also formatted the space where your home/user folders would be located?

And if you did that, does this mean that you're using a LiveCD or someone elses computer to communicate on the forum here?

---

### Post by anubis2814 on 2010-05-31
@wowriddance I used liveCD and I only formatted the mountpoint otherwise I'd use a reinstall.  Using my windows os right now to communicate

---

### Post by WinRiddance on 2010-05-31
Well, I might be going out on a limb here with this assumption ...

... but it doesn't sound like you've actually been very busy yet with your installed Ubuntu since you didn't "yell bloddy moider" due to not being able to use various programs, have access to your personal data, and so on. If I'm right and it was just an initial installation that you were getting ready to customize for yourself ... then the easiest and fastest way to correct your problem would be by doing another fresh installation of Ubuntu.

Using the LiveCD you already have experience with sizing your partitions. Do so as you see fit and then format the partition that you used for Ubuntu before as the **ext4** file system. Once done, just reboot with the LiveCD and then install Ubuntu fresh into the same partition as before. The installation will once again recognize your Windows installation and provide you with the option to use the dual-boot setup. That's the best that I can advise for now.

---

### Post by anubis2814 on 2010-05-31
@winriddance

Well luckily I have a linux reader on my windows so file access is not a problem.  I could reinstall but I'm wondering if there is another way.  Thanks for your help though.

---

### Post by John Bean on 2010-05-31
> **anubis2814 said:**
> @winriddance

Well luckily I have a linux reader on my windows so file access is not a problem.  I could reinstall but I'm wondering if there is another way.  Thanks for your help though.

Testdisk *may* help. Read the documentation carefully before using it.

It's probably simpler to just reinstall if you haven't actually lost data though.

---

