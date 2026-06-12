---
title: "Ubuntu to windows"
date: 2009-07-13
forum: General Help
---

### Post by matt12345 on 2009-07-13
Hello there :)

I was wondering since there is a program called Wubi, that installs Ubuntu onto a window OS. Is there any such thing that will allow you to install windows on a Ubuntu. The reason I would like to do this is, I will use ubuntu for work. And winodws for gaming,chatting,ect. I do have a Windows XP disk but in my opinion that takes way to long to install.

---

### Post by Bradj47 on 2009-07-13
Yes, there's a Sun product called VirtualBox. You can get it at [http://www.virtualbox.org/](http://www.virtualbox.org/) or ```
sudo apt-get install virtualbox-ose
```
You can run other OS on VirtualBox too but Windows XP definitely works the best.

---

### Post by The Cog on 2009-07-13
No. You could try and run windows inside VirtualBox on Ubuntu, but it's not really suitable for gaming because the graphics hardware acceleration isn't there. Your best approach for gaming is to go for a normal dual-boot where each OS has its own boot partition.

---

### Post by GCoffee on 2009-07-13
Wubi doesnt install ubuntu onto windows, its an easier way to install it.

---

### Post by matt12345 on 2009-07-13
so say I had windows vista on a disk I could use that to install? Or does it all ready have the file like wubi does?

---

### Post by Bradj47 on 2009-07-13
Oh, sorry I didn't realize you had gaming in the list there. You really don't want to use VirtualBox for gaming or any high-graphics applications.

---

### Post by TeamJ on 2009-07-13
I would suggest dual booting XP and Ubuntu. you could also install VMWare Server or Workstation onto both. then set each up to use the other partition as the disk. therefore you can boot into one, but have easy access to the other if you change your mind without the need to reboot.

---

