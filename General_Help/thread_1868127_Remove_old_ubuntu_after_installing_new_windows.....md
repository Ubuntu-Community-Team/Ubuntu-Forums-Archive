---
title: "Remove old ubuntu after installing new windows...."
date: 2011-10-23
forum: General Help
---

### Post by Lateralus138 on 2011-10-23
Im sorry if this isnt the right place to post, but I wasnt sure how to categorize this... I had Windows Vista Ultimate with Ubuntu as a duel OS, but recently i upgraded my Vista to 7 ultimate and of course when I did now I no longer have access to the grub loader and cant see any of the files of course cant find it with bcd... It is taking up disc space of course so does anyone have a suggestion of how to find and remove it? If I try to install another Ubuntu will it find the old installation? or is there some way to view the ubuntu file system in ntfs other than bcd? Id appreciate any help.

---

### Post by techvish81 on 2011-10-23
boot with live ubuntu cd, install boot rescue , u will have to just click on the first option which did the job for me. 
Google with boot rescue after booting in live cd. u will get how to install it if is not in the repos.

---

### Post by Lateralus138 on 2011-10-23
Awesome thanx... I had thought I had seen something like that before on the disc, but it had been quite a while and wasnt for sure.

---

### Post by techvish81 on 2011-10-23
> **Lateralus138 said:**
> Awesome thanx... I had thought I had seen something like that before on the disc, but it had been quite a while and wasnt for sure.

after taking backup of your old ubuntu files u can again install newer version of ubuntu , it will find both of your operating systems and wil give you the option of installing new ubuntu alongside them. but it is better to install ubuntu on the partition where old ubuntu was, if you Dont need it any more.

---

### Post by Lateralus138 on 2011-10-24
I found the old install with the disc and I just decided to upgrade it since the oldone was 11.04 (or something liek that) and the new is 11.10. Thanx for the help, I do appreciate it.

---

### Post by linuxwin2 on 2011-10-25
To install grub:
1- boot in rescue mode with live cd
2- ```
# grub-install /dev/sda
```

---

