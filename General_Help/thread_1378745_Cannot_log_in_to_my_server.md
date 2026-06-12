---
title: "Cannot log in to my server"
date: 2010-01-11
forum: General Help
---

### Post by zagabar on 2010-01-11
Yo. 

I was connected to my ubuntu server with putty when I suddenly ran out of disk space. Then when I tried to log in with FTP to delete stuff, I could not get permission to log in. I couldn't connect with mumble either. Not even with putty to new shells. However I was already logged in. Then I used putty to delete some stuff on the full partition (both home and root are on it) and I managed to free 4 gb. Then I sent a reboot command and I never managed to connect again. Something was terribly wrong...

Now when I have finally got home from my vacation, I connected a monitor and keyboard to the server and started it up. It seemed to boot fine, but when trying to log in, I get: "[SIZE=2]Cannot execute /bin/bash: Permission denied[/SIZE]"

I started recovery mode and logged in as root. I still have 4 gb free on that disk. It isn't marked as noexec in fstab, nor is it mounted as it when I check with "mount". Someone suggested me to reinstall all packages becuase there might be a possibility for corruputed files due to the space shortage. When trying that, I get the error message: "i wasn't able to locate file for the linux-image-2.6.24-24-server package. This might mean you need to manually fix this package."

I am kinda noobish and I have no clue on what to try next or what the problem might be. I would gladly apreciate any help.^^

Cheers.

---

### Post by zagabar on 2010-01-12
bump

---

### Post by zagabar on 2010-01-12
No one knows?  D: Please, I am using my server for email and many other stuff and I have no clue at all on how to fix it. :/

---

