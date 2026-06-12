---
title: "USB Devices and VirtualBox."
date: 2012-05-12
forum: General Help
---

### Post by chrispche on 2012-05-12
I have created a VirtualBox of Windows XP. However I get the following message.

[[img]http://i45.servimg.com/u/f45/11/95/68/21/screen11.jpg[/img]](http://www.servimg.com/image_preview.php?i=50&u=11956821)

Can anyone tell me how to remedy this as I want USB access on my Windows XP Virtual Box.

Thanks.

---

### Post by d.atanasov on 2012-05-12
Just open the file /etc/group and find where the line for vboxuser is written. You have to add your username at the end of the e.g. 

```
vboxusers:x:Numbers:"username" 
```

You change username with yours.

---

### Post by chrispche on 2012-05-12
Thank you that worked.

---

