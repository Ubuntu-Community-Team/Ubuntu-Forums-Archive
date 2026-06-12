---
title: "accessing ubuntu after installing windows 7 ?"
date: 2012-04-12
forum: General Help
---

### Post by mohd z on 2012-04-12
Hi .,

i'm having a problem here where i just need the files in the Ubuntu partition ..

first i formatted my whole hard drive and made two partitions. after that i installed windows 8 consumer preview in the first one , and Ubuntu 11.10 in the other .. and everything was working ok that when i start the laptop i chose which OS to start on ..

after that i wanted to go back to the windows 7 so i just installed it over windows 8, after installing windows 7 i couldn't get a chance to choose my OS .. it automatically starts to windows without asking

so my problem here is that i just need a few files from the desktop of my ubuntu.. i tried using ubuntu from a storage device and transfer the files to an external hard drive.. but then it tells me that i don't have enough permissions to do that..

so i just want one of two options.. either a way to get into my ubuntu OS for only one time to copy my files and then re-install it.. or a way that i can take the files in any way possible to any storage media..

thank you

---

### Post by kc1di on 2012-04-12
What happens when your re-install windows is that windows re-writes the Master Boot Record and no longer uses grub2 as the boot program thus you can not access your Ubuntu install. 
What you will have to do is re-install Grub2 here's a webpage with 3 possibilities. from complicated to easy. one should work for you.

[http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7]("http://askubuntu.com/questions/83771/recovering-grub-after-installing-windows-7")
Good Luck.

---

### Post by mkstallings1 on 2012-04-12
I downloaded the .iso of Boot Repair and burned it to a CD.  I keep it in my toolkit because it does a great job of fixing boot problems.  I'm pretty sure it will fix your problem automatically in just a few minutes.

---

