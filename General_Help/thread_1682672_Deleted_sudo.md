---
title: "Deleted sudo?"
date: 2011-02-06
forum: General Help
---

### Post by John2lhotal on 2011-02-06
Hey guys,

Has you can probably tell with the title of this post; I am fairly new to Ubuntu.

Ok, So i had installed couple of packages a while back that i did not want anymore. I will refer those packages as: "packageList" in this post.

I had pre-type in the terminal: sudo apt-get remove 

I then pasted the packagelist INCLUDING (by mistake) sudo apt-get install PackageList

What i mean by this is that the cmd was then:

sudo apt-get remove sudo apt-get install packageList

By the time i realized it, i had already clicked enter.

Therefore, it seems that i do not have the sudo package anymore.

Whenever i do something in the terminal with the sudo keyword i get this msg:

sudo apt-get install whatever
The program 'sudo' can be found in the following packages:
 * sudo
 * sudo-ldap
Try: sudo apt-get install <selected package>

any advice on how i get sudo back?

Cheers,

---

### Post by whatthefunk on 2011-02-06
Have you tried to install it through the Package Manager?

---

### Post by MiKOTRON on 2011-02-06
This is the biggest problem that I have with Ubuntu.  I really think that not having your root password set and put in a safe place is a detriment to the linux user.  If you set your root password you wouldn't be in this situation at all.  You could just su to root and reinstall sudo.  Just my 2 cents.

As for your situation...  I think you can boot into a live session using the CD and chroot into your system to put sudo back in its place.  

I'll check on that further.  Good luck.

---

### Post by John2lhotal on 2011-02-06
yah, i can't open the package manager, i get this error msg:

Could not launch 'Synaptic PAckage Manager'
Failed to execute child process "gksu" (No such file or directory)


cheers,

---

### Post by cgroza on 2011-02-06
You can enter in single user mode from the grub menu by selecting the recovery mode. You will be given another menu and there should be an option to drop you on a bash shell. You will be root. Run:
```
apt-get install sudo
```

---

### Post by John2lhotal on 2011-02-06
Lemme try. It is what i was reading about :) wasn't sure, but will try it right now. Thx !

---

### Post by dollzii on 2011-02-06
Maybe try;

```
gksu gnome-terminal
```

Just a tip, don't know if the gksu is a part of the sudo package?

Edit: Sorry, a little too late :S

---

### Post by ajgreeny on 2011-02-06
Boot to **recovery mode** from the grub menu and choose the **command line with networking**.  Run ```
apt-get install sudo
``` from there, which is root already, and you should be able to get sudo back again easily.

**gksu** is a different package but will also have gone as sudo is a dependency of it.  Simplest may be to ```
apt-get install ubuntu-desktop
``` which will bring in anything taken out along with sudo which you have not noticed.

---

### Post by John2lhotal on 2011-02-06
thx, there is another problem...i am unable to boot into recovery mode...i dont got any grub boot menu...i tried loading the live cd and i end up right away at the menu where i can either install ubuntu or try ubuntu.

any tips?? running on a dell latitude e5410 laptop

---

### Post by [Snc] on 2011-02-06
If you press 'e' at boot/startup, you get to the grub menu, that is where the recovery mode option is.

---

### Post by John2lhotal on 2011-02-06
i also tried that...
i tap 'e' from the beginning (even b4 the manufacturer logo) and keep tapping it but nothing happens and i end up in my normal ubuntu session log in page

---

### Post by John2lhotal on 2011-02-06
i tried that, but i never see the grub menu appear.
i tap e from at the boot (even b4 the manufacturer appears) but nothing. i end up at the normal ubuntu session log in

---

### Post by [Snc] on 2011-02-06
> **John2lhotal said:**
> i tried that, but i never see the grub menu appear.
i tap e from at the boot (even b4 the manufacturer appears) but nothing. i end up at the normal ubuntu session log in

Hows about booting to a live CD/USB and putting sudo to a location from there

