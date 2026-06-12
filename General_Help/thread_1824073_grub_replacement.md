---
title: "grub replacement"
date: 2011-08-13
forum: General Help
---

### Post by raja.genupula on 2011-08-13
i have installed 11.04 first and 10.04 after 11.04 . is it possible to make the grub of 11.04 as primary . i mean in booting i wanna move with grub.cfg of 11.04 .

is it possible ? 

thanks in advance

---

### Post by raja.genupula on 2011-08-13
man i dint get your language . i am running with very small english what i know .

---

### Post by garvinrick4 on 2011-08-13
Boot into 11.04:
```
sudo grub-install /dev/sda
``````
sudo update-grub
```If from a live cd: with grub version 1.99 (11.04 and up)
```
sudo mount /dev/sd[COLOR=Red]xy[/COLOR] /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
sudo umount /mnt
```If from live cd with grub version 1.98 or below
```
sudo mount /dev/sd[COLOR=Red]xy[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
```[COLOR=Red]x[/COLOR] being drive letter and [COLOR=Red]y[/COLOR] being partition number
```
grub-install --version
```Above will give you version of grub using

---

### Post by SidebySide on 2011-08-13
Boot from 11.04 disk in live case & replace grub from its terminal.

Edit: sorry, when i was sending mine, above answer wasn't. so now, this is repetitive

---

### Post by raja.genupula on 2011-08-13
> **garvinrick4 said:**
> Boot into 11.04:
```
sudo grub-install /dev/sda
``````
sudo update-grub
```If from a live cd: with grub version 1.99 (11.04 and up)
```
sudo mount /dev/sd[COLOR=Red]xy[/COLOR] /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
sudo umount /mnt
```If from live cd with grub version 1.98 or below
```
sudo mount /dev/sd[COLOR=Red]xy[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt
```[COLOR=Red]x[/COLOR] being drive letter and [COLOR=Red]y[/COLOR] being partition number
```
grub-install --version
```Above will give you version of grub using


 ```
ubuntu@genupulas:~$ sudo grub-install /dev/sda1
[sudo] password for assassin: 
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.


``` 

i got as this .

---

### Post by raja.genupula on 2011-08-13
os-prober not detecting my 11.04 

here is the code , i had installed my 11.04 in sda1 


```
ubuntu@genupulas:~$ sudo os-prober
/dev/sda7:Ubuntu 10.10 (10.10):Ubuntu:linux
ubuntu@genupulas:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              49G  9.0G   37G  20% /

```

---

### Post by dcstar on 2011-08-13
> **raja.genupula said:**
> i have installed 11.04 first and 10.04 after 11.04 . is it possible to make the grub of 11.04 as primary . i mean in booting i wanna move with grub.cfg of 11.04 .

is it possible ? 

thanks in advance

Boot into 11.04 and run the following:

```
sudo dpkg-reconfigure grub-pc
```

---

### Post by Quackers on 2011-08-13
garvinrick4 suggested that you run this ```
sudo grub-install /dev/sda
``` from your booted 11.04 installation.
You appear to have run this ```
ubuntu@genupulas:~$ sudo grub-install /dev/sda1
``` The two are not the same! garvinrick4's comand installs grub to the mbr of the hard drive (if sda is the drive you want it on).
The command you appear to have used installs grub to the sda1 partition - not the mbr of the drive. This is a big difference.

---

### Post by raja.genupula on 2011-08-13
> **dcstar said:**
> Boot into 11.04 and run the following:

```
sudo dpkg-reconfigure grub-pc
```

hey i got this , seems  done right 

```
assassin@genupulas:~$ sudo dpkg-reconfigure grub-pc
[sudo] password for assassin: 
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda7
done

```

---

### Post by Quackers on 2011-08-13
That looks better :-)

---

### Post by raja.genupula on 2011-08-13
thanks to all friends , now i am back to grub of 11.04
 


 actually i have  two ubuntu's 11.04 and 10.10 . once i got grub crash while i am with 11.04 . to clear it i had tried many but i didnt get any thing useful . then i installed 10.10 to get back to my 11.04 . just now i check it by restarting my system . now i have the grub of my 11.04 .

            now i am free to  format my 10.10 drive ?

---

### Post by Quackers on 2011-08-13
Yes, if you want to delete the 10.10 partition you can now do that without affecting grub.
If you run ```
sudo update-grub
``` afterwards the grub menu entry for 10.10 will disappear.

---

### Post by raja.genupula on 2011-08-13
yeah ! i am successfully completed of removing my 10.10 part and then updating grub 
got this and sounds success 


```
assassin@genupulas:~$ sudo update-grub
[sudo] password for assassin: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin

```

thanks to all who picked this thread . i am closing this .

---

### Post by Quackers on 2011-08-13
Nice one :-)
Well done!

---

