---
title: "Unencrypt Encrypted Home"
date: 2010-03-03
forum: General Help
---

### Post by darukka on 2010-03-03
I set up my Ubuntu install to use encrypted home directories. As I found out later that encrypted home directories and autologin doesn't work together I would like to unencrypt my home dir now. Can someone tell me how to do this, without reinstalling the system?

thanks in advance!

---

### Post by bodhi.zazen on 2010-03-03
Easiest is obviously that you will need to log in (disable auto-login).

Second you could simply log in, make a new home directory, and then copy you un-encrypted files to the new home.

```
sudo usermod -d /home/new_home
```

You could also make a new user.

You can remove ecryptfs following the instructions posted here:

[https://answers.launchpad.net/ubuntu/+source/ecryptfs-utils/+question/48636](https://answers.launchpad.net/ubuntu/+source/ecryptfs-utils/+question/48636)

See also:

[http://www.charlescurley.com/blog/archives/2009/11/24/recovering_from_login_failure_on_ubuntu_9_10/index.html](http://www.charlescurley.com/blog/archives/2009/11/24/recovering_from_login_failure_on_ubuntu_9_10/index.html)

---

