---
title: "Edit GRUB boot options"
date: 2011-07-01
forum: General Help
---

### Post by mihalybaci on 2011-07-01
I recently switched my laptop from Ubuntu 11.04 to 10.04.2, and during the process, I used GPARTED to partition the drive so that I could have both versions installed simultaneously while I transferred files and settings and such. A few days ago, I removed the 11.04 partition, formatted and added that disk space to 10.04's /home partition. However, when I boot up, GRUB still gives me the option of loading into the newer 11.04 partition with the newer kernels. How do I remove those options from the GRUB menu? I checked the Ubuntu GRUB help pages, but didn't feel confident that I could do edits without messing up the 10.04 boot settings. 

Thanks in advance.

---

### Post by collisionystm on 2011-07-01
> **mihalybaci said:**
> I recently switched my laptop from Ubuntu 11.04 to 10.04.2, and during the process, I used GPARTED to partition the drive so that I could have both versions installed simultaneously while I transferred files and settings and such. A few days ago, I removed the 11.04 partition, formatted and added that disk space to 10.04's /home partition. However, when I boot up, GRUB still gives me the option of loading into the newer 11.04 partition with the newer kernels. How do I remove those options from the GRUB menu? I checked the Ubuntu GRUB help pages, but didn't feel confident that I could do edits without messing up the 10.04 boot settings. 

Thanks in advance.


Install Startup-Manager from the software center.

---

### Post by Rubi1200 on 2011-07-01
First run ```
sudo update-grub 
```to see if that resolves the issue.


I recommend Grub Customizer for configuring GRUB menu options:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by mihalybaci on 2011-07-01
Hmmm...didn't realize there were programs, I thought I'd have to do it manually. I'll check those programs out tonight. Thanks for the fast replies!

---

### Post by drs305 on 2011-07-01
Grub Customizer is a great app designed for Grub 2. Click on the ''Customizer link in my signature line.

---

### Post by mihalybaci on 2011-07-01
Thanks for the replies. "update-grub" did the trick, but it's really nice to know that I can edit the boot so easily with those programs (I checked them both out).

---

### Post by Rubi1200 on 2011-07-02
Excellent! I am glad this worked for you.

Enjoy :)

---

