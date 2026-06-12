---
title: "Cannot boot Ubuntu after package updates"
date: 2010-12-04
forum: General Help
---

### Post by ganesh_k on 2010-12-04
I am having a dual boot with Windows 7 OS(64 bit) and Ubuntu 10.10. I installed Ubuntu through Wubi installer from my Windows 7. Usually when I start my computer it first shows my Windows Boot Manager screen. It shows a menu with 2 options Windows 7 and Ubuntu. For getting into Windows 7 I need to choose the first option. For booting into Ubuntu I need to choose the 2nd option i.e Ubuntu. And then it would show me a Grub boot menu with the options being different kernel versions and recovery modes etc. The latest I had was some 2.6.26 version.

I recently did a package update with update-manager. After the update I am not able to boot into Ubuntu. After the Windows boot manager screen it takes me to a screen that says something like
Try (hd0, 0): NTFS5: No wubuildr
Try (hd0, 1): NTFS5: No wubuildr
Try (hd0, 2): NTFS5: 

After this the screen turns into full white and then it automatically reboots! It doesn't take me to the Grub menu! It happens quite fast that to even read the above 3 lines it took to try booting a number of times!

One thing I noticed in the package update was that grub was one of the updated packages. Another thing is that in my Windows 7 in c: directory there is a file called wubuildr whose creation time is almost the same time as when the package update happened. There is also a wubuildr.mbr but it's creation and last modification times are much older. But then I am clueless as to what is the purpose of the file and so I am not sure how to use it to fix this problem if possible.

Also through ext2explore program from Windows 7 I could copy the /boot/grub/grub.cfg and /var/log/dpkg.log files. I have attached grub.cfg and dpkg.log with .txt extensions. In the dpkg.log file that I attached I just removed all lines except those containing "upgrade" so that it wouldn't be too long a file and you can easily see just what packages were upgraded. Please let me know if you would like me to attach the original file.

Please help me solve this booting problem. Thanks in advance.

Thanks,
Ganesh

---

### Post by karthick87 on 2010-12-04
Can you post the results of **[[COLOR=Sienna]Bootscript[/COLOR]]("http://bootinfoscript.sourceforge.net/").**

---

### Post by ganesh_k on 2010-12-04
Hey karthick87,

I have attached the RESULTS.txt file from boot_info_script055.sh as you asked for. Sorry it took me a while since I didn't have a readymade live CD available with me.

Thanks,
Ganesh

---

### Post by Rubi1200 on 2010-12-04
Explanation and fix for Wubi installs:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
In your case, you would mount sda3 since this is the Windows partition containing the root.disk

For a more permanent fix once Ubuntu is booting again:
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

(edit: and my apologies to karthick87 for jumping in)

---

### Post by karthick87 on 2010-12-04
@Rubi1200 No problem,we are here to help others :)

---

### Post by ganesh_k on 2010-12-04
Thank you very much @Rubi1200 and @karthik87 for the favor. Now my Ubuntu is booting up! :)

---

### Post by Rubi1200 on 2010-12-05
You are more than welcome :)

---

