---
title: "X startup problem"
date: 2012-02-14
forum: General Help
---

### Post by superfrank on 2012-02-14
Hi,
After upgrading my ubuntu 11.10 box on Sunday (mythbuntu) it no longer boots to the login screen so I cannot get to the desktop. What happens is the ubuntu progress screen appears for a while, then the nvidia logo briefly appears before the screen reverts to text (showing info about starting services), instead of bringing up the login screen or desktop.

I have made a youtube video of this happening here [http://www.youtube.com/watch?v=vKibc9wvrX8#t=00m38s](http://www.youtube.com/watch?v=vKibc9wvrX8#t=00m38s)

when I get to the text screen, ctrl-alt-F2/3/4/5/6 go to login prompts, ctrl-alt-F7 goes to the text screen showing service startup , and ctrl-alt-F1 does nothing.

I guess that the problem lies with the nvidia driver so I checked /var/log/X.org.0.log and there are no (EE) statements there. There is nothing relevant in the dmesg log either.

packages installed are the latest from ubuntu 11.10:
nvidia-current-dev version 280.13-0ubuntu6
linux-generic 3.0.0.16.19

Any ideas where I should look?

thanks,
frankie

---

### Post by kc1di on 2012-02-14
Only Idea I have is to try re-installing the Nvidia drivers. that last update did update the kernel so perhaps it did not correctly reload the nivida modules for the new kernel. But this is just a shot in the dark. 
good Luck

---

### Post by raja.genupula on 2012-02-14
yeah you'd  try that .
at your grub menu make a boot to  recovery mode (press & Hold shift key your system is in booting ) . then boot to failsafeX mode and from there re install your graphics drivers . 


if anything comes up , let us know . 
all the best .

---

### Post by superfrank on 2012-02-14
I've reinstalled rebuilt the nvidia-common for the most recent kernel and also all previous kernels that are installed but it does not boot to the desktop with either kernel revision 13 or revision 16.  in the process list there is a display running on :1 (instead of :0) which is a little unusual.  /usr/bin/Xorg :1 -br -verbose -auth /var/run/gdm/auth-for-gdm-Bj0JuE/database -nolisten tcp

---

### Post by superfrank on 2012-02-14
ok I did "sudo dpkg --purge lightdm gdm" then "sudo apt-get install gdm" and it worked again.

---

