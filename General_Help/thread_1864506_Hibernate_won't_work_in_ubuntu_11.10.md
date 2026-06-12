---
title: "Hibernate won't work in ubuntu 11.10"
date: 2011-10-19
forum: General Help
---

### Post by Byb on 2011-10-19
Hi
My laptop Fujitsu-Siemens Amilo M7405 won't hibernate : on hibernate request, the screen goes black then immediately prompts for my password to logging again, like if the hibernate process was hooked to "Lock screen" command Super+L.
Any idea boys ?
Thanks

---

### Post by JohnDoe365 on 2011-10-22
check if 
[http://ubuntuforums.org/showpost.php?p=11380886&postcount=3](http://ubuntuforums.org/showpost.php?p=11380886&postcount=3)

helps

---

### Post by Byb on 2011-10-24
Thanks man. It was the exact problem.
I got the UUID info in gparted, so I changed my /etc/initramfs-tools/conf.d/resume and fstab according to the real UUID, then launched
```
sudo update-initramfs -u -k $(uname -r)
```It works fine now.
I think the issue reborn when I tryied to change my swap partition size 

I found this "old" tip here [http://doc.ubuntu-fr.org/uuid_et_label#uuid_swap_et_hibernation](http://doc.ubuntu-fr.org/uuid_et_label#uuid_swap_et_hibernation)

Now it remains the problem of suspend to RAM not working but it seems to be a completely different issue.


THank a lot

---

