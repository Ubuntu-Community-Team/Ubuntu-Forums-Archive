---
title: "copy user directory from another user account"
date: 2009-11-09
forum: General Help
---

### Post by yilin on 2009-11-09
I tried to create a new user account to solve problems after upgraded to 9.10. It's better but still have one thing wrong. Then I found that I have another account (rescue account since 8.10) that seem better. So I decide to copy that account over my new account.

```
# mv /home/user2 /home/user2_bak
# cp -r /home/user0 /home/user2
# chown user2:user2 /home/user2

```

After that, I got into my new account and it seems fine except one thing:
for some reason it asked me for the password of default keyring everytime my network applet trys to connect to my home wireless network.

I've to provide my rescue account's password to unlock the thing for wireless.

Anyone can help me get rid of this anorying thing?

In general, what need to change after a copy of account directory from another account?

Thanks a lot

---

