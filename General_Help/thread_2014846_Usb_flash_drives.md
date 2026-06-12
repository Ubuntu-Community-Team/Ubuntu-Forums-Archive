---
title: "Usb flash drives"
date: 2012-07-02
forum: General Help
---

### Post by meduser on 2012-07-02
Ok..I am getting very frustrated with Ubuntu these days. I have had numerous issues with flash/ shockwave. I don't even want to deal with it anymore.

Now, I am trying to copy some files to a usb stick. Every single stick used says it is read only. I have formatted some of them in Ubuntu, and I drag anything to it, and says read only.

I have 8 different sticks, and I have the same for every single one of them. If I go to windows, it allows me copy whatever to it, without even blinking an eye.

I have tried to use:

sudo chmod 777 /dev/sdb1

terminal thinks for a second, but the stick is still read only. I have tried to change permissions for the sticks in the home folder, but it does not let me change it, even though it lists me as the owner.

I would like to be able to stick a usb stick in, and just write to it. I have not been able to do that since 12.04 was installed. At this point in time, I hate 12.04, it has caused nothing but grief since I installed. 

Can I set up a way to just write to the usb thumbdrive? A simple thing like moving files is taking a long time due to permissions..grr

---

### Post by ajgreeny on 2012-07-02
> **meduser said:**
> Ok..I am getting very frustrated with Ubuntu these days. I have had numerous issues with flash/ shockwave. I don't even want to deal with it anymore.

Now, I am trying to copy some files to a usb stick. Every single stick used says it is read only. I have formatted some of them in Ubuntu, and I drag anything to it, and says read only.

I have 8 different sticks, and I have the same for every single one of them. If I go to windows, it allows me copy whatever to it, without even blinking an eye.

I have tried to use:

sudo chmod 777 /dev/sdb1

terminal thinks for a second, but the stick is still read only. I have tried to change permissions for the sticks in the home folder, but it does not let me change it, even though it lists me as the owner.

I would like to be able to stick a usb stick in, and just write to it. I have not been able to do that since 12.04 was installed. At this point in time, I hate 12.04, it has caused nothing but grief since I installed. 

Can I set up a way to just write to the usb thumbdrive? A simple thing like moving files is taking a long time due to permissions..grr
What filesystem did you format them to?  If they are any of the linux filesystems they will need the mountpoints permissions changed to allow you to write to them.  YOur command ```
sudo chmod 777 /dev/sdb1
``` will not work, but will need to be ```
sudo chmod 777 /media/*mountfolder*
``` or you can also change the folder owner with ```
sudo chown *user:user* /media/*mountfolder*
``` You will also need to sort out the permissions if they are NTFS, but I am not sure how you do that, and don't use any windows filesystems any more, so will leave you to search that yourself.  A fat32 usb drive should be writeable with no further action, so if that is your situation I have no idea where to look for answers.

---

### Post by cwsnyder on 2012-07-02
When you first plug in the USB drive, an icon should pop up, if you are using anything but Unity, which you can then right-click with your pointer and select **mount** from the context menu.  You may need to enter your password to finish the mounting process, but then your thumb drive should show up in Places/File Manager and you can drag files and drop on the icon or open a window to that drive.

You can also right-click to 'safely remove' or eject the drive for safe removal.

If you are using Unity desktop, the icon should still show up in File Manager for you to right-click and mount.

Note:  The second time or following in a session which you plug in the thumb drive it _won't_ show up.

---

### Post by coffeecat on 2012-07-02
> **meduser said:**
> Now, I am trying to copy some files to a usb stick. Every single stick used says it is read only.

This is not typical behaviour. 

> **meduser said:**
>  I have formatted some of them in Ubuntu, and I drag anything to it, and says read only.

How have you formatted them? What filesystem? The fact that you can use them in Windows suggests either FAT32 or NTFS both of which should automount read-write by default, and neither of which it would be appropriate to use chmod on because they are Microsoft filesystems.

Plug one of these USB drives in and then post the terminal output of this command:

```
mount
```

Then we'll have some needed information to go on, such as filesystem and mount options.

---

### Post by meduser on 2012-07-02
ok..I am using unity

When I go to the unity bar and click on the home folder, I can see the usb sticks listed and they have the eject button besides them. I can then click on the stick and view the contents.

I have right clicked on the icon in the unity bar that appears after I have plugged in the device and formatted them. At first, I tried compatible with all filesystems(FAT). I then tried to copy over some folders from my downloaded folder. No go.

I then formatted again using compatable with Linux(EXT4), and still no go.

If I plug the usb stick into a windows machine, it is recognized right away, and I can right click and format, no issues...so I know the sticks are good.

