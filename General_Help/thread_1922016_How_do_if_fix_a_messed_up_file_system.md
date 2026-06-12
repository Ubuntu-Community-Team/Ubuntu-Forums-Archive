---
title: "How do if fix a messed up file system?"
date: 2012-02-07
forum: General Help
---

### Post by Rgibbons on 2012-02-07
I was attempting to install an application via command line in 11.10 and had the task freeze up after 3/4 of the files had been written. As a result, I am unable to install Computer Janitor to clean it up. When I try to install it using the software center or terminal, I get an error. 

Is there a way to use the live CD to clean this up?

---

### Post by mike555 on 2012-02-07
I would not recommend using "computer janitor" for anything .....you should use synaptic package manager.

---

### Post by oldos2er on 2012-02-07
> **Rgibbons said:**
> I was attempting to install an application via command line in 11.10 and had the task freeze up after 3/4 of the files had been written. As a result, I am unable to install Computer Janitor to clean it up. When I try to install it using the software center or terminal, I get an error. 

Is there a way to use the live CD to clean this up?

What is the error you're getting? If the problem only exists in APT (i.e., with a package manager) there's no need to boot from a LiveCD to fix it. If, on the other hand, there is a problem with the file system, you need to run fsck on the *un*mounted partition(s). The LiveCD would be perfect for that; or you can have fsck run on next boot by running ```
sudo touch /forcefsck
``` in a terminal.

---

### Post by Rgibbons on 2012-02-09
Thanks all. That helped a lot.

---

