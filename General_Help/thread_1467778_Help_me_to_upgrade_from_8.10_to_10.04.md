---
title: "Help me to upgrade from 8.10 to 10.04"
date: 2010-05-01
forum: General Help
---

### Post by sunnyengineeer on 2010-05-01
Hello,
      I've a dual boot Windows XP alongwith UBuntu 8.10.
Now I've got the CD of Ubuntu 10.04.I want to let the WIndows XP as it is & install 10.04 to the place where I had 8.10 i.e hd(0,13).
         Can somebody plz guid eme how to do this...So that I goes cleanly without interupting my WIndows which is working fine & I don't want to disturb it..


Thanks
Sunny Sharma

---

### Post by sunnyengineeer on 2010-05-01
Plz somebody guide me how to do this??

I do want 10.04 in place of 8.10but also don't want to disturb Windows.....

Thnx

---

### Post by polki@mac.com on 2010-05-01
It's very easy, just do what you always should do with an upgrade to any OS: Backup your files and install. If you have a seperate /home partition, then it's easy sailing!

---

### Post by Archmage on 2010-05-01
To upgrade from 8.10 to 10.04 you must update to 9.04 than to 9.10 and than finally you can upgrade to 10.04. (However you would be able to upgrade from 8.04 directly to 10.04.)

---

### Post by briandu on 2010-05-01
So do this.

Always backup up your data first - Golden Rule

The open terminal and then enter
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

You can upgrade from an early version to the latest. 

However you will not receive all the benefits such as ext4

Good luck

---

### Post by ssdt on 2010-05-02
Can't I go straight to it, to 10.04?

---

### Post by polki@mac.com on 2010-05-03
Only from 8.04 or 9.10.

---

