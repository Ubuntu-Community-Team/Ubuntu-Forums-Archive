---
title: "Zimbra desktop beta 2"
date: 2010-06-07
forum: General Help
---

### Post by ailmarpete on 2010-06-07
Hey guys, I'm an Ubuntu noob, so am requesting some assistance on this one. I'm thinking my issue is a 64 bit related one.  
Zimbra desktop is  a mail client.
Comes with it's own installer, works fine "out of the box" on OpenSuse 64 bit, had to install xulrunner.i686 on Fedroa 13 64 bit to get it running.
Now I'm getting the same error on Ubuntu 10.04 64 bit as I got on Fedora 13, The error is:

  ```
Details: Failed to execute child process "/opt/zimbra/zdesktop/linux/prism/zdclient" (No such file or directory)
```

The path is valid, permissions are fine etc.
When I try to install xulrunner this is what happens:

```
sudo apt-get install xulrunner.i686
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xulrunner.i686 
```

I have checked and I have xulrunner installed (xulrunner-1.9.2.3+nobinonly-Oubuntu2 (lucid)) 

What else am I missing?
Thanks for any assistance.
Regards Peter.

---

