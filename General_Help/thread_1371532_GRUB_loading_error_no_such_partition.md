---
title: "GRUB loading error: no such partition"
date: 2010-01-03
forum: General Help
---

### Post by vyszard on 2010-01-03
I have my netbook on dual-boot, Ubuntu Netbook Remix and Windows 7. Just now I'm trying to shrink C: drive of Windows to give more spaces for UNR and my data. Surely, it has to be done on restart. I expect to see partition wizard to edit my partition, but what showed up on booting is:

GRUB loading.
error: no such partition
grub rescue>

Doesn't matter what I type, it always says "Unknown command"
Well now I realize that I accidentally delete the whole ubuntu partition on the process. I still have my windows 7, though. Is there any way to skip this GRUB process?

[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

I tried using my USB flash disk to boot and reinstall ubuntu, but all I got is a blank black screen with blinking cursor at top-left. And I can't do anything about it.

Please help, this is so urgent I need some of my files and I need it really bad.

---

### Post by vyszard on 2010-01-03
Now I found two commands that work, but I have absolute no idea what's that mean.
When I enter ls:

grub rescue> ls
(hd0) (hd0,3) (hd0,2) (hd0,1) (fd0)

When I enter set:

grub rescue> set
prefix=(hd0,5)/boot/grub
root=hd0,5

---

### Post by Leppie on 2010-01-03
> **vyszard said:**
> Now I found two commands that work, but I have absolute no idea what's that mean.
When I enter ls:

grub rescue> ls
(hd0) (hd0,3) (hd0,2) (hd0,1) (fd0)

When I enter set:

grub rescue> set
prefix=(hd0,5)/boot/grub
root=hd0,5

then:
```
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro		
initrd /initrd.img		
boot
```

---

### Post by vyszard on 2010-01-04
> **Leppie said:**
> then:
```
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro		
initrd /initrd.img		
boot
```

I tried it, but all I got is "error: no such partition"

I think the problem here is windows 7 has already deleted ubuntu partition, but I don't know why it is still loading to the GRUB instead of windows.

I need to skip this GRUB and boot directly to windows, so I can fix the partition and reinstall ubuntu. But how can I do that?

---

### Post by xxterry1xx on 2010-01-04
> **vyszard said:**
> I tried it, but all I got is "error: no such partition"

I think the problem here is windows 7 has already deleted ubuntu partition, but I don't know why it is still loading to the GRUB instead of windows.

I need to skip this GRUB and boot directly to windows, so I can fix the partition and reinstall ubuntu. But how can I do that? if you got the windows 7 cd then boot it up go to repair my computer go to command prompt and type fixmbr and reboot

---

### Post by vyszard on 2010-01-04
> **xxterry1xx said:**
> if you got the windows 7 cd then boot it up go to repair my computer go to command prompt and type fixmbr and reboot

Well, fixmbr still didn't work, so I end up booting up windows 7 with flash disk (no DVD-ROM in my netbook) and reinstall everything, boot again with UNR 9.10, delete all windows partition and install it. No more dual booting on my side :lolflag:

Thanks, though.

---

### Post by Craig21 on 2010-01-09
I have the same problem. I cannot boot from a disc though because the external optical drive is going into repair and I do not have a USB stick to correct the issue.

Is there any other way that I could recover and do this without using the above methods please?

It's really important that I get the Acer Aspire One Netbook back to it's previous state or at the very least boot into the Ubuntu Netbook Remix which I had tried to dualboot with Windows Vista.

If you can help me it would be much appreciated.

Craig.

---

### Post by floydsp on 2010-01-09
If you put your cd of win7 in and when it loads go to repair then startup repair. it will write win7 boot and no more grub

floydsp

---

### Post by Craig21 on 2010-01-09
> **floydsp said:**
> If you put your cd of win7 in and when it loads go to repair then startup repair. it will write win7 boot and no more grub

floydsp

It's Windows Vista that I have and I do not have a CD that will recover the system because it's a net-book. As I said above, the external optical DVD, DVD RW drive I have is broke so I'm unable to work from that since it's being returned to be fixed.

It's a Acer Netbook that uses (Acer ERecovery) that had pre-installed software that should recover the net-book. But because I have attempted to install Ubuntu Netbook Remix as a dual-boot it's giving me the same error as above at boot prompt (Grub2 Rescue).

I'm looking for assistance with this command prompt for grub to potentially solve my issue and recover the system. I am unable to recover until I can sort this grub problem and boot to the Ubuntu Net-book Remix that I have installed on sda 7 and sda 8.

I believe Windows Vista is on sda 1 and 2 but it's not booting the correct partition.

Is there anyway that without a CD nor a USB stick someone out there can help me in fixing this issue since it's really important?

Thanks for any assistance with this matter.

Craig

---

### Post by vyszard on 2010-01-09
> **Craig21 said:**
> I have the same problem. I cannot boot from a disc though because the external optical drive is going into repair and I do not have a USB stick to correct the issue.

Is there any other way that I could recover and do this without using the above methods please?

It's really important that I get the Acer Aspire One Netbook back to it's previous state or at the very least boot into the Ubuntu Netbook Remix which I had tried to dualboot with Windows Vista.

If you can help me it would be much appreciated.

Craig.

I don't know any other way... perhaps you can borrow USB stick or external optical drive from your friend?

I'm sorry if it's not really helping.

---

### Post by Leppie on 2010-01-09
> **Craig21 said:**
> I'm looking for assistance with this command prompt for grub to potentially solve my issue and recover the system. I am unable to recover until I can sort this grub problem and boot to the Ubuntu Net-book Remix that I have installed on sda 7 and sda 8.
have you tried some commands?
first try to get to the normal mode:
```
normal
```

then try setting the root:
```
set root=hd0,7
```
you may want to try 8 instead of 7 as well.

do you have a seperate /boot partition?

---

### Post by Craig21 on 2010-01-10
Thanks for replying. I'll try your method Leppie and see if that works. I'm not sure it will though since it seems not to respond to any commands I have inputed so far but it's worth a try.

I have two partitions, I think, two operating systems on different partitions (to protect the windows installation because it's needed for work) but since grub has replaced the windows one it will not boot into windows but I'm confident the Windows installation is still on the net-book.

Thanks again.

EDIT:

Yeah, it's responding back as Unknown Command 'Normal'

---

### Post by Craig21 on 2010-01-10
The Grub Recue responds to these commands by the way. 

grub rescue> insmod /boot/grub/normal.mod
To go to the normal grub prompt.

grub> insmod /boot/grub/ext2.mod
To load ext2 module.

I tried that but the result was error: _**no such partition**_.

---

### Post by Leppie on 2010-01-10
after the normal command, try issuing "ls" (with lowercase L) to see which partitions it detects.

---

### Post by Craig21 on 2010-01-10
Okay cheers, I'll give that a try.

---

### Post by Craig21 on 2010-01-10
Okay, here is what is listed. (Hd0) - (Hd0,6) - (Hd0,5) - (Hd0,2) - (Hd0,1)

Edit: For some reason my partition seems to be on hd0,7 after entering the command _**set**_. I've tried to change it too the correct one but the commands previously posted on here will not work for me unfortunately.

I have tried the following commands **set root=hd0,x**,**set boot=hd0,x**,**set prefix=hd0,x**. These commands when I type _**set**_  in the display it shows the values that I input. The problem is when I reboot these settings change back to the previous ones so it wont boot from the hd0,x that I put in. 

Can you please tell me, is there any command to save these settings so that it may load these values that I input or will it not make any difference? 

Thanks for your help.

Craig.

---

### Post by Craig21 on 2010-01-13
Anyone know what to do next?

---

### Post by Leppie on 2010-01-13
which version of grub do you have installed? or which ubuntu release do you have installed (and have you upgraded the system)?

you may want to use a livecd to be able to obtain more information.
if would be very helpful if you could [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt.

---

### Post by Craig21 on 2010-01-13
> **Leppie said:**
> which version of grub do you have installed? or which ubuntu release do you have installed (and have you upgraded the system)?

you may want to use a livecd to be able to obtain more information.
if would be very helpful if you could [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt.

It would be using grub that came with the Ubuntu Netbook Remix (the very latest) which is installed but it seems the grub is not loading the correct hd0,x.

I cannot use a CD to fix this issue because the External CD drive that I have is in for repair (it had to be sent away since it was ordered from Amazon) which "might of caused this failure of not being installed correctly on the right partition".

If there was a possibility that I could use a CD that would of been the first thing I would of done and I would of resolved the issue by myself no questions asked. But because it's a bit more complicated in terms of it occurring in grub.

I want to know if anyone on here would know any command that I could input in Grub Rescue that would respond and boot the correct hd0,x if it's possible. That would be a great help for me and for others who run into this problem somewhere down the line and are in the same situation.

If nobody can help me further, I understand and I'd like to thank you for your time.

Cheers. :)

---

### Post by Leppie on 2010-01-13
new try:
```
insmod normal
set root=(hd0,7)
insmod linux
insmod ext2
linux /vmlinuz root=/dev/sda7
initrd /initrd.img
boot
```

if hd0,7 doesn't work, try hd0,6

---

### Post by Craig21 on 2010-01-13
> **Leppie said:**
> new try:
```
insmod normal
set root=(hd0,7)
insmod linux
insmod ext2
linux /vmlinuz root=/dev/sda7
initrd /initrd.img
boot
```if hd0,7 doesn't work, try hd0,6

insmod normal = unknown command

set root=(hd0,6) = There is no error message saying the partition cannot be found on this one.

indmod ext2 = works.

insmod linux = Unknown command "insmod"

linux /vmlinuz root=/dev/sda7 = Unknown command "linux"

And the other two commands are unknown as well. It's getting annoying now, thanks for your help though.

---

### Post by Leppie on 2010-01-13
how about this one:
```
insmod /boot/grub/normal.mod
set root=(hd0,6)
insmod /boot/grub/linux.mod
insmod ext2
linux /vmlinuz-2.6.31-17-generic root=/dev/sda7
initrd /initrd.img-2.6.31-17-generic
boot
```

do you remember which kernel version you do have installed for sure?

---

### Post by Craig21 on 2010-01-13
I'm not absolutely sure on that mate because I was never able to boot up into the UNR since after I installed it it went to Grub Rescue.

I'd imagine it was the kernel that was put on the CD though.

What I initially did was delete Mandriva 2010 and what should be installed on the net-book is UNR and Windows Vista.

---

### Post by Leppie on 2010-01-13
then you might want to try to substitute the "17" with 14, 15 or 16.

---

### Post by Craig21 on 2010-01-13
> **Leppie said:**
> then you might want to try to substitute the "17" with 14, 15 or 16.

Thanks, I'll give that a try.

---

### Post by Leppie on 2010-01-13
> **Craig21 said:**
> Thanks, I'll give that a try.
keep us posted

---

### Post by Thumbrchelb on 2010-01-13
I had this error as well, but the best solution is install on empty hard drive to primary partition sda1 and keep some free space for  ntfs or fat32 if needed. Internal hard drives must be unplugged before and during install.

---

### Post by Leppie on 2010-01-13
> **Thumbrchelb said:**
> I had this error as well, but the best solution is install on empty hard drive to primary partition sda1 and keep some free space for  ntfs or fat32 if needed. Internal hard drives must be unplugged before and during install.
i don't know how easy/difficult it is to disconnect the hd in his netbook.

---

### Post by Thumbrchelb on 2010-01-13
> **Leppie said:**
> i don't know how easy/difficult it is to disconnect the hd in his netbook.
If disconnection of a HD is impossible for some reason the only advice is to be sure that Ubuntu setup places boot record on the right place, not on the internal HD. Advanced options on the summary screen right before installation process, should be used right sda.

This also can help:
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

---

### Post by rahat_420 on 2010-01-15
insert your winxp disc and boot from cd/dvd
the select the partition in which ubuntu is installed.
it will say you can't install winxp in this partition.then go back and delete the ubuntu partition and press f3 to quit installation and restart your computer.waaalaaaaaaaaaaaa

---

### Post by rahat_420 on 2010-01-15
thanks every body

---

### Post by Craig21 on 2010-01-18
> **rahat_420 said:**
> insert your winxp disc and boot from cd/dvd
the select the partition in which ubuntu is installed.
it will say you can't install winxp in this partition.then go back and delete the ubuntu partition and press f3 to quit installation and restart your computer.waaalaaaaaaaaaaaa

I was unable to do this a few days ago because the external optical disk drive was broke. 

It  came back today, I installed the Windows XP factory CD from another computer but never installed anything (I just let it load the windows files) for the net-book because like I said before the Windows installation was still there.

Now it's back up and running Windows Vista again and it's boot loader. I wont be taking the risk of installing anything Linux on this net-book again (or anything that does not have a built in disk drive) that is for sure. 

Thanks for all your support. :)

---

### Post by errornosuchpartition on 2010-09-05
Hi, I am new to linux, I have an ASUS G73, with Windows 7 64bit. I tried putting ubuntu on side by side, and succeeded, however I had no idea how to use it, and ultimately ended up deleting the taskbar by accident. I figured I would try again the next day so I went back into windows and reformatted the partition that ubuntu was on. The next day I turned on my computer, and got the following error message:

error: no such partition
grub rescue>

Same as most people on this thread. Now I have spent the last couple of days searching for a solution to this, the best one seems to be to use the windows install disk, and have the windows bootlogger override grub. However I am stuck on one thing...

HOW DO I BOOT FROM THE INSTALL DISK IF THE ONLY THING I SEE ON MY SCREEN IS:

error: no such partition
grub rescue>

I have no clue how to boot from the disk from this grub error screen.

Please help.

[UPDATE] Ok, so I configured BIOS to boot from the DVD drive, and I booted up my windows 7 install disk, I got to the command prompt and entered:

bootrec.exe/fixboot

and

bootrec.exe/fixmbr

I exited the command prompt, hit restart, and removed my install disk. When it restarted, it asks to hit a key to boot off the disk, so I restart again and reconfigured BIOS to load from the hard disk. Ok, now here is where my problem is; when I start the computer, it just has a flashing underscore, goes down a line, and then shows a little orange rectangle... what the hell?!?!

---

