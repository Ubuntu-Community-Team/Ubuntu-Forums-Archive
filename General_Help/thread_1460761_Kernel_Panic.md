---
title: "Kernel Panic"
date: 2010-04-23
forum: General Help
---

### Post by joelw135 on 2010-04-23
I have version 10.4 running on my computer, but when I boot I get a kernel panic. I then restart hit ESC and load a previous working copy. How do I reinstall over my 10.4 without loosing my programs etc? Thanks. my problems started after a normal morning update.

---

### Post by klemes on 2010-04-23
Yes today we got a new kernel(I at least got it today...)2.6.32-21.
If I get it right you are still able to boot with the older kernel(s) but no joy with the new one....correct me if I am wrong.
Then I would definately first try to reinstall the newest kernel by something like 
sudo dpkg-reconfigure linux-image-2.6.32-21-generic

or even better 

sudo apt-get install --reinstall  linux-image-2.6.32-21-generic

Then reboot with the new kernel to see now if it's working.
If not and you still get a kernel panic try rebooting using [Alt+SysRq+R+E+I+S+U+B] and boot from GRUB with an older kernel and see the kernel logs for details about the last crash.

---

### Post by joelw135 on 2010-04-23
> **klemes said:**
> Yes today we got a new kernel(I at least got it today...)2.6.32-21.
If I get it right you are still able to boot with the older kernel(s) but no joy with the new one....correct me if I am wrong.
Then I would definately first try to reinstall the newest kernel by something like 
sudo dpkg-reconfigure linux-image-2.6.32-21-generic

or even better 

sudo apt-get install --reinstall  linux-image-2.6.32-21-generic

Then reboot with the new kernel to see now if it's working.
If not and you still get a kernel panic try rebooting using [Alt+SysRq+R+E+I+S+U+B] and boot from GRUB with an older kernel and see the kernel logs for details about the last crash.

Tried that and get the following on boot. Kernel Panic - not syncing: Unable to mount root fs on unknown-block(0,0)..

Any ideas?

---

### Post by gawadelnil2002 on 2010-04-23
> **joelw135 said:**
> Tried that and get the following on boot. Kernel Panic - not syncing: Unable to mount root fs on unknown-block(0,0)..
 
Any ideas?
 
yes I have one it worked for me when i got gave up waiting rooting device
I just replaced that line in grub menu by pressing "E" on the menu entry the find
root=uuid=xxxxxxxxxxxxxxxxxxxxxxxxxx
and make it
root=yyyyyyyyyyyyyyyyyyyyyyy
where x is ur partition uuid
and y is the partition name in the form /dev/sda
it may /dev/sda1 or /dev/sda2 or /dev/sda3 it depend on ur partition

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> yes I have one it worked for me when i got gave up waiting rooting device
I just replaced that line in grub menu by pressing "E" on the menu entry the find
root=uuid=xxxxxxxxxxxxxxxxxxxxxxxxxx
and make it
root=yyyyyyyyyyyyyyyyyyyyyyy
where x is ur partition uuid
and y is the partition name in the form /dev/sda
it may /dev/sda1 or /dev/sda2 or /dev/sda3 it depend on ur partition

OK that is way above my skill level, so I am lost.

---

### Post by klemes on 2010-04-23
It seems that your kernel is booting fine but does not find the root partition leading to kernel panic.
Could you try a 
sudo update-initramfs -u /boot/initrd.img-2.6.32-21-generic
and try rebooting with the new kernel (....-21) and report bac?.It could not hurt as you have already a non-running kernel and this command only used to create (update) the kernel modules and other stuff the kernel needs to boot properly. 
Always remember to Alt Sysrq REISUB in case it goes wrong again.
And maybe list your complete /boot/grub/grub.cfg this time before you do anything else just in case along with the output of sudo blkid command?

---

### Post by klemes on 2010-04-23
> **joelw135 said:**
> OK that is way above my skill level, so I am lost.


Do not panic I am sure it is something easily fixable.
And in any case you still have a working system.....:):popcorn:

