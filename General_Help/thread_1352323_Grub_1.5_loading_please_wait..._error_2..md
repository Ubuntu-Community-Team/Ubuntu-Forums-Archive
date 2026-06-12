---
title: "Grub 1.5 loading please wait... error 2."
date: 2009-12-11
forum: General Help
---

### Post by crist360 on 2009-12-11
I have an Acer Aspire One netbook model ZG5 (ssd storage version) running Jaunty pretty well. Some days ago my system started to become slower and it showed lots of errors while booting. I turned it off by pressing the power button and when it started again I received a message which said **Grub 1.5 loading please wait... error 2**. Now, every time I start my system I receive the same message, indeed, I cannot format my system and install Ubuntu again because I receive an error that says **Input/Output Error during write on dev/sda** while the installation is running. I've been researching on many websites and there isn't any solution that really works. 

I would like to know how to fix, delete, reinstall the grub or whatever to install Ubuntu again, I have used a live version of Ubuntu from a pendrive to work in the terminal in order to fix the grub, but nothing works. The message is still there.

---

### Post by MichaelDance on 2009-12-11
That is not a problem mate that is just the grub loading

---

### Post by crist360 on 2009-12-11
> **MichaelDance said:**
> That is not a problem mate that is just the grub loading

I think I didn't explain my message in a good way hahaa. I know it is the GRUB loading, but it doesn't load because it gets an error 2 and I can't access to my system. My netbook doesn't have any contact with the ssd storage drive. My system just keeps with the black screen and the grub error 2. I know the grub is damaged and while I don't fix it, I'm not able to format my system and install Ubuntu again. 

;)

---

### Post by joes7 on 2009-12-11
Launch LiveCD and access "install grub". Overwrite your current installation. Once done, open a terminal and write
```

update-grub

```
Done.

---

### Post by crist360 on 2009-12-11
> **joes7 said:**
> Launch LiveCD and access "install grub". Overwrite your current installation. Once done, open a terminal and write
```

update-grub

```Done.

It's not possible to do that because it says that there is a bad superblock on /dev/sda1. I think the main problem doesn't come from the grub, my file system is involved.

---

