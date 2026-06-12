---
title: "Black- Screen after Login"
date: 2012-06-15
forum: General Help
---

### Post by Wiking on 2012-06-15
After logging into Kubuntu I only get a black screen with a mouse pointer.

I tried several of the commands and updates but so far nothing has worked. In fact before I could see the login screen, now the login screen is just black like a console.

The only way the GUI works is if I start Kubuntu in Repair Mode and then select 'fix packages' let it update a bit and then resume normal startup. I would prefer if I didn't have to do this everytime I started Kubuntu.

I  have a Gefor Fx Go5200 for a video card (laptop), I tried running some apt-get commands to update the Nvidia drivers, but the line returned: "Packages not found".

---

### Post by cortman on 2012-06-15
Sound like you're logging into a bare X session, with no DE or WM loaded.
Boot into recovery mode (from the GRUB menu) and run the command

```
sudo apt-get install kubuntu-desktop --reinstall
```

To see if you can just reinstall the DE.

---

### Post by Wiking on 2012-06-15
I typed in the command and got the following:

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

---

### Post by cortman on 2012-06-15
Apparently you still have an apt or dpkg process running. You can either log out and back in or follow [these instructions]("http://cortman.wordpress.com/2012/02/24/unable-to-obtain-lock-for-software-installation/") to release the lock.

---

### Post by Wiking on 2012-06-15
I followed the instructions and I only got either one of these messages:

Warning: Program '/bin/bash/' crashed.

or

kill: No such process

---

### Post by cortman on 2012-06-15
Whoa. That's not good.
Try rebooting and then running the reinstall command.

---

### Post by Wiking on 2012-06-15
Yes I tried all that. 

Last night I edited the xconfig file, I had to create it, it wasn't even there.

---

### Post by Wiking on 2012-06-15
I think I will just reinstall.

---

### Post by cortman on 2012-06-15
I think that's probably your best option at this point.

---

