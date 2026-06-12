---
title: "Grub rescue"
date: 2010-09-13
forum: General Help
---

### Post by rapattack1 on 2010-09-13
Hi i didn't google about this issue as i never seem to understand any page that comes up about any Linux issue so here it is. I installed Ubuntu 9.10 a few days ago, did the updates, surfed on the net, mounted a slave drive and read everything on it, shut down, pulled the slave out and now i can't boot. After the post screens i get: Verifying DMI pool data
Grub loading
error: the symbol 'grub-device-open' not found
grub rescue>

I think way back i had to reinstall grub or something on another machine i had but i don't remember anything about it. Is that what i have to do and how? Is it because i pulled that slave drive out that this happened? Would appreciate some help as i want to get some more files off the slave as i wasn't finished. Just too tired and had to go to bed!

---

### Post by garvinrick4 on 2010-09-13
> **rapattack1 said:**
> Hi i didn't google about this issue as i never seem to understand any page that comes up about any Linux issue so here it is. I installed Ubuntu 9.10 a few days ago, did the updates, surfed on the net, mounted a slave drive and read everything on it, shut down, pulled the slave out and now i can't boot. After the post screens i get: Verifying DMI pool data
Grub loading
error: the symbol 'grub-device-open' not found
grub rescue>

I think way back i had to reinstall grub or something on another machine i had but i don't remember anything about it. Is that what i have to do and how? Is it because i pulled that slave drive out that this happened? Would appreciate some help as i want to get some more files off the slave as i wasn't finished. Just too tired and had to go to bed!
You have to find which ubuntu install you are using to boot from and the install grub from that install.
sudo fdisk -l (small L)

Find which one is your Ubuntu install. Lets say sda5 for this.
                   ```
sudo mount /dev/sda5 /mnt 
```                    ```
sudo grub-install --recheck --root-directory=/mnt /dev/sda 
``````
sudo update-grub
```

---

### Post by rapattack1 on 2010-09-13
How do i do a command from that > ? I don't know how to get from the last thing that is on the screen?
I don't know what you mean about which drive the ubuntu install is on. I installed ubuntu on the single drive that is in the machine as i said i surfed and other stuff and much later....days maybe i plugged in the slave.

---

### Post by garvinrick4 on 2010-09-13
Put in your Ubuntu install Cd and reboot and choose Try Ubuntu not the install. When it gets to the desktop go from System to Administration to Terminal and click on the terminal then copy and paste the commands one at a time into the Terminal (command Line). You will see when you type in 
```
sudo fdisk -l 
```( small L)

It will give you your drive like sda1, sda2 sda3 and so on and on. sda1 is like C, D, E and so forth in linux. linux just uses these #'s instead of letter. You will see run the command.
Copy and paste here if you want us to pick out your linux install.

---

### Post by rapattack1 on 2010-09-13
Hi the Live CD won't let me 'try'.  In white writing it has 'Press F4 to select alternative start-up and installation modes'. When i press enter anyway and little thing pops up saying 'Boot loader live' with an ok button. I click enter and it goes away leaving me back with the above. I press F4 and i can choose 'normal or safe graphics mode or Use driver update disc or OEM install(for manufacturers)'. What should i do?

---

### Post by garvinrick4 on 2010-09-13
> **rapattack1 said:**
> Hi the Live CD won't let me 'try'.  In white writing it has 'Press F4 to select alternative start-up and installation modes'. When i press enter anyway and little thing pops up saying 'Boot loader live' with an ok button. I click enter and it goes away leaving me back with the above. I press F4 and i can choose 'normal or safe graphics mode or Use driver update disc or OEM install(for manufacturers)'. What should i do?
Who's Cd are you using?

---

### Post by rapattack1 on 2010-09-13
Its a cd that i ordered from the Conicel website. I know i spelled that wrong. That is the cd i used to install Ubuntu.

The attached picture show the first thing i mentioned.

Oh finally it got me in....this is what i got!
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01d501d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
/dev/sda5 looks like swapspace - not mounted
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grib-install --recheck --root-directory=/mnt /dev/sda1
sudo: grib-install: command not found
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ 


---

### Post by rapattack1 on 2010-09-13
Tried again and no luck! Same results as listed :0(

---

### Post by Soul-Sing on 2010-09-13
```
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
not sda1!

please run the boot_info_script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
stored on your desktop:  ```
sudo bash ~/Desktop/boot_info_script*.sh
```

post the results here between tags

---

### Post by Scunnered on 2010-09-13
I managed to delete my grub entry when attempting to work with another OS.

I was directed to :

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

which worked for me.

I hope this assists

---

### Post by garvinrick4 on 2010-09-13
Run:
```
sudo update-grub
```When you boot into linux.

Remember your linux is in sda1 and your boot always go's into sda.
Swap area is for scratch disk for extra RAM if needed in sda5.

Are you up and running?

---

### Post by rapattack1 on 2010-09-14
[PHP]ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt /dev/sda
grub-probe: error: cannot find a device for /mnt/boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 

[/PHP]

Ah I am a bit confused on what to do after this as there is just too much information in front of me and things are not going correctly according to the above so i will stop until i am advised by someone ....i don't understand what a scratch disk is and the other stuff so will wait!
I am using the LiveCD right now!

Sorry if i got the thing wrong above. I don't remember where the tag thing is....forgot!

---

### Post by rapattack1 on 2010-09-14
Gee now i am back on my windows machine because the damn machine i had the livecd in won't boot. I have no idea what is happening. I went to do the Livecd in the windows machine but i got tired of going in the bios in the other machine and it not working. I have no idea why it keeps going in circles. It gets as far as choosing the language and the error like before with the white writing. Then reboots and does it again and again and again. I changed the bios battery thinking that that could be it. Also at some point the video card played up so i changed that. **** i don't know what is going on. I tried another(factory made) live cd(Ubuntu 8) and that didn't work either.

Oh this is odd i tried both versions of Ubuntu in my windows machine and the system didn't see them at all. I set the first boot device as the cd drive and there was a marked slowness in booting but it did eventually boot. How odd that both Ubuntu cd got corrupted somehow. Damn!

---

### Post by garvinrick4 on 2010-09-15
Put in a live CD
```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --root-directory=/mnt/ /dev/sda
```If that returns any errors run:
```
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
```You have to mount the partition that holds your linux install. Yours is sda1
Next we put the grub from sda1 into sda  (google mbr to explain)
If it comes back with errors we gave it the recheck command.

Make sure when you get back into Ubuntu on hard drive you run:
sudo update-grub
Now all your installs Windows and linux installs will be in grub menu to select from:
[COLOR=#000000][COLOR=#0000bb]

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$  

You forgot to download Script to DESKTOP. Then run the:
[/COLOR][/COLOR]```
sudo bash ~/Desktop/boot_info_script*.sh
```Script is here and download to DESKTOP.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by rapattack1 on 2010-09-15
I can't do any commands. It is not going into the desktop now. It is rebooting itself and doesn't load the livecd thing properly. ONly gets as far as what language and then reboots.

No windows -Windowsxp is on another machine . I tried to use the livecd on one machine that has the grub problem (and ubuntu)first and that is what this post is all about and then i tried yesterday or whatever on the windows machine.

So not able to do whatever that script thing is. I have to fix whatever is the reason why i can't use the livecd 's anymore????

The cd's aren't scratched by the way. I also tried an old cd i have that has puppy linux and i think another one. None working. All of my machines are 32bit so i can't think why this has happened.

---

### Post by rapattack1 on 2010-12-15
Don't remember what happened after this but i suspect i am using a different computer and i just installed Ubuntu 10

---

