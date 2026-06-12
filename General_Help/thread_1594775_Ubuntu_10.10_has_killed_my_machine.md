---
title: "Ubuntu 10.10 has killed my machine?"
date: 2010-10-12
forum: General Help
---

### Post by ahayzen on 2010-10-12
Hi

i previously had Ubuntu 10.04 on my machaine and I was trying to install ubuntu 10.10, it started the install started copying the files then if stopped with: 
installer encountered an error copying files 
Errno 5 input/output error.

So i tried it again, same thing. then i tried redownloading the iso and got the same thing. i ahve tried burning on different cd drives and i have also tried using a memory stick. All have come to the same problem.

Next i tried to reinstall the old Ubuntu 10.04 and got:
and error saying something along the lines of
Couldn't complete copy (can't remember exactly) then 
/target/usr/lib/firefox-3.6.3/libxul.so and the same message:
installer encountered an error copying files 
Errno 5 input/output error

So what have i done to my machine? Is it the ISO, CD Drive, computer or the HDD or what? I can't even boot from it anymore because the install wiped the / directory and i am currently writing to you from the live CD.

Please help get my computer running again.

Andy

---

### Post by cek on 2010-10-12
Sounds like a hardware issue.  Since you are able to run from the live CD, likely points to a hard drive issue.  :(

If you already created the partitions you could manually check them by unmounting them from within the live CD session and manually running fsck to see if it gives any errors.

---

### Post by ahayzen on 2010-10-12
thx for the reply. i did that and it resulted in an i/o error, for sda and sda1. But i can see and use all of the files in /home which is on a separate partition. So would a reformat fix this or is it a hard disk fault even though i can read the files? Andy.

---

### Post by Colo2 on 2010-10-12
If it was me, I'd try formatting it before claiming the drive to be dead.

---

### Post by ahayzen on 2010-10-12
ok thx for the help. Is there a command to format? Because i don't think the installer is doing a full format just a quick one. Andy

---

### Post by cek on 2010-10-13
If you know the correct partition the command is simple, but depends on the file system type you want to make.  For now, I'd try something simple like ext3, you can format with the following command in a terminal if the partition is unmounted.

sudo mke2fs -j /dev/sdaX

where /dev/sdaX is the partition you want to format (/dev/sda1 for instance).  Be careful not to format your /home partition (unless you have a back up and want to do that).

---

### Post by ahayzen on 2010-10-13
Thank you for the reply cek.

I reformatted the partition and then tried running:

sudo mkfs.ext4 /dev/sda1 -cc

In terminal and let it run the tests but it came to no problems. I then tried the installer again and it said that it could read from the squashfs (something like a bad sector). So i am downloading another iso of 10.10 from a different location and then i am going to burn that to CD and see if that works.

I will also try your code sek (sudo mke2fs -j /dev/sda1) if that doesn't work.

I will report further when i have tried this CD.

Hopefully i can have my desktop back soon.

Thank you for all your help so far guys.

Andy

---

### Post by viralmeme on 2010-10-13
> **ahayzen said:**
> I was trying to install ubuntu 10.10, it started the install started copying the files then if stopped with: installer encountered an error copying files 
Errno 5 input/output error.

It's a bad burn, or an incompatible DVD player ..

> The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.


---

### Post by mike555 on 2010-10-13
a thumb print on the cd will also return errors , just saying.

---

### Post by ahayzen on 2010-10-13
Ok so i have tried everything and can't get it to work.

i have tried running from a memory stick and installing that way, error.
i have tried burning CD's from different drives and running them in different drives, still error.

The most worrying thing is that i have tried running the old 10.04 install and that failed at 38% with:
'The installer encountered an unrecoverable error. A desktop session will now be run so that you can investigate the problem or try installing again.'

But the interesting thing was that i tried resizing the swap and / partitions and that it got all the way to 38% where as it normally gets about 15%. So is it just a bad sector on part of my HDD, meaning that if i put the partitions in the right place i would be able to dodge the error?

So what should i do now.

many thanks for all your help

Andy

Another thing to note is that i can read perfectly from the files that are stored onto the HDD. So any of the files stored in /home and 'installed' on / I can see, hope that helps.

---

### Post by ahayzen on 2010-10-13
Hi

i have just had a window pop up and say that there was a bug in ubiquity so i clicked report problem and it has submitted my results to this page:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/660085](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/660085)