---

### Post by joelw135 on 2010-04-23
> **klemes said:**
> It seems that your kernel is booting fine but does not find the root partition leading to kernel panic.
Could you try a 
sudo update-initramfs -u /boot/initrd.img-2.6.32-21-generic
and try rebooting with the new kernel (....-21) and report bac?.It could not hurt as you have already a non-running kernel and this command only used to create (update) the kernel modules and other stuff the kernel needs to boot properly. 
Always remember to Alt Sysrq REISUB in case it goes wrong again.
And maybe list your complete /boot/grub/grub.cfg this time before you do anything else just in case along with the output of sudo blkid command?

Still get kernel panic. When I hit ESC at boot the kernel I choose and that loads is 2.6.32-21 generic. So it seems like I have the right kernel. So how would I delete the two lines in the menu so I boot from the working kernel?

---

### Post by gawadelnil2002 on 2010-04-23
> **joelw135 said:**
> OK that is way above my skill level, so I am lost.
ok If you can boot with the old kernel
I will make u do it by very simple way
type that in terminal
```
sudo gedit /etc/default/grub
```
it will ask u for ur password just type ur password then ENTER
search for that line it will the in the last 3 or 4 line
```
#GRUB_DISABLE_LINUX_UUID=true
``` 
just uncomment it to be like
```
GRUB_DISABLE_LINUX_UUID=true
```
then close gedit and save 
then update grub by
```
sudo update-grub
```
then reboot and see
I hope u can do it 
there is no harm in that dont worry
Dont forget to tell me what happened ?

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> ok If you can boot with the old kernel
I will make u do it by very simple way
type that in terminal
```
sudo gedit /etc/default/grub
```
it will ask u for ur password just type ur password then ENTER
search for that line it will the in the last 3 or 4 line
```
#GRUB_DISABLE_LINUX_UUID=true
``` 
just uncomment it to be like
```
GRUB_DISABLE_LINUX_UUID=true
```
then close gedit and save 
then update grub by
```
sudo update-grub
```
then reboot and see
I hope u can do it 
there is no harm in that dont worry
Dont forget to tell me what happened ?

It loads Grub edit, but there is nothing in the file.

---

### Post by gawadelnil2002 on 2010-04-23
> **joelw135 said:**
> It loads Grub edit, but there is nothing in the file.
try again its there just to make sure
sudo gedit /etc/default/grub```
sudo gedit /etc/default/grub
```
all small letters
 
I'm sure its there im very sure u should have it to make grub working and if u dont have it so that is the probelm cause everytime u install new kernel grub will upadet itself using this file and if u dont have it we may get probelms like urs
search again even go using nautilus into etc then default then u will see grub there

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> try again its there just to make sure
sudo gedit /etc/default/grub```
sudo gedit /etc/default/grub
```
all small letters

Typed as shown but the file has nothing in that I can see.

---

### Post by gawadelnil2002 on 2010-04-23
> **joelw135 said:**
> Typed as shown but the file has nothing in that I can see.
go using nautilus to /etc
then search for default directory
open it
then search for grub
if u dont have it tell me
and tell me is it grub2 or what ??
I did te same like i was talking 1 hour ago the file was there on ubuntu 10.4

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> go using nautilus to /etc
then search for default directory
open it
then search for grub
if u dont have it tell me
and tell me is it grub2 or what ??
In the etc/default there is grub.d and that is it. I tried using your command and instead of grub I used grub.d and got an empty text file.

---

### Post by gawadelnil2002 on 2010-04-23
> **joelw135 said:**
> In the etc/default there is grub.d and that is it. I tried using your command and instead of grub I used grub.d and got an empty text file.
grub is not insatlled as it should be on ur system
what live cd u used and it version?
does it the RC one or what ??
i think that the probelm that grub is not installed well
 
    I'm with u tell the end

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> grub is not insatlled as it should be on ur system
what live cd u used and it version?
does it the RC one or what ??
i think that the probelm that grub is not installed well

