---
title: "Grub cannot find partition"
date: 2011-06-27
forum: General Help
---

### Post by cdyrssen on 2011-06-27
Ok. So I recently installed Ubuntu 11.04 on a clean hard drive. Everything went well and I ended up giving /home it's own partition. After a while I figured I would dual boot with windows 7 and my mbr got overwritten. Now after this happened I googles how to fix it and found the same answer almost everywhere. It had me go into terminal and run grub an find my partition and setup grub again. All of this was done off a livecd. The only problem was that my livecd didn't have the grub shell installed. Everytime I ran "sudo grub" it would say "sudo: grub: command not found" I tried to install it but it kept giving me errors and I only once actually got into grub, but it could not find my partition. Whenever I typed "find /boot/grub/stage1" it said directory does not exist. So I attempted to fix it my own way. I installed another version of ubuntu along Sid the first. This allowed me to triple boot between the two versions of ubuntu and windows 7. So I booted into my original ubuntu (11.04) and deleted the older version of ubuntu with gparted. I deleted the partition and restarted, but when I restarted I got an error saying that grub could not find the partition. I can boot into my original ubuntu through the ultimate boot cd but it is a round a bout way of doing it. Is there anyway I can set grub to search for ubuntu 11.04 on startup instead of the deleted version of ubuntu?

---

### Post by garvinrick4 on 2011-06-27
In Live CD:.
```
sudo mount /dev/sdax /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```[COLOR=Red]x [/COLOR]being whatever your partition # is in:
```
sudo fdisk -l 
```(lower case L)

Now reboot:
Go into ubuntu install and:
```
sudo update-grub
```#You are installing grub to sda and it looks for the boot files in whatever install you tell
grub to (the sda[COLOR=Red]x[/COLOR] you tell to mount).
#There are numerous ways to do this, this above is one way, here are a couple of links that are nice
for you to keep around below:

[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 
##You cannot do a "sudo update-grub" in a live CD unless you use the "chroot method"  as in How To- Purge and Reinstall Grub 2 link:

---

### Post by cdyrssen on 2011-06-27
Ok I did everything you said to do in your post and it worked :) but now the Grub menu doesn't show at startup so I can't choose between windows and ubuntu how do I edit grub so that it shows up before ubuntu loads. I have attempted to edit the menu.lst file and comment the hiddenmenu option and save it but it seemed to do nothing. I have also tried to uncheck the hidden menu option in grub customizer but didn't get any results. Any ideas?

---

### Post by drs305 on 2011-06-27
Have you run "sudo update-grub" since you rebooted? You need to run that command so Grub 2 can find Windows and include it in the Grub menu. Until Grub 2 is aware of another OS (via update-grub) by default it won't display the menu during boot. As you run the 'update-grub' command, watch the terminal output and see if it finds Windows.

If the menu still doesn't display on boot, reboot and hold down the SHIFT key as the computer boots. The Grub menu *should* display. See if the Window entry exists.

---

### Post by cdyrssen on 2011-06-27
Ok so I did the update and no windows was found in the update. Then when I used shift during bootup it showed the grub menu but still no windows. Is there any way to reinstall windows without overwriting grub as the mbr?

---

### Post by drs305 on 2011-06-27
Before you reinstall Windows, you might do two things.

First, ensure os-prober is installed and working properly.
```

sudo chmod +x /etc/grub.d/30_os-prober  # Ensures the script is executable
sudo os-prober # Checks to see if the OS searcher is installed/working
```
If it doesn't appear to do anything or isn't found:
```
sudo apt-get install os-prober
sudo update-grub
```

Second: It's possible that Windows is missing critical boot files, in which case Grub won't find or list Windows. If you run the boot info script (click on the 'BIS' link in my signature line) and post the contents of RESULTS.txt we might be able to see what the problem is.

You may need to install Windows, but doing these things first will probably be faster and may prevent a reinstallation. You may at worst just have to run the Windows repair commands.

---

### Post by cdyrssen on 2011-06-27
the RESULTS.txt file is attached to this post.

---

### Post by drs305 on 2011-06-27
Neither the boot info script nor Grub is finding your Windows files. 

It looks like your Windows installation could be on sda3 or sdb1. There is reference to truecrypt, and also /dev/dm-1 and /dev/mapper. I don't know enough about Windows or truecrypt to tell you what the problem is but hopefully someone will come along that does.

It may help them if you can elaborate on any special setup you are running or ran on these drives (truecrypt, RAID, etc).

---

### Post by cdyrssen on 2011-06-27
sdb is the truecrypt mount of my external hard drive. I encrypted it because my brother kept cutting my movies to his computer without my knowing and i kept loosing them. The sda3 partition has my windows 7 installation.

---

### Post by drs305 on 2011-06-27
Normally in the Windows partition there should be the following boot files/folders:
/bootmgr /Boot/BCD /Windows/System32/winload.exe

From the LiveCD, if you mount the Windows partition and take a look with a file browser, do you see them?

```
sudo mount /dev/sda3 /mnt
gksu nautilus /mnt
```

---

### Post by cdyrssen on 2011-06-27
All the files/folders stated existed in the windows partition. Do have any advice?

---

### Post by drs305 on 2011-06-27
There are some things I might try on my machine but I'm not sure I'd recommend them to someone else (since I'm used to trashing my system and repairing it).

I'd wait to see if someone with a solid Windows background responds to your thread.

If it were my machine, I would probably purge and reinstall Grub2. The reason is that you have parts of Grub legacy still hanging around in your /boot/grub folder. There isn't any purpose to having them, and although I don't know if can do any harm, it can't do any good... This might or might not allow Windows to display. I think probably not, since the boot info script didn't find the Windows files either.

The second thing I'd do, if I knew more about Windows, would be to run chkdsk on the Windows partition from a Windows CD. Then I might try repairing Windows, again using a Windows CD. [Post 7]("http://ubuntuforums.org/showthread.php?p=9826152")

But again, I'd probably wait for someone else to respond.

---

### Post by cdyrssen on 2011-06-28
I can still boot into windows with Super Grub2 from the ultimate boot cd i have. I will try to run a repair while in windows and post what happens. Thanks for your help. I may not have been able to fix all of the problems, but i learnt some new things that will be useful in the future.

---

### Post by cdyrssen on 2011-06-30
I was not able to get grub to recognize the windows partition even after a complete windows reinstallation, so i reinstalled ubuntu and everything works great now:) i was worried i would lose all of my preferences, but luckily my /home directory was a different partition and all the preferences i was worried about were saved there. In the end everything worked out. I just had to do some reinstalling of programs. Thanks for your help.

---

### Post by drs305 on 2011-06-30
Sorry you had to go the 'reinstall' route but glad everything is now working.

Happy Ubuntu-ing !

---

