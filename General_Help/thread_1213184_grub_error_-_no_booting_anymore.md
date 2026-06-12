---
title: "grub error - no booting anymore"
date: 2009-07-14
forum: General Help
---

### Post by lorenz_b on 2009-07-14
hi folks,

after having Ubuntu running for 5 month without any severe problems, I got a faulty grub today.
I have Ubuntu 64 (9.04) installed on a multiboot machine together with vista 64. The nst_grub.mbr file is located on C:\ on the primary windows partition. However I originally had vista as my main system, I lately switched over and used Ubuntu only in the last couple of weeks. So it is obvious, that there were no changes from the vista side.
Today I was facing an grub error :"minimal BASH-like line editing is supported..." where I have very limited possibilities. I tried to fix grub from the vista side via EasyBCD, but I didn`t know what to do, since the entrys looked ok.
One thing that I did before I got this error was that I put my laptop in ?hibernation/suspend to RAM (Ruhezustand, I am not sure if hibernation is the right term) and waked up succesfully, but then got the error at the next boot event. Additionally I did the regular Ubuntu updates suggested by the system and I did clean my /tmp directory.
Booting into vista is fine, but booting into Linux doesnt work.
Is there anything that I could do to fix this problem. I searched the forum, but I thought that the related problems that I found didnt apply to my situation.
Hopefully there is a solution without the liveCD, because I am abroad and I didnt bring my external CD drive
I hope someone can help.
cheers
Lorenzb

---

### Post by kogger on 2009-07-14
If your problem is booting into Linux again, then you can do that from the grub command-line with something like this:

[http://www.gnu.org/software/grub/manual/grub.html#GNU_002fLinux](http://www.gnu.org/software/grub/manual/grub.html#GNU_002fLinux)

---

### Post by lorenz_b on 2009-07-14
Thanks, I just tried, but find /vmlinuz is giving me "error file not found" and, initrd and boot dont work, they require kernel to be loaded.

---

### Post by kogger on 2009-07-14
Try just:

```
kernel /vmlinuz root=/dev/sdaX
boot
```

Replace X with the partition number linux is installed on.

---

### Post by lorenz_b on 2009-07-14
Just tried this as well, where I cant exactly remember which sda my linux is installed at. but Itried from 1 to 9 where I only have 6 Partitions, and I always got an error back saying like: wrong directory or file.
if it is of any importance:
find /vmlinuz and find /sbin/init is giving me the error file not found.
uuid is giving the following:
(hd0,0) ntfs ...
(hd0,1) ntfs ...
(hd0,2) ntfs ...
(hd0,5) ext3 ...
(hd0,6) ext3 ...(where ... is some numbers and letters)

---

### Post by lorenz_b on 2009-07-15
no ideas?
are there any changes in the booting process that may happen after putting the laptop in hibernation/standby that may caused my problem?

---

### Post by lorenz_b on 2009-07-15
please, someone?

---

### Post by m4tic on 2009-07-15
You could always try your windows cd to repair

---

### Post by lorenz_b on 2009-07-15
windows boots fine, the problem is, that I cant boot into linux

---

### Post by nikhilbhardwaj on 2009-07-15
(hd0,5) ext3 ...
(hd0,6) ext3 ...(where ... is some numbers and letters)

your root is either hd0,5 or 0,6
try this
    
    kernel root (hd0,5)/boot/vmlinuz

now when you press tabafter vmlinuz you'll be able to use autocomplete
if hd0,5 doesnt work try replacing 5 with 6

---

### Post by nacho32 on 2009-07-15
a must have tool burn to cd supergrub boot loader
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by lorenz_b on 2009-07-15
> **nikhilbhardwaj said:**
> (hd0,5) ext3 ...
(hd0,6) ext3 ...(where ... is some numbers and letters)

your root is either hd0,5 or 0,6
try this
    
    kernel root (hd0,5)/boot/vmlinuz

now when you press tabafter vmlinuz you'll be able to use autocomplete
if hd0,5 doesnt work try replacing 5 with 6

thanks for your help. unfortunately kernel root (hd0,5)/boot/vmlinuz is giving me "Error 1: Filename must be either an absolute pathname or blocklist". same happens, when I exchange 5 with 6. :(

---

### Post by lorenz_b on 2009-07-16
I will try super grub disk this weekend. hopefully I can fix the problem.

---

### Post by nikhilbhardwaj on 2009-07-16
> **lorenz_b said:**
> thanks for your help. unfortunately kernel root (hd0,5)/boot/vmlinuz is giving me "Error 1: Filename must be either an absolute pathname or blocklist". same happens, when I exchange 5 with 6. :(

that is because vmlinuz is not there
after you type 
kernel (hd0,5)/boot/vm

now press tab
grub has an auto complete
it'll show you the complete filename such as vmlinuz-2.26.8 or something else depending on the kernel you are using

and you have to type that filename in place of simply vmlinuz

---

### Post by lorenz_b on 2009-07-17
> **nikhilbhardwaj said:**
> that is because vmlinuz is not there
after you type 
kernel (hd0,5)/boot/vm

now press tab
grub has an auto complete
it'll show you the complete filename such as vmlinuz-2.26.8 or something else depending on the kernel you are using

and you have to type that filename in place of simply vmlinuz

I am aware of that, but obviously there is no kernel (hd0,5)/boot/vm... whatever, because using Tab gives me : "Error 11: Unrecognized device string". It doesnt even Tab-complete kernel (hd0,5)/b... or /boo..

---

### Post by lorenz_b on 2009-07-18
the filesystem on my main linux partition seems to be totally f***** up. via the grub menu i can see my home direcitory, which is on another partition, but i cannot see anything on my main partition. Does anyone know how i could fix this?
cheers Lorenz

---

### Post by lorenz_b on 2009-07-19
turned out, that the file system was corrupt, somehow. with help of the live cd and fsck, I could make it boot again, but programs like firefox and thunderbird just dont start any more. any suggestions or links?

cheers Lorenz

---

