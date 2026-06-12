---
title: "gparted my self to hell"
date: 2012-06-21
forum: General Help
---

### Post by danielbrackett on 2012-06-21
Hi, 
I have Ubuntu 10.04.4 installed. I wanted to try out xubuntu so I gave it an install. 
I then decided that I did not want xubuntu any more.
I subsequently downloaded gparted and deleted the partition that it resided on. Now this is where I am at;

When I boot the machine it* error: no such partition *and stays at the command line and displays *grub rescue> *

My question is what do I do next? How can I fix this mess I got myself into?

---

### Post by wilee-nilee on 2012-06-21
Try this tool, using the recommended repair, using a live ubuntu cd to run it.

This also runs the bootinfo summary when used, save the http address to post if the problem persists.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dynosis on 2012-06-21
boot with ubuntu live dvd that you have. go go restore mbr et voila you done!

---

### Post by danielbrackett on 2012-06-21
Hi again thanks for the help guys!!! I am so happy to have my puter back.

---

### Post by steve7777777 on 2012-06-21
> **danielbrackett said:**
> Hi again thanks for the help guys!!! I am so happy to have my puter back.

Please state exactly what you did to fix grub so it will help somebody else:p

---

### Post by danielbrackett on 2012-06-21
OK, so I put in the live CD and booted from it.
Then I followed the link to the [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I open the command-line and  typed;
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

then;
sudo apt-get install -y boot-repair && boot-repair

when the GUI came up I did the recommended fix. 
During the process A window opened and asked me something, 
(I forget what) I clicked on yes though and 
then when prompted 
I rebooted the machine. 
Presto things where back to as they were before.

---

