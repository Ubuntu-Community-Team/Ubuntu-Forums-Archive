---
title: "Changing Grub2 to not show memtest problem"
date: 2010-01-09
forum: General Help
---

### Post by DXM31 on 2010-01-09
according to this
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
I issue this command
sudo chmod -x 20_memtest86+
when I do that I get this error
chmod: cannot access `20_memtest86+': No such file or directory
I know it is something simple but, I don't get it.

Never mind...doh!

---

### Post by rbc on 2010-01-09
Perhaps a silly question, but have you navigated to the /etc/grub.d directory prior to issuing the command

---

### Post by DXM31 on 2010-01-09
> **rbc said:**
> Perhaps a silly question, but have you navigated to the /etc/grub.d directory prior to issuing the command

Thanks, I finally figured that out, see original post.
Mostly the reason for edit;)

---

