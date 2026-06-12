---
title: "Does one have to create files under /etc/modprobe.d?"
date: 2012-05-25
forum: General Help
---

### Post by PeterTaps on 2012-05-25
Folks,

I am running Ubuntu 11.10.

The following command works for me:

$ sudo modprobe i2c-dev

After this command, I am able to do what I wanted to.

Now, I want to make this permanent. From what I have read, I need to add the following line in either /etc/modprobe.d/aliases file or /etc/modprobe.d/local.

alias char-major-89 i2c-dev

However, on my system, I don't have either of these files. Should I just create one or is there a better way to do this?

Thank you in advance for your help.

Regards,
Peter

---

### Post by diesch on 2012-05-25
Create one of these files. I suggest* /etc/modprobe.d/local *as this is less likely to be used by any package in future versions.

---

### Post by PeterTaps on 2012-05-28
Thank you for your help.

I created a new file  /etc/modprobe.d/local with the line I had mentioned and rebooted the  machine. However, it appears i2c-dev was not loaded automatically.

I finally figured out that I just need to add i2c-dev to /etc/modules file.

Regards,
Peter

---

