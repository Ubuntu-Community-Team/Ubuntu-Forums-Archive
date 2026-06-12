---
title: "Help with Gparted?"
date: 2011-04-27
forum: General Help
---

### Post by mattintc10 on 2011-04-27
I am sorry to bug you guys again but you seem to be VERY useful. 

Someone recomended i used Gparted to do a system check and fix one of my problems. I have googled how to do this but i am beyond confused of what i use if i use the terminal or what. Anymore help would be beyond appreciated and i thank you guys so much for your patients

---

### Post by lithopsian on 2011-04-27
gparted is for managing partitions rather than checking filesystems.  Still:
```
sudo gparted
```
and take a look for yourself.  If you need to make changes to your system partitions then you'll have to boot from a Live CD, or possibly a different OS, since you can't mess with a mounted partition.

---

### Post by mattintc10 on 2011-04-27
> **lithopsian said:**
> gparted is for managing partitions rather than checking filesystems.  Still:
```
sudo gparted
```and take a look for yourself.  If you need to make changes to your system partitions then you'll have to boot from a Live CD, or possibly a different OS, since you can't mess with a mounted partition.

im confused. i have been booting from a CD and i dont know if its live or not but any help on this would be greatly appreciated.

I tried that and it went back to its partition screen. I get that but i am trying to fix my error of stupidity when i shut it down to quickly while installing ubuntu software on the allocate harddrive screen.

---

### Post by K_45 on 2011-04-27
Its actually

```
gksu gparted
```

and what are you trying to fix? Partition alignment? File system check? S.M.A.R.T status?

---

### Post by mattintc10 on 2011-04-27
> **K_45 said:**
> Its actually

```
gksu gparted
```and what are you trying to fix? Partition alignment? File system check? S.M.A.R.T status?

Dumbass me like i said in my earlier post had shut down the laptop without it unmounting and what not and it would not go back into the installation software of ubuntu and what not and im having huge problems.

---

### Post by Buntumatic on 2011-04-27
You should boot with CD and run **fsck** first. If it errors out then you may be experiencing a hard drive failure.

---

### Post by K_45 on 2011-04-27
```
sudo fsck -y /dev/sda1
``` - to find out the right /dev:

```
sudo fdisk -l
``` - that's an l

as above.

---

### Post by mattintc10 on 2011-04-27
> **Buntumatic said:**
> You should boot with CD and run **fsck** first. If it errors out then you may be experiencing a hard drive failure.

Boot the ubuntu installation CD and how do i run FSCK first?

---

### Post by lithopsian on 2011-04-27
> **K_45 said:**
> Its actually

```
gksu gparted
```

Depends where you're starting it from.  Typing "sudo gparted" in a terminal works perfectly well.  gksu is only needed where an application is not being started from a command line which would allow a password to be entered.  For example, if you put it on a panel/launcher or type it in gmrun.

---

### Post by K_45 on 2011-04-27
> **lithopsian said:**
> Depends where you're starting it from.  Typing "sudo gparted" in a terminal works perfectly well.  gksu is only needed where an application is not being started from a command line which would allow a password to be entered.  For example, if you put it on a panel/launcher or type it in gmrun.

True, but Gparted needs permission to access the filesystem(s) in the system.

---