My usb slots on the pc work, as I can plug my iPhone into either of them, and it detects and charges right away.

I have tried the CHMOD 777 command, and I get nowhere with it.

I have tried chown, but I am already listed as the owner.

The USB's appear to auto mount, as I have to eject them to remove safely.

This particular stick has OSX files on it (kexts), and this is the terminal response:


gary@gary:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)
/dev/sdb1 on /media/MACHELP type hfsplus (ro,nosuid,nodev,uhelper=udisks)

mounting a usb stick that was formatted using Ubuntu:
gary@gary:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)
/dev/sdb1 on /media/Gary1 type ext4 (rw,nosuid,nodev,uhelper=udisks)


Neither of these will allow me to write to them.

I have others here, but the same issues.

I really appreciate the help..I just don't know what I am doing wrong

---

### Post by coffeecat on 2012-07-03
> **meduser said:**
> At first, I tried compatible with all filesystems(FAT). I then tried to copy over some folders from my downloaded folder. No go.

You have not given us the mount information for a FAT-formatted device. The mount outputs you have given us I comment on below. You should have no problem writing to a FAT formatted USB stick whether you formatted it in Ubuntu or Windows. Please plug a FAT-formatted USB stick in and post the mount output.

> **meduser said:**
> This particular stick has OSX files on it (kexts), and this is the terminal response:

gary@gary:~$ mount
<snip>
/dev/sdb1 on /media/MACHELP type hfsplus ([COLOR="Red"]ro[/COLOR],nosuid,nodev,uhelper=udisks)

For a HFS+ formatted device this is exactly as it should be. The journalled version of Apple's MacOS is mounted read-only in Ubuntu, or in any version of Linux. If you wish to write to a HFS+ formatted device you need to format it with the non-journalled version of HFS+ in MacOS's Disk Utility. Even so, you may run into permissions problems if you are sharing files between MacOS and Ubuntu because your UUIDs will be different in the two OSs.

> **meduser said:**
> mounting a usb stick that was formatted using Ubuntu:
gary@gary:~$ mount
<snip>
/dev/sdb1 on /media/Gary1 type ext4 (rw,nosuid,nodev,uhelper=udisks)

This one is formatted with a Linux filesystem and you do need to chown and chmod it, but you did the chmod wrongly earlier. As ajgreeny pointed out, you tried to chmod the device node (which won't work), rather than the mountpoint.

There are two ways of doing this, the more complicated way for a device you have already formatted ext4, and the quick simple way by reformtting with Disk Utility.

**The complicated way:**

Take your device with the label "Gary1" and plug it in. Make sure that it is mounted to /media/Gary1 or the following won't work. Run the mount command to be sure. Now, from a terminal:

```
sudo chown gary:gary /media/Gary1
sudo chmod 777 /media/Gary1
```

Adjust those commands if the mountpoint is different. That will allow not just you, but everyone to write to it.

**The simple way:**

This involves reformatting the device. Plug it in and either right-click -> format and click on the Disk Utility button, or open Disk Utility from the dash. Highlight the device in the left pane of Disk Utility and then click on "Format Volume" in the right pane. In the little window that pops up, ensure that type is ext4 and that "Take ownership of file system" is ticked. Click on format. All that "Take ownership of filesystem" does is the chown command above.

---

### Post by meduser on 2012-07-03
ok, here is the mount info from terminal on a freshly formatted usb stick to:
compatible with all filesystems(FAT)
Still says that it is read only.

gary@gary:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)
/dev/sdb1 on /media/Gary2 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)



I just used these commands to try and get permission to write. I changed Gary1 to Gary2 as this usb stick is called Gary2.


gary@gary:~$ sudo chown gary:gary /media/Gary2
[sudo] password for gary: 
gary@gary:~$ sudo chmod 777 /media/Gary2


I still get destination is read only.

I put Gary1 back in..

gary@gary:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)
/dev/sdb1 on /media/Gary1 type ext4 (rw,nosuid,nodev,uhelper=udisks)

Then typed:
gary@gary:~$ sudo chown gary:gary /media/Gary1
gary@gary:~$ sudo chmod 777 /media/Gary1


still get the read only destination.


Went to a Windows 7 machine, and formatted there. Here is the info:

gary@gary:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)
/dev/sdb1 on /media/GARY2 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


Typed the following:
gary@gary:~$ sudo chown gary:gary /media/GARY2
gary@gary:~$ sudo chmod 777 /media/GARY2


Still get read only.

Hopefully you can help me get this going right.

---

### Post by coffeecat on 2012-07-03
First:

> **meduser said:**
> gary@gary:~$ sudo chown gary:gary /media/Gary2
[sudo] password for gary: 
gary@gary:~$ sudo chmod 777 /media/Gary2


