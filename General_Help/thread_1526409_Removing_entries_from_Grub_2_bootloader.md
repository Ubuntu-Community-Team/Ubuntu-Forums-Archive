---
title: "Removing entries from Grub 2 bootloader"
date: 2010-07-08
forum: General Help
---

### Post by dohzer on 2010-07-08
Since I've been using Ubuntu, I've noticed that new entries for Ubuntu (the same but with the final number changed) occasionally appear in the Grub 2 boot loader. I'm talking about the first two entries in this picture, compared with the third and fourth entries here: [https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.chainload.grub.sm.png](https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.chainload.grub.sm.png)

Two questions:

1. What are these entries? They appear to simply be the same OS but different versions.  Are they generated when Ubuntu updates?

2. Can I delete them? If so, what is the easiest way to do this?

---

### Post by garvinrick4 on 2010-07-08
> **dohzer said:**
> Since I've been using Ubuntu, I've noticed that new entries for Ubuntu (the same but with the final number changed) occasionally appear in the Grub 2 boot loader. I'm talking about the first two entries in this picture, compared with the third and fourth entries here: [https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.chainload.grub.sm.png](https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=grub2.chainload.grub.sm.png)

Two questions:

1. What are these entries? They appear to simply be the same OS but different versions.  Are they generated when Ubuntu updates?

2. Can I delete them? If so, what is the easiest way to do this?
They are different kernels of Linux. Leave 2 in the boot menu and remove any more than that is usually preferred. 
 Go to Synaptics in System/Admin and type in which one you want to get rid of and remove it. Like 2.6.32-xx in search box and it will bring up 1 image generic and 2 headers remove them.

---

### Post by scouser73 on 2010-07-08
You can either remove the old grub entries via Synaptic Package Manager, or a much easier way is to do it via Ubuntu Tweak.

Firstly, go to [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) & download and install the software.

Once you have Ubuntu Tweak installed, you will find it under the System Tools menu.

Click on it, and once it's loaded select Package Cleaner, click on Unlock in the bottom right-hand corner & enter your password when prompted.

Then click on Clean Kernels, now you will see a list of old kernels that you no longer need. Click Cleanup and the old grub entries will be removed and it will keep only the newest version installed.

---

### Post by dohzer on 2010-07-22
Hugely delayed response.
Thanks for the replies guys, I ended up deleting them with the Synaptic Package Manager, and it worked fine.

---

