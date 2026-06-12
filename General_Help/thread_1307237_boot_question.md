---
title: "boot question"
date: 2009-10-30
forum: General Help
---

### Post by Gio0110 on 2009-10-30
hi everyone: i am new with ubuntu and i trying to familiarised with it and i have a question regarding the booting part. 

when i start my laptop and the multyboot option appears and it let me only 10 seconds to choose eather linux or windows. so my question is: how i change the bootable time from ten to 30 seconds from my terminal in ubuntu?

---

### Post by scouser73 on 2009-10-31
Install StartUp Manager from Synaptic Package Manager, once installed you will find it under **System** > **Administration** > **StartUp Manager**.  Click on startUp Manager and go to Timeout and set it to thirty seconds.

[[IMG]http://img265.imageshack.us/img265/6426/screenshot1y.th.png[/IMG]](http://img265.imageshack.us/i/screenshot1y.png/)

---

### Post by ikacer on 2009-10-31
you will have to edit the config file. It's found in /etc/default/grub
you can edit it by opening a terminal and entering:
```
gksu gedit "/etc/default/grub"
```
you can change the GRUB_TIMEOUT from 10 to 30, then save the file. Then, in a terminal, enter:
```
sudo update-grub
```


Cheers.

---

### Post by kaibob on 2009-10-31
> **Gio0110 said:**
> hi everyone: i am new with ubuntu and i trying to familiarised with it and i have a question regarding the booting part. 

when i start my laptop and the multyboot option appears and it let me only 10 seconds to choose eather linux or windows. so my question is: how i change the bootable time from ten to 30 seconds from my terminal in ubuntu?
Which version of Ubuntu are you using--it makes a difference. If it's 9.10, then the procedure described by ikacer is the correct one.

---

