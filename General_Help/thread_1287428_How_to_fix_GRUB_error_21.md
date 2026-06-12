---
title: "How to fix GRUB error 21"
date: 2009-10-10
forum: General Help
---

### Post by Rick Abraham on 2009-10-10
I have Win XP installed on my first primary HD and Ubuntu installed on a completly seperate second HD.
I am getting a GRUB error 21 when I boot.
I have downloaded and burnt to CD SuperGrubDisk but have no idea how to use it.

Can some one please give me some guidance.

I have read about Error 21 and have some idea of what is going on, I think I must have a error in my boot entry menu.lst and GRUB must think I have a third HD hd2,0 for example.

How can I go in and check this boot menu.lst to see whats happening, or can SuperGrubDisk automatically restore things for me ?????

Any help would be great.

---

### Post by mhgsys on 2009-10-10
First of all I have a question. 

Do you get a grub error 21 when you try to boot into Xp? Or are you having this error when booting ubuntu?

---

### Post by Rick Abraham on 2009-10-11
As soon as I boot my pc the BIOS screen loads and then GRUB gives me a error 21 before I even get a chance to select what OS I want to boot. The GRUB menu doesn't even come up.

---

### Post by mhgsys on 2009-10-11
First of all> check if your bios is booting from the right drive, try to boot from the other drive and if that doesn't work, put back the boot settings and reconfigure grub.

To reconfigure grub;  this is a good way to do that;

Bootup a live cd, open a terminal and do the following.

sudo grub
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```

find /boot/grub/stage1

```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```

root (hd?,?)

```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```

setup (hd0)

```
Finally exit the grub shell
```

quit

```

Hope this helps for you, and if not; we need some more information.

In order to get a clearer picture of your setup, boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop from here; 

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and type:

```


sudo bash ~/Desktop/boot_info_script*.sh

```
This will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

Meantime, People will be here to help you with the information provided by the info_script if help is needed.

Hope this works out for you with reinstalling grub though,

---

### Post by blueridgedog on 2009-10-11
One small addition.  The setup (hd0) command will setup the first hard drive and is the default 99% of the time.  However, new bios chips can boot from other drives and if you have changed the boot drive in your bios, you will need to adjust the command accordingly.

---

