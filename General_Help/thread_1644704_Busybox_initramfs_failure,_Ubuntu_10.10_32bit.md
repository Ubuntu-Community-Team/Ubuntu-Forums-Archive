---
title: "Busybox initramfs failure, Ubuntu 10.10 32bit"
date: 2010-12-13
forum: General Help
---

### Post by akzouu on 2010-12-13
Hey, here is a problem what i face everytime when i've installed Ubuntu 10.10 and have done updates, it's a problem with Busybox initramfs. So what's wrong in this situation? I would be very grateful if you guys could help me with this. I had installed Ubuntu 10.04 after this. And then i installed Ubuntu 10.10 again today. So, still i'd like to use Ubuntu 10.10. The link for a screen is below.

Cheers from Finland

---

### Post by neveruse513 on 2010-12-28
bump/rant

I'm having similar problems. It seems like a lot of people are. Haven't found a good answer yet.

The 6-month release cycle is starting to rear it's ugly head...

---

### Post by kongoon on 2011-01-03
> **akzouu said:**
> Hey, here is a problem what i face everytime when i've installed Ubuntu 10.10 and have done updates, it's a problem with Busybox initramfs. So what's wrong in this situation? I would be very grateful if you guys could help me with this. I had installed Ubuntu 10.04 after this. And then i installed Ubuntu 10.10 again today. So, still i'd like to use Ubuntu 10.10. The link for a screen is below.

Cheers from Finland

1.download [http://www.supergrubdisk.org/2011/01/02/rescatux-0-22-released/](http://www.supergrubdisk.org/2011/01/02/rescatux-0-22-released/)
2.burn cd
3.run from cd and go go go!
--------------------------------------------------
or this step
Navigate to the GRUB prompt, when starting boot. 

Add 'splash all_generic_ide' at the end of line quiet ==>quiet splash all_generic_ide

Ctrl+X to boot edit

---

### Post by taur on 2011-02-15
bump

---

### Post by gandaran on 2011-02-15
> **taur said:**
> bump
if you need help please post your question, don't bump someone else's thread.

---

### Post by Hippytaff on 2011-02-15
I would say a corrup iso. try checking the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by akzouu on 2011-02-15
This will help: [http://ubuntuforums.org/showthread.php?p=9863783](http://ubuntuforums.org/showthread.php?p=9863783) . See the comment from randyklein99

---