The bug reporter has attached all of the logs.

Andy

---

### Post by ahayzen on 2010-10-13
Hi everyone

I managed to get it working!!!

i put the iso onto a memory stick. The installer ran and it said failed to copy:

/target/usr/lib/dri/r300_dri.so

i clicked skip and the install continued and finished.

The only thing is that i don't have the r300_dri.so is this file for Ati Radeon cards? Because if it is then i won't need to add it because i have nvidia. i am right in thinking this?

Thank you for your help

Andy

---

### Post by ahayzen on 2010-10-13
Hi everyone
 
Bad news. After installing further applications the system just froze and started presenting errors. Now when i boot it goes to initramfs and i have to use the cli interface. It is presenting the errors no file or directory /proc /sys /dev.
 
I think i have a bad sector on the hdd. Has anyone got any ideas in to how i could get round this or should i just get a new hard drive?     
Thanks again 
 
Andy

---

### Post by ahayzen on 2010-10-18
Hi everyone

I have just received my new HDD that i ordered and I have tried to install Ubuntu 10.10 and 10.04 on it. However as soon as I click install they both instantly say I/O error to /dev/sda. How can i fix this does this mean I have received a faulty HDD or is it another problem. I am becoming desperate now because I need to use the computer to get on with work.

I am going to try putting some old RAM in to see if that fixes it because I did a memory test for about 5Mins and it received loads of errors. Will report back soon.

Does anyone else have any ideas why my computer is not working?

Thanks again.

Andy

---

### Post by ahayzen on 2010-10-18
Hi 
 
Looks like it was a ram problem as the installer has just run fine without any errors. Now i just wish i had known this before at buying a new hard disk.
 
Thanks again 
 
Andy

---

### Post by ahayzen on 2010-10-18
Or not?

The install got right to the end and then it failed to install GRUB.
So I am going to attempt to install it manually. But can anyone think why this is happening, with a new HDD and different RAM?

Andy

---

### Post by ahayzen on 2010-10-18
Hi

OK so I have swapped the ram and that seemed to stop some errors. I managed to install Ubuntu 10.04, the installation ran flawlessly. However I noticed that sometimes my sda drive (new hard disk) would drop off the list of in the partition manager however the BIOS would still recognise the disk. So I think I might have a faulty SATA port, which I will try tomorrow. This would also explain what happen next after the installation. Basically I booted and the first time it came up with loads of errors saying things about not finding files on sda. I then restarted and it booted all the way to the desktop and finally crashed when trying to access the sdb drive. So I restarted and it presented me with the CLI and not even Gnome. So I'm now back to where I am in the first post.

So what is still wrong with my computer?
I have changed:
RAM
HDD
CD drive
Multiple burns of CD image
Multiple downloads of iso
Used a memory stick to install

So the only thing I can think of is that the SATA port or controller has become faulty causing the disk to become unreadable and the presenting i/o errors.

Please tell me if you have any other ideas or tests that you want me to run.

Thanks for your help.

Andy

---

### Post by sandyd on 2010-10-18
> **ahayzen said:**
> Hi

OK so I have swapped the ram and that seemed to stop some errors. I managed to install Ubuntu 10.04, the installation ran flawlessly. However I noticed that sometimes my sda drive (new hard disk) would drop off the list of in the partition manager however the BIOS would still recognise the disk. So I think I might have a faulty SATA port, which I will try tomorrow. This would also explain what happen next after the installation. Basically I booted and the first time it came up with loads of errors saying things about not finding files on sda. I then restarted and it booted all the way to the desktop and finally crashed when trying to access the sdb drive. So I restarted and it presented me with the CLI and not even Gnome. So I'm now back to where I am in the first post.

