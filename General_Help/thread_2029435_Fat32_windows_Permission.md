---
title: "Fat32 /windows Permission"
date: 2012-07-19
forum: General Help
---

### Post by sdglinux on 2012-07-19
Recently installed 12.04 on dedicated PC (AMD cpu, 32bit)
4 Partitions put on Hard Drive (root /,  swap, /home, /windows) during install.
Ubuntu PC is in a home network with 3(2 Windows XP, 1 Windows 7) PCs, and 2 iPads.
Using Nautilus, sharing select  /home folders on windows PCs works like a champ.
/windows is useless at sharing as it is root owned and will not allow permission change.
I can create folders in /windows and drag files from /home  to those folders but cannot share anything on a Windows PC that is in /windows.
Using searches I have tried all kinds of forum posted solutions and avoided solutions that only a user of many years experience can understand. 
1.  Bottom line is, how can I change the permission of the /windows partition from root to user and make it useful? 
2.  I had hoped to use this Ubuntu PC as a file access device for the home network and eventually change my two XP machines to Ubuntu machines.   
3.  Any help in the form of step by step would sure be appreciated.  Thanks.

---

### Post by t0p on 2012-07-19
I'm not sure if this will work with 12.04... but with earlier versions I'd open a terminal, enter command

```
gksudo nautilus
```

and that would have given me an instance of Nautilus (file manager) with superuser powers.  Then navigate to /windows, change permissions - then once done, kill that superuser instance of Nautilus before you screwed up something with it!

Like I said, that would've been my pre-12.04 method. But maybe someone knows a better way nowadays.

---

### Post by sdglinux on 2012-07-19
gksudo nautilus is what I have used on /home folder sharing and it works fine there on 12.04.  However, on 12.04, it will not work on /windows  to change  permission or owner and I cannot tell from your answer as to whether it worked on a /windows owned by root in your prior to 12.04 version.

In a previous ubuntu/windows dual boot system that I built, where ubuntu had its own drive with a /windows partition and windows was on another drive, there was no problem with the two systems "sharing" using the /windows partition as both systems are not running at the same time.  Thus, Ubuntu is not "protecting" /windows when Windows is the booted system and Ubuntu can mount and share any partition on the Windows drive when Ubuntu is the booted system.

I suspect that no one knows how to do what I am asking (change permission, or owner, of the /windows partition on 12.04) and that you should NEVER use at FAT32 /windows on a standalone drive/PC with Ubuntu.  Even though Ubuntu allows you to partition that way it is useless as it cannot share with Windows over a network.  Anybody agree or disagree?

---

### Post by idoitprone on 2012-07-19
> **sdglinux said:**
> gksudo nautilus is what I have used on /home folder sharing and it works fine there on 12.04.  However, on 12.04, it will not work on /windows  to change  permission or owner and I cannot tell from your answer as to whether it worked on a /windows owned by root in your prior to 12.04 version.

In a previous ubuntu/windows dual boot system that I built, where ubuntu had its own drive with a /windows partition and windows was on another drive, there was no problem with the two systems "sharing" using the /windows partition as both systems are not running at the same time.  Thus, Ubuntu is not "protecting" /windows when Windows is the booted system and Ubuntu can mount and share any partition on the Windows drive when Ubuntu is the booted system.

I suspect that no one knows how to do what I am asking (change permission, or owner, of the /windows partition on 12.04) and that you should NEVER use at FAT32 /windows on a standalone drive/PC with Ubuntu.  Even though Ubuntu allows you to partition that way it is useless as it cannot share with Windows over a network.  Anybody agree or disagree?

fat32 permission are determined on mount. After it is mounted it cannot change

umount it and remount it with the correct permissions. it is the only way

---

### Post by sdglinux on 2012-07-19
I guess I will give up.  I used the Storage Device Manager to unmount, mount and change owner.  Everything seems to set up fine in Ubuntu with no messages or errors but when I go to the Windows PC and try to open the folder it says I do not have permission.  Plus, it does not even ask for any ID or PW meaning it is totally locked up access wise to Windows.

So, it must not be possible.  I think I will look into changing the /windows partition (get rid of FAT32) to something that will share like /home does on 12.04.  Thanks for your assistances.

---

### Post by oldfred on 2012-07-19
Are you having issues with a Windows formated partition on one computer or with Samba from another?

If just one computer:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I also do not recommend FAT32 anymore. Ok for small devices like those with a camera or phone, but any file over 4GB will be truncated. I lost (luckily did not need) all my backups that I thought I had saved into a FAT32 partition. For some reason they were all 4GB and even as I kept using system they were still 4GB. Then I learned that was the limit. 
FAT32 also does not have a journal. File recovery from a small device will not matter but if larger you need a journal to have any hope of repair.

---

