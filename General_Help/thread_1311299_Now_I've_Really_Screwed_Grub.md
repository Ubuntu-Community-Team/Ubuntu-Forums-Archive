---
title: "Now I've Really Screwed Grub"
date: 2009-11-02
forum: General Help
---

### Post by kolisikepu on 2009-11-02
Hi Community,

Looking for some desperate help.  I had installed Vista on my lappy which got rid of Grub.  Now I'm trying to get grub back so I can get back into my Ubuntu, but I followed instructions from [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and now I get a sh>grub and text that don't make sense.

Any thoughts?

I'm using LiveCD to get into.

I get [ Minimal BASH-like line editing is supported. yadi-yadi-yadi-ahh... when booting up.

---

### Post by ajgreeny on 2009-11-02
You don't say in detail exactly what you did, but the following works faultlessly if you have a standard setup with windows on the first partition of the machine's disk 1 (the disk you boot from).  Give it a try if it is different from what you did, and good luck.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

All of this assumes you are still on ubuntu 9.04 and have not gone to 9.10 and grub2, where the job becomes more complicated.  If you do have grub2 see
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
for more info on that.

---

### Post by kolisikepu on 2009-11-02
Thanks AJ... it worked!

---

### Post by ajgreeny on 2009-11-02
Great!!!

---

