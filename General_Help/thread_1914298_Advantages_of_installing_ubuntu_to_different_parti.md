---
title: "Advantages of installing ubuntu to different partition than virtual"
date: 2012-01-24
forum: General Help
---

### Post by sifarat on 2012-01-24
Hi. I have just installed ubuntu 11.10 using Wubi installer on my windows7 - it's working good, but not as fast as my Windows 7 is. I have hp dv6 corei5 laptop with 2gb ram 300gb hdd. 

And sometime it's laggy too esp., when installing or uninstalling software on ubuntu. I just wonder is it because of virtual partition that wubi creates by default on win7? Should I create another partition and move my Wubi install to that? would that improve ubuntu performance?

Or do you think it's unrelated, and it just could be due to lower ram, i guess 2 gb is enough for ubuntu?

Please suggest me thanks.

---

### Post by sudodus on 2012-01-24
> **sifarat said:**
> Hi. I have just installed ubuntu 11.10 using Wubi installer on my windows7 - it's working good, but not as fast as my Windows 7 is. I have hp dv6 corei5 laptop with 2gb ram 300gb hdd. 

And sometime it's laggy too esp., when installing or uninstalling software on ubuntu. I just wonder is it because of virtual partition that wubi? Should I create another partition and move my Wubi install to that? would that improve ubuntu performance?

Or do you think it's unrelated, and it just could be because lower ram, i guess 2 gb is enough for ubuntu?

Please suggest me thanks. In some special cases it is probably the best to run Ubuntu from Wubi, but if you want to have full performance, you should install it to an own partition. If you installed your Ubuntu very recently, and you have not customized it a lot, I suggest that you

- delete the wubi installation

- backup your system

- defragment the windows partition

- make new partitions with gparted. I suggest
. shrinking the windows partition to get free space and
. making an extended partition with
. one logical partition for the linux file system ***ext3*** or ***ext4*** and
. one logical ***swap*** partition of at least the same size as the RAM
using the free space. Run gparted from a live session booted from the Ubuntu installation CD or USB drive).

- install Ubuntu. When asked about partitions, select the manual method and tell it to select the new ***ext*** partition for the linux file system /. It will select the swap partition automatically.

---

### Post by sanderd17 on 2012-01-24
Your specs seem good enough for Ubuntu.

When you install it with wubi, you can indeed lose a bit of snappiness. But the biggest disadvantage of wubi is the stability. A wubi installation depends on a good working Windows installation. If you start using Ubuntu more and more, an forget about maintaining Windows, there is a chance that Windows will crash, and pull Wubi with it.

As you say it's mainly during installing software, I believe it has something to do with the filesystem. Do you have enough space left for Ubuntu? Or does Ubuntu have to compress itself? Something else to try is to defragment Windows.

Maybe, if you want a more snappy environment, you can also install a lighter one. Try installing XFCE or LXDE from the software center. Afterwards, you can switch to that environment from the login screen.

---

### Post by WasMeHere on 2012-01-24
Hi sifarat,

Welcome to the Ubuntu Forums :-)

> **sifarat said:**
> Hi. I have just installed ubuntu 11.10 using Wubi installer on my windows7 - it's working good, but not as fast as my Windows 7 is. I have hp dv6 corei5 laptop with 2gb ram 300gb hdd. 
...
Please suggest me thanks.

Your computer should run Ubuntu without problems. The 'only' problems might be the graphics and the wireless LAN. If you let us know about them, we can give advice, but you can find out yourself running a live session from your CD or USB installation drive. Maybe the system offers to install a proprietary graphics driver. Do that only to test, it will not stay (unless you run a persistent live system).

I agree with the previous posts, that Ubuntu runs faster when it is installed to an own partition. With 2GB RAM, I suggest you install a swap partition of 4GB, because you might double your RAM in the future and then you need that size of swap for hibernation.

Have fun finding out about Ubuntu
Olle

---

### Post by nipunshakya on 2012-01-24
Hi. First off all welcome to the forum.
In order to ubuntu working to its full potential, i would also suggest you go for an installation in a seperate partition. That way, you can have 2 OSs working in perfect harmony, both at their full potential of working. If you need assistance on dual boot, check the website below:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
This will guide you how to partition and how to install in a proper way.

If you want more information about advantages and disadvantages, go through following site:
[http://ubuntuforums.org/showthread.php?t=481219&highlight=catch](http://ubuntuforums.org/showthread.php?t=481219&highlight=catch)

Hope they help you out.
Goodluck.
Regards,WinuxUser

---

### Post by sifarat on 2012-01-24
> **sudodus said:**
> In some special cases it is probably the best to run Ubuntu from Wubi, but if you want to have full performance, you should install it to an own partition. If you installed your Ubuntu very recently, and you have not customized it a lot, I suggest that you

- delete the wubi installation

- backup your system

- defragment the windows partition

- make new partitions with gparted. I suggest
. shrinking the windows partition to get free space and
. making an extended partition with
. one logical partition for the linux file system ***ext3*** or ***ext4*** and
. one logical ***swap*** partition of at least the same size as the RAM
using the free space. Run gparted from a live session booted from the Ubuntu installation CD or USB drive).

- install Ubuntu. When asked about partitions, select the manual method and tell it to select the new ***ext*** partition for the linux file system /. It will select the swap partition automatically.


thanks i am exactly doing this right now.. wish me luck being a ubuntu newbie ;}}

---

### Post by raja.genupula on 2012-01-24
> **sifarat said:**
> thanks i am exactly doing this right now.. wish me luck being a ubuntu newbie ;}}

All the best man , it will be fine .If you got anything then notice here.

All the best .

---

### Post by WasMeHere on 2012-01-24
> **sifarat said:**
> thanks i am exactly doing this right now.. wish me luck being a ubuntu newbie ;}}

Good luck, and don't forget to come back and report about your result, even if you succeed at once :-)

---

### Post by sudodus on 2012-01-24
> **sifarat said:**
> thanks i am exactly doing this right now.. wish me luck being a ubuntu newbie ;}}
+1
Good luck from me too :-)

---

### Post by mastablasta on 2012-01-24
i would also try OpenSUSE on that mashcine, just because HP ships some of these notebooks here with SUSE linux preinstalled.
 
also if you create only empty disk space on that separate partition (unformatted disk space) you don't have to worry about Swap and such as this is all done automaticly by Ubuntu during install. just go with defaults afterwards and you should be fine.
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

