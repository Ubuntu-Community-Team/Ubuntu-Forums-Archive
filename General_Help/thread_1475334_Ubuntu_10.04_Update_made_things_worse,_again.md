---
title: "Ubuntu 10.04 Update made things worse, again"
date: 2010-05-06
forum: General Help
---

### Post by jschille on 2010-05-06
Ugg. Ubuntu I loved you so much and never had a problem with you and since 10.04 I am thinking about removing Ubuntu.

When I first installed 10.04 I had a handful of problems on the Ubuntu side (which I have fixed and are still fixed), but on my Window's side whenever I tried to log into Windows it would just get stuck in a loop on the Window's Loading screen.

I would be forced to force shut down.  Turn system back on and choose the Windows partition again where it would take me to some Windows Repair.  Window's repaired itself and both partitions worked.

Just today I downloaded the new updates for 10.04 and AGAIN my windows partition won't work.  Is there a reason for the Ubuntu updates to make my Window's partition not work?

Any help would be much appreciated.

Edit: I forget to mention.  I have to turn windows updates OFF because whenever I download an update and try to restart it will freeze again at bootup.

---

### Post by OldGoat58 on 2010-05-06
Forgive me, I'm really not trying to be disrespectful, but I learned a long time ago that a slave cannot serve 2 masters.  I have never dual booted personally, and I'm sure someone will have the answer to your problem, but Ubuntu will do anything Windows will do so I don't really see the need.  That is purely my opinion.

Mike
Fairless Hills, PA

](*,)

---

### Post by jschille on 2010-05-06
> **OldGoat58 said:**
> Forgive me, I'm really not trying to be disrespectful, but I learned a long time ago that a slave cannot serve 2 masters.  I have never dual booted personally, and I'm sure someone will have the answer to your problem, but Ubuntu will do anything Windows will do so I don't really see the need.  That is purely my opinion.

Mike
Fairless Hills, PA

](*,)


Im currently in law school and the ONLY time I use windows is for exam purposes because we are required to use a program called Exam Soft which can ONLY run on windows, no mac os or linux.  Finals are coming up this week and stressing over Ubuntu messing up my computer (for the first time in over a year) is the last thing i need.

---

### Post by TheNerdAL on 2010-05-06
You can always use virtual box.

---

### Post by jschille on 2010-05-06
I appreciate the recommendations.  
Instead of ways of working around this issue though, is there any ideas on what the problem could be?

---

### Post by jbrown96 on 2010-05-06
I'm guessing that your NTFS partition has some problem. Microsoft has the best drivers, obviously, and can work around the problem, but the Ubuntu drivers are having problems. 

The output of ```
sudo fdisk -l
``` would be helpful.

Does this only happen when you mount your Windows partition? If it automounts, then it would be a good idea trying to disable it. If there is no problem when its not mounted and you need access to files, then maybe doing a read-only mount would be worth trying. 

What version of Windows? When you installed Ubuntu (even before 10.04), did you resize the Windows partition?
Does Windows give any specific error messages? Try checking the Event Viewer and see if there's any error codes or anything.

---

### Post by jbrown96 on 2010-05-06
I work IT at my Uni's law school, and I hate those exam programs. We use Exam4, and I've spent the past two weeks fixing computers so it will run.

---

### Post by jschille on 2010-05-07
> **jbrown96 said:**
> I'm guessing that your NTFS partition has some problem. Microsoft has the best drivers, obviously, and can work around the problem, but the Ubuntu drivers are having problems. 

The output of ```
sudo fdisk -l
``` would be helpful.

Does this only happen when you mount your Windows partition? If it automounts, then it would be a good idea trying to disable it. If there is no problem when its not mounted and you need access to files, then maybe doing a read-only mount would be worth trying. 

What version of Windows? When you installed Ubuntu (even before 10.04), did you resize the Windows partition?
Does Windows give any specific error messages? Try checking the Event Viewer and see if there's any error codes or anything.

Hey, thanks for the response.  Here is fdisk -l

```

jb@jb-laptop:~$ sudo fdisk -l
[sudo] password for jb: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf7c0c486

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1918    15360000    7  HPFS/NTFS
/dev/sda3   *        1918       47728   367967024    7  HPFS/NTFS
/dev/sda4           47729       60801   105008872+   5  Extended
/dev/sda5           47729       60264   100695388+  83  Linux
/dev/sda6           60265       60801     4313421   82  Linux swap / Solaris
```

