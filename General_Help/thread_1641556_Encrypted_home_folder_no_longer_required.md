---
title: "Encrypted home folder no longer required"
date: 2010-12-09
forum: General Help
---

### Post by welshmike on 2010-12-09
During the installation of 10.04 I opted to have my home folder encrypted.
I no longer want my home folder to be encrypted.
How may I achieve this please?

---

### Post by James_Lochhead on 2010-12-09
[http://ubuntuforums.org/showthread.php?t=1135796](http://ubuntuforums.org/showthread.php?t=1135796)

4th post

---

### Post by welshmike on 2010-12-09
Thank you for the reference.

I will follow the "script" by CAPPED but am a little nervous about its success given that the Forum  message shows Beans: 1.
So I will backup my Home folder to an external HDD first.

One thing I have not found out is whether 
1. the whole of an encrypted Home folder gets decrypted at Log in
or
2. individual files get decrypted when referred to.
If it is 1. the speed of decryption of my 17GB Home folder is amazing

---

### Post by Megaptera on 2010-12-09
Don't be put off by the bean count. That person could be 999,999,999 beans at another Ubuntu / linux forum.

---

### Post by welshmike on 2010-12-09
Well. I failed at the first hurdle:
mike@mike-i3-notebook:~$ sudo mkdir /backup/
mike@mike-i3-notebook:~$ sudo cp -R /home/mike /backup
cp: cannot stat `/home/mike/.gvfs': Permission denied

---

### Post by welshmike on 2010-12-10
Second attempt failed too.
I bypassed step 2 and copied my home folder using Gnome.
I followed the script precisely from step 3 and when I rebooted at step 4 no desktop contents appeared such as icons and panel, just the default desktop background and no input being accepted from keyboard or mouse. 
Fortunately I had a second admin user, mike2, that I could log in to after I restarted Ubuntu using Ctrl Alt Del and removed the #s from the start of the lines in the three files that referred to pam_ecryptfs. I then logged out of mike2 and logged in to mike, my working user that has the encrypted home folder. This showed desktop contents and panel satisfactorily. 
Phew !!!

---

