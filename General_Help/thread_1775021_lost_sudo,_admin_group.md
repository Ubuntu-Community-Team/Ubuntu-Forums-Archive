---
title: "lost sudo, admin group?"
date: 2011-06-04
forum: General Help
---

### Post by berryboy on 2011-06-04
apparently im no longer in the list of sudoers
i'v been adding groups and users and this may have caused the problem. is there a limit as to how many groups a user canbe a member of?

also anyway of fixing this? really dont want to format just got everything perfect :/

i connect via remote desktop / putty
ubuntu desktop 10.04 LTS

please help!

---

### Post by Thewhistlingwind on 2011-06-04
Live CD, then add yourself to the sudoers file.

---

### Post by garvinrick4 on 2011-06-04
First to open /etc/sudoers as root in terminal, run the follwing commands:
  ```
sudo -i
``` ```
visudo
```

  Now, scroll to the bottom of the file and add the following line:
  username ALL=(ALL) ALL

  where “username” is the username you use to login to your computer.
Press Ctrl+O followed by ENTER to save /etc/sudoers and you are done.
 Hope this helps.

---

### Post by garvinrick4 on 2011-06-04
Now if you cannot get into root account have to use live cd and chroot:
or another install of same architecture (32 or 64 bit) and use your own sda#
I am using sda5 for this: sudo fdisk -l (lower case L) to find your linux sda#
```
sudo mount /dev/sda5 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
``````
sudo chroot /mnt
``````
visudo
```Now, scroll to the bottom of the file and add the following line: or whatever you want to add:
  username ALL=(ALL) ALL

  where &#8220;username&#8221; is the username you use to login to your computer.
Press Ctrl+O followed by ENTER to save /etc/sudoers and you are done.
    
```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
``````
sudo umount /mnt
``````
sudo reboot
```

---

### Post by jerome1232 on 2011-06-04
You could just use recovery mode, get into a root shell and add your user back to the admin group

Just select recovery mode at the grub prompt (if you don't get one hit shift repeatedly while the computer is starting up you'll get it)
Select root shell at the menu that appears.

Replace the red text with your users name.

```
root@somecomputer:~# adduser [COLOR="Red"]username[/COLOR] admin
root@somecomputer:~# reboot
```

And all should be good

---

### Post by berryboy on 2011-06-04
i dont have physical access to the computer only remotedesktop and putty :'(

many thanks for your reply's

---

