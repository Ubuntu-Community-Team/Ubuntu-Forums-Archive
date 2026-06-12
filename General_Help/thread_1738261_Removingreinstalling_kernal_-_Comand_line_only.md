---
title: "Removing/reinstalling kernal - Comand line only"
date: 2011-04-24
forum: General Help
---

### Post by tweaked on 2011-04-24
I setup Server 10.10. Two kernals were showing on Grub. Somehow 2.6.35.28 crashed hard and neither it or recovery would boot. 2.6.35.22 is fine.

So I ran:

apt-get remove --purge 2.6.35.28

which seemed to do the trick, but now I would like to have another kernal again in case.

apt-get update
apt-get upgrade
apt-get dist-upgrade

does not find anything.
What am I missing?

Thanks

---

### Post by KegHead on 2011-04-24
Hi!

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

KegHead

---

### Post by tweaked on 2011-04-24
Thanks you very much, and for the archives, I am able to specify the exact kernal with 

apt-get install linux-image-2.6.35-24-generic -f

---

### Post by KegHead on 2011-04-24
Hi!

Congrats!

If you're satisfied please mark your thread as "solved".

KegHead

---

