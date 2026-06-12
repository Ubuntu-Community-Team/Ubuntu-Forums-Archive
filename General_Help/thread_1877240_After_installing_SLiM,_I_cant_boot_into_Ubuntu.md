---
title: "After installing SLiM, I cant boot into Ubuntu"
date: 2011-11-07
forum: General Help
---

### Post by llamas612 on 2011-11-07
I recently installed the SLiM login manager, and on the first boot after install, my computer stays at a black screen after I chose to boot to ubuntu in GRUB. Obviously something must've gone wrong when I installed SLiM, but I didn't get any errors, so I'm not sure what it could be. I installed it from the repos. 

I would prefer to get SLiM working, but I'm not against going back to GDM if SLiM isn't workable. I just want to be able to login again.

I'm running Ubuntu 10.10, by the way.

---

### Post by utnubuuser on 2011-11-07
It's fairly easy to get into a system if you're not afraid to use grub commands.  I'm not saying this will fix your problem, though if you can't get in by usual means, you can get to a grub command by pressing c when you're at the grub menu.  

And here is a link on how to boot an OS manually:[http://sazeit.com/articles/boot-ubuntu-from-grub-prompt]("http://sazeit.com/articles/boot-ubuntu-from-grub-prompt")

You'll see at the bottom of the tutorial that you don't need a lot of information to start, since the "ls" command together with TAB can help you to find your partition and kernel/initrd version.

Just remember, when using TAB to give grub as much information as possible, ie: "linux /boot/vm" instead of just "linux /boot/" or "linux /boot.

...then fix SLIM once you're in, or use Boot Repair to fix grub. Boot Repair:[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair]("http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair")

You can also boot a liveCD and use Boot Repair to straighten out your grub setup

---

### Post by llamas612 on 2011-11-08
Thanks for the quick reply, but i think i misstated my problem.

There aren't any problems with grub, as the machine boots fine. The problem is, it hangs on the part when i get to the Login Manager. It just says "Starting X display manager: slim", and doesn't go past that.

---

### Post by jacob.david on 2011-11-08
Try alt+F2 which should get you to a command prompt and run the following
sudo dpkg-reconfigure gdm

---

### Post by jacob.david on 2011-11-08
Actually Press ‘Ctrl + Alt + F1&#8242; to go to the console mode and then execute the above command.

---

### Post by llamas612 on 2011-11-08
Ok i figured it out. [This]("http://ubuntuforums.org/showthread.php?t=1780508") thread helped me. Basically, i had to use the recovery console to drop to the command line. Then i just typed GDM, and it brought me to the GDM screen. Once i logged in, i removed SLiM and then ran 

sudo dpkg-reconfigure gdm 

to restore GDM. I still dont know whats wrong with SLiM though, but i guess thats for another day.

---

### Post by llamas612 on 2011-11-08
Hah, i didn't see your reply jacob.david.

Thanks for the info

---

