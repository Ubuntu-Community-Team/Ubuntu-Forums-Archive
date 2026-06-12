---
title: "automount encrypted usb at boot"
date: 2010-10-22
forum: General Help
---

### Post by sonic6567 on 2010-10-22
Hello,

can anyone assist?  I have searched google but cannot find exactly what I need.

I have an external usb stick that is encrypted and always plugged in.

On boot i want to it automatically be mounted (so I don't have to go to places and click on it and enter the decryption phrase)

Can anyone help?

Thanks

---

### Post by sonic6567 on 2010-10-25
bump

---

### Post by Wayne_V on 2010-10-25
pam_mount should do this.   See here for an example using Dropbox:

[http://pragmattica.wordpress.com/2009/05/10/encrypting-your-dropbox-seamlessly-and-automatically/](http://pragmattica.wordpress.com/2009/05/10/encrypting-your-dropbox-seamlessly-and-automatically/)

---

### Post by sonic6567 on 2010-10-25
Thanks for the info.

pam_mount will not work in this case. It is for password protected filesystem and requires that your ubuntu login and decrypt key be the same.

But it did point me in the right direction and I found this that solved it for me.

[http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

basically: /etc/crypttab

Thanks

---

