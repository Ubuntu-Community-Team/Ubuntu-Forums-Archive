---
title: "Change GRUB timeout?"
date: 2010-02-22
forum: General Help
---

### Post by johnnytwohats on 2010-02-22
Hi, Im a newbie. I just installed kubuntu 910 via cd iso. now i want to change the default grub timeout. It says i dont have permission to edit etc/default/grub so what do i do? i dont know how to login as root user. please help thanks.

---

### Post by karthick87 on 2010-02-22
Edit the file using this command **sudo gedit etc/default/grub **

---

### Post by johnnytwohats on 2010-02-22
Doesnt work, cannot open display error message. Im using kde so I dont know how to login as root. Please help, Im pulling my hair out.

---

### Post by amsterdamharu on 2010-02-22
The easy way would be to install startup manager. Under system -> administration -> synaptic package manager you can install it.

Then under system -> administration startup manager you can change the settings.

It will ask for **your** password to do administrative tasks.

---

### Post by r_s on 2010-02-22
kate is the default editor in kubuntu and not gedit.

---

### Post by derande on 2010-02-22
is there an equivalent to StartUp-Manager in kubuntu?
I use SUM to set grub timeout and boot order.

---

### Post by m4tic on 2010-02-22
easy. use sudo dolphin . go to /boot/grub/grub.cfg and look for timeout, its default to 10 seconds, change that one and save

---

### Post by earlf on 2011-02-02
for anyone who finds this thread and is wondering how to edit the grub file:

  ```
sudo gedit /etc/default/grub
``` did not work for me.
```
 gksu gedit /etc/default/grub
``` did work. 

I'm using Ubuntu 10.10

---