When I first installed Ubuntu I did take away from the Windows partition because I think the entire hard drive was allocated to it. 

It happened the first time I tried logging into Windows after installing 10.04 and then each time after installing an update after Windows Recovery ran.  The first time loading Windows (running Vista) it would just sit on the Loading Window's screen, id force shut down, restart, then it would take me to Windows Recovery.

And now that I have installed the 10.04 update my Wireless connection is going out every 10 mins or so and I have to reconnect. Ug.

In regards to the law application: Will virtual box fix allow me to lose the window's partition and run Exam Soft?

Appreciate the help!

---

### Post by longanduselessname on 2010-05-07
> **jschille said:**
> Hey, thanks for the response.  Here is fdisk -l

In regards to the law application: Will virtual box fix allow me to lose the window's partition and run Exam Soft?

Appreciate the help!

Yes. Install windows as a virtual machine and you have a full, if slower, windows os. 

Or you can have some fun and try running the software in WINE!

---

### Post by john newbuntu on 2010-05-07
I get the feeling that you are using the Windows partition (probably /dev/sda2) as the linux bootsector.  To verify this, please follow the procedure to download and run the boot info script courtesy of our forum member meierfra.  Boot from the Ubuntu liveCD/liveUSB and choose "Try ubuntu without any changes".
Then open a browser window and go to: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Download and run the boot_info_script and post the output.

---

### Post by jschille on 2010-05-07
> **john newbuntu said:**
> I get the feeling that you are using the Windows partition (probably /dev/sda2) as the linux bootsector.  To verify this, please follow the procedure to download and run the boot info script courtesy of our forum member meierfra.  Boot from the Ubuntu liveCD/liveUSB and choose "Try ubuntu without any changes".
Then open a browser window and go to: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Download and run the boot_info_script and post the output.

I would follow your instructions but my wireless connection continually is dropping on ubuntu right now so I am using the window's partition.  I can tell you though when Grub loads it states Window's is using /dev/sda3

Hope that helps.

---

### Post by john newbuntu on 2010-05-07
Ok, till you get your internet up and running, can you please post the output of:

```
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub
sudo blkid -c /dev/null
grub-install -v
```For your wireless issue, see if changing mtu helps:
```
sudo ifconfig eth0 mtu 1492
```If this does not help, choose a different kernel on startup and see if that helps.

---

### Post by jbrown96 on 2010-05-07
longanduselessname is wrong. Exam Soft will not work in Virtualbox.
No, that exam software is designed specifically to not be run in virtualized environments. They have extensive security features, so they can lock down the computer and keep you from cheating and will easily detect a virtualization. 

Since Vista, Windows always creates two partitions. /dev/sda2 is a small boot sector that is automatically created. It's usually ~100MB; don't mess with it. /dev/sda3 is your Vista installation. 

Check /etc/fstab and see if either /dev/sda2 or /dev/sda3 are listed in it. ```
cat /etc/fstab
``` If so, then place a # at the beginning of those lines using a text editor like nano ```
sudo nano /etc/fstab
``` I don't use Gnome, so I'm sure how to keep it from auto-mounting those partitions. Perhaps, someone else can post some instructions. 
After you get that taken care of, then reboot to make sure they don't automount (check with ```
mount -l
```). Once you are sure they are not automounting, then boot into Windows and let it do its repair procedure. After it's all fixed, then reboot into Ubuntu and back to Windows. Does it have to repair again? Post back the results.

---

### Post by rnerwein on 2010-05-07
hi
same problem - i post it 4 days ago but no answer ( search for: grub2 - the never ending story ).
but i know whats going on ( i am running lucid lynx LTS ).
here in short is my fstab:
[COLOR=Red]/dev/sda1[/COLOR] 1 1828 14680064 27 Unbekannt ( system recovery i think )
/dev/sda2 * 1828 46484 358701056 7 HPFS/NTFS __________ ( vista C: )
/dev/sda3 46484 58566 97046524 7 HPFS/NTFS __________ ( vista D: )
/dev/sda4 58567 91201 262140607 f W95 Erw. (LBA)
/dev/sda5 58567 58828 2104483+ 82 Linux Swap / Solaris
/dev/sda6 58829 61439 20972826 83 Linux 
/dev/sda7 61440 70425 72180013+ 83 Linux
.....
as you can see /dev/sda1 is unknown ( it's the recovery stuff that was installed by default )
and here is my grub entry for vista:
menuentry "Windows Vista (loader) (on /dev/sda1)" {
insmod ntfs
[COLOR=Red]set root='(hd0,1)'[/COLOR]
search --no-floppy --fs-uuid --set 2820378c2037604c
chainloader +1
}
as you see it points to /dev/sda1 ( hd0,1 ) --> that will never work vista is at /dev/sda2 !
chaged my grub and everythink is ok.
ciao

---

### Post by jschille on 2010-05-07
> **john newbuntu said:**
> Ok, till you get your internet up and running, can you please post the output of:

```
sudo grub-probe -t device /boot/grub
        **/dev/sda5**
