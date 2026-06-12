---
title: "Problem with hibernate in Ubuntu"
date: 2011-11-24
forum: General Help
---

### Post by yourself65 on 2011-11-24
Hello everyone,,

after browsing for a long long time
i found this thread: 
[http://ubuntuforums.org/showthread.php?t=1454029&page=2](http://ubuntuforums.org/showthread.php?t=1454029&page=2)

i managed to get hibernate appear again :D

but when i press it, the screen freezes for a while then appears again like (lock the screen) or something

i thought there might be a problem with my vga
so here is mine if u 'll ask for it:
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller

p.s. i don't have a problem with (suspend or sleep) at all from the beginning

---

### Post by San_SS! on 2011-11-24
Have you checked that your swap space is bigger than the RAM memory you have?

---

### Post by yourself65 on 2011-11-24
> **San_SS! said:**
> Have you checked that your swap space is bigger than the RAM memory you have?

yes i extend it..
here is the new size 

total used free shared buffers cached
Mem:               3924 1413 2511 0 53 705
-/+ buffers/cache: 654 3270
Swap:              4614 0 4614

---

### Post by plucky on 2011-11-24
> **yourself65 said:**
> yes i extend it..
here is the new size 

total used free shared buffers cached
Mem:               3924 1413 2511 0 53 705
-/+ buffers/cache: 654 3270
Swap:              4614 0 4614

Please post output from a terminal for ```
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by prshah on 2011-11-25
> **yourself65 said:**
> 
but when i press it, the screen freezes for a while then appears again like (lock the screen) or something

If you have recreated swap, you need to match UUIDs for hibernate to work. See [Re: hibernate not working]("http://ubuntuforums.org/showpost.php?p=5370529&postcount=2") for details.

Please post back results and error messages in this thread, for further help if required.

Regards,

---

### Post by yourself65 on 2011-11-25
i have already matched UUIDs
here is what i got in termina:


mirooz@mirooz-HP-Pavilion-dv6-Notebook-PC:~$ sudo blkid

/dev/sda1: UUID="E2B8EB0FB8EAE0D1" TYPE="ntfs" 
/dev/sda5: LABEL="iDeSigN" UUID="5952875E0769E824" TYPE="ntfs" 
/dev/sda6: UUID="0c0ffab8-dd1d-462c-b35f-601d58c376ee" TYPE="ext4" 
/dev/sda7: LABEL="Video" UUID="01CC766528A49170" TYPE="ntfs" 
/dev/sda8: UUID="03819721-b309-42ff-b4ac-efd64581ea8f" TYPE="swap" 


mirooz@mirooz-HP-Pavilion-dv6-Notebook-PC:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=03819721-b309-42ff-b4ac-efd64581ea8f

---

### Post by yourself65 on 2011-11-27
So what 's neXt ??? :=|

---

### Post by yourself65 on 2011-11-30
heeeeeeeeeeeey...

any solutions guyys :|

---

### Post by plucky on 2011-11-30
The only thing I can think of is,since you changed the UUID to the swap partition,have you run ```
sudo update-initramfs
```


Good Luck

---

### Post by prshah on 2011-12-01
> **yourself65 said:**
> 
but when i press it, the screen freezes for a while then appears again like (lock the screen) or something


Have you recently enabled WoL (Wake on Lan/Wake on Ring) technologies in the BIOS? If you have, try disabling it and then attempting to hibernate.

If you still find this problem, then you can re-enable it.

If you have done nothing like this, then you should probably ignore this entire advice.

---

