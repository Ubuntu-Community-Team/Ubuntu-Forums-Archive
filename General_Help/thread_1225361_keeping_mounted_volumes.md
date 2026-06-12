---
title: "keeping mounted volumes"
date: 2009-07-28
forum: General Help
---

### Post by zerovashstyle on 2009-07-28
I just recently partitioned my laptop to where i have all my media on one and the OS on the other. When I first mounted the media one it worked just fine but when I restarted my comp it wasnt there anymore and i had to remount it 

Is there anyway I can make it to where i dont have to remount it everytime i restart my comp?

---

### Post by drs305 on 2009-07-28
You can make an entry in fstab. For us to help, we need to know what you want the mountpoint to be (/media/XXX or /mnt/XXX), why type of partition (ext3, ntfs, fat32), and preferably either the label or UUID.

To get the second two:
```

sudo blkid

```

---

### Post by zerovashstyle on 2009-07-28
its /media/misc ntfs and A6FO36C9F0369F8B

---

### Post by drs305 on 2009-07-28
> **zerovashstyle said:**
> its /media/misc ntfs and A6FO36C9F0369F8B


```
sudo cp /etc/fstab /etc/fstab.old  # Make a backup copy.
mkdir /media/misc   # If doesn't exist
sudo chown -R *yourusername*: /media/misc  # Makes you the owner.
gksudo gedit /etc/fstab
```
Substitute your own *username* in the above command.
Making yourself the owner of /media/misc is not necessary.
Add this line:
```

UUID=A6FO36C9F0369F8B /media/misc ntfs  auto,users,uid=1000,umask=027,utf8 0 0

```
This assumes you are user 1000. You can check with the "id" command.
Save the file, then:
```
sudo umount -a  # You will get some busy messages. You can use "sudo umount /dev/sdXX" if you know the designation or "sudo umount /media/misc".
sudo mount -a
```

If you don't get any errors, the partition successfully mounted.
Note: There is a very good app called ntfs-config that can do the above automatically.

---

### Post by zerovashstyle on 2009-07-28
i did all that and i got this message in the terminal

ntfs-3g: Failed to access volume '/dev/disk/by-uuid/A6FO36C9F0369F8B': No such file or directory

and i also got the ntfs-config app and it only mounted my 3rd partition. i have 3 one for ubuntu, vista and media.

---

### Post by drs305 on 2009-07-28
> **zerovashstyle said:**
> i did all that and i got this message in the terminal

ntfs-3g: Failed to access volume '/dev/disk/by-uuid/A6FO36C9F0369F8B': No such file or directory

and i also got the ntfs-config app and it only mounted my 3rd partition. i have 3 one for ubuntu, vista and media.

Just in case the cached UUID is not correct, run the following, then compare the result of the command as well as the UUID in fstab:
```

sudo blkid -c /dev/null
cat /etc/fstab | grep "UUID="

```

If the UUIDs are correct, did you safely unmount the partition the last time you used windows? If not, remount it in Windows and shut down normally.

You can also try to replace the "UUID=XXXXXX" with "/dev/sdXX" if you know the device designation (sdb1, sdc2, etc).

If you can't see the problem, please post your fstab and the results of the blkid command.

---

### Post by zerovashstyle on 2009-07-28
gambit@gambit-laptop:~$ sudo blkid -c dev/null
/dev/sda1: UUID="F6C2A5C6C2A58C05" TYPE="ntfs" 
/dev/sda2: UUID="a36397d2-74f6-400c-9ff4-cf3cc7dd6174" TYPE="ext3" 
/dev/sda3: UUID="A6F036C9F0369F8B" TYPE="ntfs" 


gambit@gambit-laptop:~$ cat /etc/fstab | grep "UUID"
UUID=a36397d2-74f6-400c-9ff4-cf3cc7dd6174 / ext3 relatime,errors=remount-ro 0 1
UUID=A6FO36C9F0369F8B /media/misc ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

