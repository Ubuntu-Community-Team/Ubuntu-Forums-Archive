---
title: "does not save on USB flash drive"
date: 2009-10-29
forum: General Help
---

### Post by Chorda on 2009-10-29
Hi,

I just installed 9.10 on a USB flash drive, but it does not save anything -- no new user account, no configuration, even files that I create with OpenOffice -- it seems that the whole Ubuntu gets reset to default when I reboot my machine.

Any idea?
Thanks,
CT

---

### Post by falconindy on 2009-10-29
What filesystems are being used? if its NTFS, you need to be mounting with ntfs-3g or else you won't have the ability to write.

---

### Post by Chorda on 2009-10-30
Fat32

---

### Post by P4man on 2009-10-30
On a live cd the default "ubuntu" user is recreated each boot. assuming you made a persisent USB stick, make a new user and try logging in with that, see if it saves your stuff

---

### Post by Chorda on 2009-10-30
I downloaded the CD image which I installed on a USB flashdrive. I created a user account with admin priviledges. When I log off, I can log in with this new account, but when I reboot, the account has been deleted. The same goes with anything I same (images, doc giles...).

How do I make a persistent USB stick?

Thanks,
CT

---

### Post by P4man on 2009-10-30
> **Chorda said:**
> I downloaded the CD image which I installed on a USB flashdrive. I created a user account with admin priviledges. When I log off, I can log in with this new account, but when I reboot, the account has been deleted. The same goes with anything I same (images, doc giles...).

How do I make a persistent USB stick?

Thanks,
CT

How are you making the live USB stick? If you are making it from ubuntu's live usb creator, then just select the (default) option to  "store documents and settings in reserved extra space" and set a size for it. If you dont have ubuntu installed, you could still use this if you have 2 sticks. One to boot from like you do now, and then launch the USB creator (which you will find in sysem > administration ), and use the other stick  as target for the persistent live usb stick.

If you are doing this from windows, then follow this guide;
[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

It is for 9.04 but I expect it should work for 9.10 just as well, just use the 9.10 iso and follow the rest as it is written.

---

### Post by Chorda on 2009-10-31
I used u910p and created/resized casper-rw.
That works now. Thanks!

Can someone clarify this for me please:

Is it that casper-rw is a file in which all of my preferences, notes, music and videos are saved? If so, is it that if this file gets corrupt I lose everything?

Thanks,
CT

---