sudo grub-probe -t fs_uuid /boot/grub
       **75d59b76-ab9f - 4260 - 94a3 - 42d24bc1a280**
sudo blkid -c /dev/null
      [B]/dev/sda1: msdos  DellUtilitity vfat
      /dev/sda2: LABEL = "RECOVERY"  ntfs
      /dev/sda3: LABEL = "OS"  ntfs
      /dev/sda5: UUID = [/B]**75d59b76-ab9f - 4260 - 94a3 - 42d24bc1a280**    [B]ext3
     /dev/sda6:
[/B] grub-install -v
    **(GNU GRUB 1.98 -lubuntu6)**

```For your wireless issue, see if changing mtu helps:
```
sudo ifconfig eth0 mtu 1492
```If this does not help, choose a different kernel on startup and see if that helps.

[B]Changing the MTU did nothing.  I now have no wireless connection.  When clicking on wireless connections no connections are even shown.  This happened after running the command 
[/B]```

sudo apt-get install linux-backports-modules-wireless-lucid-generic

```

---

### Post by jschille on 2010-05-07
> **jbrown96 said:**
> longanduselessname is wrong. Exam Soft will not work in Virtualbox.
No, that exam software is designed specifically to not be run in virtualized environments. They have extensive security features, so they can lock down the computer and keep you from cheating and will easily detect a virtualization. 

Since Vista, Windows always creates two partitions. /dev/sda2 is a small boot sector that is automatically created. It's usually ~100MB; don't mess with it. /dev/sda3 is your Vista installation. 

Check /etc/fstab and see if either /dev/sda2 or /dev/sda3 are listed in it. ```
cat /etc/fstab
``` If so, then place a # at the beginning of those lines using a text editor like nano ```
sudo nano /etc/fstab
``` I don't use Gnome, so I'm sure how to keep it from auto-mounting those partitions. Perhaps, someone else can post some instructions. 
After you get that taken care of, then reboot to make sure they don't automount (check with ```
mount -l
```). Once you are sure they are not automounting, then boot into Windows and let it do its repair procedure. After it's all fixed, then reboot into Ubuntu and back to Windows. Does it have to repair again? Post back the results.

Thanks for the help so far!
I ran the command ```
 cat /ect/fstab
``` 
and only sda5 and 6 show up and both have #'s infront of them.

---

### Post by jbrown96 on 2010-05-07
> **jschille said:**
> Thanks for the help so far!
I ran the command ```
 cat /ect/fstab
