---
title: "Postfix smtp configuration"
date: 2010-05-13
forum: General Help
---

### Post by jdege on 2010-05-13
Can someone give me a hint as to how to setup a really simple Postfix config?

I'm running Postfix primarily as a local email server.  There is no email coming in from other machines, and there are no other machines using it to send mail.  But I'd like it to be able to send mail.

I use Evolution for my normal email stuff, and it's configured to send mail to my ISP's smtp server, and that's working fine.  But I occasionally send mail from the command line, using the "mail" or "mutt" utilities.  (Mutt because the standard mail doesn't support attachments.)

These don't use Evolution's configuration, they depend upon whatever is listening to port 25 - and that's Postfix.  So all I should need to do is to give Postfix the smtp server, user name, and password.

My problem is that Postfix has voluminous documentation online, and I haven't been able to find this simple configuration in it.

Can someone tell me what I need to do, or where I need to look?

---

### Post by nickzeff on 2010-10-04
Try this article in the Ubuntu Documentation:

[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

---

### Post by dcstar on 2010-10-04
> **jdege said:**
> Can someone give me a hint as to how to setup a really simple Postfix config?
.........
Can someone tell me what I need to do, or where I need to look?

```
sudo dpkg-reconfigure postfix
```

---

### Post by HereInOz on 2010-10-04
Falco has a nice "step by step" setup here:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p5](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p5)

---

