---
title: "No partition select"
date: 2009-12-15
forum: General Help
---

### Post by metaltroubador on 2009-12-15
Basically I had my hard drive completely Ubuntu.  But I need a windows installation, so I created a seperate partition and installed windows xp.  Everything installed fine, but after installing when I start my computer instead of booting to a select partition screen where I can choose which partition to load it just directly boots windows xp.  The other partition still exists I just can't find a way to load it.  Is there a way I can get the computer to always go to a select partition screen?

---

### Post by RedSingularity on 2009-12-15
You mean the "grub" menu.  Do you have a live cd?

---

### Post by metaltroubador on 2009-12-15
You mean something like the Ubuntu 9.10 install disc, yeah I have that.

---

### Post by RedSingularity on 2009-12-15
Ok good.  What you can do is follow [this](http://ubuntuforums.org/showthread.php?t=224351) guide.  It is very easy to do you'll see.

---

### Post by metaltroubador on 2009-12-15
Thanks very much.

---

### Post by RedSingularity on 2009-12-15
No problem, let us know how you make out.

---

### Post by PRC09 on 2009-12-15
Is there a difference in re-installing Grub2 as the OP said he has 9.10 cd... 


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by RedSingularity on 2009-12-15
> **PRC09 said:**
> Is there a difference in re-installing Grub2 as the OP said he has 9.10 cd... 


Not that i am aware of at the moment.

---

### Post by ajgreeny on 2009-12-15
> **PRC09 said:**
> Is there a difference in re-installing Grub2 as the OP said he has 9.10 cd... 


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Yes there is.

How to restore the Ubuntu grub bootloader (9.10 and beyond)

Ubuntu 9.10 uses Grub 2, so you need to find out what your drives are using live CD:
    ```
sudo fdisk -l
```
From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
Still in the terminal, type:
    ```
sudo mkdir /media/sda5
```
    ```
sudo mount /dev/sda5 /media/sda5
```
To reinstall grub:
    ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```
Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

---

### Post by metaltroubador on 2009-12-15
Ok the first suggestion didn't work so when I came back here and saw the other thing I tried that. It appeared to work, but when i restarted my computer it took me straight to a command prompt with the grub> and doesn't load any partition what should I do now?

---

### Post by RedSingularity on 2009-12-15
See if this command works from grub.

find /boot/grub/stage1

---

### Post by RedSingularity on 2009-12-15
Look [here](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html) and see if that guide can set it up for you.

---

### Post by metaltroubador on 2009-12-15
That didn't work either I copied all my files to my laptop before I did this so I'm just going to format the entire hard drive, and install windows xp first then Ubuntu 9.10 so that should take care of everything hopefully.  Thank you for all your help though, I really do appreciate it.

---

