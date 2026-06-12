---
title: "How to disable splashscreen ?"
date: 2010-05-01
forum: General Help
---

### Post by nomemory on 2010-05-01
Hello,

I have no interest in eye-candy. I want to know how do I disable the boot splashscreen completely. I prefer a text-only boot screen, without any images or animation.

Thank you.


NOTE: I am using Ubuntu 10.04 .

---

### Post by WorMzy on 2010-05-01
Edit /boot/grub/menu.lst. Remove "splash" from the kernel argument.

If you're using grub2, I can't help. Try consulting the man pages.

---

### Post by linuxman94 on 2010-05-01
To change the boot screen to text only, run the first command and choose option 2.  Then run the command below it.
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

---

### Post by nomemory on 2010-05-01
> **linuxman94 said:**
> To change the boot screen to text only, run the first command and choose option 2.  Then run the command below it.
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```

I've tried the above command, unfortunately I don't have any option 2:
```
sudo update-alternatives --config default.plymouth
There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.
```
Any suggestions ?

---

### Post by mikewhatever on 2010-05-01
How about editing /etc/default/grub? Find the following line and remove 'splash'.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
When done, run *sudo update-grub*

---

### Post by linuxman94 on 2010-05-01
Oops.  I forgot you have to install the text theme.

```
sudo apt-get install plymouth-theme-ubuntu-text
```
Then run:

```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```

---

### Post by cracker on 2010-07-14
> **linuxman94 said:**
> Oops.  I forgot you have to install the text theme.

```
sudo apt-get install plymouth-theme-ubuntu-text
```
Then run:

```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```

While this does get rid of the fancy graphics, it doesn't get rid of the splash screen, and still hides the important text that used to show. You must still press escape to see this, and it doesn't even show all of it. Is there any way to tell plymouth to not splash at all? If not, there should be. This has caused me plenty of headaches, the most important being that I can no longer see the progress of fsck on my very large data partition (even after pressing escape).

---

### Post by lordskid on 2010-07-14
> **mikewhatever said:**
> How about editing /etc/default/grub? Find the following line and remove 'splash'.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
When done, run *sudo update-grub*

remove the quiet too to show boot messages.

---

### Post by emoguitarist06 on 2010-07-15
I'm running UBUNTU 9.10 and I want to keep my BOOT splash screen but I would like to remove the SHUTDOWN splash screen.

The reason I ask is because the shutdown splash is extremely distorted and the Ubuntu logo runs across the screan Diagionally from right to left and slowly moving down... it looks like poop! 

So my ultimate solution would be to have the splash fixed to show a solid flashing ubuntu logo just like in boot up.

Is that possible?
(PS my netbook is posted in my sig)

EDIT: I found this post. Look at post number 3, Would this help?
[http://ubuntuforums.org/showthread.php?t=865670](http://ubuntuforums.org/showthread.php?t=865670)

---

### Post by linuxman94 on 2010-07-15
@emoguitarist06

You will get better help if you create a new thread.

---

### Post by emoguitarist06 on 2010-07-15
> **linuxman94 said:**
> @emoguitarist06

You will get better help if you create a new thread.

Roger roger ;)

---

