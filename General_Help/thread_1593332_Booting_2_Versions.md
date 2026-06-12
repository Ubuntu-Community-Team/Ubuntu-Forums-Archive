---
title: "Booting 2 Versions"
date: 2010-10-11
forum: General Help
---

### Post by |Enraiha on 2010-10-11
I want install 10.10 Maverick on a new partition alongside my OS X and 10.04 Lucid installs to see if it works on my machine. I'm a little unsure about some things.

1)Do I need to install the GRUB boot loader on this new partition?

2)Can I use the same swap space or is recommended to create a new swap?

Thanks.

---

### Post by ubunterooster on 2010-10-11
1) No, but you will want to make sure that Grub is updated on the old partition

2)I've done it using the same swap space but my system never uses the swap so I am not sure if this would be a problem

---

### Post by |Enraiha on 2010-10-11
How do I check the version of GRUB, and how do I update it?

---

### Post by ubunterooster on 2010-10-11
Just boot into your current install and run ```
sudo update-grub
```

I'm not sure how to check the grub version though

---

### Post by |Enraiha on 2010-10-11
Thanks for your help, I'll try an install now:)

---

### Post by ubunterooster on 2010-10-11
Glad to have helped, any problems and I'll try to help some more

---

