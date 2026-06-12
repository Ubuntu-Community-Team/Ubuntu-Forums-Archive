---
title: "Desperate hard drive help needed.."
date: 2012-06-14
forum: General Help
---

### Post by Cameronmx9 on 2012-06-14
I'm going to try and explain my situation as clearly as possible. I'm a CS major and decided that I needed to install ubuntu on my desktop since we will be using the terminal to SSH alot this semester. I have three hard drives, the first is my 40gb SSD which has Windows OS installed, the second is my 250gb spare drive with my music and pictures, the third is my 1tb drive that hasn't been filled much. I initially installed ubuntu on my 1tb drive, but accidentally set the partition size way too large causing it to take up literally the whole drive. I then went into windows and deleted the ubuntu partion myself, which I'm assuming deleted the needed bootloader file. I tried and tried to restore it, but ended up having to reformat windows on my SSD drive. But before the fresh install, I installed ubuntu on the 250gb drive too, thinking that this would allow me to install the correct bootloader, which i didn't. 

Long story short, I am on the ubuntu portion of my 250gb hard drive posting this plea of assistance. I cannot access the 250gb partion that contains my music via Windows without Windows freezing. I can see the hard drive on My Computer, but it doesn't show it's size nor space. I opened up Disk Utility on ubuntu and this is what I see. 

[IMG]http://i49.tinypic.com/vg5to3.png

This is the only method that allows me to even see the other partition that contains my music. I'm sorry if my terminology is off, but I'm a very inexperienced Linux/Ubuntu user. My first try at this OS resulting in failure. Can anyone offer any advice? Thanks in advanced.

---

### Post by Cameronmx9 on 2012-06-14
I installed GParted and this is what I'm seeing. I clicked manage flags on the partition of my drive that I'm wanting to access and this is what shows. Help me please!! :confused:

[IMG]http://i49.tinypic.com/24zgojk.png

---

### Post by gsgleason on 2012-06-14
I cannot imagine what would cause windows to freeze when accessing the 250GB drive's data.

Windows is stupid like that.  Maybe a windows forum might be more appropriate.

If I was in your shoes, I would use ubuntu's disk utility (palimpsest) to format drive, then format volume on the 1TB drive, creating a new windows-compatible filesystem on which you can copy all the music and whatnot from the 250GB drive using ubuntu.

Basically, secure your data FIRST!!!  Get it onto another drive and leave it alone.

Then try to troubleshoot your broken microsoft product.

---

### Post by Financing Dragons on 2012-06-14
I think you may have formated the harddrive to ext which cannot be dirrectly accessed from windows. Are you able to access your music while running ubuntu? If you are, I would suggest what he did, and copy all your data to another harddrive while formatting this drive, for safety.
 
It is an external harddrive right? The 250gb

---

### Post by Financing Dragons on 2012-06-14
from what I see from you gparted output. All your drives seem to be ext which would explain why you can't access from windows. There are various programmes that allow you to access from windows such as. 
 
Check this article out [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows) will let you know what can be done to access ext drives from windows

---

### Post by Cameronmx9 on 2012-06-14
Thanks for the replies guys.. I'm going to give that link a shot and I'll report back. :)

---

### Post by JC Cheloven on 2012-06-14
Cameronmx9:
You probably resized the initial partition of your pics&music disk (ntfs, initially whole disk) to something smaller (~110Gb) from Linux. This is not good practice and leads occasionally to errors, specially since windows7, due to some sector boundary issue. For future occasions, good practices are:
- Resize windows partitions (ntfs) from within windows.
- Create and edit linux partitions (ext4...) from within linux, using live CD.
- Always install Linux AFTER windows. Usually in an extended partition.
- If you accidentally delete the bootloader (grub, as you did), you can reinstall grub ([see here]("https://help.ubuntu.com/community/Grub2/Installing")),or you can reinstall the windows bootloader using a windows install cd. No need to reinstall windows.
- Offtopic: it's better to plan you partition scheme in advance, then actually create the partitions, then install. For example: you don't need 8Gb swap except if you plan to hibernate, and you have 9Gb of left space over there...

