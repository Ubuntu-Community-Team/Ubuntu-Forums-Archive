---
title: "Kubuntu Acces Password"
date: 2010-04-29
forum: General Help
---

### Post by samos255 on 2010-04-29
Hello,i want to know how i can skip this... Because this is my Windows Partition,where is all of my music,the problem is Amarok cant play these files so i dont have them in collection till i dont give here password,so amarok must again Scan all the files (about 6000 songs) and it takes long and i want to know any way to skip this. Thxs for replys :)[IMG]http://i43.tinypic.com/35brp6p.jpg[/IMG]

---

### Post by lisati on 2010-04-29
Try the password you use to login to your system. Feel free to let us know how you get on.

---

### Post by samos255 on 2010-04-29
> **lisati said:**
> Try the password you use to login to your system. Feel free to let us know how you get on.

Sure it work,i know pass but i want to skip this asking.

---

### Post by kooldino on 2010-04-30
So you want it to remember your password and not prompt you each time, yes?

What you probably want to do is to auto mount that partition in your /etc/fstab file.

Copy and paste the output of this command: 

```
sudo fdisk -l
```

---

### Post by samos255 on 2010-05-01
> **kooldino said:**
> So you want it to remember your password and not prompt you each time, yes?

What you probably want to do is to auto mount that partition in your /etc/fstab file.

Copy and paste the output of this command: 

```
sudo fdisk -l
```

Thx for really,i doesnt have this problem anymore because i installed from Kubuntu to Newest Build Of Ubuntu (Sound problems,etc.) anyway thanks for solution.

---

