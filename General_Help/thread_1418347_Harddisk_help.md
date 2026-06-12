---
title: "Harddisk help"
date: 2010-02-28
forum: General Help
---

### Post by termal on 2010-02-28
Dear Ubuntu community,

I have recently installed Ubuntu using wubi and decided to try Fluxbox. Everything is working fine.

But now I have discovered one problem. Every time I open nautlius (using no-desktop) and want to go to my primary HDD with Windows installed it says "Authentification is required". In Gnome it just asks for password and everything is fine, but here there is no password request. Just error. Anyone know how to disable authentification request, or how to make password window appear again?

Also this hard disk is not appearing in Thunar. So I cant even switch harddrive in thunar.

Thanks.

---

### Post by termal on 2010-03-01
Nobody knows? :(

---

### Post by namluc on 2010-03-01
Never used wubi, so i can't be sure but you can try this, if you know the name of your drive:

sudo bash to become root

cd to media my drive was just labeled disk

sudo chown -R (username) disk
sudo chmod 777 disk

and now i own the drive and able to copy to it

that should work. I'd wait for a second opinion though as like i said, i've never used wubi

---

### Post by termal on 2010-03-01
How to find out my disk name? just to make sure.... I am pretty noob in this things... 

I dont know if it's correct i found "df" i saw /dev/loop0 with the size of my hard drive (so i guess its the hard drive)

when i go
cd /dev/loop0 as you said it says "Not a directory"

---

### Post by namluc on 2010-03-01
wait
don't listen to my advice, wait for someone cleverer to tell you what to do, soz

---

### Post by termal on 2010-03-02
Ok, I wont. Anyone knows how to help me? :(

---

