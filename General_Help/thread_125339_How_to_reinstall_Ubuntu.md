---
title: "How to reinstall Ubuntu?"
date: 2006-02-03
forum: General Help
---

### Post by globemast on 2006-02-03
Hello guys,

I am a newbie to Ubuntu and Linux in general and today i have messed things up big time. 

For the past 2 weeks i installed Ubuntu on my laptop and i was playing with it so i can get familiar with Linux. Today i tried to remove some applications using Synaptics and by mistake\\:D/ \\:D/  i removed also something called "apt".

I know that this "apt" must be something important because now ubuntu boots in text mode. Also before rebooting all the application icons were lost and no application could start.

Can you please tell me how can i make a new clean installation of Ubuntu.

BTW i have also installed on my laptop Windows XP as my first O/S and i select at boot time which O/S to boot.

Thanks in advance.

---

### Post by christhemonkey on 2006-02-03
If you want to reinstall ubuntu, just boot from the install CD and select all the same things as you did when you first installed it.

---

### Post by globemast on 2006-02-03
Will this remove the current installation and create a new clean installation?? I

I have tried reinstalling from the CD but it asks me again to reconfigure the partitions.

---

### Post by christhemonkey on 2006-02-03
I assume that it will overwrite your current Ubuntu, if you do not want this then go to your Text only interface and type:
```
sudo apt-get ubuntu-desktop
```
This should help fix things.

---

### Post by globemast on 2006-02-04
Thanks,

i have re installed Ubuntu from the begining by using the DVD.

---

