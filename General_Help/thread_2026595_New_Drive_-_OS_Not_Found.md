---
title: "New Drive - OS Not Found"
date: 2012-07-15
forum: General Help
---

### Post by Hungry Man on 2012-07-15
I just put in a 128GB SSD. I turn it on, get the BIOS for a long time, and then the error "Operating System Not Found."

I've tried reinstalling, separating /boot, all sorts of things.

Help?

lol loose wire fml took me 3 hours to realize that

---

### Post by hal8000 on 2012-07-15
I yhad a laptop with a small 16G SSD, it was recognised in linux as /dev/sda and the windows partition as /dev/sda1.

Do you have another HD installed or trying to boot from the SSD?
I would use rthe Ubuntu CD in live mode and post output of:


sudo fdisk -l
sudo blkid

---

