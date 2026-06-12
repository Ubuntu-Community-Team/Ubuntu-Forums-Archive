---
title: "Dealing with drives in terminal"
date: 2012-05-17
forum: General Help
---

### Post by zealkaiser on 2012-05-17
I have been trying to learn linux. To learn linux commands and understand it more better I prefer to work only in Terminal. I had learned a lot about linux command but still don know how to deal with filesystem. For instance I know how to use cp,mv,rename,rmdir,mkdir, etc. I also know liltle bit know about /dev/ and can also mount drives.

What I can't do is list all the drives(hard disk, usb, cdrom) and know about their Label, total capacity, filled and free space.

I would prefer if your answer does not need GUI or extra packages to be installed

---

### Post by Cavsfan on 2012-05-17
> **zealkaiser said:**
> I have been trying to learn linux. To learn linux commands and understand it more better I prefer to work only in Terminal. I had learned a lot about linux command but still don know how to deal with filesystem. For instance I know how to use cp,mv,rename,rmdir,mkdir, etc. I also know liltle bit know about /dev/ and can also mount drives.

What I can't do is list all the drives(hard disk, usb, cdrom) and know about their Label, total capacity, filled and free space.

I would prefer if your answer does not need GUI or extra packages to be installed

There are many CLI commands explained here including those involving disk drives.

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by oldos2er on 2012-05-17
```
mount
``` will show you all mounted partitions. ```
sudo fdisk -l
``` lists partitions (mounted or not) and some info about them. ```
df -h
``` shows disk usage in size and percentage used. ```
du
``` shows disk usage too, for files and directories. Use ```
man du
``` for more info.

If you don't have **mc** installed already, you should check it out. It's a great little CLI file manager.

---

### Post by zealkaiser on 2012-05-17
Thanks for reply. The links is very Useful.

The df -h gives me information but only about the mounted drives.

How can I know about drives(Label, Type, Size) which are not even mounted.

---

### Post by CharlesA on 2012-05-17
> **zealkaiser said:**
> Thanks for reply. The links is very Useful.

The df -h gives me information but only about the mounted drives.

How can I know about drives(Label, Type, Size) which are not even mounted.
fdisk will tell you the size.

```
sudo fdisk -l
```

You'd have to use blkid to tell the label.

```
sudo blkid -c /dev/null
```

---

### Post by Cavsfan on 2012-05-17
> **zealkaiser said:**
> Thanks for reply. The links is very Useful.

The df -h gives me information but only about the mounted drives.

How can I know about drives(Label, Type, Size) which are not even mounted.

Enter **man df** to see what the options are for that command.
Preceed man (manual) before any of these commands to see what options exist.

---

### Post by zealkaiser on 2012-05-17
> **CharlesA said:**
> fdisk will tell you the size.

```
sudo fdisk -l
```

You'd have to use blkid to tell the label.

```
sudo blkid -c /dev/null
```
Thanks a lot!!!!!!!

Actually I was trying the fdisk -l command but without sudo :-P So, I thought this command does not work and hence started this thread

What so ever, Thanks a lot!!!!

---

### Post by zealkaiser on 2012-05-18
Is there any way to do it without sudo i.e without root priviledges

---

### Post by Cheesemill on 2012-05-18
> **zealkaiser said:**
> Is there any way to do it without sudo i.e without root priviledges
I would hope not.
fdisk is used for creating and deleting partitions (you are only using the --list option though). I wouldn't want anyone without sudo privileges being able to delete partitions on my machines.

---

### Post by CharlesA on 2012-05-18
> **zealkaiser said:**
> Is there any way to do it without sudo i.e without root priviledges
Nope. You can remove the password prompt from sudo, but that is not recommended.

---

