---
title: "sudoers permission problem"
date: 2011-09-20
forum: General Help
---

### Post by sropensrc on 2011-09-20
Hi,

I'm running 10.04 lucid and my sudoers file has 0640 permission.  I can't sudo to change and I can't sudo su.  I rebooted into recovery mode, when prompted for root password, it would not take it (I'm positive it's correct).  I booted into passwordless single user mode, it worked but system can't see keyboard. 

I need to change the sudoers file permission to 0440 permisison then I think I can sudo again.  Any suggestions?

Thanks

---

### Post by haqking on 2011-09-20
> **sropensrc said:**
> Hi,

I'm running 10.04 lucid and my sudoers file has 0640 permission.  I can't sudo to change and I can't sudo su.  I rebooted into recovery mode, when prompted for root password, it would not take it (I'm positive it's correct).  I booted into passwordless single user mode, it worked but system can't see keyboard. 

I need to change the sudoers file permission to 0440 permisison then I think I can sudo again.  Any suggestions?

Thanks

Recovery mode asked you for a root password ? did you unlock the root account at some point ? 

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by sisco311 on 2011-09-20
> **sropensrc said:**
> I booted into passwordless single user mode, it worked but system can't see keyboard. 


When you say single user mode, I guess, you mean you booted with the init=/bin/bash kernel parameter. If so, you have to remove the **splash** parameter. I think, the splash screen is causing the problem. 

Once the system boots up, you might have to remount the root partition rw:
```
mount -o remount,rw /
```

But, you can boot a Live CD/USB, mount the root partition and change the permissions of the sudoers file.

BTW, you should always use visudo to edit sudoers. Some editors might overwrite the permissions of the file. ;)

---

### Post by sropensrc on 2011-09-20
I added "rw init=/bin/bash" after the splash.  I will try the remove splash method tonight.  Thank you for adding the Live CD/USB method also.

Thanks for the quick reply, sisco311 and haqking.

---

### Post by sisco311 on 2011-09-20
Also, if the reboot command doesn't work in single user mode, then try Ctr+Alt+Del to reboot or ["Raising Elephants"]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.22Raising_Elephants.22_mnemonic_device").

---

### Post by sropensrc on 2011-09-21
I removed "splash", put in "rw init=/bin/bash", booted and still no keyboard input.  I tried the LiveCD but I didn't get the option to "Try Ubuntu without any change to your computer", I downloaded the server version, that's probably the problem.

I downloaded Ubuntu Desktop, on a test server I was able to boot CD and go into the "Try Ubuntu..." mode.  I tested changing permission on file on local disk, it worked.  I will attempt to change permission on sudoers file on live server tonight.

---

### Post by sropensrc on 2011-09-22
Since it couldn't see keyboard in single-user I used the boot LiveCD method.
Booted from ubuntu desktop cd and took the "Try Ubuntu without any change to your computer".
Open a terminal and mounted the hd root partition as /mnt, 
  sudo mount /dev/sda3 /mnt.
  ls -l /mnt/etc/sudoers, permission shows 640
  sudo chmod 0440 /mnt/etc/sudoers
  ls -l /mnt/etc/sudoers, permission now shows 440
  sudo umount /mnt
sudo is now working.

Thanks again haqking and sisco311.

---

