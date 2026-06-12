---
title: "Permanently delete swapfile?"
date: 2011-03-16
forum: General Help
---

### Post by 5149.5 on 2011-03-16
I have a swap partition and I would like to delete the swapfile setting that is a leftover from the install. I can turn it off using the dphys-swapfile swapoff command  but it returns after a boot.

dan@dan-AOD255://var$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda6                               partition    5119996    0    -1
/var/swap                               file        2097148    0    -2

---

### Post by Strongman332 on 2011-03-16
um i don't think you can get rid of it as it is a partition. maybe you can resize it and make it smaller. but if you do get rid of it expect problems later. no hibernate. oh and if your run out of ram Im not sure what will happen

---

### Post by wojox on 2011-03-16
Look in /etc/fstab and comment it out and see what happens.

---

### Post by 5149.5 on 2011-03-16
I want to get rid of the file not the partition. The entry in fstab is for the partition that I want to keep.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=dd029b11-e1e0-4b3e-a0e5-3f7518e07ab5 / ext4 errors=remount-ro,user_xattr 0 1
/dev/sda6       none            swap    sw              0       0
/dev/sda7    /home2   ext4    defaults     0        2

I want to use sda6 for swap space.




dan@dan-AOD255:/var$ ls -l swap*
-rw------- 1 root root 2147483648 2011-03-16 18:36 swap

I want to get rid of this file.

---

### Post by wojox on 2011-03-16
Oh, you didn't make that very clear. :P

```
sudo rm -rf /var/swap
```

---

### Post by 5149.5 on 2011-03-16
> **wojox said:**
> Oh, you didn't make that very clear. :P

```
sudo rm -rf /var/swap
```


I tried that.

rm: cannot remove `/var/swap': Operation not permitted

---

### Post by wojox on 2011-03-16
```
sudo su
```

```
rm -rf /var/swap
```

---

### Post by 5149.5 on 2011-03-16
> **wojox said:**
> ```
sudo su
``````
rm -rf /var/swap
```


dan@dan-AOD255:/var$ sudo su
[sudo] password for dan: 
root@dan-AOD255:/var# rm -rf /var/swap
rm: cannot remove `/var/swap': Operation not permitted

---

### Post by wojox on 2011-03-16
Did you disable swap before trying?

---

### Post by 5149.5 on 2011-03-17
> **wojox said:**
> Did you disable swap before trying?


:oops::oops: I thought I did. It works better with swap disabled. Now will the file get recreated after a boot. Or will the computer complain because it's not there now. Only one way to find out. Back in a minute.

---

### Post by wojox on 2011-03-17
> **5149.5 said:**
> :oops::oops: I thought I did. It works better with swap disabled. Now will the file get recreated after a boot. Or will the computer complain because it's not there now. Only one way to find out. Back in a minute.

No it should use your partition now.

---

### Post by 5149.5 on 2011-03-17
The file was recreated during the boot. I guess the real question is: How do I permanently disable the phys-swapfile process? I've done the uninstall of it.

---

### Post by wojox on 2011-03-17
See what this renders:

```
sudo apt-get purge dphys-swapfile
```

---

### Post by 5149.5 on 2011-03-17
> **wojox said:**
> See what this renders:

```
sudo apt-get purge dphys-swapfile
```


That looks like it worked. I was looking at the script in init.d and trying to figure out the best way to defeat it. You came up with a more elegant and safer solution. One more boot to see what happens.

---

### Post by 5149.5 on 2011-03-17
Thanks a bunch wojox. That's a fix. No more swapfile and swap is running on the partition now.

---

### Post by wojox on 2011-03-17
Cool man. :P

---

### Post by 5149.5 on 2011-03-17
> **wojox said:**
> Cool man. :P

Thank You again! I appreciate your help..

---

