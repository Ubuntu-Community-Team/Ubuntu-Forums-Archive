---
title: "Change the Root ownership of the HDD"
date: 2011-11-26
forum: General Help
---

### Post by maiandros on 2011-11-26
Hello Guys!
I`m facing a strange problem here! 
I was using my HDD 1TB NTFS and last night i decided to format it cause it was reporting that i had to chkdsk/f in Windows before reuse it!
 I did the format first in the Disk Utlity under the option of FORMAT VOLUME ! Then in my windows i did another format always staying to the NTFS format! 
The problem now is that i cannot paste nor delete in that HDD cause its permissions is on ROOT only.
I`ve tried using gksu nautilus to change the ownership from the properties of the HDD but nothing has changed at the end! 

By giving the gksu gedit /etc/fstab command i see this : 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /    ext4    errors=remount-ro    0    1
/dev/sdd1    /media/SISYPHUS    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/sda3    none    swap    sw    0    0

I see that it`s unmask=0022 that supposed to mean that anyone can read/write no?
The HDD is auto-mounted in every restart of my computer,i can access it but i cannot write or delete any stuff from it.


Is anyone willing to give me some hint or a solution to my problem? 

Thanks in advance !

---

### Post by Morbius1 on 2011-11-26
>  I see that it`s unmask=0022 that supposed to mean that anyone can read/write no?No.
umask is the opposite of an octal chmod. It represents the permissions you want to remove not allow. So a "2" removes write access. 

You want either:
umask=0000 which allows read write access to everyone even though it's owned by root. 

Or,  

umask=0022,uid=1000 which allows read write access to you ( uid=1000 ) and read access to everyone else.

/dev/sdd1    /media/SISYPHUS    ntfs    defaults,nls=utf8,**[COLOR=Blue]umask=0022,uid=1000[/COLOR]**    0    0

---

### Post by maiandros on 2011-11-26
Ok! Thanks Morbius...but something weird is going on! 
I ll try to explain ... the ownership changes all the times between my external HDDs! 
Before editing anything i thought that it might be some problem of the  disks so i`ve shut down my pc and i ve reattached all my disks to my USB  HUB ! The result was that one different HDD was now with root ownership  and the first disk was back to normal. I rebooted again changing the  usb ports that were connected my disks and the result was again  different ...a new drive had root ownership and the other two where  normal...!
The only thing i can say for sure is that always is the same mount point /dev/sdd1 that creates this malfunction.
The problem is that this port is one of the 8 ports on my usb hub and it  had never done anything strange before...i had my HDDs there attached  for more than 3 months ...why has it gone crazy now on the sudden?
Besides that the name of the mount point is not going away....it is not  changing by the name of the HDD i ve attached there,but it insists on  saying **/media/SISYPHUS** . 
I understand that i might have confused u with my description thus i ll  try to make u a list to help u understand. Here are the mounting points of all my disks : 
**/dev/sdb1    /media/HERACLES** 
**/dev/sdc1     /media/SISYPHUS**_ 
**/dev/sdd1     /media/SISYPHUS** 
**/dev/sde1     /media/ORPHEUS** 

So the HDDs on **sdb1** and **sde1** are working fine.The HDD on **sdc1** works fine but the true name of the disk is without the low dash line. The HDD on **sdd1** has the root ownership and it has a complete different name in reality even though here it is titled as SISYPHUS . 

I don`t know what else i can give u in order to help u figure out what`s going on...! I`d appreciate any help...!

---

### Post by Morbius1 on 2011-11-26
With all these drives attached run the following command:
```
sudo blkid -c /dev/null
```You will get an output for an ntfs volume that looks something like this:
> /dev/sdxy: LABEL="label-name" UUID="66E4DC83E4DC56C1" TYPE="ntfs" In your fstab change this:
>  /dev/sdd1    /media/SISYPHUS    ntfs    defaults,nls=utf8,[COLOR=Black]umask=0022,uid=1000[/COLOR]    0    0     To this:
> [COLOR=Blue]**UUID=66E4DC83E4DC56C1**[/COLOR] /media/SISYPHUS    ntfs    defaults,nls=utf8,[COLOR=Black]umask=0022,uid=1000[/COLOR]    0    0 
Your device names ( /dev/sdxy ) are changeing based on when they are used. UUID is a sort of serial number and is unique for that particular partition and will never change.

EDIT: Come to think of it this is rather odd as well:
>  /dev/sda2    /    ext4    errors=remount-ro    0    1
Linux hasn't used /dev/sdxy in an install in quite some time so I'm surprised to see it as you root partition. You must have used some type of GUI to manage your partitions. Those GUI's were all created before the move to UUID's.

---

### Post by maiandros on 2011-11-27
I apologise for abusing ur kindness Morbius...
By giving the comand **sudo blkid -c /dev/null** i get this :

