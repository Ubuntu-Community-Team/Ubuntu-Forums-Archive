---
title: "Running bootable iso image with kexec"
date: 2011-04-09
forum: General Help
---

### Post by ntesla123 on 2011-04-09
I just tried to run the command

```

kexec memtest86-4.0.iso

```To boot into memtest86 using kexec.

This is the output:
Cannot determine the file type of memtest86-4.0.iso

How am I supposed to do this?

---

### Post by kiyop on 2011-04-09
I could not succeed in booting memtest86 by kexec.

You should first loop-mount the iso file.
```
sudo mount -o loop memtest86-4.0.iso /mnt
```You may need to add "-t iso9660".

In my case, I downloaded [http://www.memtest.org/download/4.00/memtest86+-4.00.iso.zip](http://www.memtest.org/download/4.00/memtest86+-4.00.iso.zip) and unzipped.

Then, you can find the kernel to be "kexec'ed".
```
ls /mnt/boot
```I tried to kexec by
```
kexec -l /mnt/boot/memtest.img
```but the following error message came:
Cannot determine the file type of ./memtest.img

"file" command tells:
memtest.img: Linux x86 kernel

I do not know how to boot "Linux x86 kernel" by kexec.

"kexec --help" tells me there is option "-t" with type:
multiboot-x86
elf-x86
beoboot-x86
nbi-x86

---

