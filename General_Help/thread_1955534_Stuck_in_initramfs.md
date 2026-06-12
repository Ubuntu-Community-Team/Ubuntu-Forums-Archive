---
title: "Stuck in initramfs"
date: 2012-04-09
forum: General Help
---

### Post by Alexcunn on 2012-04-09
I am stuck in initramfs. I have tryed mounting my hard drive but it says it does not exist.

```
Mount -t ntfs /dev/sda1 /root
```

Is what I am using. I have also tryed exit but tye kernel goes into panic and locks me out.

I do not have any other operating system so i am screwed as far as making a boot disk plus my cd drive is broke. Please help.

---

### Post by raja.genupula on 2012-04-09
[http://ubuntuforums.org/archive/index.php/t-1244466.html](http://ubuntuforums.org/archive/index.php/t-1244466.html)

---

### Post by Alexcunn on 2012-04-09
This talks about using the live cd and i do not have a working cd drive. And it also is talking about theubuntu terminal commands which do not work. Is there a wget fix?

---

### Post by riderplus on 2012-04-10
Try making a live usb and solve it.

---

### Post by Alexcunn on 2012-04-10
Can i have a url i can use?

---

### Post by gokurab on 2012-04-11
check your partitions using ```
sudo fdisk -l
```
Then try mounting using sudo mount [partition] [some folder]
Also, why you are trying to mount an ntfs partition!

---

### Post by raja.genupula on 2012-04-11
> **Alexcunn said:**
> Can i have a url i can use?

for what . making a LIVE USB  ?

you can Unetbootin and startup disk creator .

---

### Post by raja.genupula on 2012-04-11
> **Alexcunn said:**
> This talks about using the live cd and i do not have a working cd drive. And it also is talking about theubuntu terminal commands which do not work. Is there a wget fix?

do as mentioned in post #20 
[http://ubuntuforums.org/showthread.php?p=9863783](http://ubuntuforums.org/showthread.php?p=9863783)

---

### Post by Alexcunn on 2012-04-12
ok the problem is that I have no other computer to make a live USB. I have read all these posts but they have commands of the Ubuntu terminal which I do not have access to. blkid is not in the initramfs commands. all I have is wget, mount, du, mkdir, etc. I am getting the error that it can not find /etc/fstab I made the directory and then redid the mount command and it said that /dev/sda1 is not in there. /root is my root folder. it already has all the files and everything in it and it is showing all the required files when I run du. I am really confused. I do not get an error on boot saying a that it can't boot. I am running grub 2 if this helps any. :( please tell me my computer is fixable.

---

### Post by Alexcunn on 2012-04-12
I have tried looking everywhere. du command says that dev is empty. I have looked in the folder /devices because that is what it says my keyboard and mouse is in. No luck doing anything. now there is a /root/dev

---

### Post by riderplus on 2012-04-12
> **raja.genupula said:**
> for what . making a LIVE USB  ?

you can Unetbootin and startup disk creator .

The OP has no access to that.
Alexcunn, I don't know if there's any easy way to get it working without having access to another computer and creating a live cd/usb. How did you install the OS in the first place?

---

### Post by Alexcunn on 2012-04-12
from a USB but that was when I had 7 nw the USB has different stuff on it

---

### Post by Alexcunn on 2012-04-12
bump

---

### Post by Alexcunn on 2012-04-16
Ok I found the problem but I do not know how to fix it. At some point my fs climbed up ti /root I ran a du scan on /boot and there is no such thing as boot but in the root directory it has everything. Is there a fix?

I will be uploading a photo

---

