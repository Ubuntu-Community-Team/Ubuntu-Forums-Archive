---
title: "neavoux"
date: 2011-01-07
forum: General Help
---

### Post by mmsmc on 2011-01-07
my neavoux driver is preventing a nvidia driver from installing, i heard i can blacklidt the driver, how do i do that?

---

### Post by Frogs Hair on 2011-01-07
This is for 10.04.[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

---

### Post by mmsmc on 2011-01-07
thanks ill try it, hopefully it doesnt crash

---

### Post by mmsmc on 2011-01-07
how do i know what nvidia driver i need?

---

### Post by Frogs Hair on 2011-01-07
At the Nvidia driver download site in the search filter , select the one for your graphics card model / linux , operating system and 32 or 64 bit . Do you know what model of card you have ?

---

### Post by mmsmc on 2011-01-07
nope

---

### Post by Frogs Hair on 2011-01-07
Install Sysinfo from the software center and use it to find out what model of card you have. It will appear under system tools on the menu.

---

### Post by mmsmc on 2011-01-07
ok

---

### Post by mmsmc on 2011-01-07
under what catagory would it be?

---

### Post by mmsmc on 2011-01-07
here

---

### Post by Frogs Hair on 2011-01-07
See the screen shot graphics card on the menu on the right and hardware on the left panel.

---

### Post by mmsmc on 2011-01-07
thats nvidia, shouldnt it already have nvidia installed?

---

### Post by Frogs Hair on 2011-01-07
When you go to Nvidia driver downloads your input should look like this except for 32 or 64 bit because I don't know what you're using . press search after entering the data.

---

### Post by Frogs Hair on 2011-01-07
> **mmsmc said:**
> thats nvidia, shouldnt it already have nvidia installed?

I don't know you were requesting information on blacklisting . I assumed you had attempted  installation and failed.

System > Administration > additional drivers , then install the recommended driver if not already.

---

### Post by mmsmc on 2011-01-07
i followed these instructions [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html) and it still wont work, im stuck in tty and cant connect to the internet

---

### Post by Frogs Hair on 2011-01-07
I found your other thread , I was not aware that you were in tty when you started this thread or would not have posted a link to the instructions. Now you will need to search the forums and Google. I will see what I can find.

---

### Post by mmsmc on 2011-01-07
this thread and that other thread are unrelated, i reinstalled ubuntu after that thread and tried to instal nvidia a different way, but getting out of tty and onto nvidia is now a priority, thanks

---

### Post by Frogs Hair on 2011-01-07
Try searching restart Xserver and see this thread.[http://ubuntuforums.org/showthread.php?t=1659717&highlight=Can%27t+install+Nvidia+drivers](http://ubuntuforums.org/showthread.php?t=1659717&highlight=Can%27t+install+Nvidia+drivers)

---

### Post by mmsmc on 2011-01-07
screw it, i dual boot with windows 7, how do i delete my ubuntu without deleting wiindows? i need to reinstall

---

### Post by mmsmc on 2011-01-07
hello?

---

### Post by efflandt on 2011-01-07
Did you do a regular install with Ubuntu in its own partition(s) or Wubi install withing Windows?

If a regular install, you do not need to uninstall Ubuntu to reinstall.  Just install again, but use manual partitioning mode to select the partition used for original Ubuntu install as "/" (and any other partitions like if you made separate /home).  In that case you can check to format / but not /home.  Install will automatically find any swap partitions.

Then try **System** > **Administration** > **Additional Drivers**, to see what it suggests to "activate" for nvidia.  If you need a newer nvidia driver than the default for Lucid or Maverick, you can add x-swat to your repositories by doing:
[FONT=monospace]
[/FONT]```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```Then go to Additional Drivers.  But if you already activated an earlier driver, first "remove" nvidia from there, reboot, then use Additional Drivers to "activate" the newer one, and reboot.

---

### Post by mmsmc on 2011-01-07
thanks

---

