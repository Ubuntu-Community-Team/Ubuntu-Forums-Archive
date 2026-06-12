---
title: "removing other linuxes on a multi-boot system"
date: 2011-08-16
forum: General Help
---

### Post by layers on 2011-08-16
I have a few linuxes installed I would like to keep only one of them. Each has its own partition. I have no idea where the boot loader is, and even if I did, I don't know what to do with it. Since I do not want to remove all, and then erase all the other ones, and then boot into Live mode, I am looking for a way to just over write that boot loader and place it where the system I will be keeping is. How can I do that?

---

### Post by cottfcfan on 2011-08-16
1st thing - Does the o/s you want to keep control grub?
If not use the live cd of the o/s you want to keep to reinstall grub, following these instructions:
[https://help.ubuntu.com/community/Grub2/#Reinstalling](https://help.ubuntu.com/community/Grub2/#Reinstalling) GRUB2
Then use gparted to delete the partitions of the o/ss you do not want.
finally run "sudo update-grub"

---

### Post by layers on 2011-08-16
> **cottfcfan said:**
> 1st thing - Does the o/s you want to keep control grub?
If not use the live cd of the o/s you want to keep to reinstall grub, following these instructions:
[https://help.ubuntu.com/community/Grub2/#Reinstalling](https://help.ubuntu.com/community/Grub2/#Reinstalling) GRUB2
Then use gparted to delete the partitions of the o/ss you do not want.
finally run "sudo update-grub"
There will be only one left (can you have no grub at all?).

So it definitely won't work if I just boot into the system I want, use Disk Utility to remove partitions, and then update-grub?

---

### Post by cottfcfan on 2011-08-16
You can't boot without grub.
That's why before you delete anything, make sure the system you're keeping controls grub, using the link in my last post.
It would help if you let us know what linux system you want to keep, then using gparted take a screenshot of your systems partitions, and tell us what partition the one you want to keep is on.

---

### Post by layers on 2011-08-16
[http://imageshack.us/photo/my-images/841/screenshot1rit.png/](http://imageshack.us/photo/my-images/841/screenshot1rit.png/)[IMG]http://imageshack.us/photo/my-images/841/screenshot1rit.png/[/IMG]> **cottfcfan said:**
> You can't boot without grub.
That's why before you delete anything, make sure the system you're keeping controls grub, using the link in my last post.
It would help if you let us know what linux system you want to keep, then using gparted take a screenshot of your systems partitions, and tell us what partition the one you want to keep is on.
Here - sdsa6, 7, 8, 9, 10 and 11 - I want merged into one, but 7, 8, 9, 10 and 11 contain other operating systems, which were installed after the system on sda5 (the keeper)
[IMG]http://imageshack.us/photo/my-images/841/screenshot1rit.png/[/IMG]

---

### Post by cottfcfan on 2011-08-17
OK.
I'm assuming sda6 is your Home folder.
So sda1 (swap),5 & 6 need to be kept.
Before we continue what operating system is on sda5?
Need to know if were dealing with Grub or Grub2.

---

### Post by raja.genupula on 2011-08-17
hmm no issues. listen here  . first , boot to the OS which you wanna keep . open terminal then do this 
```
sudo dpkg-reconfigure grub-pc 
```

this will make this os grub is the main grub , then delete the other os partitions and do what ever you want . 
then do this 

```
sudo update-grub
``` 

 give us what you got

---

### Post by cottfcfan on 2011-08-17
rajas suggestion will also work.
I was going down the live cd root, because imo its safer to mess with and delete partitions, when they're all unmounted.

---

### Post by layers on 2011-08-17
I ended up just deleting the partitions and using Boot Repair. That did succeed in removing all other operating systems, but there is still some Grub 1.99 menu for a memory test and recovery, which I don't know how to remove. How can I do that?

(or remove the wait time?)

---

### Post by layers on 2011-08-17
Is it possible that I don't have a /boot/grub/menu.lst?

---

### Post by oldos2er on 2011-08-17
Very possible, since that file is no longer used in grub2. Take a look at grub customizer: [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by layers on 2011-08-17
> **oldos2er said:**
> Very possible, since that file is no longer used in grub2. Take a look at grub customizer: [https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

When I try to install it, I get this:
```
In file included from /home/ibo/Desktop/untitled folder/src/view/grublistCfgDlgGtk.cpp:1:0:
/home/ibo/Desktop/untitled folder/src/view/grublistCfgDlgGtk.h:3:19: fatal error: gtkmm.h: No such file or directory
compilation terminated.
make[2]: *** [CMakeFiles/grub-customizer.dir/src/view/grublistCfgDlgGtk.cpp.o] Error 1
make[1]: *** [CMakeFiles/grub-customizer.dir/all] Error 2
make: *** [all] Error 2
```


The readme file says this:
```
To compile this you have to install libgtkmm-2.4-dev, cmake and cmake

Then run:
	cmake .
	make
	sudo make install
```

I did install cmake, how do I get hold of that library?

---

### Post by oldos2er on 2011-08-18
I'm sorry, I sent you the wrong URL. You can install it in *.deb form from this PPA: [https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

---

### Post by layers on 2011-08-18
> **oldos2er said:**
> I'm sorry, I sent you the wrong URL. You can install it in *.deb form from this PPA: [https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

Thanks, I installed it, but too scared to do trial and error. Which value do I have to change in order to not see the grub menu at all (so it chooses the first ooption directly)? Or which timeout?
[[IMG]http://img546.imageshack.us/img546/3405/screenshotuu.th.png[/IMG]](http://imageshack.us/photo/my-images/546/screenshotuu.png/)

---

### Post by raja.genupula on 2011-08-18
> **layers said:**
> I ended up just deleting the partitions and using Boot Repair. That did succeed in removing all other operating systems, but there is still some Grub 1.99 menu for a memory test and recovery, which I don't know how to remove. How can I do that?

(or remove the wait time?)
are you getting those for your OS or removed OS's . 
if you feel you have something still of removed OS things then run " sudo update-grub " once .

---

### Post by layers on 2011-08-18
> **raja.genupula said:**
> are you getting those for your OS or removed OS's . 
if you feel you have something still of removed OS things then run " sudo update-grub " once .

Other operating systems are gone.
All I have remaining is something like this:

Ubuntu kernel xx
Ubuntu kernel xx (recovery)
Memetest

I do not want to get this choice - just boot up into the first choice.

---

### Post by oldos2er on 2011-08-18
> **layers said:**
> Thanks, I installed it, but too scared to do trial and error. Which value do I have to change in order to not see the grub menu at all (so it chooses the first ooption directly)? Or which timeout?
[[IMG]http://img546.imageshack.us/img546/3405/screenshotuu.th.png[/IMG]](http://imageshack.us/photo/my-images/546/screenshotuu.png/)

Check in the Preferences menu, there are several options there. I acutally don't use grub-customizer any more now that KDE 4.7 comes with its own grub2 settings configuration app.

---

### Post by cottfcfan on 2011-08-19
If you don't want the choice, install "startupmanager", then in the time out in seconds tab change it to 0.
It will now boot straight into the O/S.

---

### Post by YannBuntu on 2011-08-23
Dear all,

There is a tool to uninstall any OS in 1 click : [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[IMG]http://pix.toile-libre.org/upload/original/1313035409.png[/IMG]

Enjoy :)

---