/dev/sda1: LABEL="C" UUID="055F8FDB3E227F2C" TYPE="ntfs" 
/dev/sda2: UUID="92d0d3a3-3269-45ba-8395-b9fa5ed6de84" TYPE="ext4" 
/dev/sda3: UUID="baf0d5c3-7db0-4351-81ef-55c92f9347e3" TYPE="swap" 
/dev/sdb1: LABEL="HERACLES" UUID="6E05A0B64651CD20" TYPE="ntfs" 
/dev/sdc1: LABEL="SISYPHUS" UUID="467414007413F183" TYPE="ntfs" 
/dev/sdd1: LABEL="OEDIPUS" UUID="7E12811E4F835EB6" TYPE="ntfs" 
/dev/sde1: LABEL="ORPHEUS" UUID="BEA857E0A85795AD" TYPE="ntfs" 

And with the [B]gksu gedit /etc/fstab : 

[/B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /    ext4    errors=remount-ro    0    1
/dev/sdd1    /media/SISYPHUS    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/sda3    none    swap    sw    0    0 


I know it is rather strange cause i haven`t used any other software to make any changes other than Disk Utility that i have used to format my disk. 
One other thing that it is happening ( this problem started the same time with the root ownership problem) is that sometime when i reboot my system tends to mount twice the same HDD... when this happens it uses the same name for "both" mounted disks and one of them is normal and the other is with root privileges.Probably a side effect of the same problem...!

So if i change the fstab as u propose that means that i.m not going to be able to switch usb ports between my HDDs again...or at least that port of my usb hub will be occupied by this particular HDD for ever.
Do i have to connect the SISYPHUS HDD to the problematic usb port and afterwards follow this procedure? 

Thanks again for ur precious help!

---

### Post by Morbius1 on 2011-11-27
> I know it is rather strange cause i haven`t used any other software to  make any changes other than Disk Utility that i have used to format my  disk. "Disk Utility" a.k.a. gnome-disk-utility a.k.a. Palimpsest is likely the culprit. The phenomenon of a disk being recognized as /dev/sdab one time and /dev/sdxy the other can be seen here:

When you first created your line in fstab SISYPHUS was at /dev/sdd1:
>  [COLOR=Blue]**/dev/sdd1**[/COLOR]    /media/SISYPHUS    ntfs    defaults,nls=utf8,umask=0222    0    0Now it's at:
>  [COLOR=Blue]**/dev/sdc1**[/COLOR]: LABEL="SISYPHUS" UUID="467414007413F183" TYPE="ntfs" This isn't your fault it's because the developers at Palimpsest didn't get the memo.
> So if i change the fstab as u propose that means that i.m not going to  be able to switch usb ports between my HDDs again...or at least that  port of my usb hub will be occupied by this particular HDD for ever.No. Every time the system sees that partition's UUID number it will mount to a specific mount point. 

Let's step back a moment to get an overall picture of what should be happening by default. The way the system is designed as far as these external drives is concerned is that if you do nothing at all ( no fstab entries for these drives ) it will create a temporary mount point at:
```
/media/label-name
``` when you connect them. In your case it will create a temporary mount point at /media/SISYPHUS. Then it will mount the partition to that mount point with ownership = you and with permissions for you to read and write. You can create an entry to change the ownership and permissions of the mounted partition but if you are the only user on that box I'm not sure why you'd want to.

---

### Post by maiandros on 2011-11-27
Thanks a lot Morbius ... everything seems to work fine now! 

Just in case here is the result of my new fstab : 

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2    /    ext4    errors=remount-ro    0    1
UUID=467414007413F183 /media/SISYPHUS    ntfs    defaults,nls=utf8,umask=0022,uid=1000    0    0
/dev/sda3    none    swap    sw    0    0[/B] 

Have i done it right?

Thank you again for ur patience and ur effort !

---

### Post by Morbius1 on 2011-11-28
It looks OK to me but the ultimate test is if it does what you want it to do and it appears that it does.

---

### Post by maiandros on 2011-12-31
Am i so unfortunate ?

Just when i thought everything was ok ...darn it! 

OK...the hard drives are fine i`ve solved this problem with the precious contribution of Morbius. But now there is something else correlated to the first problem....if the hard drive is not attached to my PC Ubuntu will not load! It keeps freezing during the loading screen and stays there for ever. 

Any idea how can i solve this?
If i totaly erase the fstab file and reboot will it be ok?

---

### Post by Morbius1 on 2011-12-31
>  If i totally erase the fstab file and reboot will it be ok?Absolutely NOT.

Go into fstab and place a # sign in fron of the NTFS line. This will tell the system to ignore that line.

---

### Post by maiandros on 2012-01-02
> **Morbius1 said:**
> Absolutely NOT.

Go into fstab and place a # sign in fron of the NTFS line. This will tell the system to ignore that line.

Ok...it works properly now! I`m logged in my Ubuntu finally! Morbius:KS i owe u one more ! 
I just hope i don`t abuse ur kindness with my ignorance...what will it be from now on? 
Am i supposed to add and remove the # from the fstab every time i use my HDD or should i leave it that way and the next time i attach my HDD a new string will appear in the fstab?

---

### Post by Morbius1 on 2012-01-02
> Am i supposed to add and remove the # from the fstab every time i use my HDD or should i leave it that way and the next time i attach my HDD a new string will appear in the fstab?The way Ubuntu works with external hard drives is that when they are attached the system will automatically mount them to /media/"label-name" if there is a label on that partition or /media/"UUID-number" if they are not. They will mount with you as owner and full access to you so there is no need to add anything to fstab for these devices.

---

