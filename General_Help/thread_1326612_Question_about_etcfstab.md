---
title: "Question about /etc/fstab"
date: 2009-11-14
forum: General Help
---

### Post by salu on 2009-11-14
Hi, I am new to Ubuntu. I have a question about fstab file. Please help! Thanks!
 
My ubuntu server is: 6.06 LTS amd-64bit server edition
My current fstab:
 
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]# /etc/fstab: static file system information.[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]#[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]# <file system> <mount point>   <type>  <options>                     <dump>  <pass>[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]proc                        /proc           proc       defaults                            0           0[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]/dev/md1                 /                 ext3    defaults,errors=remount-ro     0           1[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]/dev/md0                 /boot           ext3      defaults                             0           2[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]/dev/md2                none            swap        sw                                  0           0[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]/dev/hdb               /media/cdrom0   udf,iso9660 user,noauto               0           0[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]/dev/fd0                /media/floppy0  auto    rw,user,noauto                    0           0[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial][/FONT][/COLOR][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=navy][FONT=Arial][COLOR=black]*********************[/COLOR][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial]Now I add an additional hard disk -- sdc1 into my server and mount it to a folder **/zim/bkfolder**, and add a line into fstab:[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial][/FONT][/COLOR][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=navy][COLOR=navy][FONT=Arial][FONT=Arial][SIZE=2][COLOR=navy][FONT=Arial][COLOR=blue]**/dev/sdc1       /zim/bkfolder      ext3    defaults        0       2**[/COLOR][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=navy][FONT=Arial][COLOR=blue][/COLOR][/FONT][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=navy][FONT=Arial][COLOR=blue]**I would like to know if /dev/sdc1 <pass> number should be 2 or 0, or both are fine? Because someone said the system can not boot up if wrong pass # is set. **[/COLOR][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000ff][COLOR=navy][FONT=Arial][/FONT][/COLOR][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=#0000ff][COLOR=navy][FONT=Arial]**Thanks in advance!**[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000ff][COLOR=navy][FONT=Arial][/FONT][/COLOR][/COLOR][/SIZE][/FONT] 
[/FONT][/COLOR][/COLOR][/SIZE][/FONT]

---

### Post by Zoot7 on 2009-11-14
The last two numbers in the fstab file are dump and fsck respectively. Dump is a backup utility and fsck is the file system check. 
I've never used the dump option or read of anyone using it myself. Setting the second number to anything other than zero tells fsck to automatically force a file system check every X times it's mounted. It's useful if you've data you'd rather not lose on that drive.

So as you have fstab now, it's fine. ;)

---

### Post by salu on 2009-11-14
Thanks Zoot7! 
 
In my fstab, if both of two devices' <pass># are set to 2, will it cause system not boot up?
[FONT=Arial][SIZE=2][COLOR=#000080]**/dev/md0 /boot               ext3 defaults 0 2**[/COLOR][/SIZE][/FONT]
**[FONT=Arial][SIZE=2][COLOR=#0000ff]/dev/sdc1 /zim/bkfolder  ext3 defaults 0 2[/COLOR][/SIZE][/FONT]**

---

### Post by Zoot7 on 2009-11-14
> **salu said:**
> Thanks Zoot7! 
 
In my fstab, if both of two devices' <pass># are set to 2, will it cause system not boot up?
[FONT=Arial][SIZE=2][COLOR=#000080]**/dev/md0 /boot               ext3 defaults 0 2**[/COLOR][/SIZE][/FONT]
**[FONT=Arial][SIZE=2][COLOR=#0000ff]/dev/sdc1 /zim/bkfolder  ext3 defaults 0 2[/COLOR][/SIZE][/FONT]**
Only if there's a file system will the system fail to boot. Otherwise you should be fine.

---

### Post by falconindy on 2009-11-14
The 'pass' option specifies the **order** drives are checked in, not the frequency. All drives other than root should be either a 0 or a 2. Root should always be a 1.

---

### Post by salu on 2009-11-14
Hi Thanks a lot for your reply!

---

