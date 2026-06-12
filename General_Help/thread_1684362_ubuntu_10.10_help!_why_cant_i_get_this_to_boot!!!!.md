---
title: "ubuntu 10.10 help?! why cant i get this to boot!!!!"
date: 2011-02-09
forum: General Help
---

### Post by anthonyubunt on 2011-02-09
aighty, little background.  im a noob, just found out about ubuntu, downloaded the netbook 10.10 and ran it live from a usb drive. needless to say, awwwwwwesome. so i went on to install (im currently using windows 7 as my primary os).  created 2 partitions, one for swap and one for ubuntu install was slow, awkardly enough, pressing keys randomly seemed to move things along.  long story short, the download installed and said it was ready to reboot.  rebooted and get left with a screen that says "gave up waiting for root device... blah blah blah... dropping to shell".  
noticed a lot of people are having similar troubles but im so new to linux i have no idea what half the acronyms mean.  could i get some advice in layman's terms?  i really enjoyed the live install and ultimately want to run ubuntu as my primary os on my netbook.  really looking forward to getting this working, even if you can just push me in the right direction, any help would be greatly appreciated.  thanks

---

### Post by Quackers on 2011-02-09
Welcome to UF.
Firstly please give details of your hardware - graphics card, amount of ram etc.
Then please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by P4man on 2011-02-09
Sounds like there is an issue with the drive/controller. 
What machine are you installing this on? What sort of drive does it have (regular sata drive or flash memory?)

---

