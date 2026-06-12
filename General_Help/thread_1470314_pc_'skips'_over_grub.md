---
title: "pc 'skips' over grub"
date: 2010-05-02
forum: General Help
---

### Post by Spanklord on 2010-05-02
i think i had this problem with prev ubuntu versions but never got around to solving it but just going back to windows. and again after a few hours this time im still not any closer to a solution. 

problem :
when i start my pc it flashes the grub menu and then it loads ubuntu. i want to dual boot with win7. when i goto startup-manager i can set my default to boot win 7. witch i did one time and it loaded win7 but then i couldnt get back to ubuntu and that took me some time to fix as well. 

anybody have any idea why it just flashes past the grub menu ? my timer isnt 0 . i changed it from 10 to 5 to see if anything had changed etc. but nothing. 


any ideas are welcome

Msi-wind U100 : win7+latest ubuntu

---

### Post by techunit on 2010-05-02
Go to software update and update ubuntu should fix the problem...

---

### Post by sbailey85 on 2010-05-02
also try holding shift right after your bios screen finishes

---

### Post by techunit on 2010-05-02
That may help as well. Holding shift will bring up the GRUB menu

---

### Post by Spanklord on 2010-05-02
thanks for the suggestions but i already tried these things

---

### Post by Hman242 on 2010-05-02
Run 
```
sudo update-grub
```in the Terminal in Ubuntu. Does Windows show in the list now? I remember when I had only Ubuntu installed and since it didn't see any other OS it would just boot Ubuntu.

---

### Post by Spanklord on 2010-05-02
yeah this is not the problem ... windows 7 does appear in the list but grub skips over so fast i cant pick it . as i said in my first post i can change it to the default but this will be even more problem and it doesnt really solve anything. 


and before someone ask .... no my enter key isnt pressed constantly

---

### Post by Hman242 on 2010-05-02
[Take a look at this.]("http://www.howtogeek.com/howto/ubuntu/change-the-grub-menu-timeout-on-ubuntu/")

---

### Post by techunit on 2010-05-02
Looks promising I would recommend that you give it a try. At this point pretty much any ideas are good ones.

---

### Post by Spanklord on 2010-05-02
im using grub2 so this doesnt really apply and as i said i changed my timer in the gui as well as in the /etc/default/grub

anybody know if i could make an empty entry in the grub list and then set that as my default ? so it would try and select that but nothing would happen so i can chose myself ?

---

### Post by techunit on 2010-05-02
Well Ok Give me a second... Ok here is some info about GRUB2 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by techunit on 2010-05-03
I don't know if I can help much further I don't know what to say but may be providing more information could help. Like The Circumstances that you installed ubuntu.

---

### Post by john newbuntu on 2010-05-04
Open up a terminal (Apps..->Acces..->Terminal) and run the following command.  
```
grub-editenv /boot/grub/grubenv list
```
Check if you can see the string "recordfail=".  If you do, unset the variable as follows:
```
sudo grub-editenv /boot/grub/grubenv unset recordfail
```
Check if your next boot is ok.

---

### Post by techunit on 2010-05-04
Good luck hope it works out..

---

