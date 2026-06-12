---
title: "What is the first part of a kernel?Can we able to call a c program using initramfs"
date: 2011-03-17
forum: General Help
---

### Post by muhammed irshad on 2011-03-17
Can i add a c program file to initramfs such that it runs when kernel loads and before root file system getting busy...

---

### Post by kiyop on 2011-03-17
Uncompress initramfs and make change as you like and compress into a new intiramfs.

For example,
```
mkdir initrd
cd initrd[FONT=monospace]
[/FONT]gzip -dc /boot/initrd.img-$(uname -r) | cpio -i
[COLOR=red] make change in initrd directory[/COLOR]
```
The file "init" is executed after the initramfs file is loaded.
So, you can add command in "init" to run your c program.
To generate a changed initramfs,
```
find .|cpio -H newc -o|gzip -9 > ../initrd.img-new
```The generated "inirtrd.img-new" is changed initramfs.

If you want to use the generated initramfs instead of the current used one,
```
sudo cp /boot/initrd.img-$(uname -r) /boot/initrd.img-$(uname -r)-backup
sudo cp ../initrd.img-new /boot/initrd.img-$(uname -r)
```Be careful.
If you made bad initramfs, you may not boot the system. In such case, replace /boot/intird.img-... with /boot/initrd.img-...-backup.

---

### Post by muhammed irshad on 2011-03-20
K.....Thank You very much for your reply...
I have 1 more doubt...
How can i access my root files from the c program which runs before root files are mounted....

---

### Post by kiyop on 2011-03-20
I cannot understand what you want to do.

What does "root (/) file system getting busy" means?

Do you want to "access files in / partition before / partition is mounted" ?
I do not know.
You should understand the structure of file system of your / partition.

It may help you to understand the contents of "init" in uncompressed initramfs.;)
It depends on the version of Ubuntu.
There should be "mount" command.

<<Edit at 3/21 13:18 Japan>>

I have got the following message  from you:
[QUOTE=muhammed irshad]Hi Thank you very much for your reply to me
Actually i am doing my mini project which back ups  sum of the essential  OS files.So i require this while restoring the os files.Because it may  be busy during runtime.
But I have a doubt in this.
Initramfs is the minimal root rite?
So will it be able to access the actual root by my c program in order to restore it?
If possible how can i specify the root files to my program?Can i specify it simply giving path to it?
Can you please reply for it.....[/QUOTE]

Of course, you can mount the actual root partition by the command "mount".
You can rewrite "init" as you like.

---

