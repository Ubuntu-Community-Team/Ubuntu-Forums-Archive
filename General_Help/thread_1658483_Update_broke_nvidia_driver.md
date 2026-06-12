---
title: "Update broke nvidia driver"
date: 2011-01-02
forum: General Help
---

### Post by Dans564 on 2011-01-02
Latest update broke nvidia driver. It's happened twice today on two new installs. It happened both installing driver first then update, and update then driver. Now on reboot I get text only mode.

---

### Post by Hippytaff on 2011-01-02
When you get to the bit of the boot where you get to choose OSes and kernels (assuming your dual booting?) highlight ubuntu and press e. change (I think it says) default splash (definitely something splash) to nomodeset. then press CTRL+X to boot. if you get into ubuntu reinstall the recommended nvidia driver.

---

### Post by Dans564 on 2011-01-02
The grub menu never shows up. How do I get the grub menu?

---

### Post by Hippytaff on 2011-01-02
try pressing shift during boot

---

### Post by Dans564 on 2011-01-02
Did the nomodeset thing and although I now have verbose mode boot, I still only get text after boot

---

### Post by Dans564 on 2011-01-02
So I was able to get x to start in fail-safe mode. I then uninstalled the nvidia driver, rebooted, then installed them again...... And still I have only text after boot.

---

### Post by pqwoerituytrueiwoq on 2011-01-02
using the built in driver installer or a manual install from the run file on nvidia's site?
i have to reinstall the driver after a kernel version update (using nvidia's file)

---

### Post by Dans564 on 2011-01-02
nope im using the ubuntu driver manager version not the nvidia run file.  Im in failsafe right now with a lowres desktop so this might be easier then fixing in text mode only.  Are there any logs that i can post to help u guys... well help me?

---

### Post by pqwoerituytrueiwoq on 2011-01-02
your xorg.conf file may have been screwed up
you can check a backup
ls /etc/X11

---

### Post by Dans564 on 2011-01-02
> **pqwoerituytrueiwoq said:**
> your xorg.conf file may have been screwed up
you can check a backup
ls /etc/X11

no i dont think so cause i have ran ```
sudo nvidia-xconfig
``` and rebooted without anyluck

---

### Post by celldweller1591 on 2011-01-02
if xorg.conf is the problem then it can be replaced simply with the contents of the xorg.cong.bak file. !

---

### Post by Dans564 on 2011-01-02
> **Dans564 said:**
> no i dont think so cause i have ran ```
sudo nvidia-xconfig
``` and rebooted without anyluck
I dont think that xorg.conf is the problem, its got to be something else cause if it were broken running the command above would have fixed it. :(

---

### Post by Dans564 on 2011-01-02
pleaaaasssseeeee people.  i need this comp for school tomorrow.:confused:

---

### Post by pqwoerituytrueiwoq on 2011-01-02
if this is a desktop you can do what i did with xubuntu since the nvida driver make it so i could not login i purged the system of nvidia drivers and replaced xorg.conf with the failsafe copy
i removed the nvidia card since the integrated card works better can the nvidia card with the driver

---

### Post by Dans564 on 2011-01-03
thanks for the solution but mine is a custom built system, i dont have an integrated gpu, only my two GTX 460's.  There has to be other people that this is happening too.  
timeline:
1st)repartitioned to delete windows 7
2nd)installed ubuntu and rebooted
3rd)screen was at a low reso so i installed nvidia driver that ubuntu suggestedthrough the driver utility and then restarted 
4)after reboot screen was at max resolution and working fine
5)10mins later ubuntu said to install about 120 updates and reboot
6)reboot shows no bootsplash now and goes right into terminal only mode

remember i can still get to the gnome desktop, that is a very low resolution desktop, if i go into failsafeX mode.  I only say this because it might aid in the solution.

---

### Post by Hippytaff on 2011-01-03
The only thing I can suggest is uninstalling and reinstalling the nvidia driver...and check that the driver is not blacklisted for whatever reason (though others may already have suggested this)

---

### Post by Dans564 on 2011-01-03
after unistalling the driver system boots in low graphics mode.  I then reinstall the driver and same problem occurs.  BUT, i just realized that i can boot using the older kernel choice in grub just fine.  It is only when I use the newest kernel that the problem occurs.  Hope this gives some insight

---

### Post by cSquall on 2011-01-03
@Dans564,

Maybe I missed it further up the thread, but which kernel broke your machine? Which older kernel worked for you? I think I have the same problem with my son's comp.

Thanks!

---

### Post by Dans564 on 2011-01-03
once i realized this this mainly kernel related I made a new thread.  Ill post the kernel versions there.
[http://ubuntuforums.org/showthread.php?p=10312743#post10312743](http://ubuntuforums.org/showthread.php?p=10312743#post10312743)

---

### Post by tekkidd on 2011-01-03
That is normal when you update your kernel. Just reinstall your drivers.

---

### Post by Elfy on 2011-01-03
> **Dans564 said:**
> once i realized this this mainly kernel related I made a new thread.  Ill post the kernel versions there.
[http://ubuntuforums.org/showthread.php?p=10312743#post10312743](http://ubuntuforums.org/showthread.php?p=10312743#post10312743)

Given this I'll close now.

---

