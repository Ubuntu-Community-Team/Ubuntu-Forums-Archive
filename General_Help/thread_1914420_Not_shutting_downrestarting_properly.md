---
title: "Not shutting down/restarting properly"
date: 2012-01-24
forum: General Help
---

### Post by xly15 on 2012-01-24
Whenever I shutdown or restart my computer I get the screen in the picture.

and when i start up it is always using the resume function to do so. I am on 11.10. can anyone help me?

---

### Post by xly15 on 2012-01-24
No help with my problem?

---

### Post by BC59 on 2012-01-24
Check this if it works for you:
```
sudo nano /etc/default/grub
```
Change > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"  to > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"then
```
sudo update-grub2
```

---

### Post by xly15 on 2012-01-24
That seems to haved solved the error of the shutdown screen. Now I just need to stop it from using the resume function when it starts up. Any ideas?

---

### Post by BC59 on 2012-01-24
What to you mean with resume function?

---

### Post by xly15 on 2012-01-24
When ubuntu starts up it does not start up the normal way. It says resume:libgcrypt version #. Is it suppose to do that?

---

### Post by BC59 on 2012-01-24
It's a bug. Check here:
[https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/108230](https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/108230)
[https://bugs.launchpad.net/ubuntu/+source/libgcrypt11/+bug/665932](https://bugs.launchpad.net/ubuntu/+source/libgcrypt11/+bug/665932)

---

### Post by xly15 on 2012-01-24
Thanks man. Something the second link you posted really helped me. I think the problem was related to hibernating.

---

