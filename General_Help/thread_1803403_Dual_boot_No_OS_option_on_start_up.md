---
title: "Dual boot: No OS option on start up"
date: 2011-07-13
forum: General Help
---

### Post by tompadfield on 2011-07-13
Hello all,

I'm completely new to Linux and have just installed Ubuntu alongside Windows 7. I just went along with the manual set-up all through the install. I was expecting to see an obvious option on starting up my computer as to whether to run Ubuntu or Windows but it just goes right ahead and runs windows exactly as it did before the install. Can anyone tell me where to go from here.

Thanks,
Tom.

---

### Post by raja.genupula on 2011-07-13
are you seeing anything like grub loader while booting ? 

or
was grub also not showing, & directly  booting to windows  ? ?

---

### Post by tompadfield on 2011-07-13
Nope, not seeing the Grub loader or anything at all, it just loads up Windows up directly as it always has.

---

### Post by dino99 on 2011-07-13
no that mean your dont have installed grub (the bootloader) while installing ubuntu. Boot from the livecd to install it on /dev/sda

---

### Post by tompadfield on 2011-07-14
Thanks for your advice, folks, but I'm afraid I really need it spelt out to me in words of one syllable. 

I found this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) which sort of helps, but what worries me is the where it says:

 'an explicit warning (though it is mentioned) that this guide will write  GRUB to the MBR (just in case someone is using a different boot loader  on their MBR and would like to reinstall GRUB to a partition'

Well, wanting to run a dual boot then, then my hard drive is partitioned, so does this warning apply to me?

---

### Post by dino99 on 2011-07-14
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

