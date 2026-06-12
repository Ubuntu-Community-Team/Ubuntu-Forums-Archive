---
title: "After uninstalling Ubuntu, Windows 7 won't boot grub error."
date: 2011-02-10
forum: General Help
---

### Post by Andrewdance on 2011-02-10
I had ubuntu installed on an external HDD, and Windows 7 on the internal. After trying out Ubuntu for a while, i decided to uninstall off my PC to later install it on an old Dell (which worked great).

Now whenever I turn on the computer it wont boot completely, giving me this error after verifying DMI pool data:

[COLOR="Red"]Error: No such device: b43acdf3-19cf-4da5-9fee-3d6dc7e876d6
grub rescue> _[/COLOR]


This would also happen if i left the external HDD unplugged when booting the computer, fixed by just plugging it in, then it would let me choose which OS to use.

Now it just hangs there, same thing happens when i try to boot from any Windows dvd (Vista or 7)

and when I try to reinstall Ubuntu, it starts like normal, then the screen gets all glitchy, black with random colors scattered around the screen and freezes. 
:confused: this is killing me!

---

### Post by pages on 2011-02-10
Won't claim to know how to fix the problem but this is what the experts will tell you to do 

First get a Ubuntu LiveCD and go into try Ubuntu
Access the internet and go to 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instructions and post the RESULTS.txt here for more advice



--- 
I had the same problem and i found reinstalling Ubuntu from the LiveCD fixed everything

---

### Post by ajgreeny on 2011-02-10
You certainly could reinstall ubuntu and then you would have grub back, and a working grub means a working windows OS.  

However, here are a few other possibilities:-

1.  Use the supergrub CD:  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

2.  Try using lilo from live ubuntu CD
[INDENT]Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR
[/INDENT]3.  Get the right repair utility from [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I hope one or other of these is successful for you, but if not come back again and I'm sure someone will try to help more.

---

### Post by Robert Finley on 2011-06-22
So, that second link doesn't work, and what I'm hearing is that if you didn't make a rescue disk before you wiped out windows, there is NO way to put the windows bootloader back once you've installed grub or lilo over it? Really?  The only option is to substitute it?  The crazy thing to me is that I can find rescue disks for all the previous versions of windows but the Windows 7 rescue disks can't be downloaded anywhere.

---

### Post by haqking on 2011-06-22
> **ajgreeny said:**
> You certainly could reinstall ubuntu and then you would have grub back, and a working grub means a working windows OS.  

However, here are a few other possibilities:-

1.  Use the supergrub CD:  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

2.  Try using lilo from live ubuntu CD[INDENT]Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR
[/INDENT]3.  Get the right repair utility from [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I hope one or other of these is successful for you, but if not come back again and I'm sure someone will try to help more.



> **Robert Finley said:**
> So, that second link doesn't work, and what I'm hearing is that if you didn't make a rescue disk before you wiped out windows, there is NO way to put the windows bootloader back once you've installed grub or lilo over it? Really?  The only option is to substitute it?  The crazy thing to me is that I can find rescue disks for all the previous versions of windows but the Windows 7 rescue disks can be downloaded anywhere.

Would you crash your car then think its mad that you didnt get insurance beforehand and so your not covered;-)

it is called a rescue disk for a reason ;-)

---

### Post by sarge77 on 2011-06-22
Is windows really wiped out did you check the content of the windows HDD to verify if its wiped then just reinstall like most windows users do if its still there and you want to just go back to windows without ubuntu try using gparted to make that primary drive boot again after gparted loads goto manage flags and choose SDA1 as boot save and its should work if you want ubuntu back you need to fix grub.

You probably just have to rewrite the MBR also load the Windows 7 disc and goto recovery console 
try this site for windows 7 MBR
[http://technet.microsoft.com/en-us/magazine/ee851681.aspx](http://technet.microsoft.com/en-us/magazine/ee851681.aspx)

heres another site 
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

I found this very usefull from youtube how to fix grub from ubuntu 10.10 live CD
[http://www.youtube.com/watch?v=cbIHWoJhIII](http://www.youtube.com/watch?v=cbIHWoJhIII)
 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu

after your done and restart goto ubuntu and in terminal sudo update-grub and it auto detects the OS make
sure you have your external plugged in 

I used this after I got a Grub error code.

---

### Post by oldfred on 2011-06-22
The lilo boot loader works just like windows boot loader in that all it does is look for a partition with the boot flag and jump to that partition to continue to boot. Lilo will also jump to logical partitions where windows will not, but that is about the  only difference. 

You can reinstall the windows boot loader after lilo or grub or install any boot loader any time. It is just some code in the MBR.

You could boot with lilo then once in windows run the repair console to install the windows boot loader if you want.

If you can boot to a recovery console with lilo or Supergrub:
Make your own recoveryCD:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

