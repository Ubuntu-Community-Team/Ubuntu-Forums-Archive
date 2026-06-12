---
title: "Can't boot 2.6.31-19-generic"
date: 2010-02-12
forum: General Help
---

### Post by kyletstrand on 2010-02-12
Hello, all.

I'm running 9.10 and I'm having a real hard time loading the new 2.6.31-19-generic kernel from the grub2 boot menu.   Whenever I try to load it, it responds with the following error:

"error: You need to load the kernel first.

Press any key to continue..."

It then just kicks me right back to the boot menu.  I checked the grub.cfg file and everything seems to check out and I also checked the settings in grub (pressing 'e' with 2.6.31-19-generic selected...I'm still pretty new with ubuntu, so forgive my simplicity).  I also made sure the file "vmlinuz-2.6.31-19-generic" is in the boot folder.  I also tried manually booting from the grub2 command line using:

```
sh:grub>linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-19-generic
sh:grub>boot

```I might be missing something obvious, but I'm not sure.  As I said, I'm still fairly new with Ubuntu (I love it!), so any help with this would be greatly appreciated!

Thanks!

---

### Post by jerrrys on 2010-02-13
when i run across this the easiest thing to do is just go back one kernel...

---

### Post by kyletstrand on 2010-02-15
The only kernel I'm actually able to run is 2.6.31-14-generic...so I'm quite a ways back.

Beginner question:  Is there any notable/important updates from kernel to kernel?

---

### Post by kyletstrand on 2010-02-17
I guess I can forget about all of this...had to reformat and reinstall.

---

### Post by meierfra. on 2010-02-17
> had to reformat and reinstall.
Why?

Anyway you should have a look at this:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by daka90 on 2010-02-18
Hi everyone,

I upgrade to -19 kernel and as a lots of people ran through troubles...
After launching my computer and choosing ubuntu from the computer display immediatly the grub1.97~BETA4 SHELL
No booting for me too
I've read like 50 pages and figured that going back too -17 was a solution very fine for me.
 so I've looked for a detailed process (found [here]("http://www.omaregan.com/?p=583") )
 applied it but I continuously get a message like 'the magical number is invalid'.
I think the root directory is "broken"...
for root=/dev/sd** the directory simply doesn't exist 

to check my partition I did 
```
sh:grub> ls -l
```and got info on device loop0, UUID
 Device hd0, partition hd0,1, type ntfs,UUID

nothing more when I checked the mapdevice file partion are suposed to be maped in /dev/sda

but in /dev there isn't any sd** file 

...... so don't know what to do next...

And one last thing here:

```
loop=/ubuntu/disks/root.disk ro
```IF /ubuntu is supposed to be an existing directory, this is not here too....

Thanks in advance, great forum !
bye

---

### Post by Akavashi on 2010-02-18
Try booting into an older kernel version and then run in terminal (updates the grub.cfg file):
```
sudo update-grub2
```
Reboot and try new kernel again.

If that doesn't work, reboot into the old kernel version and run this command in terminal:
```
sudo apt-get --reinstall linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-image-2.6.31-19-generic && sudo update-grub2
```
Apart from those, have no other suggestions other than to completely remove the newest kernel version and attempt an update again.
Never had to do this before though, so someone may want to clarify a little more.

---

### Post by meierfra. on 2010-02-18
> IF /ubuntu is supposed to be an existing directory, this is not here too....
"/ubuntu" is supposed to  a directory on your "C:" drive (or whatever drive is containing your Wubi file)

I suggest to first follow these  instructions:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

It cures almost all Wubi boot problems caused by updates.

If this does not work,  and reinstalling the kernels also did not help, please follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run boot info script and post the "RESULTS.txt"

---

### Post by daka90 on 2010-02-18
Fantastic. GREAT. I was beginning to lost hope here !
The patch worked perfectly, I didn't even go back to 2.6.31-17

Thanks for helping
Great community 
Bye :)

---

### Post by j-la on 2010-02-20
Great find as well.  Thank you.  As per the wiki, I updated the wubild file on c:\ and 2.6.31-19 generic was then fine.  Nice wiki, and thank you.

My first post!

---

