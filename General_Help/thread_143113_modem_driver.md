---
title: "modem driver"
date: 2006-03-11
forum: General Help
---

### Post by chris23 on 2006-03-11
hello
I'm looking for a driver for HSP56 MicroModem Pctel

I've downloaded the stable version from 
[http://linmodems.technion.ac.il/pctel-linux/welcome.html](http://linmodems.technion.ac.il/pctel-linux/welcome.html)
 but unfortunately the setup didn't find my modem...
any help
thanks in advance

---

### Post by red_shrike on 2006-03-31
Use kernel 24 or try manual install

---

### Post by towsonu2003 on 2006-04-14
any news here (worked / did not work)?

---

### Post by red_shrike on 2006-04-15
YES. It is alive :))))))) I compiled kernel 2.6.8.1 vanilla from kernel.org and it worked perfectly. If someone wants my comments and help with instructions post it here pliz. [http://pctelcompdb.sourceforge.net/](http://pctelcompdb.sourceforge.net/) is the modem. it supports kernel 2.6.0 -> 2.6.8.1 and all 2.4 kernels. For dialing up you can use gnome-ppp via synaptic or kppp (slow...).

---

### Post by towsonu2003 on 2006-04-15
could you by any chance add your instructions to the wiki (second link in my signature)? Just register, log in, click "edit" while on the page, put them in, and we'll clean it out :) hope it's not too much to ask? wiki doesn't have a section on pctel as far as i know -thanks :)

PS. Congrats :) good news

---

### Post by red_shrike on 2006-04-16
Oh boy. Once again, my writing skills are needed. OK, I will give my input under one term only: somebody please (as promise towsonu2003) edit my post to conform higher standards of english and syntaks. Tonight I will give my preliminary method which should be enough to get you started!!! Soon, we will all browse on Ubuntu! Long live the penguin! Just out of curiosity, are you tows* using dial up or dsl?

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=red_shrike]Just out of curiosity, are you tows* using dial up or dsl?[/QUOTE]
as per my obsession, I'm using dial up... which kept me away from linux for a long time... 

don't worry about the writing part :)

---

### Post by red_shrike on 2006-04-16
Since wiki doesnt want to log me in, I will post my instructions here. I am sure that is because I am a balkan. Yup. We eat kids for supper and therefore we cant write wikis. I hate people. So here it comes:

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=red_shrike]Since wiki doesnt want to log me in, I will post my instructions here. I am sure that is because I am a balkan. Yup. We eat kids for supper and therefore we cant write wikis. I hate people. So here it comes:[/QUOTE]
Let me know (with a new post to here or with a private message once you complete it. I'm pretty much sure you'll be even more angry after writing that stuff though :) I'll put them in for you. 

as per not being able to log in, make sure you enabled cookies and javascript for the site ubuntu.com... correct login username and password... another browser (like epiphany which doesn't have much security stuff in it). 

if that doesn't work, post a new thread to the "forum discussion" so someone who knows whom to contact can contact someone about your issue. That shouldn't happen, wiki should be open to everyone, regardless of eating habits ;)

I'm turkish and we don't like eating kids. Not enough meat...all bones...

---

### Post by red_shrike on 2006-04-16
OK guys. In order to use PcTEL Micromodem 56 (or any other modem supported by driver) you will have to switch to kernel 2.6.8.1 or lower. Even so, some units will NOT work with 2.6 kernel (consult README file in driver archive), but all of them work with 2.4 kernels. To make the short story long, going online on Ubuntu 5.10 aka. Breezy Badger you have to do four things: (before u do all this, read this wiki until the end) 
I.     get some utilities (gcc & initrd among else) 
II.  get vanilla kernel on [www.kernel.org](www.kernel.org) (I suggest) 2.6.8.1 (but 2.6.7 is a safe bet)
III.  Recompile the kernel
IV.Install the driver and configure ppp  

