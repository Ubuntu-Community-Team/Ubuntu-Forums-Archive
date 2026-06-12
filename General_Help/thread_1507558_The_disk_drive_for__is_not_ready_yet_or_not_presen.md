---
title: "The disk drive for / is not ready yet or not present"
date: 2010-06-11
forum: General Help
---

### Post by Saltwaterfishin on 2010-06-11
Hi,

I'm a total newby.  I tried to upgrade to the newest ubuntu version (10.04 I think).  Now I can't even boot my computer.  After the initial "boot" stuff, the ubuntu screen comes on and then locks up in the process.  I get the message "The disk drive for / is not ready yet or not present.  Continue to wait; or press s to skip mounting or M for manual recovery."

I've tried "waiting" overnight to no avail.  I tried the "S" command to skip and got the message "[141.233783] Adding 1502036k Swap on /dev/sdb5. Priority-1 extents:1 across:1502036k"

I think the manual recovery is what I need to do.  When I type the "M" for manual recovery I get a maintenance shell with the last line being

root@jay-desktop:~#

Can anyone please give me some commands to fix this problem?  I have an OLD ubuntu boot disk.  How can I get my computer to boot from it?  I tried hitting "esc" while booting up to no avail.  I also tried hitting F1 while booting up.  I think that used to allow me to boot from the CD drive...but doesn't work now.

Please help

Jay

---

### Post by jv2112 on 2010-06-11
You need to set the bios to boot to the DVD-Rom drive.

F1,Del, F12 etc --> Depends on your mother board. Some boards have a boot options by command key. 

Once you get in I would recommend a fresh install with default options. Sounds like the partitions got set incorrectly.

---

### Post by aenesias on 2010-08-23
i have a similar problem related with it if u dont mind. I am using win xp and ubuntu 10.4 dual booting. I am okey with file system checks it does it sometimes without a problem with the ntfs partition and ubuntu partition but for the last check i got this message “The disk drive for /media/25C74B07FB07878 is not ready or not present continue waiting or press s to skip or M for manual recovery” i waited for it but nothing happened. Then now i have to press “s” to skip everytime. I have my ubuntu working fine and the ntsf drives and the xp everything is fine. I couldnt find which "media" does this message is talking aboout? Do u have any ideas for this problem thanx in advance

---

### Post by smackwacker on 2010-11-19
You can solve this manually:
During boot write down the UUID of the drive and press S to skip mounting the drive.
Open the terminal window and type:
**sudo gedit /etc/fstab**
[FONT=Courier New][SIZE=1]
[/SIZE][/FONT][LEFT][FONT=Verdana]Locate the entry with the UUID you wrote down and put a dash (#) before that line to disable it. The file will look something like this[/FONT] and I highlighted the line that I disabled:
[/LEFT]
[FONT=Courier New][SIZE=1]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda1 :
UUID=31b7ed42-80c5-4d3e-ab89-fd5fb6cbc7df    /..........
#Entry for /dev/sdc5 :
[COLOR=Red]**#UUID=15DB122A7DAE9399    /.........**[/COLOR]
#Entry for /dev/sda5 :
UUID=db6830a1-c2f8-4f7a-b04b-3b3662c2455d    none    swap    sw    0    0
[/SIZE][/FONT]
Save the file and at the next reboot no questions asked :)

You get this message because you disconnected that disc and is still mounted when the system is booting.

Good luck!

---

### Post by RBruiser on 2011-02-28
oops.

---

### Post by ondrejch on 2011-05-03
I have the same problem after upgrade to 11.04. I have separate root and home partitions, both on soft raid1 (mdadm).

The system boots into recovery, I remount the root filesystem RW and type "mountall", and it happily starts up. 

I checked that UUIDs are fine in /etc/fstab, I tried putting /dev/mdN instead of UUIDs in there, I tried to uncomment the root FS from fstab - all gives me the same problem. 

During the upgrade the cmake package failed, and I recovered by usual apt-get -f install, dpkg --configure  -a etc. 

Any ideas where to look? thanks

---

### Post by maphew on 2011-05-06
> **ondrejch said:**
> I have the same problem after upgrade to 11.04. I have separate root and home partitions, both on soft raid1 (mdadm).


I also have the same problem after upgrading to 11.04. I'm not using soft raid though I do have distinct home and root partitions. There were failed packages during the upgrade but I don't recall their names.

