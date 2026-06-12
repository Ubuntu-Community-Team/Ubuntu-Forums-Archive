---
title: "Virtualbox Woes."
date: 2012-05-12
forum: General Help
---

### Post by chrispche on 2012-05-12
I have had to go back to a previous kernel:

```
Kernel Linux 3.0.0-17-generic
```

Due to 3.2.0-24-generic causing a what can only be described as a sort of blue screen of death. The computer is unusable. That was until I backdated to 3.0.0-17-generic. Now it's all running fine except for Virtualbox I can't run my Virtual Windows XP installation.

I get a number of errors of which:

```
chrispche@chrispche-VGN-AR51M:~$ virtualbox
WARNING: The vboxdrv kernel module is not loaded. Either there is no module
         available for the current kernel (3.0.0-17-generic) or it failed to
         load. Please recompile the kernel module and install it by

           sudo /etc/init.d/vboxdrv setup

         You will not be able to start VMs until this problem is fixed.
Error opening file for reading: Permission denied
chrispche@chrispche-VGN-AR51M:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for chrispche: 
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  Error! Your kernel headers for kernel 3.0.0-17-generic cannot be found.
Please install the linux-headers-3.0.0-17-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
chrispche@chrispche-VGN-AR51M:~$ 

```

Also here is a screenshot:

[[img]http://i45.servimg.com/u/f45/11/95/68/21/screen12.jpg[/img]](http://www.servimg.com/image_preview.php?i=51&u=11956821)

I have installed DKMS and this has made no difference. Any help would be greatly appreciated.

Thank you in advance.

---

### Post by PhantomTurtle on 2012-05-12
So you ran
```
sudo /etc/init.d/vboxdrv setup
```
? (you weren't too clear on that)
I have had this too (and with my XP vmachine as well). Running that command, which recompiles the kernel driver, fixed it for me.

---

### Post by chrispche on 2012-05-12
Yes I ran that. It quite clearly shows in the code I posted.

---

### Post by SeijiSensei on 2012-05-12
> Please install the linux-headers-3.0.0-17-generic package

You need to do what the instructions say, install that package.  Then run "sudo /etc/init.d/vboxdrv setup".  If you still get errors make sure you've installed the build-essential package as well so you'll get the compiler and associated files.

---

### Post by PhantomTurtle on 2012-05-12
> **chrispche said:**
> Yes I ran that. It quite clearly shows in the code I posted.

Oh yes you have, I'm completely blind(sorry about that).

---

