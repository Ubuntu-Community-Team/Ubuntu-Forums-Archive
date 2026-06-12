---
title: "Re-Disabling root -- did I do this correctly?"
date: 2010-02-27
forum: General Help
---

### Post by Khufucius on 2010-02-27
Hi,

I accidentally typed "sudo passwd" and changed the UNIX password.  I meant to change my non-root user account password, but mindlessly typed "sudo" because it seemed like a relatively official, administrative action.  Stupid, I know.

Anyways, when I realized my mistake, I googled "re-disabling root login ubuntu" and did

"sudo usermod -p '!' root"

Is everything back to how it was before?  Or is there a hashed root password floating around somewhere, even though root login is not allowed?  I just want to be as sure as possible that I didn't accidentally leave something wide open.

Thanks,

-Khufu

---

### Post by dcstar on 2010-02-27
> **Khufucius said:**
> Hi,

I accidentally typed "sudo passwd" and changed the UNIX password.  I meant to change my non-root user account password, but mindlessly typed "sudo" because it seemed like a relatively official, administrative action.  Stupid, I know.

Anyways, when I realized my mistake, I googled "re-disabling root login ubuntu" and did

"sudo usermod -p '!' root"

Is everything back to how it was before?  Or is there a hashed root password floating around somewhere, even though root login is not allowed?  I just want to be as sure as possible that I didn't accidentally leave something wide open.
.......

Nothing is "wide open" even if the root account is enabled, it is still password protected.

It is just another level safer with the root account disabled as that account name is a known account name, whereas your account name that you initially set up with admin privileges has to be guessed.

Unless you expose your machine directly to the Internet with login ports open, there is little that anything/anyone can do to access your PC to use the root account apart from your own keyboard and screen.

---

### Post by Khufucius on 2010-02-27
Thank you,

that clarifies things quite nicely.

-K

---

