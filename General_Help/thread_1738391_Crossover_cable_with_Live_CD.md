---
title: "Crossover cable with Live CD"
date: 2011-04-24
forum: General Help
---

### Post by swedstal on 2011-04-24
My old Toshiba laptop runs Windows XP but has recently stopped booting into Windows. To make sure my hardware is still functional I am running Ubuntu from a live CD. I think I am going to end up just wiping the laptop clean and starting over with Ubuntu. However, I have about 60GB of files that I would like to rescue before formating.

In Windows it is very easy to connect two PCs with a crossover cable and then just drag and drop files between the two machines. I have found the task a bit more arduous in Ubuntu.

(Note: My desktop runs 10.04 Ubuntu Studio and uses wicd as the network manager; Laptop is 10.04 from the Live CD; Yes, I'm sure it is a crossover cable not just a normal network cable)

I was working from the guide here: [http://ubuntuforums.org/archive/index.php/t-50825.html](http://ubuntuforums.org/archive/index.php/t-50825.html)

and did

```

sudo ifconfig eth0 192.168.0.1
```

then
```

sudo ifconfig eth0 192.168.0.2


```

I was able to successfully ping the laptop from my desktop but not the desktop from my laptop.

Is that how it should be? I know very little about networking. Any thoughts on next steps would be greatly appreciated.

If I don't get it figured out tonight I'll just to the old back-and-forth-with-flashdrive trick.

I know I'm probably preaching to the choir, but having a Linux live CD is absolutely essential for any Windows user. I wish I would have known this trick years ago.

---

