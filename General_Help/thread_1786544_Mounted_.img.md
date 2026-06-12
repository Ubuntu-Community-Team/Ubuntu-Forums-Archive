---
title: "Mounted .img"
date: 2011-06-19
forum: General Help
---

### Post by ki4jgt on 2011-06-19
I have a mounted image file that I need to copy to a memory card for booting on an external device.

I was told to use this command:
```
cp -RvPp /path/to/mounted/image/. /path/to/mounted/sd/card/partition/1.ext3
```

Because of the crappiness of my computer's card reader, I can't use that command. The terminal states that my card is full. It's a 4 gig card, and a 1 gig image. I can write and read from the card when I'm using regular files access. The problem is, this won't work :-( I have friends who have gotten it to fit on the one gig card. So, I wondered, if I copied it a few files at a time (using sudo su in nautilus) would I be able to do that? Would the links still be preserved? (It's a live OS) Would file ownership change? I thought of Unetbootin but then I remembered how it likes to change the bootloader :-( any and all help is appriciated.

---

### Post by crispy_420 on 2011-06-20
sudo apt-get install usb-imagewriter

[http://www.ubun2.com/question/353/how_burn_img_image_bootable_usb_flash_disk_drive_linux_ubuntu](http://www.ubun2.com/question/353/how_burn_img_image_bootable_usb_flash_disk_drive_linux_ubuntu)

---

### Post by ki4jgt on 2011-06-20
Thanks. . . already found out how to copy them though, the website said to use dev. I used media.

---

### Post by crispy_420 on 2011-06-20
Mark as solved?

---

### Post by ki4jgt on 2011-06-20
> **crispy_420 said:**
> Mark as solved?

Already did.

---