``` 
and only sda5 and 6 show up and both have #'s infront of them.

What about ```
mount -l
``` That will tell you if they are mounted.

---

### Post by jschille on 2010-05-07
```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc  (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jb/.gvfs type fuse.gvfs-fuse-daemon  (rw,nosuid,nodev,user=jb)

```
Going to post my boot log right after this.  Just noticed that when Grub  starts my Window's partition states "Window's Recovery Environment"

---

### Post by jschille on 2010-05-07
```


                                 Boot Info Script 0.55    dated February 15th, 2010                     
 ============================= Boot Info Summary ==============================   

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #5 for /boot/grub.  

sda1: _________________________________________________________________________     

  File system:       vfat     
  Boot sector type:  Dell Utility: Fat16     
  Boot sector info:  No errors found in the Boot Parameter Block.     
  Operating System:      
  Boot files/dirs:   /COMMAND.COM  

sda2: _________________________________________________________________________      

   File system:       ntfs     
   Boot sector type:  Windows Vista/7     
   Boot sector info:  No errors found in the Boot Parameter Block.    
  Operating System:  Windows Vista     
  Boot files/dirs:   /Windows/System32/winload.exe  

sda3: _________________________________________________________________________      

   File system:       ntfs     
   Boot sector type:  Windows Vista/7     
   Boot sector info:  No errors found in the Boot Parameter Block.     
   Operating System:  Windows Vista    
  Boot files/dirs:   /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD                        
                         /Windows/System32/winload.exe                         
                        /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 

 sda4: _________________________________________________________________________      

      File system:       Extended Partition    
      Boot sector type:  -     
      Boot sector info:    

sda5: _________________________________________________________________________      
 
     File system:       ext3     
     Boot sector type:  -     
     Boot sector info:       
     Operating System:  Ubuntu 10.04 LTS     
     Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab                         
                             /boot/grub/core.img  

sda6: _________________________________________________________________________      

   File system:       swap     
   Boot sector type:  -     
   Boot sector info:   

 =========================== Drive/Partition Info: =============================  

Drive: sda ___________________ _____________________________________________________ 

Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders,
 total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical):
 512 bytes / 512 bytes  Partition  Boot         Start           End          Size  Id System  /dev/sda1
                  63        80,324        80,262  de Dell Utility /dev/sda2              80,325    30,800,324  
  30,720,000   7 HPFS/NTFS /dev/sda3    *     30,800,325   766,734,372   735,934,048   
7 HPFS/NTFS /dev/sda4         766,750,320   976,768,064   210,017,745   5 Extended /dev/sda5 
        766,750,383   968,141,159   201,390,777  83 Linux /dev/sda6         968,141,223   976,768,064 
    8,626,842  82 Linux swap / Solaris   blkid -c /dev/
null: ____________________________________________________________  
Device           UUID                                   TYPE       LABEL                           /dev/sda1        3030-3030                           
   vfat       DellUtility                    /dev/sda2        6A346D70346D4065                       ntfs       RECOVERY                    
   /dev/sda3        46686F9A686F878F                       ntfs       OS                             /dev/sda4: PTTYPE="dos"  /dev/sda5      
  75d59b76-ab9f-4260-94a3-42d24bc1a280   ext3                                    
  /dev/sda6        5108b146-fc4b-4920-b330-1ff8b5df4a37   swap                                   
   /dev/sda: PTTYPE="dos"  

```Hope this can help someone. Ug, I feel so defeated :(

---

### Post by jbrown96 on 2010-05-07
I'd say that this is a Windows problem. If Ubuntu isn't mounting your NTFS drives, then it can't be causing the problem. 
I think that if you can fix your auto-update problem in Windows, then this will stop happening. 

The first thing that I would try is to do a recovery install in Vista. This won't mess up any of your programs or files. Boot from your Vista DVD or access your recovery partition (usually F9 during boot). 
If that doesn't work, then try using Microsoft's [MBSA]("http://en.wikipedia.org/wiki/Microsoft_Baseline_Security_Analyzer") to download the updates with out Win Updater. 

I just don't think that Ubuntu is causing this problem, and even if it is causing the symptoms, there's not really anything that can be done from Ubuntu to fix it.

---

### Post by john newbuntu on 2010-05-08
There should be more info in the RESULTS.txt file since what is posted here is clipped version of it.  The full output would have shown the details of a file called /boot/grub/grub.cfg which would have given insight into your problem booting windows.  But that part is missing from your output.  If you can, please post the complete output.

The boot info script output says that you also have a WUBI install of ubuntu.  I suppose we are not talking about that in this discussion.  Correct?  If you are not using WUBI, get rid of it by going to "add and remove programs" in windows.

Because of the presence of menu.lst in the boot partition on /dev/sda5, it is also likely that you have legacy grub or remnants of it in your system.   Although I do not think this would cause any problems in Windows.  Open synaptic package manager (system->admin->synaptic) and seach for grub and see if the package "grub" is installed.

I do not understand why a windows update would mess the windows boot sector or installation.  However, I would recommend you to do chkdsk on all your NTFS partitions just to make sure those are ok.

---

