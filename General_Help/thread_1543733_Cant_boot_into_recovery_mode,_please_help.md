---
title: "Cant boot into recovery mode, please help?"
date: 2010-08-01
forum: General Help
---

### Post by jabalsad on 2010-08-01
Hi all,

I have an encrypted file system and recently installed proprietary ATI drivers for my graphics card. The moment I did that, Ubuntu boots with a black screen. Now I'm attempting to get back into the OS to remove the drivers, but when I choose Ubuntu Recovery Mode from the grub boot screen, it shows some dmesg output and then the screen goes black. Whats interesting is it doesn't even ask me to decrypt the hard drive (like it normally does). Can someone please tell me how I can get back into the OS to remove the drivers?

Much appreciated.

---

### Post by jabalsad on 2010-08-01
So I left it for a little while and eventually the decrypt screen came on, except it goes black every now and then... I continued to decrypt the drive, but now its just doing nothing and the screen is black :|

---

### Post by jabalsad on 2010-08-01
Ok, I used the alternate install CD to get into a shell on my root filesystem. How do I know where the ATI drivers are located and how to remove them?

---

### Post by jabalsad on 2010-08-01
I did 'n dpkg -r fglrx and its dependencies... Still no love ;<

---

### Post by jabalsad on 2010-08-02
Ended up reformatting :( Now I'll know not to install that driver...

---

