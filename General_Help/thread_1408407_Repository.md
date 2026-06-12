---
title: "Repository"
date: 2010-02-16
forum: General Help
---

### Post by mihir786 on 2010-02-16
Hello,
     I have kubuntu 9.10 and I am leaving in hostel and hostel is LAN connected and here internet connection is too slow to download all things from net or actually from kubuntu server.What I want to do is that i have installed all things from my home with good speed of internet is there any easy way to make repository locally not in DVD or CD i want to make repository so when any one write like

**sudo apt-get install httpd**

It ll download from my pc insted of main server is there any way if yes than please explain me...

Thank you,
Regards,
Mihir Soni.

---

### Post by lykwydchykyn on 2010-02-16
> **mihir786 said:**
> Hello,
     I have kubuntu 9.10 and I am leaving in hostel and hostel is LAN connected and here internet connection is too slow to download all things from net or actually from kubuntu server.What I want to do is that i have installed all things from my home with good speed of internet is there any easy way to make repository locally not in DVD or CD i want to make repository so when any one write like

**sudo apt-get install httpd**

It ll download from my pc insted of main server is there any way if yes than please explain me...

Thank you,
Regards,
Mihir Soni.

You can use apt-mirror to create a local repository, and have it synchronize regularly with the real repositories.

Have a look at this:
[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

