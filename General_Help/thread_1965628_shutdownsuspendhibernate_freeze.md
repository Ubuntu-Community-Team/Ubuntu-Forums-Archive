---
title: "shutdown/suspend/hibernate freeze"
date: 2012-04-26
forum: General Help
---

### Post by muhammad86 on 2012-04-26
Dear friends

I have newly installed ubuntu 12.04 beta, and I have a problem now. I can not shutdown/suspend, or hibernate my laptop ( a vaio VGN-SR, and my VGA is intel ATI) since it freezes in the process. I had ubuntu 10.04 previously and I didn't have such a problem. I have read other threads [here]("http://ubuntuforums.org/showthread.php?t=1694262"), but the solution they proposed didn't applied to me because the drivers they have talked about is not what I have (or I think I don't have).

the case in suspending, is that after suspension I could not activate the OS. and I just face a blank screen.

If anyone have a suggestion please let me know. 

Muhammad

---

### Post by Toz on 2012-05-02
> **muhammad86 said:**
> ( a vaio VGN-SR, and my VGA is intel ATI)

Have you installed the proprietary ATI drivers (I believe the menu item is called "Additional Drivers")

Can you post back the contents of the following files:
- /var/log/pm-suspend.log
- /var/log/dmesg
- /var/log/Xorg.0.log

and the results of the following command (run from a terminal window):
```
cat /proc/cmdline
```

---