I installed it using update-manager -d

---

### Post by klemes on 2010-04-23
It is important to now what version of grub you have installed.
For making sure type in the console:

dpkg -l |grep grub


note the letter after the dash (-) is small L,
and the character after the small L is the special character (don't know it's name sorry)
you get with SHIFT pressed  plus the '\' (slash)symbol.

---

### Post by klemes on 2010-04-23
> **joelw135 said:**
> I installed it using update-manager -d

Then you may have GRUB1 also known as GRUB-legacy still installed.
That's why we were not able to find an /etc/default/grub entry.
But if its indeed grublegacy then you must have a menu.lst file in /boot/grub directory.
Could you please paste it's contents here?

---

### Post by joelw135 on 2010-04-23
> **klemes said:**
> It is important to now what version of grub you have installed.
For making sure type in the console:

dpkg -l |grep grub


note the letter after the dash (-) is small L,
and the character after the small L is the special character (don't know it's name sorry)
you get with SHIFT pressed  plus the '\' (slash)symbol.

I have the following for grub 0.97-29ubuntu60 and for grub common 1.98-lubuntu5

---

### Post by gawadelnil2002 on 2010-04-23
U had to say that from begening that u have the old grub still
look I always like and i heared people recopmmend to install the system using the cd not by upgrading alot of probelms happening by upgrading form version to another
 
I installed the system 2 hours ago using a cd then i got a problem like urs
i couldnt boot the first time to ubuntu cause i got kernel panic on my sata harddisk that the kernel cant find root device 
i solved it like i told u by editing the grub entry
 
so as i see on google now
u should upgrade grub when ur ubuntu upgraded and if u didnt try to do that 
```
sudo update-from-grub-legacy
```
then
then update grub again using "sudo update-grub" without "
so grub well be installed proberly and try again
if it didnt work
just creat urself the file missing 
by the same order
```
sudo nano /etc/default/grub
```
u will have empty file
I will give u what u should put in it but tell me first what u did

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> U had to say that from begening that u have the old grub still
look I always like and i heared people recopmmend to install the system using the cd not by upgrading alot of probelms happening by upgrading form version to another
 
I installed the system 2 hours ago using a cd then i got a problem like urs
i couldnt boot the first time to ubuntu cause i got kernel panic on my sata harddisk that the kernel cant find root device 
i solved it like i told u by editing the grub entry
 
so as i see on google now
u should upgrade grub when ur ubuntu upgraded and if u didnt try to do that 
```
sudo update-from-grub-legacy
```
then
then update grub again using "sudo update-grub" without "
so grub well be installed proberly and try again
if it didnt work
just creat urself the file missing 
by the same order
```
sudo nano /etc/default/grub
```
u will have empty file
I will give u what u should put in it but tell me first what u did

OK I am waiting for the text to enter by cut and paste correct?

---

### Post by gawadelnil2002 on 2010-04-23
U should too have grub-pc installed 
U have alot of missing packages Dont upgrade like that again believe me sometimes it works another times it will make u sad
ubuntu is very good if we take care about what we do 
alot of times before i didnt sleep trying to fix stuff i dont form where i get it

---

### Post by gawadelnil2002 on 2010-04-23
> **joelw135 said:**
> OK I am waiting for the text to enter by cut and paste correct?
 just wait u have to do that first
 
```
sudo apt-get update && sudo apt-get remove --purge ubuntu-desktop && sudo apt-get install ubuntu-desktop && sudo apt-get dist-upgrade
```
then
```
sudo update-from-grub-legacy
```
then reboot and if didnt work u will find the text
:)

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> U should too have grub-pc installed 
U have alot of missing packages Dont upgrade like that again believe me sometimes it works another times it will make u sad
ubuntu is very good if we take care about what we do 
alot of times before i didnt sleep trying to fix stuff i dont form where i get it

What do I do next, I have the empty grub file open.

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> just wait u have to do that first
 
