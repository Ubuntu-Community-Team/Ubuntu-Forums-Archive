---
title: "Can not cat into file in FAT32"
date: 2010-11-17
forum: General Help
---

### Post by darkcoffee on 2010-11-17
External HDD is FAT32.  I can edit a file and copy a file into FAT32, but why can I not "sudo cat file1 file2 > file 3"?

---

### Post by coffeecat on 2010-11-17
I have no idea. I can cat several files together in a FAT32 filesystem. However, two points:

You do not need sudo, unless you have mounted your FAT32 filesystem with root-only access, in which case you need to look at your mount options.

In..

> sudo cat file1 file2 > file 3

... there is a space between 'file' and '3' which would give you an output file named 'file' and the error:

```
cat: 3: No such file or directory
```

---

### Post by darkcoffee on 2010-11-17
Typo; the "file 3" should be "file3".  I can not write to a FAT32 external HDD unless I use sudo.  I am using the default options.  I mounted it with "sudo mount /dev/sdb1 /media/usb".  What should I have mounted it with?

---

### Post by coffeecat on 2010-11-17
> **darkcoffee said:**
> I mounted it with "sudo mount /dev/sdb1 /media/usb".  What should I have mounted it with?

Is it not automounting when you plug it in?

**Edit:** sorry, should have added: Some people do seem to have problems with automounting of some devices. This could be down to  the device firmware. Whatever, the problem is uncommon. But if your device is not being automounted, you could try this code. I don't know whether it will work, but it's worth trying.

```
udisks --mount /dev/sdb1
```

---

### Post by DaithiF on 2010-11-17
to mount it with owner and group set to your own id (rather than root)

```
sudo mount blah blah **-o rw,uid=yourname,gid=yourname**

```And the reason why sudo cat file1 file2 > file3 fails on a mount where you don't have write permission is that the sudo only applies to the command before the redirection operator.  To write to that mount you would have had to do:
```
cat file1 file2 | sudo tee file3
```
(assuming you have read-access to file1, file2, if you have neither read nor write then:
```
sudo cat file1 file2 | sudo tee file3
```

but this is a moot point once you get the mount mounted with your id.

---

### Post by TSJason on 2010-11-17
additionally, if you want to redirect output with sudo you have to make it a single command. Something like this:

```
sudo bash -c "cat file1 file2 > file3"
```

---

