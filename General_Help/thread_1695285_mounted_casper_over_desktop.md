---
title: "mounted casper over desktop"
date: 2011-02-25
forum: General Help
---

### Post by hakkafusion on 2011-02-25
Screwed myself by mounting my casper-rw over my desktop, is there anyway to undo it? or would it reset after reboot? Thanks.

my casper-rw is located on the desktop, and I think that is the reason why I cannot unmount it. Checked fstab & mtab, nothing useful in either file.

Here's what I did:

sudo mount -o loop casper-rw /home/username

then:

sudo umount -f /home/username
umount2: Invalid argument
umount: /home/username: not found

also tried 
sudo umount -f /dev/loop0
sudo umount -f /dev/loop1

no good either

---

