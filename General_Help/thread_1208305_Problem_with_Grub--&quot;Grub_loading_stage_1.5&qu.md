---
title: "Problem with Grub--&quot;Grub loading stage 1.5&quot;"
date: 2009-07-09
forum: General Help
---

### Post by msaifee786 on 2009-07-09
Hi there, 
I'm a newbie to linux and I installed jaunty (dual booting with vista) about a week ago. Both work fine individually, but whenever I boot up in vista and then reboot, grub hangs at startup with "Grub loading stage 1.5". I booted up with the Ubuntu liveCD and reinstalled Grub, which fixed the problem, but whenever I boot into vista the same problem arises. 

It feels like vista overwrites something when it boots up so that it messes with Grub, but its just speculation on my part. 

Any help would be greatly appreciated. Thanks. 

msaifee786

PS: I found someone with a similar problem ([http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1188633&highlight=grub+stage](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1188633&highlight=grub+stage)) but that problem seems to be unresolved as of now. Thanks!

---

### Post by danwood76 on 2009-07-09
Certainly odd that vista affects this.
I dual booted Ubuntu and Vista for a couple of years now with no issues.

I would think that the issue is caused by grub itself and not vista.

When in your ubuntu can you post the output of the following command from the terminal:
```

cat /boot/grub/menu.lst

```

---

