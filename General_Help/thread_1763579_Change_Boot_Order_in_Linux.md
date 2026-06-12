---
title: "Change Boot Order in Linux ?"
date: 2011-05-20
forum: General Help
---

### Post by eipapp on 2011-05-20
I have a dual boot linux system with Mint 10 and Ubuntu 11.
Currently Mint is the first OS in the boot order. How difficult is it to change that config so that Ubuntu is first (or default) and Mint second ?

Thanks,
Bruce

---

### Post by hwttdz on 2011-05-20
Shouldn't be an issue, make the change in /etc/default/grub and run "sudo update-grub".

---

### Post by eipapp on 2011-05-21
OK, I must be doing something wrong as I got the message "command not found". I  assumed that I was to run /etc/default/grub in the command line in terminal, was that correct and if so why the message command not found.

Thanks,
Bruce

---

### Post by drs305 on 2011-05-21
Grub-Customizer is a good GUI tool for making changes. 
[Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183")

If you would prefer to edit the actual files, check out the following (but I'd use GC myself).
[http://ubuntuforums.org/showthread.php?t=1302743]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by cbowman57 on 2011-05-21
> **drs305 said:**
> Grub-Customizer is a good GUI tool for making changes. 
[Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183")

If you would prefer to edit the actual files, check out the following (but I'd use GC myself).
[http://ubuntuforums.org/showthread.php?t=1302743]("http://ubuntuforums.org/showthread.php?t=1302743")

+1, it's a great tool.  Personally I like to set mine to use last booted rather than setting it to a particular installation, but that's just personal preference.

---

