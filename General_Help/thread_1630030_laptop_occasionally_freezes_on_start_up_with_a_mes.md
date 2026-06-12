---
title: "laptop occasionally freezes on start up with a message"
date: 2010-11-24
forum: General Help
---

### Post by andypearce on 2010-11-24
Hi, another problem.... I am using 10.4 on a Toshiba satellite pro L100 and have got it working well enough with ubuntu. However, every now and again it freezes on start up and I think it may be before the automatic disc driver check and scan that happens on start up now and again. It gets stuck and tells me 

[  33.117318][drm:rs400_gart_adjust_size]*ERROR*forcing to 32M GART SIZE (because of ASIC bug?)

Should I be worried... I only ask as I have to do a hard shut down and computers don't like them do they?

Thanks 
Andy

---

### Post by wojox on 2010-11-24
It appears to be a kernel that has yet to be resolved. [*ERROR* Forcing to 32M GART size]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843")

Look at number #34 for a quick fix maybe?

---

### Post by andypearce on 2010-11-26
hi,
wojox, you said 'Look at number #34 for a quick fix maybe?', what did you mean by this? I am not very proficient at this kind of thing, but learning fast.
thanks
andy

---

### Post by plucky on 2010-11-26
> **andypearce said:**
> hi,
wojox, you said 'Look at number #34 for a quick fix maybe?', what did you mean by this? I am not very proficient at this kind of thing, but learning fast.
thanks
andy

Click on the link and scroll down to post #34 and you will see ```
lazenge wrote on 2010-08-24: 	#34

fix that works for me:

in /etc/default/grub

add radeon.modeset=0 to GRUB_CMDLINE_LINUX_DEFAULT

then sudo update-grub2

```

Good Luck

---

### Post by andypearce on 2010-11-28
Oh yes... I see now, bit embarrassed but thanks for that I will look at it.
Thanks
Andy

---