(i didn't find it yet, all i find is /usr/lib[64]/sudo/sudo_noexec.so)

---

### Post by jroa on 2011-02-06
> **John2lhotal said:**
> thx, there is another problem...i am unable to boot into recovery mode...i dont got any grub boot menu...i tried loading the live cd and i end up right away at the menu where i can either install ubuntu or try ubuntu.

any tips?? running on a dell latitude e5410 laptop

Select try Ubuntu.  This will open a live desktop.

---

### Post by John2lhotal on 2011-02-06
> **jroa said:**
> Select try Ubuntu.  This will open a live desktop.

and what should i do from here? 
cheers

---

### Post by pqwoerituytrueiwoq on 2011-02-06
maybe you can boot off the cd and copy the sudo file to the system
sudo cp /usr/bin/sudo /media/YOUR_INSTALL/usr/bin/sudo
then you may be able to install without the cd

---

### Post by MiKOTRON on 2011-02-06
boot into the live cd and open a terminal.

```
# mkdir /mnt/ubuntu
# mkdir /mnt/ubuntu/boot
# mkdir /mnt/ubuntu/proc
# mkdir /mnt/ubuntu/dev
```then mount your system to your directories that you just made

```
# mount /dev/sda3 /mnt/ubuntu
# mount /dev/sda1 /mnt/ubuntu/boot 
# mount -t proc none /mnt/ubuntu/proc 
# mount -o bind /dev /mnt/ubuntu/dev
```Then copy over [COLOR=darkgreen][FONT=monospace][B]/etc/resolv.conf

[/B][/FONT][/COLOR]```
# cp -L /etc/resolv.conf /mnt/ubuntu/etc/resolv.conf
```Okay now chroot into your system

```
# chroot /mnt/ubuntu /bin/bash 
# env -i chroot /bin/bash -l
# source /etc/profile 
# export PS1="(chroot) $PS1" 
```It should read 
```
(chroot) # 
```at this point 
```
(chroot) # apt-get install sudo
```all should be well now.  Exit the chroot environment
```
(chroot) # exit 
# umount /mnt/ubuntu/boot /mnt/ubuntu/dev /mnt/ubuntu/proc /mnt/ubuntu
```good luck

---

### Post by John2lhotal on 2011-02-06
> **MiKOTRON said:**
> boot into the live cd and open a terminal.

```
# md /mnt/ubuntu
# md /mnt/ubuntu/boot
# md /mnt/ubuntu/proc
# md /mnt/ubuntu/dev
```

then mount your system to your directories that you just made

```
# mount /dev/sda3 /mnt/ubuntu
# mount /dev/sda1 /mnt/ubuntu/boot 
# mount -t proc none /mnt/ubuntu/proc 
# mount -o bind /dev /mnt/ubuntu/dev
```

Then copy over [COLOR=darkgreen][FONT=monospace][B]/etc/resolv.conf

[/B][/FONT][/COLOR]```
# cp -L /etc/resolv.conf /mnt/ubuntu/etc/resolv.conf
```

Okay now chroot into your system

```
# chroot /mnt/ubuntu /bin/bash 
# env -i chroot /bin/bash -l
# source /etc/profile 
# export PS1="(chroot) $PS1" 
```

It should read 
```
(chroot) # 
```

at this point 
```
(chroot) # apt-get install sudo
```

all should be well now.  Exit the chroot environment
```
(chroot) # exit 
# umount /mnt/ubuntu/boot /mnt/ubuntu/dev /mnt/ubuntu/proc /mnt/ubuntu
```

good luck


thx alot for the detailed help. When u say that i have to go to the live CD, as in recovery mode? (which i cant) or you mean while 'trying' ubuntu and typin ur code from a terminal there?

---

### Post by dino99 on 2011-02-06
if you dont glance after headache, better to make a fresh install (easier & faster)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by MiKOTRON on 2011-02-06
Yeah the second part of that.  Trying Ubuntu and typing the commands in a terminal window.

---

### Post by ajgreeny on 2011-02-06
Are you really still using Ubuntu 7.10?
Or have you simply not caught up and changed your profile details?

My goodness!  Ignore those recent suggestions; they are certainly not needed, as far as I can see, but yopur problem can be sorted out from recovery mode.

If using 7.10 you have legacy grub and need to press Esc as you boot; if 9.10 or later it will normally be grub2 and that needs Shift for the grub menu to appear.  Now go back to my previous post, choose recovery mode and run ```
apt-get install ubuntu-desktop
```No sudo needed from recovery mode as it is already root.

---

### Post by Krytarik on 2011-02-06
@ajgreeny: I'm just curious. How can it be, if not somehow altered, that no boot menu is displayed upon boot unless you press a special key?

---

### Post by MiKOTRON on 2011-02-06
ajgreeny's right. I didn't think about that.  It would be much easier if you can boot into recovery mode.

The KISS method is the best policy.

---

### Post by ajgreeny on 2011-02-07
> **Krytarik said:**
> @ajgreeny: I'm just curious. How can it be, if not somehow altered, that no boot menu is displayed upon boot unless you press a special key?
By default the grub menu does not show if you have only a single OS on the machine, largely because the only choice you would have is the kernel to boot to.  There is always the option to show the menu by pressing a key, Esc for legacy grub, Shift for grub2.

As MIKOTRON says, KISS!

---

### Post by pqwoerituytrueiwoq on 2011-02-07
if you boot a live cd you can edit the menu.lst fill in legacy grub
comment out hidenmenus
and up the timeout
/boot/grub/menu.lst
```

...
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu
...
```
be sure to edit it as root

---

