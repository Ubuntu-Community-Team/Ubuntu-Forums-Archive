---
title: "Ubuntu Runs REALLY slow"
date: 2010-11-14
forum: General Help
---

### Post by Arkentos on 2010-11-14
I need help with ubuntu! I'm neew here so can someone explain this to me!
I have a computer with Intel Celeron D 2.8 GHz, 1GB RAM, NVidia GeForce 5200 128 MB,
HDD 160GB, and when I installed Ubuntu 10.10, it took about 2 min to boot, then everything that i run on it takes about a min to open, for example mozilla firefox and the software center!
Can someone help me how to make my ubuntu run faster?

---

### Post by Finalfantasykid on 2010-11-14
It is possible you have some rogue processes which are stealing all your CPU/Memory.

Could you open up a terminal and type:

```
top
```

wait a few seconds and copy the output and post it.

---

### Post by Arkentos on 2010-11-14
top - 07:32:26 up 5 min,  2 users,  load average: 0.92, 0.68, 0.34
Tasks: 128 total,   2 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.5%us, 21.2%sy,  3.6%ni, 44.7%id,  6.3%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   1025532k total,   459452k used,   566080k free,    87260k buffers
Swap:   974840k total,        0k used,   974840k free,   175728k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
62 root      20   0  106m  46m  10m S 14.6  4.6   0:38.52 Xorg               
 1378 nik       20   0 45816  13m  10m S  9.0  1.3   0:07.03 gnome-terminal     
 1219 nik       20   0 57896  35m   9m S  4.3  3.5   0:14.66 compiz             
 1354 nik       20   0  276m  55m  26m S  4.3  5.6   0:43.06 firefox-bin        
 1199 nik       20   0 89596 9840 7692 S  0.3  1.0   0:00.88 gnome-settings-    
 1426 nik       20   0  2544 1196  904 R  0.3  0.1   0:00.64 top                
    1 root      20   0  2796 1612 1168 S  0.0  0.2   0:00.50 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.02 events/0           
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                 
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers        
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default        
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.03 kblockd/0          
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_hotplug      
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.05 ata/0              
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ata_aux            
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd      
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd              
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kseriod            
   24 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kmmcd              
   27 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd         
   28 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0            
   29 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd               
   30 root      20   0     0    0    0 S  0.0  0.0   0:00.00 aio/0              
   31 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea    
   32 root      20   0     0    0    0 S  0.0  0.0   0:00.00 crypto/0           
   36 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0          
   37 root      20   0     0    0    0 S  0.0  0.0   0:00.08 scsi_eh_1   

this is what came out after i tipped TOP on the terminal
any idea?

---

### Post by Finalfantasykid on 2010-11-14
Nothing really pops out at me.  You arn't using that much memory, and other than Xorg, which is using a decent amount of CPU, there isn't anything there that would be eating all your CPU.

However it does look like you are using compiz desktop effects.  If you disable that, it might improve the overall performance of your desktop, however your boot time will probably remain unchanged, so there might be something else going on, maybe to do with your hard drive.

EDIT:

I'm not sure if this will work, but you can try to benchmark your harddrive by doing this command.

```
sudo hdparm -t /dev/sdaX
```

the X is the number of your partition.  It might also be hda something...

if you run the command 'mount' you will see a listing of all your partitions, maybe show the output of that as well.

---

### Post by Arkentos on 2010-11-14
Maybe, i got this HDD almost 4 ago!
And what will happen if i install Lightweight X11 Desktop Environment on ubuntu, will it run faster? I heard there are the lightest of all desktop environments, could that help?

---

### Post by Arkentos on 2010-11-14
and what should I run in terminal to disable the compiz desktop effects?

---

### Post by Finalfantasykid on 2010-11-14
Go to System > Preferences > Appearance

then to the Visual Effects tab, and select 'None' if it is not already selected.

EDIT: LXDE very light indeed, but I think your hardware should easily be able to handle Ubuntu, so switching to Lubuntu will probably not make much of a difference if there is something else which is creating problems.

If you do want to try it out type this:

```
sudo apt-get install lubuntu-desktop
```

Then log out, and select the Lubuntu/LXDE session.  I'm not sure how up to date the lubuntu is in the repositories though, so if it is working well for you, maybe a fresh install using the Lubuntu ISO would be better.

---

### Post by Arkentos on 2010-11-14
i turned the visuals off, and changed the theme to creamlooks and now ubuntu runs normal, no waiting, just like it should be! Thanks!
And you're right, the Lightweight X11 D.E. is nice, but i am used on the standard GNOME one!
Thx again!

---

### Post by Finalfantasykid on 2010-11-14
Is your startup time also better, or does it still take a couple of minutes?

---

### Post by Arkentos on 2010-11-14
Yeah, it takes 18 sec to startup ubuntu and run it!
What happend, i dont know, but it worked!!!!!

---

