---
title: "One or more of the mounts listed in /etc/fstab/ cannot yet be mounted (Karmic)"
date: 2009-10-30
forum: General Help
---

### Post by lviggiani on 2009-10-30
Hi everybody,
I'm opening a new thread as here
[http://swiss.ubuntuforums.org/showthread.php?p=8178645](http://swiss.ubuntuforums.org/showthread.php?p=8178645)
because it looks like that other people is still dealing with this problem.
I did a fresh installation of Karmic with single boot, no encryption. Full disk to Karmic.
During boot I get the message
```
One or more of the mounts listed in /etc/fstab
```

I also checked this post
[http://swiss.ubuntuforums.org/showpost.php?p=8175228&postcount=14](http://swiss.ubuntuforums.org/showpost.php?p=8175228&postcount=14)
and mountall is 1.0 but the problem still persist.
Since I'm not the only one having it and I have installed the offical release of Karmic (not beta or rc) and it is up to date, IMHO this thread should stay open until a workaround or a solution by Ubuntu team is available.
Thanks is advance for any help!

---

### Post by fab.head on 2009-10-30
Same issue here.

I did a fresh install of Karmic and now I get the "One or more of the mounts listed in /etc/fstab" message at boot.

---

### Post by slibuntu on 2009-10-30
I get the same error, it seems harmless, as my laptop boots fine afterwards, but what is causing it? What check is done that throws this error, why is it an error? 

Hopefully, since Ubuntu is Open Source, we'll be able to get answers to these questions!

---

### Post by wcorey on 2009-10-31
Upon an in-place upgrade from 9.04 my machine shut off when I rebooted I received

One or more mounts listed in /etc/fstab cannot yet be mounted

/ : waiting for /dev/disk/b4-uuid/.......
/tmp : waiting for null
/swap : waiting for uuid.......

It will not boot at all beyond this.

The first two upgrades (laptop 32bit and desktop alternate lvm) went flawlessly.
This last one won't boot. 

How can I fix it or, at least, save existing / mount?

---

### Post by Leed on 2009-11-01
I get this message to, listing all my partitions.... 

and it takes terribly long to boot, I'm really not happy with this change, it takes at least a minute longer than to boot with jaunty. 

The rumours were that karmic should be faster

---

### Post by user1024 on 2009-11-01
Following a fresh install of Karmic I also got this warning during boot. With the warning my machine did boot successfully. 

One of my partitions is fat32. I followed the suggestion here
[http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html](http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html)
and got rid of the warning by editing /etc/fstab. I only changed the one fat32 line in /etc/fstab.

I'm not entirely comfortable disabling fsck on this partition. It seems likely that this workaround hides an underlying issue.

---

### Post by ubuntubrian on 2009-11-01
I discovered this problem when trying to play Youtube vids in movieplayer and got a mountpoint error and vids wouldn't load. If I killed totem and restarted it then the vids load so the mountpoint issue must have gotten resolved in the kill.

I then tied it in with the startup error that this thread refers to but I have suffered no major problems and Karmic boots normally and very quickly after the message appears.

I don't want to start mucking with fstab but will wait for a real fix.

---

### Post by ubuntubrian on 2009-11-01
Sorry, I wanted to link the thread I started though it's not resolved....


[http://ubuntuforums.org/showthread.php?p=8214457&posted=1#post8214457](http://ubuntuforums.org/showthread.php?p=8214457&posted=1#post8214457)

---

### Post by lviggiani on 2009-11-03
After latest Ubuntu updates I'm not getting that message any more

---

### Post by ubunny on 2009-11-05
I'll just chime in and say, yes I get the same error.  My laptop loads and all, but it looks like it has to reboot itself 3 or 4 times just to get to the login screen, thus making my bootup time 4 times longer!!  This really sucks.. argh..  Even Jaunty was faster.

The error itself seems to be having a problem mounting the /home partition (/dev/sda4) then reboots until it does work, which it eventually does.  The UUID for the partition seems to be unknown to Karmic and like grub, maybe it just needs to be updated.  So I tried update-grub but I still get the UUID error in the /etc/fstab.  No dice. Grub 1.5 is used but I don't know if that's relevant or not.  

Q.Is there a grub command to check the UUIDs?

Here's what happens as far as I can tell; 
On bootup, it flashes the grub menu, shows the OS list, counts down then shows hd(1,0) line at the top, but blinks this two or three times, then goes black, opens white ubuntu symbol, then gets error, then goes back to the hd(1,0) point again, then loads xsplash, then finally the login window.  Yeesh

Q. Why are there two different ubuntu graphics used on bootup?  
Q. Where can I view the message that the initial white graphic error displays?  dmesg and /var/log/messages didn't have the fstab error listed.
Q. Is there already a Launchpad ticket on this for ubuntu?  That's where to put this issue for developers to see, and act on it.

---

### Post by ubunny on 2009-11-05
Here's exactly what happens:: [http://www.youtube.com/watch?v=lRoMuY4bDPk](http://www.youtube.com/watch?v=lRoMuY4bDPk)

0:07--0:12 power on
0:12--0:14 POST
0:14--0:19 Grub (short countdown)
0:19--0:20 First boot message to hd(1,0) 
0:20--0:24 Second boot message
0:24--0:44 Lets stare at a white ubuntu logo for a while (no error mentioned this time)
0:44--0:51 Third boot message 
0:51--0:55 Screen Goes Black
0:55--1:08 New Ubuntu xsplash (no progress!?) so let's wait a while
1:08--1:19 Login window at last!
1:19--1:30 Loading....or doing something, or whatever.  Let's wait some more
1:30--1:34 Chime
1:34--1:46 Grudgingly loads background
1:46--1:54 Finish menu loading...and Done

Jaunty took about 40 sec to load.  Karmic is pushing 2 minutes.  Yikes

---

### Post by ubunny on 2009-11-05
At end of this thread I also rmmod the floppy and blacklisted it.  This reduced the boot up time by about 20 seconds.  Still a bit more than twice as slow as Jaunty boot up.




[https://bugs.launchpad.net/ubuntu/+bug/405270](https://bugs.launchpad.net/ubuntu/+bug/405270)

"""ianst  wrote on 2009-08-11:  	  #4

I've discovered today:

[https://bugs.launchpad.net/linux/+bug/384579](https://bugs.launchpad.net/linux/+bug/384579)

and somebody there proposed this:

echo "blacklist floppy" | sudo tee /etc/modprobe.d/blacklist-floppy.conf && sudo rmmod floppy && sudo update-initramfs -u

I had to run that twice, first run resulted in an error message "floppy in use", after the second run and the restart the booting was fast as pre-karmic. So it's certain now that a floppy handling made a delay. I think that this bug can be considered a duplicate of 384579.

"""

---

### Post by Pataforce8 on 2009-11-05
Hi, I'm getting the same message however it seems to run at the same speed booting up until I get the message. Right when it seems the Ubuntu loading screen should start filling the bar instead of bouncing back and forth I get the error. It won't boot into Ubuntu :(
It also says :
  /: waiting for /dev/disk/by-uuid/af28fcac-2fd1-40a9-b796-fb1dd6ae66dc
  /tmp: waiting for (null)
  swap: waiting for UUID=7cf156ad-8459-4ec7-8455-878833ff4f7b

---

### Post by Leed on 2009-11-09
I think it's time this thread gets a bump...

after all it is a rather critical problem. I have the impression it may have something to do with my harddrive, as gparted takes pretty long to scan the disc. Maybe Karmic is doing something similar on boot.

---

### Post by josekym on 2009-11-10
Hello there,  I installed Karmic on my laptop via Update Manager and immediately got the same error message on topic at boot-up.  Updates did not solve it, but editing the /etc/fstab file did.  I just put back the commented /dev/sdx lines in place of the ones with UUID and all is now well. :)

---

### Post by waba on 2009-11-10
iv got the same problem, and iv dual booted with XP. now i cant mount the partition that XP was on, even though i could with jaunty - it asks for autherisation, then doesnt mount the volume, it just freezes.

---

### Post by planetaires.net on 2009-11-11
I have upgrading from 9.04 to Karmic this morning... and same problem.
I try to mount the partition manually, and mount say me that the partition don't exist...
I start Gparted ... and I see that all partition's names have changed. 
All the partitions named /dev/sdaxx in 9.04 are now named /dev/sdbxx in Karmic and all the partitions named /dev/sdbxx are now named /dev/sdaxx
I have changed my fstab file and now all the partitions are working fine!

---

### Post by pheedback on 2009-11-13
I saw some other posts on the forums that seem pretty similar to this. I was able to fix my issue by following the steps **[here]("http://ubuntuforums.org/showpost.php?p=8175339&postcount=15")**. I had trouble getting my root password accepted so I reset the password, but once I was in it forced a file system check. The check went through and had errors. It suggested that I run the fsck program without any -a, -p or whatever else added. It went through and I had to fix some issues, but I am back in.

---

### Post by freacert on 2009-11-17
Same problem here, yesterday upgraded to Karmic, no problems, this morning karmic stated it can not load the swap disc. In gparted i see it is not activated. and also see see in gparted that the sdb turned into sda. the old sda is not there. 
Can load ubuntu without seeing any icons, dropdown lists pop up though. So can work in it.

---

### Post by freacert on 2009-11-17
> **freacert said:**
> Same problem here, yesterday upgraded to Karmic, no problems, this morning karmic stated it can not load the swap disc. In gparted i see it is not activated. and also see see in gparted that the sdb turned into sda. the old sda is not there. 
Can load ubuntu without seeing any icons, dropdown lists pop up though. So can work in it.

So fixed it with sudo gedit /etc/fstab.
changed the driveletters, according to the gparted information and fixed an entry line for the swap partition
# Entry for /dev/sda6 swap:
UUID=your harddisc id none swap sw 0 0

runs fine:p
now fixing the alsa sound thing, will be back in the forums..:-|

---

### Post by virender singh Thakur on 2009-11-17
[U]see the contents of fstab, it shows some ERROR mesage how to remove that 
still i a,m getting the same message before I Login[/U]

[U][B]" One or more of the mounts listed in /etc/fstab can not be mounted swap waiting for UUID=XXXXXXXXXXXX(some number )
Press Esc to enter"[/B][/U]

Then as i Press Esc ,,,,easily i can enter with normal login and password "
But how to remove this message

_**please see my fstab file also for idea **_


[http://pastebin.com/f45b4e05](http://pastebin.com/f45b4e05)

:p:popcorn:


and the command , dont generate any output, see as below

root@virender-laptop:/home/virender# sudo mount -a
root@virender-laptop:/home/virender#

---

### Post by Leed on 2009-11-17
Fixed my version of the problem... upon checking my system with gparted I found out what a sinner I used to be. Ok, it was my first Ubuntu installation back then using Dapper, but still I was naughty.

My Ubuntu was installed on Logical Drive. The error message contained all drives on that extended partition, so it was very confusing at first. Before Karmic no Ubuntu seem to be bothered by this "bad" setting. Well I just had to sort those partitions and reinstall, but now things work as they should

---

### Post by donjorge22 on 2009-11-17
I have this problem too, although I don't have any partitions - it was a clean install over Vista.  Boots up okay, although a little slower than my friend's Ubuntu.  Any ideas?

---

### Post by pablo pica piedra on 2009-11-21
have you solved your problem ...????
i have it too and i am pulling my hair of ...!!! 
hope you can help me

---

### Post by kemistri on 2009-11-21
having the same problem and i have to reboot like 3 times to get ubuntu to start up right. 

I hope this gets  fixed soon

---

### Post by shaibn on 2009-12-01
You should check out [this]("http://newyork.ubuntuforums.org/showpost.php?p=8151569&postcount=10") solution (worked for me).

> **kentaur said:**
> Your installs have failed.

remount your filesystem like this:

```

mount -o remount,rw / 
```then do a 

```
sudo dpkg --configure -a 
```And the installation will continue.

When you get the error, hit Enter. Type in the root password and continue solution above.

---

### Post by mbuller10 on 2009-12-01
thanks shaibn, that seems to have worked for me too, i got the error rebooted once and now no error I'm going to reboot again

---

### Post by mbuller10 on 2009-12-02
Never mind that did not work for me, after shutting down and starting back i still get the same error

---

### Post by mbuller10 on 2009-12-02
okay every i tried this and I think I got it working, if your /etc/fstab looks like this 

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9bed9bbf-8076-451e-8f57-3d0ef83c64ff /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cb6a8be6-d4e2-4c9b-9f20-63607bbbfccf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

replace it with this
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
# UUID=9bed9bbf-8076-451e-8f57-3d0ef83c64ff /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
# UUID=cb6a8be6-d4e2-4c9b-9f20-63607bbbfccf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda5 			/               ext4    errors=remount-ro 0       1
/dev/sda6 			none            swap    sw              0       0

---

### Post by oblivia on 2009-12-08
I had moved my swap partition and that was what was creating problems. (I'm a total noobie and this is my first post so please pardon me - and let me know! - if what I'm writing is totally obvious to others or if I describe things somehow incorrectly). It seems that the UUID that the swap partition was looking for was incorrect.

I ran "sudo blkid" to find out the UUID for each partition.
Then I ran "sudo gedit /etc/fstab" and changed the UUID to the correct one for the swap partition, saved the fstab file, rebooted and I no longer get the error.

---

### Post by hawthornso23 on 2009-12-09
Not all people in this thread are in the same situation. Some (like the OP) have a functional ubuntu with a warning message about unmounted partitions at boot. In most such cases it is the swap partition that is not being mounted. Others have a more serious problem because their root partition is not mounting.

I leave it to others to deal with the more serious case. If your buntu is functional however and simply can't find the swap partition it is likely because the UUID of your swap partition changed during the upgrade. This happened to me. There are many ways to fix this. Here is one.

[LIST]
[*]Run System-Adminstration-GParted to browse your partitions.
[*]Find the swap partition ( in my case /dev/sdb5 ). You might need to select a different disk if you have more than one (button in top right).
[*]Right click on the swap partition and select information.
[*]Copy the UUID (in my case b993412e-7d08-49c2-98c5-46f2bec39391 )
[*]Edit /etc/fstab and look for the line containing the word `swap'.
[*]If the UUID in that line doesn't match the actual UUID of your swap partition then you've found the problem.
[*]Copy in the correct value. Save.
[*]sudo swapon -a     (to activate the swap partition) or reboot.
[/LIST]
The fix for inability to mount other partitions is often similar. However if ubuntu isn't running and your root partition isn't mounted then that makes it a lot harder to edit fstab.

---

### Post by TAFKARS on 2009-12-11
> **oblivia said:**
> ...

I ran "sudo blkid" to find out the UUID for each partition.
Then I ran "sudo gedit /etc/fstab" and changed the UUID to the correct one for the swap partition, saved the fstab file, rebooted and I no longer get the error.

This solution worked for me. However, I HAD NOT moved my swap partition, the error was generated immediately upon upgrading to 9.10. Weird, but there you go.

---

### Post by wavesailor on 2009-12-15
This worked for me and my system just hung after boot up with the same message. I hit "ESC" and followed the instrunctions below and then rebooted:
[http://newyork.ubuntuforums.org/showpost.php?p=8151569&postcount=10]("http://newyork.ubuntuforums.org/showpost.php?p=8151569&postcount=10")

---

### Post by machine^R on 2009-12-25
My problem was that the swap partition was not being mounted at start up. I got the folowing error message at boot:

swap: waiting for UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

I tried what [hawthornso23]("http://ubuntuforums.org/member.php?u=867217") suggests above and it has been working fine since then. I tried this as I wasn't comfortable disabling fsck as was suggested elsewhere.

---

### Post by Desert69 on 2010-01-10
I've the "One or more of the mounts listed in /etc/fstab cannot yet be mounted" problem in a peculiar way.

I've made a fresh Karmic install in a dual-boot with Windows XP SP3 (but exactly the same problem occured previosly when I upgraded from Jaunty to Karmic).

This is the uncommented extract from my /etc/fstab file:
```
proc            /proc           proc    defaults        0       0
/dev/sda7 /               ext4    errors=remount-ro 0       1
/dev/sda5  /datos          vfat    utf8,umask=007,gid=46 0       1
/dev/sda1  /windows        vfat    utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

At the beginning there where the UUIDs in there, but I've replaced them with the /dev/sdaX as they said in lots of threads.


When I turn on the computer, I select Ubuntu on GRUB menu, and the bootsplash cames. After some seconds, the mentioned error shows up, offering a recovery shell by pressing ESC. If I ignore it, some seconds after (30? 60?) the message disappears, and the bootsplash goes on. Again, after a while, the same error message comes back, and, again, if I wait a while, it disappears, and the boot goes on, but with no problems this time. Then I can do login and use the computer with no troubles.

It ALWAYS shows the error message EXACTLY 2 times.


Apart from the UUID change, I also tried the "grub-update" + "dpkg -a" solution, with no results.


Another curious point is that the error message names every partition by its "/dev/sdaX", except from / ("/dev/sda7"), which is named by its UUID, even when I changed this in /etc/fstab.


I really don't know what to do now. I can use the computer, and everything is OK - except it takes a LOOOOOONG time to boot.


Any help?

---

### Post by x-shaney-x on 2010-02-02
I am using the latest Linux Mint 8 and also having exactly the same problem as the above poster.

---

### Post by Jamie Flournoy on 2010-02-07
I just had a case with the same symptoms, on a Xen domU hosted at RimuHosting. I tried a few of the suggestions here and none of them worked for me. I asked them for help and they had a good suggestion, which was to make sure my /etc/fstab was right, and if necessary create a new VPS with Karmic and inspect that to see what I was doing wrong.

It turned out to be an /etc/fstab problem after all.

Here's the WRONG /etc/fstab that I had, which worked for 9.04 and never booted (even after every other trick mentioned here) under 9.10:
```
[FONT=Courier New]
none       /dev/pts devpts mode=0620                 0 0
none       /proc    proc   defaults                  0 0
/dev/xvda1 /        ext3   defaults,noatime,relatime 1 0
/dev/xvda9 swap     swap   defaults,noatime          0 0
none       /sys     sysfs  noauto                    0 0[/FONT]

```In the recovery shell I could see that /dev/xvda1 and /dev/xvda9 were not present, and in fact only about 8 or 9 files total were in /dev.

I was able to use mknod to create the missing /dev/xvda1 and /dev/xvda9 using major and minor numbers from the first 2 columns of /proc/diskstats so that I could mount the filesystems, but those manually created entries disappeared upon reboot.

Also, and probably most importantly, I could see that /sys was *not mounted* and so "ls -l /sys" showed an empty directory. From what I read about udev, it looks in /sys and uses what it finds there to automatically generate a ton of devices (682 files total on this server now that it's working properly). So the fact that there were only about 8 files in /dev was a huge red flag.

This is the /etc/fstab that works, which is what the RimuHosting new VPS install script made:
```

[FONT=Courier New]proc           /proc   proc     defaults                  0 0
/dev/xvda1     /       ext3     defaults,noatime,relatime 1 0
/dev/xvda9     swap    swap     defaults                  0 0[/FONT]

```I believe that what was happening was that udev was not seeing anything under /sys, and therefore not generating the entries under /dev for the things it found under /sys.

I think that the cause of that problem was that my /etc/fstab had /sys last, when it should have had it first. Apparently having it not be there at all works also, and might actually be more correct. My /sys definitely has stuff under it and udev created a ton of entries once I rebooted with the new /etc/fstab above.

So if you're stuck, consider installing Karmic to an empty partition and borrowing a fresh /etc/fstab from that for your busted Karmic installation that won't boot. You could do that on a VPS provider or on a VM on another machine or on an old HD you aren't using or something. It sure helped me to have a clean reference installation of Karmic to examine. If you can do that on the same hardware that isn't booting (fresh install to spare old HD) that's probably best.

Hope this helps!

---

### Post by Linux-Djihad on 2010-02-19
I had the same problem (New Installation, Ubuntu Karmic 64bit).
I configured Eclipse and suddendly this crap got frozen and my system rebootet by itself!
After that, this error came while booting. mount -n -o remount,rw / (or any other device) did not help.

I got it working again as I startet Ubuntu with the installation CD (chose try ubuntu), and when the desktop finished loading I just mounted and unmounted the affected partitions and rebooted.

---

### Post by Desert69 on 2010-02-27
well... some updates here...


last week i re-installed my windows xp... windows xp instaler first formats the selected partition, then copies the instalation files to that partition, then reboots and boots from that partition, and just there it starts the real instalation...


well, i formated my windows partition and copied the instalation files... when the system had its reboot, it told me that the partition table was damaged, or could not be recognized, or something like that (don't remember :) )

after an hour fighting with a karmic live cd and my partitions and grub, it resulted that my partitions' path changed... what used to be '/dev/sda5' now is '/dev/sda3', and things like that...

but, the first time i could regenerate grub, my /etc/fstab file still had '/dev/sda5' (and the same with my windows partition - /dev/sda5 was a fat32 data partition, and my windows partition was fat32 too), so the system didn't mount them... just / and swap...

and, until i changed my /etc/fstab to make the system boot those fat32 partitions, it DIDN'T show the 'One or more of the mounts ... cannot yet be mounted' error...


after i changed /etc/fstab in order to mount those fat32 partitions, the error came back, and still's here...

so there's something about those fat32 partitions, i think...


in my ~ i have some symlinks to folders in my data partition (the fat32 one at /dev/sda3)... and my fstab first has the / entry, then /datos ('data', /dev/sda3) and then /windows (the other fat32 one)...

i'll try what Jamie Flournoy said... maybe first mounting /datos, so when i mount / it can resolve those symlinks... but i don't think i can mount /datos if i didn't mounted / first...


but we'll see...

---

### Post by robine on 2010-02-28
I am having this problem, as well (9.10). I have no idea what to do :|

It started this evening after Firefox crashed while I was trying to watch a YouTube video (another poster here mentioned something similar). I can't boot normally; right now I'm on the live CD to seek help.

I went to System > Administration > GParted to find the swap partition UUID (760878d8-6c0f-4841-9b96-3c80672605e1). I thought maybe that was the problem - the swap partition not mounting at boot up. I tried "sudo nano -Bw /etc/fstab" in terminal. Here is what I ended up with:

> # /etc/fstab: static file system information
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
# <file system>  <mount point>  <type>  <options>  <dump>  <pass>
proc   /proc   proc   defaults   0   0
# / was on /dev/sdb1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158  /  ext3  errors=remount=ro 0  1
# /home was on /dev/sda1 during installation
UUID=a31097ec-c78d-4760-9cf0-2cfcd5aff759  /home  ext3  defaults  0  2
# swap was on /dev/sdb5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1  none  swap  sw  0  0
/dev/scd0   media/cdrom0   udf , iso9660 user,noauto,exec,utf8  0  0
/dev/fd0   media/floppy0  auto  rw,user,noauto,exec,utf8  0  0I am only a beginner here... but I'm wondering if, from the info above, this means that one drive isn't being "seen" on boot up? It says "remount" - is this something I have to do; unmount the drive and then remount? If so... how? The UUID for the swap partition is correct, and I haven't changed any settings at all today, so I've no idea how this came about!

Also, when trying to reboot from recovery shell, here is the information on the screen (it wouldn't progress any further than this):

> init: mountall-shell main process (763) killed by TERM signal
Hangup
root@robine-desktop: ~# mountall start/starting
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@robine-desktop: ~# swapon: /dev/disk/by-uuid/760878d8-6c0f-4841-9b96-3c80672605e1: swapon failed: Device or resource busy
mountall: swapon /dev/disk/by-uuid/760878d8-6c0f-4841-9b96-3c80672605e1 [1158] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/760878d8-6c0f-4841-9b96-3c80672605e1
One or more of the mounts listed in etc/fstab cannot yet be mounted: (ESC for recovery shell)
/home: waiting for UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759
mountall: CancelledAny help is very appreciated, as I am very lost right now!!

---

### Post by doctorprojector on 2010-03-04
> **oblivia said:**
> I ran "sudo blkid" to find out the UUID for each partition.
Then I ran "sudo gedit /etc/fstab" and changed the UUID to the correct one for the swap partition, saved the fstab file, rebooted and I no longer get the error.

I have today upgraded from Jaunty to Karmic and had exactly the same problem.

Thank you, this fix with "sudo blkid" and editing /etc/fstab worked for me. Now my desktop machine boots without fuss.

doctorprojector

---

### Post by Arijit_Kundu on 2010-03-06
this has worked for me as well!

---

### Post by lousdal on 2010-03-20
I'm having the same problem as robine - it seems.

In my case the partition with my /home directory won't mount. When I try doing 'sudo blkid' I only get the UUID for /dev/sda1 and /dev/sda3 which are my / and swap.

I don't really know anything about all these things, but being able to read, I found out how to get these informations ;)

If anyone has any idea how I might progress, it would be much appreciated.

I'm running Ubuntu 9.10 - Ubuntu, Linux 2.6.31-20-generic

I don't know if anything happend before this error occured since it's the laptop of my wife (HP Compaq nx8220)

Edit: I just followed the suggestion in this thread: [http://swiss.ubuntuforums.org/showthread.php?t=1325528&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1325528&page=2) and managed to solve the problem!!!

---

### Post by _h_ on 2010-03-20
> **oblivia said:**
> I ran "sudo blkid" to find out the UUID for each partition.
Then I ran "sudo gedit /etc/fstab" and changed the UUID to the correct one for the swap partition, saved the fstab file, rebooted and I no longer get the error.

It seems weird, but I've never had to run this command at all.  It gives me this message after a fresh install of 9.10, but after updates it seems to fix itself and I rarely ever see it again. I may see it again once in a few weeks, if my drive is lagging behind on booting, but that's it.

---

### Post by Desert69 on 2010-05-09
Good news :)

For anyone having this error [my]("http://ubuntuforums.org/showpost.php?p=8640524&postcount=35") [way]("http://ubuntuforums.org/showpost.php?p=8640524&postcount=39"), yesterday I did some tests and then a friend gave me a solution.


First of all, I deleted the symlinks from my ~ to one of the troubelling fat32 partitions. This made no change. I commented the entries of both fat32 partitions in my /etc/fstab, and the system booted with no errors.

Then, I restarted the system twice, each one with only one of the fat's entries uncommented. This made the system boot, showing the error just once. Finally, I uncommented both lines (as it was in the first place) and it showed the error message twice during boot.


I told this to a friend, and the solution was easy: disabling error checking in those partitions. And it worked.

So this is how my /etc/fstab looks like now:

```
proc            /proc           proc    defaults        0       0
/dev/sda3  /datos          vfat    utf8,umask=007,gid=46 0       0
/dev/sda5 /               ext4    errors=remount-ro 0       1
/dev/sda1  /windows        vfat    utf8,umask=007,gid=46 0       0
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I hope this can help anyone else. It was a torture to me.


See ya!

---

