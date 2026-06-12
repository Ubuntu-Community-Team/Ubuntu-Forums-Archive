---
title: "Failed update 9.10"
date: 2009-10-31
forum: General Help
---

### Post by fearful on 2009-10-31
I just updated my Ubuntu to 9.10 and everything seemed to work fine until it restarted. I restart the computer and login and the screen stays in black with my mouse cursor I can move it for a few seconds then the mouse gets stuck and I cannot move it anymore and it won't go any further I can press Ctrl + Alt + F1 to go into the TTY1 so my inputs are working fine.. any ideas on this issue? Any help will be much appreciated thanks

---

### Post by P4man on 2009-10-31
Do alt F1 and alt f2 still work in gnome? IOW it is just the mouse that is not responding or more like X crashed ?

---

### Post by fearful on 2009-10-31
No they do not work I think its a problem with X is there a way I can reconfigure it through the TTY's I really need to fix this issue I have a flight tomorrow and I need to take my computer haha.. any help MUCH appreaciated

---

### Post by P4man on 2009-10-31
ive seen some people doing an upgrade and ending up with the old jaunty kernel, resulting in all sorts of problems. So lets check that. From the tty run

```
uname -a
```

you should have 2.6.31-xx. If you have 2.6.28 then you are booting a jaunty kernel. Have a look at grubs config in that case.

---

### Post by fearful on 2009-10-31
I have 2.6.28 but in the grub there is no option to boot a 2.6.31.xx?

---

### Post by fearful on 2009-10-31
I also noticed that in the /boot folder there is no 2.6.30 :S

---

### Post by P4man on 2009-10-31
> **fearful said:**
> I have 2.6.28 but in the grub there is no option to boot a 2.6.31.xx?

Well thats where it went wrong. I just enabled karmic-proposed in my software sources and noticed one of the updates fixed a bug with grub relating to what you are having.

Im not sure how to solve it the easiest way, i dont even know do you have grub1 or grub2 now ?

Perhaps try this:

```
sudo update-grub2
```
(remove the 2 if you are using grub1)

Post the output if it doesnt detect a 2.6.31 kernel. If it does, reboot and cross fingers.

---

### Post by P4man on 2009-10-31
> **fearful said:**
> I also noticed that in the /boot folder there is no 2.6.30 :S

Did you have a separate boot partition?

---

### Post by fearful on 2009-10-31
Yes I do have a seperate boot partition from home and sudo update-grub1 or sudo update-grub2 do not work, says command not found

---

### Post by fearful on 2009-10-31
i did sudo update-grub and got:
Found Kernel: /boot/vmlinuz-2.6.28-16-generic
Found Kernel: /boot/vmlinuz-2.6.28-15-generic
Found Kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst done

---

### Post by P4man on 2009-10-31
> **fearful said:**
> Yes I do have a seperate boot partition 

Okay that at least confirms its the same bug. Wish I had kept the bug report bookmarked :s

>  sudo update-grub1 or sudo update-grub2 do not work, says command not found[

Remove the 1. just sudo update-grub for grub1. But its very strange you wouldnt have that command for grub2. you sure you arent mistyping?

Anyway I guess the nuclear option here is to boot from a karmic cd and reinstall grub2. Cant give you the correct instructions for that without googling, but it should be easy to find.

edit: booting from jaunty cd should work too, it also has the grub2 tools afaik

---

### Post by P4man on 2009-10-31
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/449679"]
Karmic Koala Upgrade Uninstalls Grub 2[/URL]
[URL="https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/407750"]
[karmic] kernel upgrade from jaunty don't refresh grub entry[/URL]

try installing grub2

sudo apt-get install grub2

---

### Post by fearful on 2009-10-31
The problem is this install is from Ubuntu 8.04 I have grub1, now I just installed grub2 with sudo apt-get install grub2 but I noticed it still stayed on 2.6.28.xx

---

### Post by P4man on 2009-10-31
> **fearful said:**
> The problem is this install is from Ubuntu 8.04 I have grub1, now I just installed grub2 with sudo apt-get install grub2 but I noticed it still stayed on 2.6.28.xx

does the grub menu show as 1.9xx beta (=grub 2) or 0.9xx (grub 1) ?
Did you try running 
```
sudo update-grub2
``` ?

---

### Post by fearful on 2009-10-31
Yes I tried that too and still stays in 2.6.28.xx can I just update the kernel to .30?

---

### Post by P4man on 2009-10-31
> **fearful said:**
> Yes I tried that too and still stays in 2.6.28.xx can I just update the kernel to .30?

You should already have that somewhere. I guess it wont hurt to try though.
```

sudo apt-get install linux-image-2.6 <tab>
```

---

### Post by P4man on 2009-10-31
another thing you could try, is 

```
sudo nano /etc/apt/sources.list
```

add or uncomment

```
deb http://archive.ubuntu.com/ubuntu/ karmic-proposed restricted main multiverse universe
```

then 

```
sudo apt-get update
sudo apt-get upgrade
```

That will fetch the fresh bug fix. Not sure if after that you have to run update-grub2 or reinstall grub2 or anything to make it work

---

### Post by fearful on 2009-10-31
I have installed .31 and did sudo update-grub2 and seemed to work fine but got stuck again

---

### Post by P4man on 2009-10-31
> **fearful said:**
> I have installed .31 and did sudo update-grub2 and seemed to work fine but got stuck again

so uname -a now shows the new kernel? But X still crashes ?

---

### Post by fearful on 2009-10-31
Yea uname -a shows new kernel still same problem :(

---

### Post by P4man on 2009-10-31
Oh that sucks. Meh, here was me thinking I  was so clever deducting your problem.

ok tell me what hardware you have, especially what videocard.

---

### Post by fearful on 2009-10-31
I have all Intel hardware its a hp dv6000 I have intel corporation mobile 945/GSM... For display... Intefrated graphics control

---

### Post by P4man on 2009-10-31
Hmm.. new intel drivers are now in the kernel. Using the 28 or 31 driver ought to make a big difference, perhaps just apt-getting the kernel wasnt enough.

 Try this:

```
sudo update-initramfs -k `uname -r` -u
```

---

### Post by fearful on 2009-10-31
tried and failed nothing seems to work :S:S

---

### Post by P4man on 2009-10-31
If i where you id download the 9.10 image and try a live session. If that works then it might be some junk left over from your 8.04->8.10>-9.04>9.10 upgrades. Perhaps time for a fresh install.

If live session fails, we can dig deeper but it will probably result in a bug report.

---

### Post by fearful on 2009-10-31
Ok I will try that thank you for all your help

---

### Post by fearful on 2009-10-31
I remember there was a way to save all the installed apps in .deb format do u know the command? So I can reinstall easier my apps?

---

### Post by P4man on 2009-10-31
You could save apt's cache from 
/var/cache/apt/archives

If you want a list of installed packages from the commandline

```
dpkg --get-selections > packages.list
```

To install them all again later:

```
sudo dpkg --set-selections < packages.list 
```

---

### Post by fearful on 2009-10-31
I was able to succesfully back them up but after I did the second command nothingh happened the command was accepted but nothing installed.

---

### Post by P4man on 2009-11-01
It will select them for installation but not install. to install

```
 sudo apt-get dselect-upgrade
```

---

