---
title: "Grub please help"
date: 2006-02-16
forum: General Help
---

### Post by Typhoonsg1 on 2006-02-16
i recently installed Ubuntu onto my PC along side ******** XP and what i want to do is make it so XP is my primary OS and it's the first selection on the grub menu could you please tell me how to change the order around thanks:KS

---

### Post by Zeroangel on 2006-02-16
[http://www.ubuntuforums.org/showthread.php?t=128707](http://www.ubuntuforums.org/showthread.php?t=128707)

Look at the last few posts

---

### Post by Typhoonsg1 on 2006-02-16
Oops i'm sorry i forgot to mention that i'm  quite new to Linux could you please write it step by step thank you, oh yeah could you also explain to me what the default password for the root account is and how do i make it so i can access my windows partition (permissions) thanks for the help

---

### Post by frodon on 2006-02-16
If you can't access your window partition under linux without root access you should follow instructions contained in this link : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

The default sudo password is your user password : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)

---

### Post by Zeroangel on 2006-02-16
OK. Here goes:

1) Open up your applications menu; and select accessories -> terminal

2) Type in the following:```
sudo gedit /boot/grub/menu.lst
```You will be asked for a password. Just use the password that you used when you installed Ubuntu.

3) Scroll to the bottom of the file, then:

Remove the savedefault line from the Ubuntu boot option, and put it in the Windows XP boot option. 

(Optional) You could also copy/paste the Windows XP chunk of text and put it at the top of the list.

---

### Post by Typhoonsg1 on 2006-02-16
Ahh thank you that is music to my ears

---

