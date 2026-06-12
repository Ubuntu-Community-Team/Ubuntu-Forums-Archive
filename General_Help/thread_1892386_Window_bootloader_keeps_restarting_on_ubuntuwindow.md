---
title: "Window bootloader keeps restarting on ubuntu/window dual boot!"
date: 2011-12-07
forum: General Help
---

### Post by Stord on 2011-12-07
I have a ubuntu window dual boot. I installed windows first on a separate partition and then installed ubuntu on the rest of the partition (did not use wubi) . Whenever i attempt to boot windows from the ubuntu bootloader (i got it to show windows by using system-repair), it gets to the windows 7 logo popping up - then it restarts the computer and goes back to the ubuntu bootloader. Randomly, i am able to reach the windows login screen. Even when i do a cold shutdown and then try to boot windows, it still restarts most of the time!

Is there any way to fix this?

---

### Post by bluexrider on 2011-12-07
> **Stord said:**
> I have a ubuntu window dual boot. I installed windows first on a separate partition and then installed ubuntu on the rest of the partition (did not use wubi) . Whenever i attempt to boot windows from the ubuntu bootloader (i got it to show windows by using system-repair), it gets to the windows 7 logo popping up - then it restarts the computer and goes back to the ubuntu bootloader. Randomly, i am able to reach the windows login screen. Even when i do a cold shutdown and then try to boot windows, it still restarts most of the time!

Is there any way to fix this?


try these instructions  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

drop down to windows recovery

---

### Post by Stord on 2011-12-09
Hmm, i have a windows 7 cd already. The problem is that it sometimes will boot into windows but sometimes it will simply restart after i try to boot into windows. How will a cd fix this? 

Admittedly, the sequence of installation went like this -> install ubuntu, install windows, install ubuntu again after deleting everything on ubuntu partition... So will reinstalling windows help with the restarting problem? Also, i didnt use wubi. Should i install windows on everything and just use wubi? I dont really know anything bout it and what it does, all i really want is to split my hard drive space between both operating systems and to be able to easily reboot into either one based on my needs.

---

### Post by seawolf167 on 2011-12-09
Try reinstalling the Windows boot items, then Grub2 as the MBR after that.

Boot off your Windows 7 cd and go to the recovery prompt, then type in the following commands:

```
bootrec.exe /fixboot
bootrec.exe /fixmbr
```

then restart and make sure that your computer boots into Windows 7 normally. Once it boots into Windows normally, follow the procedure [listed here ]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")to reinstall Grub as the MBR.

Reboot and ensure that both operating systems boot normally.

---