So what is still wrong with my computer?
I have changed:
RAM
HDD
CD drive
Multiple burns of CD image
Multiple downloads of iso
Used a memory stick to install

So the only thing I can think of is that the SATA port or controller has become faulty causing the disk to become unreadable and the presenting i/o errors.

Please tell me if you have any other ideas or tests that you want me to run.

Thanks for your help.

Andy
most computers have their own diagnostic tools that can be run at boot.
see if yours has one (mine if I press F12, I get a boot device list + the dianostic tools)

---

### Post by matt_symes on 2010-10-18
Hi

When you download the ISO use md5sum to find its checksum and compare it against the ones on the ubuntu website. This will indicate a bad download.

Hmmmm. Seemed to have miss posted. Need more coffee

Kind regards.

---

### Post by ahayzen on 2010-10-18
Thanks guys for your suggestions i will try them tomorrow.
 
However i don't think it is the iso because the 10.04 disk doesn't even work which i have used on many pc's. But a good idea still.
 
Thanks again.
 
Andy

---

### Post by Danny82p on 2010-10-19
Hello All
 
I have the same problem with Ubuntu 10.10 trying to install it in my computer.
I try to install the ubuntu 10.04 also and i get the same error wen it reach at 30%.
 
I hope i din't messup my computer :confused:
 
