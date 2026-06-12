---
title: "VirtualBox on Win 7 with a Ubuntu set up for years"
date: 2010-08-23
forum: General Help
---

### Post by Raymond Day on 2010-08-23
I have VirtualBox on my Windows 7. I have Ubuntu running for years on a 1TB hard drive. I put the hard drive on my Windows 7 and Computer Management see it as "Disk 0" my Windows 7 drive is "Disk 1" The Disk 0 don't have a drive letter. I only see it in My computer manage.

How do I get VirtualBox to boot my Ubuntu hard drive that all ready has Ubuntu install and all set up on it?

-Raymond Day

---

### Post by vijushimpi on 2010-08-24
you mean you have virtual disk ? you have to open it in virtual box.

---

### Post by Raymond Day on 2010-08-28
It was hard. After all this time got it working.

Runing this on a 2 core Atom CPU. It's 64 bit and the motherboard it came out of is 64 bit CPU. I could boot the hard drive with the BIOS set up to boot from it in the Atom CPU. It was running on a cerleron 64 bit. That way it ran very good but not in VirtualBox with Windows 7 running at the same time.

Got VirtualBox to see it by doing commands in the "Adminitrator" CMD window. Have to run it as Adminitrator. Same with VirtualBox. You have to go to the folder in the CMD window were VirtualBox is installed. Then type commands.

I just made a 8GB VirtualBox drive and installed Ubuntu 10, 32 bit server from a CD. It worked real good.

Then hooked up the 1TB drive and with a DOS command got it working. I made a lot of symbolic links to the 1TB drive to set it up like it was. Works good.

I am runing this now on a 2TB drive. My Windows 7 was on a 500GB drive and I copied the 500GB to the first part of the 2TB and I have a NASlite with a 1.5TB drive and DD copied it the the last 1.5TB part of the drive.

Same thing, I had to get VirualBox to see the drive. Took me about 4 hours to get this command right like this:

C:\Program Files\Oracle\VirtualBox>VBoxManage.exe internalcommands createrawvmdk -filename "c:\Users\Raymond Day\.VirtualBox\HardDisks\GreenHD1.vmdk" -rawdisk \\.\PhysicalDrive1 -partitions 3

Never found any good help on line with Google. Just looked at the error messages was getting till I got the command right.

Had to list the drive first to see what partition number is was and that command is:

C:\Program Files\Oracle\VirtualBox>VBoxManage.exe internalcommands listpartition
s -rawdisk \\.\PhysicalDrive1

This is the type of info. I needed when I posted this about a week ago now and no one could say how.

I still don't get why VirtualBox would not run this in 64 bit mode when this Atom CPU is 64 bit. It's Windows 7 64 Bit too. I had to install a new ubuntu 32 bit server from CD and that's how it's working. I know this Atom don't have Hardware Virtualization. I guess it needs that to run in 64 bit mode in VirualBox.

-Raymond Day

---

### Post by Raymond Day on 2010-09-14
I was going to copy my 1TB and 750GB to the 2ND, 2TB drive I have on this system. But it was hard to get VirtualBox to see the other 750GB part.

So I just started to copy file copy it to the other part of the 2GB real hard drive.

I used this command.

cd /mnt/2nd_Drive/green/MEDIA/Disk-0
rsync -av 192.168.2.185::Disk-0 .

But 2 times VirtualBox would like lock up on me! I had to force it closed. My Windows 7 was saying low disk space! I have it on the 2ND 2TB drive but only the 1ST 500GB for Windows 7. I found out VirtualBox does a Snapshot of the drive. So when I was coping it it copied the same to my Window 7 drive and filled up the 500GB of it. Because the 750GB was all most full.

With time I found out can put VirtualBox in a Write-through mode. That like turns off Snapshots.

It would error in DOS when I went to do the Write-through command.

What I did was make a new createrawvmdk with a new name to the same real drive.

Then start VirtualBox and put that new name as it's Storage. Then run the Write-through command on it. That worked and under the Storage can see it say for the drive "(Writethrough, 1.82 TB)"

Here is the DOS commands to that that if it helps others.


```
cd C:\Program Files\Oracle\VirtualBox

VBoxManage.exe internalcommands createrawvmdk -filename "c:\Users\Raymond Day\.VirtualBox\HardDisks\Disk-1_server.vmdk" -rawdisk \\.\PhysicalDrive1 -partitions 3

VBoxManage.exe modifyhd "c:\Users\Raymond Day\.VirtualBox\HardDisks\Disk-1_server.vmdk" --type writethrough

```

Because I deleted the Big Snapshot files I lost all the data for days that changed.

I think it very bad that VirualBox does not auto do a write-through on a createrawvmdk command!

That's how I thought it would be and it took days to find it out by coping lot's of data over to it.

VirtualBox seems to be working very good now. It just takes a lot of time to set it up.

The Write-through command just comes right back and don't say nothing but at lest it don't give a error ether. You have to go to some other menu in BirtualBox then come back to see that it does say "Writethrough" for the drive.

-Raymond Day

---

