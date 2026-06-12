---
title: "Computer won't boot up"
date: 2009-10-05
forum: General Help
---

### Post by DanlordUK on 2009-10-05
Yesterday I was watching a video (The Code a Linux documentary actually) and it went blank for a few seconds. When it came back on it was the login screen and it wouldnt display my username and password properly when I entered it so I restarted my computer and it doesnt boot up, not even showing the Ubuntu splash screen with the progress bar, instead I get this;


Boot from (hd0,0) ext3
starting up...
Loading, Please wait
19+0 records in
19+0 records out
kinit: name_to_dev_t (/dev/disk/by-uuid/295ae18f-c186-4a1e-98cc-715447414d25) =dev (8,5)
kinit: trying to resume from /dev/disk/by-uuid/295ae18f-c186-4a1e-98cc-715447414d25
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/062a0411-d9f8-4bbf-a127-533774262650 on /root
failed: invalid arguement
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys/ on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init/.
No init found. Try passing init= bootarg

Busy Box v0.10.2 (ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'Help' for a list of built in commands

(initramfs)  _



Please help as I have some really important files on the HDD and need them desperately, thanks in advance for any help.

---

### Post by pmlxuser on 2009-10-05
try a hard shutdown (press the powr button till it shutdown) and then on again if it says the computer has to check the file system or hard disk allow it... and then see what happens and post back

---

### Post by Giblet5 on 2009-10-05
So, NOW you want to do a backup...after the hardware failure.

That might not be an option but you can try.

Boot from a live CD, mount your filesystem read-only, put a "big enough" thumb drive in, and back up your files. Then run fsck and fix the problems, or reinstall.

It sounds like you have flaky hardware.

---

### Post by DanlordUK on 2009-10-05
> **pmlxuser said:**
> try a hard shutdown (press the powr button till it shutdown) and then on again if it says the computer has to check the file system or hard disk allow it... and then see what happens and post back

I did this last night and I don't get anything else, it just does the normal loading thing with something like GRUB menu and then I got the above. How can I make it do a manual file system check or Harddrive check.


> **Giblet5 said:**
> So, NOW you want to do a backup...after the hardware failure.

That might not be an option but you can try.

Boot from a live CD, mount your filesystem read-only, put a "big enough" thumb drive in, and back up your files. Then run fsck and fix the problems, or reinstall.

It sounds like you have flaky hardware.


I am currently running Ubuntu from the LiveCD so how do I mount my filesystem read-only?

Thanks for your quick responses.

---

### Post by Giblet5 on 2009-10-05
```
sudo fdisk -l | less
```

Look for the first ext3 filesystem.

Let's assume that it is /dev/sda1:
```
sudo mount -r /dev/sda1 /mnt -text3
```

Now, let's make sure it's what we think it is:

```
ls /mnt/home
```

Look familiar? Great! Now, let's pretend we have a thumb drive named "Cruzer" plugged in and it automatically mounted (as it probably will):

```
df /media/Cruzer
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sde1            12251960         64 12507588  3%    /media/Cruzer
```

Cool. Lots of space.

```
cd /mnt
sudo tar -czf /media/Cruzer/backup.tar.gz home
```

Yea! It completed with no errors!

```
cd
sudo (sync;sync;umount /dev/sda1)
fsck -y /dev/sda1
```

That *might* fix the hard disk. If not, you have a backup of your home directory on the thumb drive.

Good luck. Start doing regular backups.

---

### Post by DanlordUK on 2009-10-05
I typed ```
sudo fdisk -l | less
``` and I get this;


```
]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ca51ca4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14628   117499378+  83  Linux
/dev/sda2   *       14629       18706    32756535    7  HPFS/NTFS
/dev/sda3           18707       19457     6032407+   5  Extended
/dev/sda5           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16       15288     3909696    c  W95 FAT32 (LBA)
(END) 
```But it leaves the 'END' part always highlighted and I cannot enter the next command so I close the terminal and enter 

```
sudo mount -r /dev/sda1 /mnt -text3
```I get this however'

```
ubuntu@ubuntu:~$ sudo mount -r /dev/sda1 /mnt -text3
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```I have a Kingston 4GB USB attatched. Any suggestions?

Sorry, I'm very new to Linux.

---

### Post by Giblet5 on 2009-10-05
> **DanlordUK said:**
> I typed ```
sudo fdisk -l | less
``` and I get this;


```
]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ca51ca4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14628   117499378+  83  Linux
/dev/sda2   *       14629       18706    32756535    7  HPFS/NTFS
/dev/sda3           18707       19457     6032407+   5  Extended
/dev/sda5           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16       15288     3909696    c  W95 FAT32 (LBA)
(END) 
```But it leaves the 'END' part always highlighted and I cannot enter the next command so I close the terminal and enter 

```
sudo mount -r /dev/sda1 /mnt -text3
```I get this however'

```
ubuntu@ubuntu:~$ sudo mount -r /dev/sda1 /mnt -text3
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```I have a Kingston 4GB USB attatched. Any suggestions?

Sorry, I'm very new to Linux.


OK, it's not looking so good...
Try all that without the "-text3" option to mount.

Still no good?
Try ```
sudo fsck -y /dev/sda1
```

When/if it completes, try again from the mount-r command, and instead of running fsck again, do ```
sudo (sync;sync;reboot)
``` and see if it boots on its own.

---

### Post by DanlordUK on 2009-10-05
I did this command and it did a lot of things, 

```
sudo fsck -y /dev/sda1
```In the end it said 

```
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 204785/7348224 files (0.8% non-contiguous), 3665203/29374844 blocks

```I did this next - its a history of after the above of what I entered in Terminal and what happened.

```
ubuntu@ubuntu:~$ sudo (sync;sync;reboot)
bash: syntax error near unexpected token `sync'
ubuntu@ubuntu:~$ sudo mount -r /dev/sda1 /mnt -text3
ubuntu@ubuntu:~$ ls /mnt/home
dan
ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ca51ca4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14628   117499378+  83  Linux
/dev/sda2   *       14629       18706    32756535    7  HPFS/NTFS
/dev/sda3           18707       19457     6032407+   5  Extended
/dev/sda5           18707       19457     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              16       15288     3909696    c  W95 FAT32 (LBA)
ubuntu@ubuntu:/mnt$ sudo tar -czf /media/KINGSTON/backup.tar.gz home

gzip: stdout: No space left on device
ubuntu@ubuntu:/mnt$ sudo tar -czf /media/KINGSTON/backup.tar.gz home

gzip: stdout: No space left on device
```'dan' was in the colour blue, my Kingston USB stick is only a 4GB, is there a way to copy just the documents instead of everything or is this what it's doing?

Thank you very much, nonetheless you have been a really big help and I can't thank you enough and I apologise for my lack of knowledge in Linux. 

I am a newcomer to Linux as I've been using Windows for years and haven;t got used to everything yet as I understand none of these commands so I cannot improvise with them for changing a directory or whatever.

---

### Post by Giblet5 on 2009-10-05
You could try using nautilus to selectively copy files from your mounted disk to the thumb drive (after deleting the partial backup).

You could also try booting from the hard disk. It may be fixed now.

---

### Post by DanlordUK on 2009-10-05
Good news and some bad news.

Good news it now boots past the splash screen and I can enter my username and password. Bad thing is when I do that it comes up with a box saying'
```

Xsession: unable to start X session -- no @/home/dan/.xsession@ file,
 no @/home/dan/.xsession@ file no session managers
, no window managers, and no terminal emulators
found: aborting
```I got so excited I thought it was working again, but then my face dropped seeing  :(

However, I can now enter my HDD and see the files, but when I want to copy the most important files, it has an emblem of a box with an X from and It says when i try to copy to my USB drive I do not have permission...help?

---

### Post by Giblet5 on 2009-10-05
Assuming that your username is "bob":
```
sudo chown -R bob:bob /home/bob
```

That will fix the permission problems.

Save your files.

Reinstall.

All of this is what I would expect to see from a system that power-failed while something important was going on.

If that's a possibility, please consider getting a UPS. You can get "broken" ones on craigslist cheap/free and hook them up to cheap car batteries.

I have an APC SmartUPS 1500, hooked to two tractor batteries that are in a metal cabinet on the front porch. That gives me about two hours of run time for BOTH of my workstations.

Good luck from now on.

---

### Post by DanlordUK on 2009-10-05
Awww I appreciate all your help today.
But when I typed that command in the terminal replacing 'bob' with 'dan' it came up with this;
```

ubuntu@ubuntu:~$ sudo chown -R dan:dan /home/dan
chown: invalid user: `dan:dan'
ubuntu@ubuntu:~$ 

```

Thanks for all your help by the way...

---

### Post by DanlordUK on 2009-10-05
:confused: :confused:

What am I I doing wrong with the command? I entered it exactly as you said replacing "bob" with 'dan' and I get an error message on the terminal ;


```
ubuntu@ubuntu:~$ sudo chown -R dan:dan /home/dan
chown: invalid user: `dan:dan'
ubuntu@ubuntu:~$
```


I really need them files and hope you can help.
Thanks in advance.

---

### Post by Giblet5 on 2009-10-05
Do you log in with username "dan"? If so, that should work.

If not, use your login user name.


Here's one way to do it if all else fails (assuming you have a GUI interface at this point):

```
sudo nautilus
```

That should allow you to back up your data.

Then reinstall.

---

### Post by DanlordUK on 2009-10-07
Hey! Sorry for the long delay in response.

I loaded up the computer, changed the session to the failsafe terminal and entered that code you said;

```
sudo nautilus
```

and I could search around the files, changed the permission and then loaded up the LiveCD and copied all my data from the HDD to my USB and now I have my files back!!

Thank you very much,

---