I booted from sysrescue cd and ran `fsck.ext4 /dev/sda6`, the root (/)  partition (based on advice from here: [http://ubuntuforums.org/showpost.php?p=10685421&postcount=6](http://ubuntuforums.org/showpost.php?p=10685421&postcount=6)). It said "file system was modified". I'm about to reboot and will follow up with the results.

---

### Post by ondrejch on 2011-05-07
I ran fsck, it checked out without problems, and the issue remains. Let me know hoe it worked for you. I am at lost here, as reumounting root filesystem rw and running "mountall" after the drop to emergency shell continues the boot process flawlessly to X login, and everything works afterwards.

---

### Post by maphew on 2011-05-07
Ok, finally solved this! The steps I took were to: boot machine with SysRescue CD, mount my root partition and `chroot` to it, run `dpkg` and `apt-get` to fix broken/incomplete packages. There are about half a dozen .deb packages in /var/cache/apt/packages which were corrupt and needed to be deleted. 

I had to run through this procedure 3 or 4 times before I finally got it all done. The following code is for reference, don't just blindly run it.

```

# sd6 is my root partition  
mount /dev/sda6 /mnt/custom  
mount -o bind /proc /mnt/custom/proc  
mount -o bind /dev /mnt/custom/dev  
mount -o bind /sys /mnt/custom/sys  

chroot /mnt/custom
$ mv /sbin/initctl /sbin/initctl.old
$ ln -s /sbin/initctl /bin/true
$ dpkg --configure -a
$ apt-get -f install
$ apt-get check
$ move /sbin/initctl.old /sbin/initctl
$ exit

reboot

```

Resources used in developing this recipe:

* "Solution 2: Reinstallation of Grub using chroot" from [http://www.sysresccd.org/Sysresccd-Partitioning-EN-Repairing-a-damaged-Grub](http://www.sysresccd.org/Sysresccd-Partitioning-EN-Repairing-a-damaged-Grub) (though the grub part made no difference on my machine)

* [http://aaronshang.wordpress.com/2010/10/15/unable-to-connect-to-upstart/](http://aaronshang.wordpress.com/2010/10/15/unable-to-connect-to-upstart/) - to fix problems with apt-get and dpkg not completing properly

---

### Post by ouch_ouch on 2011-08-01
> **aenesias said:**
>  Then now i have to press “s” to skip everytime. 

You are fortunate to have you can start your ubuntu by that way.
i have the same problem .unfortunately,i can start the system by press "S",
because when i press "s" ,it crashed.
i am using dual system ,too.the ubuntu was installed by a program for window xp (wubi).i've tried more method to recover it,but failed:-(
i don't know how i can do something for it new .

---

### Post by Ron O on 2011-09-16
I finally removed my Windoze partition and got the same boot-up error. Thanx to Smackwacker for the fstab fix- worked perfectly for me. No more Windoze and NEVER again.

---

### Post by UngodlySpoon on 2011-10-27
Thanks a ton, maphew!  You're quite a boss.  This saved me the hassle of backing up my files and doing a reinstallation.

A quick note to anyone using these tips to fix this issue: you don't really even need a RecoveryCD, I used a regular LiveCD.  I also ran 'apt-get update' and 'apt-get upgrade' so those may have helped, too.  If apt-get cannot resolve any of the server hostnames, you may have to check your /etc/resolv.conf file.  Mine was blank, so I had to populate it with the information located in the one outside of the chroot environment.  Good luck!

---

### Post by ondrejch on 2011-11-02
I ended up reinstalling the system ... since I have separate root/home partitions, it was simple. 

This all happened before the gnome2 removal / Unity disaster with 11.10.

---

### Post by Positive07 on 2012-03-05
Hello Im new in the forum! I had the same problem but I couldn't solve it I have seen that the problem is in this line were it says
> /dev/sda1          /                        ext3       errors=remount-ro     0              1
and I have to change it to 
> /dev/sdb1          /                        ext3       errors=remount-ro     0              1
But i cannot edit the fstab with gedit and i dont have any other editor in ubuntu so i cannot modify it i was thinking in using Vim from a flashdrive but i dont really know how to do that. Can you help me with this?

PD: Maybe this is revive a post but is completly necesary and also If i post it again you will say read this one and I could not find the answer here... that's why im asking....

PD2: Im new to Ubuntu so i dont really know how to use the command prompt so if you can explain it that would be awesome

---

### Post by whiskers751 on 2012-03-21
If you want to get / writable, use mount -o remount,rw /

---

### Post by Elfy on 2012-03-21
Old thread closed.

---

