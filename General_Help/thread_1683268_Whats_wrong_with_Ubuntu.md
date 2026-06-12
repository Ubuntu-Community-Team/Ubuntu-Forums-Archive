---
title: "Whats wrong with Ubuntu"
date: 2011-02-07
forum: General Help
---

### Post by babak.7 on 2011-02-07
hi
I have some problems with ubuntu , 
today I was trying to install my ubuntu into my laptop , at the beginning of the installation my display goes black , I searched and changed to nomodeset . I could Install it and after reboot my ubuntu didnt work again , black screen !!!
:confused:
and next I did this :

On the Grub Menu, I select 

"Ubuntu, with Linux 2.6.35-22-generic" and press "e" so I can edit the boot parameter. 

On 

linux /boot/vmlinuz-2.6.35-22-generic root=UUID=3df857a3-9c1b-4fd3-b0fc-52838eaa2023 ro quiet splash 

I changed it to

linux /boot/vmlinuz-2.6.35-22-generic root=UUID=3df857a3-9c1b-4fd3-b0fc-52838eaa2023 ro nomodeset single

and press 'ctrl-x'.
 and log in the startx .
it worked but I couldnt save this setting so for every reboot I had to do all things above .
after that I download and install the Nvidia driver for ubuntu , but after restarting it went to froze purple screen
thats suck !!
pleas help

---

### Post by Kirboosy on 2011-02-07
What version are you trying to install?

---

### Post by babak.7 on 2011-02-07
its Ubuntu 10.10 desktop edition

---

### Post by Smudge123 on 2011-02-07
Can you boot to a different operating system and delete the ubuntu of of your hdd?

---

### Post by babak.7 on 2011-02-08
yes I have another os , but I cannot access to ubuntu files cause I made a partition for it and windows 7 cannot read this partition
but in disk management  I can delete this partition .

---

### Post by P4man on 2011-02-08
You have to make the nomodeset change permanent by editing your grub configuration. Details in the link in my signature.

---

### Post by babak.7 on 2011-02-08
thanks for million . :p
now its working and has no problem ! I love it .

---

### Post by P4man on 2011-02-08
Glad it worked. To help other googlers, perhaps you can post your machine specs (specifically the videocard) in the how to thread.

---

