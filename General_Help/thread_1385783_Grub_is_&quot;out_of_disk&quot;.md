---
title: "Grub is &quot;out of disk&quot;"
date: 2010-01-20
forum: General Help
---

### Post by Virtualboxbuntu on 2010-01-20
I was using my computer when it froze for no apparent reason. I didn't enable ctrl-alt-backspace like I should have so I had to do a hard reset. When the computer rebooted, it tells me:

out of disk
rescue>_

I've tried mounting the filesystem through a live cd to fix it, but it gives me an error and can't mount it. What else should I try? I have important information on my hard drive that I can't afford to lose.

Thanks

---

### Post by user1397 on 2010-01-20
> **Virtualboxbuntu said:**
> I was using my computer when it froze for no apparent reason. I didn't enable ctrl-alt-backspace like I should have so I had to do a hard reset. When the computer rebooted, it tells me:

out of disk
rescue>_

I've tried mounting the filesystem through a live cd to fix it, but it gives me an error and can't mount it. What else should I try? I have important information on my hard drive that I can't afford to lose.

Thanksfollow this page on how to fix your MBR (master boot record) aka grub:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

edit: ah didn't see you couldn't mount it, yea i would free up space like cariboo907 said.

---

### Post by cariboo on 2010-01-20
It sounds like you are out of hard drive space, you may want to use the live CD to make some empty space on your hard drive.

---

