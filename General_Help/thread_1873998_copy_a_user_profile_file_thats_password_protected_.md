---
title: "copy a user profile file thats password protected useing live cd (i have thepassword)"
date: 2011-11-02
forum: General Help
---

### Post by chinolofus on 2011-11-02
my install of ubuntu 10 messed up and wont boot. i need to take some files off of the computer so i can do a fresh reinstall. problem is that its password protected (might be root). i have the password but dont see where i can enter it and when i try to copy the files to an external hard drive it says it cant be accessed because i dont have permission to read it. so what do i need to do? oh and im using ubuntu 11 live on a usb drive.

---

### Post by gandaran on 2011-11-02
was the home partition encrypted?
if not then on the live cd or usb open root nautilus file browser then you can copy the files 

terminal command
```
sudo -i nautilus
```

---

### Post by chinolofus on 2011-11-02
ok i tried that and this is what i got....

ubuntu@ubuntu:~$ sudo -i nautilus
Initializing nautilus-gdu extension
** (nautilus:5894): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


i gave it a try anyways and it still says access denied
i could however actually open the folders this time instead of just seeing the folders. also a pic i have on my desktop goes to my external drive no problem...its the pics i have in my picture folder that wont move.

---

### Post by chinolofus on 2011-11-02
oh and it wasnt encrypted that i know of. i never encrypted it. just normal password protected as far as i know.

---

### Post by chinolofus on 2011-11-02
well i figured out i can send them via right click and "send to"...a bit of a pain but it works.

---