Please help:(

---

### Post by ahayzen on 2010-10-19
Hi all
 
Firstly my bios unfortunatally doesn't feature any diagnostics tools. So i started using the ones built into the disc. I have found that the new ram doesn't present any errors and that one me my cd's has an error (10.10) and one doesn't (10.04). I will try using the  10.04 disc tomorrow as i have been using the 10.10 disc which has errors. I have also unattached the old hdd as this also seemed to be causing errors. Hopefully the recent i/o errors have been a result of a bad disc.   
 
I will report back tomorrow with more findings. 
 
Also i am sorry to here that someone else has the same issue. Hopefully we will fine the answer soon.  
  
Andy

---

### Post by Danny82p on 2010-10-22
> **ahayzen said:**
> Hi all
 
Firstly my bios unfortunatally doesn't feature any diagnostics tools. So i started using the ones built into the disc. I have found that the new ram doesn't present any errors and that one me my cd's has an error (10.10) and one doesn't (10.04). I will try using the 10.04 disc tomorrow as i have been using the 10.10 disc which has errors. I have also unattached the old hdd as this also seemed to be causing errors. Hopefully the recent i/o errors have been a result of a bad disc. 
 
I will report back tomorrow with more findings. 
 
Also i am sorry to here that someone else has the same issue. Hopefully we will fine the answer soon. 
 
Andy
 
Got any luck fixing your computer?:confused:
 
Im gona try to install windows 7, maybe that will fix it.

---

### Post by Danny82p on 2010-10-23
I just fix my machine installing windows xp.
Is any way that i can install ubuntu directly from a the internet? i hate windows and i dont want to use it in my machine.
I just dont want to mess with cd installers any more, i allways get problems with ubuntu cd installers.

---

### Post by ahayzen on 2010-10-24
Hi

I still haven't fixed my PC, although i think i am getting there. It seems to have narrowed down to either the SATA controller or I/O controller on the Motherboard. I am going to try a few more tests before getting a replacement though.

Good to hear you got your computer running, maybe the CD wasn't burnt correctly or had an error? You could try running from a memory stick if you don't want to use a CD to install.

Andy

---

### Post by K05T4R on 2010-10-31
Hi Andy and Danny, I hate that you guys had problems too, did you find a solution yet  ?
I tried the 10.10 cd and 10.10 live dvd but I couldnt get them to install correctly either.

In my case I am trying to install it on an older machine as its been a secondary pc but even Windows ran on it previously w/out issue..
I've ran lengthy diagnostics specifically for this IDE drive and it found no bad sectors, no communication problems etc, yet I get those messages of "unrecoverable error and error copying files to hard disk.. These SOUND like old Windows errors.

This happened whether I chose to create my own partitions or use the whole thing. I'm abit unhappy w/ the idea that "well it could be a bad disc burn, it could be a bad iso" .. 
Well who is supplying the freaking iso's that seem to be bad if thats the case and yet is found on the Ubuntu site ?!
If you can burn countless iso files regardless of content, successfully, then how is it people are saying well it could be your burn device/speed/media as the problem ?! 
If the machine's hardware checks out fine, then what else is it, iso problem ?! again who is making these *faulty* iso files available to the public on Ubuntu site then ?!

I checked md5 and they match perfectly.. yet still have this problem, you have any luck ?

---

### Post by Danny82p on 2010-10-31
> **K05T4R said:**
> Hi Andy and Danny, I hate that you guys had problems too, did you find a solution yet ?
I tried the 10.10 cd and 10.10 live dvd but I couldnt get them to install correctly either.
 
In my case I am trying to install it on an older machine as its been a secondary pc but even Windows ran on it previously w/out issue..
I've ran lengthy diagnostics specifically for this IDE drive and it found no bad sectors, no communication problems etc, yet I get those messages of "unrecoverable error and error copying files to hard disk.. These SOUND like old Windows errors.
 
This happened whether I chose to create my own partitions or use the whole thing. I'm abit unhappy w/ the idea that "well it could be a bad disc burn, it could be a bad iso" .. 
Well who is supplying the freaking iso's that seem to be bad if thats the case and yet is found on the Ubuntu site ?!
If you can burn countless iso files regardless of content, successfully, then how is it people are saying well it could be your burn device/speed/media as the problem ?! 
If the machine's hardware checks out fine, then what else is it, iso problem ?! again who is making these *faulty* iso files available to the public on Ubuntu site then ?!
 
I checked md5 and they match perfectly.. yet still have this problem, you have any luck ?
Hello K05T4R and everyone.
 
I have just the same question!!!! is a bad iso file or what? 
I have running the windows XP perfectly now in my T4150 E-machine's.
I also try installing with unebooting from the network and wen i run it, the installation don't want to read the partition hard disk..... whata heck? :( 
I'm NOT gonna try to install with the disc because i always get the freaking ""unrecoverable error and error copying files to hard disk"":confused:
 
Can someone help?

---

### Post by ahayzen on 2010-11-02
Hi everyone

I have managed to get my PC working. It took lots of tweaking around but i got it. The final two three things I did to fix my PC were to:

-Leave the PC without Power for a few Days
-Reset the BIOS (By crossing the jumper)
-Plugging the new HDD in a completely different SATA port (and make sure old one wasn't plugged in)

I then installed Ubuntu 10.04 (as i found the other disk had errors as stated in an above post), the install ran smoothly without too many problems. I then decided to run an upgrade to Ubuntu 10.10 and am talking to you now from this machine.

So I'm not perfectly sure what was the cause but from all the posts together it was either:

Faulty HDD (i got a new HDD)
Faulty RAM (First RAM didn't pass MemTest)
Faulty SATA controller (tried in a different port)
Faulty BIOS version (i have done a BIOS update)
Faulty BIOS setting (the reset)
Faulty CD Drive (i have two and have been alternating)
Faulty CD (Some had errors)

Out of those tests it looked to be that the SATA controller was faulty, but it could have been a mixture as i found errors as I went along in most components.

I will mark this thread as solved after a few days of testing (My PC may be hiding the errors).

Andy

---

### Post by finlost on 2010-11-07
Can we officially say that 10.10 is a polished turd?  

I doubt I will ever get to see 10.10 run since it won't install.  I keep getting a squashfs error.  I have burned the ISO to four different disks. I have used two different brands of disks.  I have used two different computers to burn disks.  I have burned at the slowest speed.  I have checked the hash total.  I have ran each disk a couple of times.

---

### Post by wei2912 on 2010-11-07
BTW, you might want to install in Windows. Boot up Windows, open up the CD (as in with file browser) and open up wubi.exe

---

