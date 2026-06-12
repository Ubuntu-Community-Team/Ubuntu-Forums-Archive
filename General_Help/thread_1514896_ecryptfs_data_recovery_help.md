---
title: "ecryptfs data recovery help"
date: 2010-06-21
forum: General Help
---

### Post by jacyt on 2010-06-21
hi everyone, i am pretty new with the ubuntu server operation system. i know the basics of how it works but i have run into a snag with the ecryptfs setup. i used ecryptfs to setup file encryption on one of my hard drives way back and no longer need it. i followed these steps from a tutorial link i found from somewhere else on the forum on how to remove the encryption and now my files are gone. 
 
any help on recovering them is much appreciated! 
 
here are the commands i used and the link i got them from:
 
from this link: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup)
**How to Remove an Encrypted Private Directory Setup**
 
 
 
 

Perhaps an Encrypted Private Directory is not for you. To remove this setup:[LIST=1]
[*]Ensure that you have moved **all** relevant data out of your ~/Private directory
[*]Unmount your encrypted private directory
[LIST]
[*]$ ecryptfs-umount-private
[/LIST]
[*]Make ~/Private writable again
[LIST]
[*]$ chmod 700 ~/Private
[/LIST]
[*]
 
 

Remove ~/Private, ~/.Private, ~/.ecryptfs (**Note: THIS IS VERY PERMANENT**)
[LIST]
[*]$ rm -rf ~/Private ~/.Private ~/.ecryptfs
[/LIST]
[*]Uninstall the utilities
[LIST]
[*]$ sudo apt-get remove ecryptfs-utils libecryptfs0
[/LIST]
[/LIST]

---

### Post by Maj Jin on 2010-06-22
I am having a near similar problem. I have a encrypted /home directory on a separate partition and I need to mount it and copy the files to my new /home directory and I do not have my pass phase. I have my original password I used to log into Ubuntu though... any help would be greatly appreciated.

---

### Post by Bachstelze on 2010-06-22
> **Maj Jin said:**
> I am having a near similar problem. I have a encrypted /home directory on a separate partition and I need to mount it and copy the files to my new /home directory and I do not have my pass phase. I have my original password I used to log into Ubuntu though... any help would be greatly appreciated.

```
ecryptfs-unwrap-passphrase
```

will ask for your login password and give you your passphrase.

---

### Post by Maj Jin on 2010-06-23
so yeah! I was able to, by using that command, obtain my mount password. So my next project is to actually mount the device and then un-encrypt the data. What the Ubuntu wiki  does not explain is that you have to find where that file wrapped-passphrase is. And then navigate to it in the terminal then run the command: ecryptfs-unwrap-passphrase

Thanks [Bachstelze]("http://ubuntuforums.org/member.php?u=51114") for your help! Hopefully I will be able to accomplish
This next part!

---

### Post by Maj Jin on 2010-06-24
So now I am stuck at the part where I  mount the drive.
my old encrypted home is located at /media/6dd6840c-ba86-492c-9c42-bbfb86337250
$ls -l
kakashi  lost+found
 I have my mount passphrase, and the second half to my fnek sig
how would I correctly enter the syntax to mount my drive so I can view  my files ?

---

