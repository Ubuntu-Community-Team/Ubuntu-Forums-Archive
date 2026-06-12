---
title: "Ubuntu 10.4 try to automount nonexisting partition"
date: 2010-05-14
forum: General Help
---

### Post by texbuntu1978 on 2010-05-14
I hope someone can help me with this.

I used to have 2 extra partitions on my hard-drive (sda7 and sda8), but have not deleted them. Whenever i try to boot into Ubuntu 10.4 the boot screen tries to mount them and halts until i press "s" to skip mounting them.

How do i remove the attempt to auto-mount them, so Ubuntu can boot without manual intervention?

---

### Post by Nythain on 2010-05-14
edit /etc/fstab with sudo permission and remove their entries... just be carefull what all you do remove from there

---

### Post by texbuntu1978 on 2010-05-14
Thank you very much Nythain, it worked perfectly :P

Just in case some (like me) ubuntu illiterate :) future reader want a more elaborate explanation, what Nythain comment said was:

Open your terminal
type "sudo gedit /ect/fstab
find the patition(s) you dont want, it should look something like this:

"/dev/sdXY                                  /media/sdXY  ext4  defaults             0  0  "

Delete the line(s)
exit editor and save.

---

### Post by Nythain on 2010-05-14
a few notes on that...
if you're opening gedit from the terminal, you should type
gksu gedit
and sometimes the lines will have
UUID=fkljda;lfjdkla;fjd
instead of /dev/sdXY, but the apropriate device will be in a commented line above it so you know which device is wich

---