```
sudo apt-get update && sudo apt-get remove --purge ubuntu-desktop && sudo apt-get install ubuntu-desktop && sudo apt-get dist-upgrade
```
then
```
sudo update-from-grub-legacy
```
then reboot and if didnt work u will find the text
:)

The last command sudo update-from-legacy said no such command found

---

### Post by gawadelnil2002 on 2010-04-23
here is the file itself take it all and put in /etc/default, its in the attached files
the file is called grub.txt rename it to only grub without .txt first
again make sure that u did all what i told u
make sure that installed grub-pc

---

### Post by gawadelnil2002 on 2010-04-23
i dont know if u have grub-pc its should work the last line
sudo apt-get install grub-pc
```
sudo apt-get install grub-pc && sudo apt-get install grub2
```
then use the last line again it will work and i will see if it right or not the line

---

### Post by gawadelnil2002 on 2010-04-23
see that its all explained [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
 
I hope I can help you

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> i dont know if u have grub-pc its should work the last line
sudo apt-get install grub-pc
```
sudo apt-get install grub-pc && sudo apt-get install grub2
```
then use the last line again it will work and i will see if it right or not the line

When I installed from the first line a dialog came up about installing grub2 and I couldn't get out of that window. I have to head for work now. I hope I can get this resolved. Thanks for all the help. Also that line did not work no command found.

---

### Post by gawadelnil2002 on 2010-04-23
> **joelw135 said:**
> When I installed from the first line a dialog came up about installing grub2 and I couldn't get out of that window. I have to head for work now. I hope I can get this resolved. Thanks for all the help. Also that line did not work no command found.
Never give up
u can get out of the annoying window by using TAb key then choose what u want accept or refuse installing
the line will not work untill u install grub2 and grub-pc

---

### Post by joelw135 on 2010-04-23
> **gawadelnil2002 said:**
> Never give up
u can get out of the annoying window by using TAb key then choose what u want accept or refuse installing
the line will not work untill u install grub2 and grub-pc

I ran the commands then used the tab key and when I boot now it comes up to the boot menu allowing me to choose what to boot from. What did I do wrong now?

---

### Post by joelw135 on 2010-04-23
OK I ran the commands and when I boot now it goes directly to the boot menu and if I let it stand it boots in 12 seconds. How do I get it to bypass the boot menu and just boot up?

---

### Post by delmore on 2010-04-29
I had a similar problem to yours and was able to fix it the following way:

# First make sure your sources are up to date and you have all the latest upgrades installed:

```
sudo apt-get update && sudo apt-get upgrade
```

# Now reinstall the 2.6.32-21-generic kernel:

```
sudo apt-get install --reinstall linux-image-2.6.32-21-generic
```

# Finally, update Grub2 :

```
sudo update-grub2
```

# Reboot.

---

### Post by nucz on 2010-05-02
hi there, 
I am new in linux and ubuntu.
I downloaded ubuntu 10.4LTS and installed it in my computer side by side with my windows 7. I have 3 partitions in my windows 
and install ubuntu in partition /e. Everthing go smooth and I am able to boot into ubuntu and using it.

The problem start when my ubuntu get panic after update I made (using package update in ubuntu). I get this message:
```

[     1,220776] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
```


I already read this forum but still dont understand what to do. Anybody can help me step by step. 

In my boot menu I have:

> Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

When I choose Ubuntu, with Linux 2.6.32-21-generic, I get:
> [     1,220776] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

When I choose Ubuntu, with Linux 2.6.32-21-generic (recovery mode), I get same problem.

When I press 'e' to edit commands, I get this screen:
> GNU GRUB version 1.98-1ubuntu5
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 736bcb40-6c3e-4520-9463-421b3e8ab\ab0
linux /boot/vmlinux-2.6.32-21-generic root=UUID=736bcb40-6c3e-4520-9\463-421b3e8abab0 ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic

When I press c, I get this screen:
grub>

what should I type here ???
I dont now how to make sudo command since I cannot entering my Ubuntu.

---

