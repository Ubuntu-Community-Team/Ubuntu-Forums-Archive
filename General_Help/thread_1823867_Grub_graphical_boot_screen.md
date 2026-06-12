---
title: "Grub graphical boot screen"
date: 2011-08-12
forum: General Help
---

### Post by ti-prgmr on 2011-08-12
Hey,
I have Ubuntu 11.04 and I was wondering if its possible to do what the person did here:

[IMG]http://www.j6o3s6e.com/blog/wp-content/uploads/2006/08/Capture-ubugrey.png[/IMG]
i have grub version 1.99~rc1-13ubuntu3
what are the steps to take, or is there an app that can do this for me?
or is this even possible on ubuntu 11.04?

---

### Post by drs305 on 2011-08-12
Take a look at forum member *towheedm's* Grub Theming thread. It takes some time to go through the entire downloadable guide, but it will produce the image you posted:
[http://ubuntuforums.org/showthread.php?t=1534689]("http://ubuntuforums.org/showthread.php?t=1534689")

In a day or so I'll be posting a "Grub 2 Theme" thread similar to the Conky and Monthly Screenshot threads in the Community Forums, which may provide simple theme.txt examples which you will be able to use. I'll put the link in this post when I create it.

---

### Post by ti-prgmr on 2011-08-12
Cool, thanks for the speedy reply. I'll try the guide, and check back for the link.

---

### Post by drs305 on 2011-08-12
Here is the link. The example I posted is *very* basic, but it's a start if you find the Theming Guide a bit too overwhelming to start with.

[Post Your Grub 2 Themes]("http://ubuntuforums.org/showthread.php?t=1823915")

---

### Post by raja.genupula on 2011-08-12
i have tried burg . this is also good .

---

### Post by drs305 on 2011-08-12
> **raja.genupula said:**
> i have tried burg . this is also good .

BURG was a great in advancing bootloader themes. I never used it but followed its use by others. I have seen numerous reports that its creator no longer is supporting BURG, which is really too bad.

The good part is that much of BURG translates to GRUB and those users who became familiar with BURG are now able to share what they learned with GRUB users as GRUB expands its theming capabilities.

---

### Post by raja.genupula on 2011-08-12
dont mind if it is silly 
i have installed 11.04 first and 10.04 after 11.04 . is it possible to make the grub of 11.04 as primary . i mean in booting i wanna move with grub.cfg of 11.04 .

               is it possible ? 

thanks in advance

---

### Post by ti-prgmr on 2011-08-13
thanks! i was just getting to where i could setup my vbox for ubuntu 11.04. I'll try the guide first, and if its too hard, i'll copy and paste the theme txts in your thread.

---

### Post by drs305 on 2011-08-13
> **raja.genupula said:**
> dont mind if it is silly 
i have installed 11.04 first and 10.04 after 11.04 . is it possible to make the grub of 11.04 as primary . i mean in booting i wanna move with grub.cfg of 11.04 .

Yes, you can make the 11.04 Grub primary by booting into that OS and then running:
```
sudo grub-install /dev/sdX
```
"sd**X**" would be the first BIOS boot drive (sda, sdb, etc). Do not include a partition number.

If you want the default OS *selected* to be from 10.04, you will need to edit the 11.04 /etc/default/grub file or use something like Grub Customizer (see signature link). The default entry will be to boot 11.04, so you need to change the default to point to your 10.04 OS.

---

### Post by raja.genupula on 2011-08-13
hey sorry , actually i had reposted my issue as a new thread and got solved .thanks for your help.

---

