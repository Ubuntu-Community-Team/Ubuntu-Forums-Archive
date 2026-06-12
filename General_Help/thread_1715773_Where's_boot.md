---
title: "Where's /boot"
date: 2011-03-25
forum: General Help
---

### Post by Itqan on 2011-03-25
i have small problem of my ubuntu 10.10 32 bit freezing after sometime i start it. so i searched around and have found a lil solution to it. 

it says that i need to set acpi=off but before tweaking the menu.lst file i need to copy it.

so i opened the ubuntu 10.10 generic opened terminal and used this code:-

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-original

but it says "cannot stat'/boot/grub/menu.lst':no such file exists". i tried opening recovery mode and selecting both "resume normal boot" and "drop to shell promp" but it isnt ther also.
i even tried pressing tab in boot menu where it takes boot options but then it says sudo dosent exist or something like that.
so how do i change that file?

---

### Post by Smart Viking on 2011-03-25
EDIT: Yeah file doesn't exist.

---

### Post by oldos2er on 2011-03-25
Grub2 doesn't use a menu.lst, instead configuration options are controlled with the files in /etc/grub.d and the file /etc/default/grub

Make a backup copy of /etc/default/grub ```
sudo cp /etc/default/grub /etc/default/grub.original
```

Edit the file ```
gksu gedit /etc/default/grub
``` Add acpi=off to the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```
Save and exit the file, run ```
sudo update-grub
``` Reboot.

See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Itqan on 2011-03-26
i had problem of crashing ubuntu so i posted this yesterday:-
[http://ubuntuforums.org/showthread.php?t=1714467](http://ubuntuforums.org/showthread.php?t=1714467)

and then exactly like this:-
> Grub2 doesn't use a menu.lst, instead configuration options are controlled with the files in /etc/grub.d and the file /etc/default/grub

Make a backup copy of /etc/default/grub
Code:
sudo cp /etc/default/grub /etc/default/grub.original
Edit the file
Code:
gksu gedit /etc/default/grub
Add acpi=off to the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Code:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
Save and exit the file, run
Code:
sudo update-grub
Reboot.


now when i try to boot into ubuntu. it dosent going to the nice looking gui login starts some console like DOS. Whats wrong? 
how do i fix this?

---

### Post by Itqan on 2011-03-26
anyone please?

---

### Post by vivek.pandey on 2011-03-26
if you have problem reaching gui window
login in the conso;e window to your account and then type startx
you will get a gui window of your account

---

### Post by oldos2er on 2011-03-26
Why didn't you post this in the original thread? Easier to keep track of that way.

---

### Post by TheHimself on 2011-03-26
What is the prompt in the console after the computer boots?

---

### Post by Itqan on 2011-03-26
now when i try to boot into ubuntu. it dosent going to the nice looking gui login starts some console like DOS. Whats wrong? 
how do i fix this?

p.s i tried logging in that console and then typing "startx" but it shows many errors like file not found fatal file or something like that, etc.

---

### Post by Itqan on 2011-03-26
hey i tried pressing the shift key while the cursor was blinking and it shows this:-

```
udev-work[86]:inotify_add_watch(6, /dev/loop0, 10) failed:no such file or directory.
```

'work' could be the name of my drive.

then it shows:-

Ubuntu 10.10 Ubuntu tty1

then i am asked for login. then after showing "Welcome to ubuntu!" and some text i get a cursor after this:-
itqanullah@ubuntu:~$

---

### Post by Itqan on 2011-03-26
please help....
im in a lil panic.

---

### Post by Itqan on 2011-03-26
ok anyone knows how to replace the file i modified with the one i saved as backup? would be super cool if u solve the previous problem though.

---

### Post by Itqan on 2011-03-27
hi its super greenhorn again. i screwed up my ubuntu 10.10's grub modifying it. but before i did that i made a copy of it with this code:-
```
sudo cp /etc/default/grub /etc/default/grub.original
```

now when its all screwed up and i cant see any gui. thes a console atleast (than god!)
so whats the command to rename and overwrite the screwed up grub with orignal one?

---

### Post by Elfy on 2011-03-27
```
sudo mv /etc/default/grub.original /etc/default/grub
```

---

### Post by TheHimself on 2011-03-27
> **Itqan said:**
> hey i tried pressing the shift key while 

then i am asked for login. then after showing "Welcome to ubuntu!" and some text i get a cursor after this:-
itqanullah@ubuntu:~$

At this point try this 
```
grub-mkconfig
```
followed by
```
grub-install /dev/sda
```

Although I'm not sure this will work. Maye others can express their expert opinion?

---

### Post by oldos2er on 2011-03-27
> **Itqan said:**
> please help.

Did you try the **startx** command?

---

### Post by Perfect Storm on 2011-03-27
Threads merged.

---

