---
title: "HELP - Laptop won't boot!!"
date: 2011-07-19
forum: General Help
---

### Post by jlbr21 on 2011-07-19
Hello, My HP Pavilion laptop will not boot. I just got up this morning, turn on the computer, and the only thing I get is the boot screen, the Ubuntu logo on the purple background, and that is it.
I installed 11.04 Natty a few weeks ago, when it was released. I don't know what other info to give you. The computer acts normally and just can't seem to get past the boot. 

Please help, I have so much stuff in this laptop.

---

### Post by khaj_vah on 2011-07-19
Maybe you installed or removed soem things before turning off or rebooting (i ****** uped like that few times)

---

### Post by Mark Phelps on 2011-07-19
Next time you boot, hold down one of the SHIFT keys.  That will force the display of the GRUB menu.  Then, select the line that has Recovery Mode.  Once that boots, select the option to Repair Broken Packages.  If that completes OK, enter "startx" on the command line and you should see a desktop again.

---

### Post by jlbr21 on 2011-07-19
I don't recall removing or installing anything. One thing I did was disconnect my other monitor in order to pack it since I am moving. That is it. Also, i tried the GRUB menu and tried to run the recovery mode and can't get to make it work either. I tried running with last kernel but last kernel is not loaded, recovery mode just throws me into this MS-DOS like work space, asks for my login and password, and then nothing, graphic failsafe mode won't do the trick either. Help!!!

---

### Post by khaj_vah on 2011-07-19
it is not MS-DOS but try marks sollution

---

### Post by jlbr21 on 2011-07-19
The Repair Broken Packages is not doing it either. I get the message it is unable to fetch some packages, then throws me into the GRUB menu again.

---

### Post by khaj_vah on 2011-07-19
i am newby but this can be solved

---

### Post by jlbr21 on 2011-07-19
When I try to run failsafe mode, I see that the system is disconnected from bus, does that tell you something?

---

### Post by khaj_vah on 2011-07-19
i would be happy to help that says nothing me 
once i had a problem like that and i reinstalled my ubuntu but lost nothing even my desktop icon were restored

---

### Post by jlbr21 on 2011-07-19
Maytbe that's what I need to do...never had this problem before.

---

### Post by 2F4U on 2011-07-19
> **jlbr21 said:**
> When I try to run failsafe mode, I see that the system is disconnected from bus, does that tell you something?

What do you mean by "disconnected from bus"? Is there any error message printed on the screen. If yes, try to reproduce it here as close as possible or try to provide a screen shot.

---

### Post by khaj_vah on 2011-07-19
well maybe but i cant insure you so if

---

### Post by jlbr21 on 2011-07-19
it said, "disconnected from system bus" and that's the last thing i see before the computer shuts down.

I'm really lost here, what should i do? should i just reinstall the system?

---

### Post by jlbr21 on 2011-07-19
OK, so after trying to edit the kernel boot options, i get teh message that the kernel is missing. what does this mean?

---

### Post by jlbr21 on 2011-07-19
Come on guys, any ideas? Should I just reinstall the system? my installation is partitioned, so it would not be such a pain, but is that what i should do?

---

### Post by khaj_vah on 2011-07-19
Mate dont reinstall still this can be solved give me a minute

---

### Post by khaj_vah on 2011-07-19
1. Install these packages

sudo apt-get install kernel-wedge kernel-package libncurses5-dev

2. Run this command

sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)

3. Create your source directory

mkdir ~/src

cd ~/src

4. Download the Kernel source

apt-get source linux-image-$(uname -r)

5. Configure your Kernel

cd linux-2.6.38

make menuconfig

6. Speed up the build

export CONCURRENCY_LEVEL=3

General rule, concurrency level = number of processor cores + 1


7. Clean up temp files from a previous compile attempt (skip if necessary)

make-kpkg clean

8. Compile your Kernel

time fakeroot make-kpkg --initrd --append-to-version=-tweak kernel-image kernel-headers

You can change -tweak to anything you wish


9. Install your Kernel 

cd ~/src

sudo dpkg -i linux-image-2.6.38.2-tweak_2.6.38.2-tweak-10.00.Custom_amd64.deb

sudo dpkg -i linux-headers-2.6.38.2-tweak_2.6.38.2-tweak-10.00.Custom_amd64.deb

10. Reboot 


i found this here: [http://linuxtweaking.blogspot.com/2011/04/how-to-recompile-your-ubuntu-1104.html](http://linuxtweaking.blogspot.com/2011/04/how-to-recompile-your-ubuntu-1104.html)


May help if no sorry for wasting your time :)

---

### Post by cipherboy_loc on 2011-07-20
One thing khaj_vah forgot to mention was that you need an internet connection for this to work. Plug your laptop in via ethernet cable as wireless would take a bit to set up.


Cipherboy

---

