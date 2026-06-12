---
title: "Having some problems. Please help!"
date: 2009-09-27
forum: General Help
---

### Post by pop_n_fresh on 2009-09-27
Hi, I'm new to Linux Ubuntu, I installed version 9.04 a few days ago and I think I may have screwed it up a little. I don't think I've partitioned any space on my hard drive for Ubuntu. I can't install or download anything.

When I try and install programmes through Add/Remove it displays a message saying > E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.So I can't even add the partition editor because this comes up and I don't understand it.
 
Also any time I try and transfer files from CD I get a message saying I only have 250kb of memory when I actually have about 90GB. I assume this is as a result of not partitioning any space.

Can anyone help me?

Oh and I still have Vista installed.

---

### Post by scouser73 on 2009-09-27
Open **Terminal** and paste this command: **sudo dpkg --configure -a**

---

### Post by credobyte on 2009-09-27
In Terminal:
```
sudo dpkg --configure -a
```

To fix your partitioning problem, boot from your LiveCD and do all the stuff from there ( Gpared is already installed ).

---

### Post by DougieFresh4U on 2009-09-27
Did you open terminal (Applications>Accessories>Terminal) and type
**sudo dpkg --configure -a**

---

### Post by drs305 on 2009-09-27
> **pop_n_fresh said:**
> 
Also any time I try and transfer files from CD I get a message saying I only have 250kb of memory when I actually have about 90GB. I assume this is as a result of not partitioning any space.

Can anyone help me?

Oh and I still have Vista installed.

After you have run the commands posted by others, it's time to explore your partitioning. Run the following command:
```

df -h

```

Do you mean 250KB of disk space (not memory)?

If you installed Ubuntu with the "side by side" option, and your / partition from the "df" command shows almost full (95-99%), then you do have a problem. There is a 'bug' in the installation that creates a default partition which is too small to effectively run Ubuntu. It's a bug that is being worked on.

I've written a couple of guides if this is the case. Run the command, let us know if you are out of disk space on the Ubuntu / partition, and we can go from there.

---

### Post by pop_n_fresh on 2009-09-27
It came up with
> dpkg: failed to write status record about `libxslt1.1' to `/var/lib/dpkg/status': No space left on device

---

### Post by pop_n_fresh on 2009-09-27
> **credobyte said:**
> In Terminal:
```
sudo dpkg --configure -a
```To fix your partitioning prolem, boot from your LiveCD and do all the stuff from there ( Gpared is already installed ).
By LiveCD I assume you mean the CD I loaded Ubuntu from, I tried this and looked around but couldn't find Gparted anywhere. 

Thanks for everyones help. I've been stressing about this and I'm about to start uni tomorrow. Could do without my laptop not working on top of everything.

---

### Post by credobyte on 2009-09-27
> **pop_n_fresh said:**
> By LiveCD I assume you mean the CD I loaded Ubuntu from, I tried this and looked around but couldn't find Gparted anywhere. 

Thanks for everyones help. I've been stressing about this and I'm about to start uni tomorrow. Could do without my laptop not working on top of everything.

Gparted can be found @ System / Administration / Partition editor :)

If you still can't find it, run ( Alt + F2 ):
```
gksudo gparted
```

---

### Post by fluxbuntu on 2009-09-27
Sounds like you didn't create a partition (resizing Vista) to install Ubuntu on and it tried to use the unallocated space on your drive which isn't enough. Don't know if you can resize Vista or not, but I would start by running the Gparted live cd, viewing the partitions and see if resizing is an option on that filesystem. Even then, if you can resize (shrink) Vista you need at least 5gb of spare space to install Ubuntu in. From that point it would probably be easier to reinstall Ubuntu.

---

### Post by pop_n_fresh on 2009-09-27
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 972M     0  972M   0% /lib/init/rw
varrun                972M  108K  972M   1% /var/run
varlock               972M     0  972M   0% /var/lock
udev                  972M  152K  972M   1% /dev
tmpfs                 972M   84K  972M   1% /dev/shm
lrm                   972M  2.4M  970M   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M  412K  612K  41% /tmp

Is the df -h results. I assume this will make sense to someone out here:)

---

### Post by drs305 on 2009-09-27
> **pop_n_fresh said:**
> By LiveCD I assume you mean the CD I loaded Ubuntu from, I tried this and looked around but couldn't find Gparted anywhere. 

Thanks for everyones help. I've been stressing about this and I'm about to start uni tomorrow. Could do without my laptop not working on top of everything.

To start Gparted, go to the main menu: System, Administration, Partition Editor (it's now GParted if running Karmic).

---

### Post by fluxbuntu on 2009-09-27
Oh, and do fdisk -l in terminal and post the results here.

---

### Post by fluxbuntu on 2009-09-27
> **pop_n_fresh said:**
> Is the df -h results. I assume this will make sense to someone out here:)

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /

sda5 is probably your installed partition and this tells you it is full at 100%. you have no room to do anything. Gparted live cd is a small os that boots from cdrom, mounts your disks, and can resize or otherwise setup partitions. It isn't your Ubuntu install cd but it works the same way. Go to their website, download it, burn it, and boot from it. Then see if you can adjust (shrink/expand) your partitions.

---

### Post by drs305 on 2009-09-27
If the results look like this:
> 
Filesystem            Size  Used Avail Use% Mounted on 
**/dev/sda5 2.3G 2.3G 0 100% /**

There is a bug in Jaunty and Karmic in the installation process Step 4 (Partitioning). If you chosse "side by side" with Windows you must adjust the slider on the partition bar at the bottom of the page. If you don't,  a default size of approximately 2.5 GB is used. This is not large enough to support a normal Ubuntu installation. 
Here is a pic of the slider, but please go to the posts that provide more detail:
[Step 4 Graphic]("http://ubuntuforums.org/attachment.php?attachmentid=121997")


With a 2.5GB partition, you have two choices: 
Reinstall and manually select a larger partition size for Ubuntu  (*Minimum* recommended is 8 GB).
Resize your existing partitions, taking space from Windows or another partition and adding it to Ubuntu's / partition. 
Both can take about the same amount of time, depending on your download speeds when updating the files.

To reinstall and resize the default selection in Step 4:
[2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")


To expand the existing Ubuntu / partition by taking space from your Windows installation (or another partition):
[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")


If your partition is larger than 8GB but you don't know why it is full:
[Disk Space Problems & Solutions]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by pop_n_fresh on 2009-09-27
You are all generous and loving gods/goddesses. :P

Thank you.

---

### Post by pop_n_fresh on 2009-09-27
There was me thinking it would all be simple. So I've downloaded the GParted .iso and put it on a CD but I don't know how to open it from the CD. It's not exactly obvious. So what do I do?

Sorry about being completely useless.

---

### Post by drs305 on 2009-09-27
> **pop_n_fresh said:**
> There was me thinking it would all be simple. So I've downloaded the GParted .iso and put it on a CD but I don't know how to open it from the CD. It's not exactly obvious. So what do I do?

Sorry about being completely useless.

Can you use the LiveCD. GParted is available on the LiveCD as well via System, Administration, Partition Editor (or GParted in Karmic).

Is your BIOS set up to boot from a CD before it selects the hard drive? If not, you would have to enter your BIOS during boot (pressing the DEL key or one of the F keys depending on your system) and change it.

Does the Gparted CD boot? If it was burned correctly it should boot to a menu.

---

### Post by pop_n_fresh on 2009-09-28
Thank you all for your help. In the end I just reinstalled Ubuntu and got rid of Windows. I don't think I have much use for it anyway :P

---