As for your present situation: I assume your pics&music being at the 110Gb ntfs partition. That partition is reported in an error status by gparted. May be due to an innapropriate closure of the filesystem, or to something else. Please try to repair this NTFS partition from windows, using windows tools (I don't use windows since years, but I remember names as "partition magic" etc, if the utilities shipped in w7 don't work for you). It's a windows filesystem after all. You have good chances to have a success in that way.

Hope this helps.

---

### Post by jmfal on 2012-06-14
Welcome to Ubuntu

If you want to see if windows is seeing that partition, boot into windows> start button >

right click computer > disk management

and check that it is still formatted as NTFS, you might have to reestablish a path to that drive(partition) in windows explorer or whatever you are using for file management.

Good news is that if you can get to that partition in ubuntu you should be able to listen to your music, I just mounted my win7 hdd and dragged a music file to ubuntu and played it.

There should be a GRUB (boot loader) some times it doesn't show up when you  start/restart.  An easy way to check:

Restart > at setup/boot menu screen> select boot menu> select ubuntu hdd > hit enter>

begin tapping space bar > GRUB screen should show up > select recovery kernal > you'll have some choices> update GRUB>   you'll have to enter your loggin psswrd > when that is done > startx > enter and it should put you in the desktop.

When I install a new OS I unplugg the other hdd's       it eliminates a lot of hassle.

---

### Post by Cameronmx9 on 2012-06-14
No luck yet.. I can't seem to boot into the drive on Windows at all, I can't even get the Grub screen to appear. I can't access the hard drive from another hard drive either, even with the supplied programs that just freeze when trying to access the drive. If I try to open the disk drive at all on ubuntu this is what I see:

[IMG]http://i50.tinypic.com/2e4ffc7.png

---

### Post by jmfal on 2012-06-14
Try unplugging the other hdd's  and  boot into windows, if everything is OK, shut down and unplug win7, and connect hdd wth ubuntu on it.

Once you get to ubuntu desktop open a terminal and do:

```
sudo apt-get install grub
```

then:

```
sudo apt-get update
```

and:
```
sudo apt-get upgrade
```

I did some surfing on the partitioning and  the reason you see that partition is because you created it  when you installed ubuntu, but I'm afraid that your files may be gone.

If you are using the unity desktop open the file manager--folder icon top left and see if that partition is listed as a device-- top left of window--mount it and see if there is anything in there.

Is ubuntu working right when you are not trying to access the other drives(partitions)??

---

### Post by Cameronmx9 on 2012-06-14
> **jmfal said:**
> Try unplugging the other hdd's  and  boot into windows, if everything is OK, shut down and unplug win7, and connect hdd wth ubuntu on it.

Once you get to ubuntu desktop open a terminal and do:

```
sudo apt-get install grub
```then:

```
sudo apt-get update
```and:
```
sudo apt-get upgrade
```I did some surfing on the partitioning and  the reason you see that partition is because you created it  when you installed ubuntu, but I'm afraid that your files may be gone.

If you are using the unity desktop open the file manager--folder icon top left and see if that partition is listed as a device-- top left of window--mount it and see if there is anything in there.

Is ubuntu working right when you are not trying to access the other drives(partitions)??

When I try and open up the Disk Drive via file manager I get this error:

Error mounting: mount exited with exit code 13: Failed to load runlist for $MFT/$DATA.
highest_vcn = 0x108, last_vcn - 1 = 0x141ff
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Yeah Ubuntu seems to be working fine other than this..

---

### Post by jmfal on 2012-06-14
You didn't say that your win7 is OK.

If you still want to partition the 250gb hdd, I would wipe the drive clean, partition it from disk management in 7. Then put ubuntu  on the other if you want, it's your call.

---

