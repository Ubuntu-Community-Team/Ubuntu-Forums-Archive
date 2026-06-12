---
title: "ubuntu does not resume from hibernate"
date: 2010-09-07
forum: General Help
---

### Post by grvsaxena419 on 2010-09-07
I have ubuntu 10.04 installed on a 50 gb partition on my hard drive
I have given a 3.5 gb partition for swap which is > 3gb ram i have.
Druing the installation of ubuntu I had specified the swap partition and its hibernate was working fine sometimes before. But I had to delete the swap partition and recreate it because of some reasons so I did that and again created a 3.5 gb partition for swap space usig ubuntu live cd. But after restart ubuntu no longer detected the swap partition it was ok as its uuid had changed 
so I specified the swap partition to be mounted automatically by adding an entry in /etc/fstab and then also added the same UUID in /etc/initramfs-tools/conf.d/resume so that it could resume.
After restarting ubuntu after adding the entrly in /etc/fstab i got the option of hibernate but after hibernate everything goes well but after hibernate when i start laptop again ubuntu first tries to resume but it does not and without giving any message it shows the login screen.
I dont know why this problem is coming. 
Please help.:(

---

### Post by jvpgomes on 2010-10-21
I have the same problem and I did the sames steps.

Please let me know if you find any solution.

Thank you!

---

### Post by jvpgomes on 2010-10-21
Now it's working! :D

I read somewhere that the UUID is also hard-coded in the /boot/initrd images

So, I decided to reinstall the kernel packages from the repositories (just the easy way). 
Don't forget to check if the UUID in the fstab is consistent with the UUI in /etc/initramfs-tools/conf.d/resume (as you described very well).

Please, let me know if this solved your problem.

---