Here are the details:
(I will assume your kernel source is in /root

Open terminal and login as root by typing $ su (or use sudo in font of every command)
$ apt-get install gcc-3.4 build-essential libncurses5-dev kernel-package gnome-ppp module-init-tools initrd-tools procps
 (this step ensures you will have easier time later on)
$ ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc (this will make your system use gcc 3.4 instead of 4.0.2)
$ cd /root
$ tar -xvfj kernel-2.6.8.1.tar.gz
$ cd kernel-2.6.8.1
$ make mrproper
$ make xconfig (if xconfig doesn't work use menuconfig or gconfig instead)
Configure your kernel if you know what you are doing, but you don't since you are reading this so don't do anything.
$ File-> Load go to /boot and load config-2.6.12-9-386
$ make-kpkg clean
$ make-kpkg --initrd --revision=custom.1.0 kernel_image
After couple of hours, or less depending on you CPU....
$ cd /root
$ dpkg -i kernel-image-2.6.8.1_custom.1.0_i386.deb

If something goes wrong go to /root and run $ make clean and repeat evrything.
	If you are using GRUB that's it. No more. If you are using LILO, browse a bit and you'll find how to configure it. Only one note here: you will not see standard Ubuntu splash on boot process; screen will be black, but the boot will go as normal. If you want to see what is happening go to /boot/grub and open menu.lst and under line that goes boot /boot/vmlinus something...something quiet splash delete this splash. Or, if you will you can go on-line and find a better way to do this. There are enough resources.
	Second, if you are messing with configuration of the kernel, DO NOT change things you are not sure about. Sure, feel free to slect only your graphic/music card or such things, but if you are not sure if you need something don't remove that. Remember, these are the settings that WORK. 
***Actually, if this compiled kernel doesn't work, you will have to add some changes... and here they are: (you can do this in the first attempt)



CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_RAM_SIZE=65536
CONFIG_BLK_DEV_INITRD=y

These settings may be changed in Block Devices in kernel configuration or you can open file /boot/config-2.6.8.1 and look for these lines (if they don't exist, make them), than use this modified config file to compile the kernel. I have Pentium II 400 Mhz @ 128 Mb RAM  and it takes three hours to compile kernel if no changes are made to config file. Final size is cca. 12 Mb, however fully custom,ized kernel is around 2 MB and it takes 30 minutes to compile. You can spped up the process by killing gdm and all the stuf you dont need. Here is how to: f1+ctrl+alt and then login as root or use sudo (i will assume u use root) Oh, yeah, some old Pc's will need support for compressed ROM filsystem that can be found on Fileysstems ->Misceleneous
$ /etc/init.d/gdm (or kdm if u use kubuntu) stop
$ kill -9 -1
now continue with $ make menuconfig...

Final step: once you have sucessfuly compiled the kernel and the drivers you will whish to be able to load the drivers every time you boot the machine. Here is how you do it: go to /etc and look for file called modules. Open it and add following lines: linmodem
         pctel
         pctel_hw


Final comment: this should be it, if someone has problems I wil be happy to share experience. Recompiling the kernel WILL do the trick. If you use the same config as in the original, thre will be no problems. If you edit it, there might not be problems, or you mighnt not be able to mount root partition. If you customise the kernel, you will speed up boot process and your whol Linux (even thugh slightly). I will tak no blame if you mess your computr up. However, you will notice that Linux, unlik windows, can use multiple kernels. Next time you reboot, you will be able to choose which kernel to use. For your first boot I reccomend recovery one.

---

### Post by towsonu2003 on 2006-04-16
I have to say "ouch"...

It seems they/you don't need to compile modem modules or download them. Is that correct? 

Here is the wiki:
[https://wiki.ubuntu.com/DialupModemHowto#head-0c2894ebe732fa55ff610db25521f306bab0a38f](https://wiki.ubuntu.com/DialupModemHowto#head-0c2894ebe732fa55ff610db25521f306bab0a38f)

I changed a couple of things (use of sudo, place for kernel source) to standardize with other kernel compile howtos, but that's all.  There is a FIXME attached to ln -s gcc...... because I'm not sure if that symlink should be temporary or not. Compilation howtos give temporary symlinks. 

Let me know if you need something changed :) Hopefully others will review and fix things i didn't know / notice :)

Thanks so much for your time and effort!

---

### Post by red_shrike on 2006-04-17
No, you will still have to download modem drivers and install them, except that this time you wil not have any problems in doing so. I even get the "install finished" message when it is done. That is simple simply run ./setup or go to ~/src and run ./configure, make, make install

---

### Post by red_shrike on 2006-04-17
OK here are some IMPORTANT changes. If you look at my post you will notice some changes like make-kpkg --initrd --revision=custom.1.0 kernel_image change is in last part, it is kernel_image, not kernel_modules. This is important because it will not work otherwise. Another thing is: if the compile doesn't work (i edited the post very shortly, perhaps you didnt see it), go to /lib/modules and remove folder with your kernel version name (ie. if you are using 2.6.8.1 kernel delete /lib/modules/2.6.8.1 folder). Second, if the compile worked, copy the sources to /usr/src For some more elaborate stuff see [http://www.falkotimme.com/howtos/debian_kernel2.6_compile/](http://www.falkotimme.com/howtos/debian_kernel2.6_compile/) which I have used in the first place, but had to adapt a bit. Remember, to use --initrd


And now: this is my contribution to you guys, since I got so much help from you it is OK if I give somebody else a little bit. Thnx tows* for help. I would suggest to use Midnight commander, it really is great. (apt-get install mc)

---

### Post by towsonu2003 on 2006-04-17
thanks a lot for the input. :)

I didn't include the info on deleting /lib/modules/bla as it seemed to be a little drastic (and I can't test it, bc downloading kernel source with dial up sucks...) They will hopefully come accross that info (if they have a problem) googling or reading this post.

---

### Post by red_shrike on 2006-04-17
Well, they will get an error message saying some old modules have been found. This happens only if you attempt to reinstall your existing kernel, but you are right,anyone who attempts doing this will probably have enough brain to correct it. Rememmber, you are not deleting the whole folder, only he folder with the name of your miss-compiled kernel.

---

### Post by helmut_hed on 2006-04-30
Hi all,

I don't believe it's necessary to use an old version of the kernel or a special version of gcc, either, in order to get your PCTel modem working.  This is all you should have to do:

Get this file:

[http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-5.tar.gz](http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-5.tar.gz)

installation process is:

tar xvzf pctel-0.9.7-9-rht-5.tar.gz
cd pctel-0.9.7-9-rht-5
su
(type your root password)
./setup

which will compile, install, and activate the driver.  I've tested it through kernel 2.6.15.1.

I'd be very interested to hear if this driver fails to work for you.

Thanks and regards,
Jeff Trull
PS: working on building an ubuntu package for this to make it easier.

---

### Post by red_shrike on 2006-05-02
Cool. I will check it out. When I wrote that rht-4 was the latest one. Unfortunately it didnt work on generic breezy kernel... thnx dude.

---

### Post by helmut_hed on 2006-05-06
Oops.  Finally installed Ubuntu and tried it out myself, and you *do* need the old gcc version.  My apologies.  I wrote up a HOWTO based on what I found, and it's here:

[http://ubuntuforums.org/showthread.php?t=171163](http://ubuntuforums.org/showthread.php?t=171163)

I'm still working on getting this made into a .deb package.  Hopefully I can get the Ubuntu or linmodem guys to host it.

---

