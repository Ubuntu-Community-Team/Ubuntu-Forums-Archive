---
title: "Ubuntu Crashed, Lost All Files?"
date: 2010-10-25
forum: General Help
---

### Post by Andante on 2010-10-25
Hi everyone,

Today Ubuntu crashed while I was suspending it. I tried turning it back on and it just hangs at the boot-up screen. I tried booting from older kernels and from "recovery" kernels to no avail. When I used ext2explore on Windows 7 to try to view the partition, the /home director is empty other than some .encryptFs stuff.

Is there any possible way to restore my files? It's currently mid-terms week at my college and I was too dumb to make back-ups of my notes and homework so this is really stressing me out.

Thank you so much for any help.

Edit: Might be useful to say I'm on 10.04. Dell Latitude E6500 (I've always had Ubuntu suspend issues with this laptop).

---

### Post by Presence on 2010-10-25
Try using a dedicated rescue cd such as RIPLinux to access the files.

[http://distrowatch.com/table.php?distribution=rip](http://distrowatch.com/table.php?distribution=rip)

---

### Post by Andante on 2010-10-26
Thanks so much for your reply! I'm running RIPLinux right now and it appears that that partition is perhaps encrypted with ecryptfs. I've been trying but with no success to install ecryptfs on RIPLinux. Is there some alternative tool that might help me?

Thanks!

---

### Post by 311005901 on 2010-10-26
I would suggest using your install CD to boot up into a live desktop of Ubuntu. You should then be able to mount the filesystem and recover your files.

---

### Post by Andante on 2010-10-26
Thanks for all the help, everyone!

I managed to access my encrypted partition through more or less this: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Not](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Not) covered in this tutorial

(Hint for anyone else retriving an encrypted file: if you keep getting an ecryptfs error that a file or directory does not exist when it clearly does, you might have input an incorrect password at one point and need to reboot your system. This really threw me off.)

---