I still get destination is read only.

**You cannot use chown and chmod on Microsoft filesystems - FAT and NTFS.** This has been said already. Use chmod and chown on Linux filesystems only.

> **meduser said:**
> 
Still says that it is read only.

gary@gary:~$ mount

<snip>

/dev/sdb1 on /media/Gary2 type vfat ([COLOR="Red"]rw[/COLOR],nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)

According to that mount output, the device has been mounted read-write - see the part I've highlighted in red - and the other permissions look OK. You say that something is telling you that it is read-only. Where do you see this read-only message? What exactly does it say? Can you post a screenshot of the message?

---

### Post by adit on 2012-07-03
You said some dialog box appeared saying "Read Only Filesystem".  Run mount command inside terminal *after* the dialog box appears.  Your mount command output is *before* the appearance of dialog box.
Actually your filesystem was intially mounted as rw, after some time it was unmounted automatically and remounted as ro.

---

### Post by coffeecat on 2012-07-03
> **adit said:**
> You said some dialog box appeared saying "Read Only Filesystem".  Run mount command inside terminal *after* the dialog box appears.  Your mount command output is *before* the appearance of dialog box.

Agreed. @medusa, you edited your post after I last posted, so we need to get the sequence of events clear.

---

### Post by robtygart on 2012-07-03
Post edit:
[COLOR="Red"]I don't know if its the same but, I had a problem too were it was not allowing me to transfer files, unless I had root permissions. Until I formated it as Fat 32.[/COLOR]

With my USB I could not get it to transfer files when I had it formated to ext2,3, or 4 it was acting like I needed root permissions.

It did work with fat32.



Post Edited in response to: 
> **coffeecat said:**
> @robtygart, please see my post #6 for how to deal with permissions on ext2/3/4 drives. But please start your own thread if you need help. Let's keep this thread clear to concentrate on the OP's problem.

---

### Post by coffeecat on 2012-07-03
> **robtygart said:**
> With my USB I could not get it to transfer files when I had it formated to ext2,3, or 4 it was acting like I needed root permissions.

@robtygart, please see my post #6 for how to deal with permissions on ext2/3/4 drives. But please start your own thread if you need help. Let's keep this thread clear to concentrate on the OP's problem.

---

### Post by meduser on 2012-07-03
Ok...

I edited the post to add the usb stick that I had formatted on Win7 box. 

I restarted my pc, and was able to write to that stick... :)

However, when I put the usb stick into the Windows box, it says it needs to be formatted.

The error message would occur when I would try to drag files to the usb stick.

I would have the stick opened on the desktop, and then I would also open my downloads folder. When I would drag a file from the downloads folder, to the usb stick, it would say

volume is read only. 
I have tried to recreate it, but it appears to be working now.

Until I need to write to them again. 

I did take an update just before I restarted, so maybe that has something to do with it.

---

### Post by robtygart on 2012-07-03
> **coffeecat said:**
>  But please start your own thread if you need help. Let's keep this thread clear to concentrate on the OP's problem.

Thought I was!!! :???:

His posted sounded like the same problem I had. And I posted the only sulition that allowed me to transfer files. 

Only when I used puppy Linux "Which signs you in as Root" then I could transfer files, as if the files system was asking for Root permissions.

Unless I am reading his output wrong, he is Formating it as ext4?

---

### Post by mdcsvt on 2012-11-05
After

$ mount

say answer is 
/dev/sdb1 on /media/usb0  ...

have to 

$ sudo umount /dev/sdb1  (or whatever)

then mount again 

$ sudo mount -t vfat -o defaults,user,exec,uid=1000,gid=1000,umask=000  /dev/sdb1 /media/where-u-want

bye
Salvatore

---

### Post by coffeecat on 2012-11-05
@mdcsvt, this:

> **mdcsvt said:**
> 
$ mount

say answer is 
/dev/sdb1 on [COLOR="Red"]/media/usb0[/COLOR]  ...


...tells us that you have installed the app usbmount. This is the cause of your problem, so please uninstall it. Usbmount is intended for GUI-less server installations and interferes with the USB automounting functionality in the GUI versions of Ubuntu.

Also - if you have a problem that you need help with, please start your own threads rather than tagging onto old ones.

---

### Post by mdcsvt on 2012-11-05
> **coffeecat said:**
> @mdcsvt, this:



...tells us that you have installed the app usbmount. This is the cause of your problem, so please uninstall it. Usbmount is intended for GUI-less server installations and interferes with the USB automounting functionality in the GUI versions of Ubuntu.

Also - if you have a problem that you need help with, please start your own threads rather than tagging onto old ones.


thank you - and sorry
Salvatore

---

