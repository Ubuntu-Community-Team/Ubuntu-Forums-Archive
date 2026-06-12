---
title: "Install hangs on &quot;Prepare Disk Space&quot; Partition Resizing"
date: 2006-06-04
forum: General Help
---

### Post by krackato on 2006-06-04
I've been trying to install Ubuntu (btw, I can't believe I can surf the internet while installing an operating system... that completely blows my mind).

I have a 250gb Maxtor drive that I already had partitioned to a 40gb C: drive for Windows XP and a 210gb D: drive for just data.  I had about 10-15gb free on the C: drive so I wanted to repartition the C: drive to dual boot windows and Ubuntu.  I figured I could probably delete the Linux partition and revert back to my original system if I wanted to.

I was installing Ubuntu but after clicking next a few times, I arrived at the "Prepare Disk Space" window and was asked "How do you want to partition the disk?"  I selected the "Resize IDE1 master, partition #1 (hda1) and use freed space" option, set the New partition size to 50% (8.7gb) and clicked next.  That was like 7 hours ago.:confused:   

The mouse icon, when focused on the prepare disk space window, shows the spinning icon.  I've switched to the process monitor by press Ctrl+Alt+F6 and it shows that partman is running and using 4.6% of the the cpu, which I'm guessing means that Ubuntu is repartitioning the drive.  I don't see a status bar in the Installer GUI, so if I didn't know how to pull up the process manager I would have thought Ubuntu had just hanged.  I'm very, very hesistant to hit cancel obviously since I don't want to destroy my Windows system.  Is it normal for a repartition to take this long?

---

### Post by mejy on 2006-06-04
[QUOTE=krackato]I've been trying to install Ubuntu (btw, I can't believe I can surf the internet while installing an operating system... that completely blows my mind).

I have a 250gb Maxtor drive that I already had partitioned to a 40gb C: drive for Windows XP and a 210gb D: drive for just data.  I had about 10-15gb free on the C: drive so I wanted to repartition the C: drive to dual boot windows and Ubuntu.  I figured I could probably delete the Linux partition and revert back to my original system if I wanted to.

I was installing Ubuntu but after clicking next a few times, I arrived at the "Prepare Disk Space" window and was asked "How do you want to partition the disk?"  I selected the "Resize IDE1 master, partition #1 (hda1) and use freed space" option, set the New partition size to 50% (8.7gb) and clicked next.  That was like 7 hours ago.:confused:   

The mouse icon, when focused on the prepare disk space window, shows the spinning icon.  I've switched to the process monitor by press Ctrl+Alt+F6 and it shows that partman is running and using 4.6% of the the cpu, which I'm guessing means that Ubuntu is repartitioning the drive.  I don't see a status bar in the Installer GUI, so if I didn't know how to pull up the process manager I would have thought Ubuntu had just hanged.  I'm very, very hesistant to hit cancel obviously since I don't want to destroy my Windows system.  Is it normal for a repartition to take this long?[/QUOTE]
If its finished now ignore this post.  However with the betas, if the installer hung you could often repartition the disk by going to system->administration->gparted and resizing things to leave some free space for ubuntu, and then choosing to use the largest available free space in the installer.  If that doesn't work, you could always try the install cd.

---

### Post by harshad on 2006-07-30
Has anybody found a better solution to this problem?

My machine has hung up on "Prepare Disk Space", Step 5. It's not hung up in the Windows sense where I can't do anything. But the installer's spinning icon has been visible on this step for over 45 minutes.

I have had several bad experiences with Linux installations in the past. It always seems to come down to "Why don't you manually partition the disks?" A task that 99.999% of computer users can't / will not do when they fear losing precious data on the machine.

I was hoping for better from Ubuntu but unfortunately even Ubuntu installation has got stuck on the scariest step where I could lose 10s of GBs of data on Windows. 

I have backups but that does not mean that the installer should ignore user concerns about data loss. 

Many people try out Linux as a dual boot with Windows , get irritated and leave Linux alone. 

Linux enthusiasts are welcome to be die-hard users and Windows haters but as long as Linux installation with Windows aren't as safe and simple as say installing a browser on Windows, Linux will not do justice to its potential.

Anyway, I tried one solution of unplugging USB devices as suggested at [http://www.evolutionnext.com/blog/2006/06/27/1151429024151.html]("http://www.evolutionnext.com/blog/2006/06/27/1151429024151.html") but unfortunately that trick didn't work in my case. I am pretty much stuck now. Can't click Cancel as I fear I will lose data.

---

### Post by harshad on 2006-07-30
Clicked Cancel. Although the Ubuntu instllation bombed, at least Windows and my data looks alive and well.

However on again trying to boot from the Ubuntu CD, the process gets stuck at the line

Uncompressing Linux... Ok, booting the kernel.

So it looks like my Ubuntu adventure is over, at least for the time being.

If you have any suggestions on the problems noted above. Please do share as I am keen on moving to Linux and Ubuntu looks like my best bet.

---

### Post by harshad on 2006-08-02
Just posting in case my experience helps someone out.

The freeze on getting the line Uncompressing the kernel disappeared for unknown reasons when I tried the next day.

AS regards the hang on reaching the Prepare Disk Space page, I think the remove USB devices trick worked. It did not work right wy but worked on restart.

Ubuntu after that installed without any issues.

Minor issues:
1) I had to mount the windows drives manually
2) OpenOffice just wouldn't work initially. But after I downloaded all the recent patches, it started working.

Still facing issues with:
1) sharing folders to make them accessible from windows machines. Keeps asking for a password that I have not at all configured.

---

