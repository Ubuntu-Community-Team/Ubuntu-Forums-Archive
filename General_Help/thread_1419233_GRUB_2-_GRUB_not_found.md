---
title: "GRUB 2- GRUB not found"
date: 2010-03-01
forum: General Help
---

### Post by henners91 on 2010-03-01
Hi, i edited my grub file to remove splash screen, this involved changing script and saving new grub file then running sudo update-grub however now whenever i try it just comes back with: /etc/default/grub: 24: GRUB: not found
 Anyone know why it would do this?
 Thankyou, ps
 i'm running ubuntu9.10 with most recent updates

---

### Post by stlsaint on 2010-03-01
might want to consider re-installing grub.

---

### Post by darolu on 2010-03-01
I also think you should consider re-installing grub2, Here is the documentation you need: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldos2er on 2010-03-01
What's the exact command you used to edit your grub file?

---

### Post by henners91 on 2010-03-01
i didn't use a command, i changed the line for= "quiet splash" to =""
 that's all i've changed, could it have saved my grub file to a different location or something?

---

### Post by oldos2er on 2010-03-02
You must've opened it in an editor, correct? If you used gedit, it should've saved a backup file /etc/default/grub~.

Doing so wouldn't cause the problem you're having though. I concur with the reinstall grub2 advice.

---

### Post by henners91 on 2010-03-02
Well, i've reinstalled the grub and it's all fine now, still don't know what happened though, i did just press save after editing the file so there's no reason why it would move the file?!

---

