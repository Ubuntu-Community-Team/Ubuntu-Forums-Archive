---
title: "General question about windows and Ubuntu"
date: 2011-11-28
forum: General Help
---

### Post by Wingsgb on 2011-11-28
I've just built my new server and was debating what OS to use, I tend to go with windows but when deciding on the build at the time I thought Linux Ubuntu would be best for my applications.*

As I've never used linux befor I've been reading up a fair bit. One thing that I noticed was in the latest Ubuntu you could run it inside of windows.

Im interested in this as there is a windows based transcoding software i use. Could i run programs Simultaneously*on both OS if Ubuntu was installed on it's own hdd. *How much added load would there be by doing this.

Thanks

---

### Post by MG&amp;TL on 2011-11-28
There's essentially three options with two (or more!) OSs on the same computer.

1. Use a virtualisation technology like VirtualBox. You can run windows in ubuntu, or ubuntu in windows. You can run apps in both operating systems simultaneously, but generally they don't interact with each other, and the hard disk (virtual and physical) will be separate. You can't save a file to your virtual disk. Slowest method. Very easy to remove.

2. Use wubi. This will modify the Windows Bootloader, allowing you to boot an image of ubuntu instead, or the usual windows. You can't run both simultaneously, and you can't really access files over both. Easy to remove if it goes wrong. Slightly faster.

3. Partition. Have separate partitions and a new bootloader, boot one at a time. You can access file from windows in linux natively, and you can use something like ext2explore for windows to access linux partition files. Fastest method. Quite difficult to remove.

---

### Post by Cavsfan on 2011-11-28
> **MG&TL said:**
> There's essentially three options with two (or more!) OSs on the same computer.

1. Use a virtualisation technology like VirtualBox. You can run windows in ubuntu, or ubuntu in windows. You can run apps in both operating systems simultaneously, but generally they don't interact with each other, and the hard disk (virtual and physical) will be separate. You can't save a file to your virtual disk. Slowest method. Very easy to remove.

2. Use wubi. This will modify the Windows Bootloader, allowing you to boot an image of ubuntu instead, or the usual windows. You can't run both simultaneously, and you can't really access files over both. Easy to remove if it goes wrong. Slightly faster.

3. Partition. Have separate partitions and a new bootloader, boot one at a time. You can access file from windows in linux natively, and you can use something like ext2explore for windows to access linux partition files. Fastest method. Quite difficult to remove.

I went with option 3 - separate partitions and the LTS (Long Term Support) Lucid Lynx 10.04. I tried changing version with every new one but, ended up falling back to the LTS. It is the most stable.
If you go that route, you might want to check out the GRUB2 tutorial in my signature. It is made for dual booting.
I love it!

---

### Post by Wingsgb on 2011-11-28
Thanks for the fast response and helpful info.

Cavsfan, I will have a read of that but am I right in saying program's wont run at same time as you can only boot one at a time.

---

### Post by Cavsfan on 2011-11-28
> **Wingsgb said:**
> Thanks for the fast response and helpful info.

Cavsfan, I will have a read

It took me a while to free up about 100GB for Ubuntu. I had to defrag it several times and then had to delete 
the $UsnJrnl that was huge and unfragmentable at the end of the drive.
It was safe to do but, lost all my restore points. Used Defraggler.

Then I put the installation disk for Ubuntu in and did the "custom" option. I made my swap file 2048MB and the rest "/" and everything went smooth.

I originally did this on Vista (which I did not like) but, now have windows 7.
If you encounter the same problem as I did with the user journal file, just look it up and you will find the command to delete it. 
It just keeps track of every little change made to any NTFS file in windows. 
If you have windows 7, you may not have the issue.

But, once you free enough space, use disk manager to shrink your windows partition to make room for Ubuntu. Then do the install.
Good luck!

---

### Post by MG&amp;TL on 2011-11-28
> **Cavsfan said:**
> It took me a while to free up about 100GB for Ubuntu. I had to defrag it several times and then had to delete 
the $UsnJrnl that was huge and unfragmentable at the end of the drive.
It was safe to do but, lost all my restore points. Used Defraggler.

Then I put the installation disk for Ubuntu in and did the "custom" option. I made my swap file 2048MB and the rest "/" and everything went smooth.

I originally did this on Vista (which I did not like) but, now have windows 7.
If you encounter the same problem as I did with the user journal file, just look it up and you will find the command to delete it. 
It just keeps track of every little change made to any NTFS file in windows. 
If you have windows 7, you may not have the issue.

But, once you free enough space, use disk manager to shrink your windows partition to make room for Ubuntu. Then do the install.
Good luck!

In most cases, it's not as difficult as all that to setup. Simply insert CD and let it do it for you-choose "alongside". But if you want to optimise/troubleshoot/safeguard, look no further than the above. :D


If you want to run two programs at once, either: 

1. Buy a smaller windows computer, and use virtual desktops and file sharing to integrate your program.

2. Use Virtual Machines. Many servers do this, in fact.

Incidentally, Linux is generally seen as more difficult to hack than Windows-so you might be onto a winner. You might want to have a look at ubuntu server edition: [http://www.ubuntu.com/business/server/overview]("http://www.ubuntu.com/business/server/overview")

-although be warned- there's no GUI by default. (although you can install one).

---

### Post by Cavsfan on 2011-11-28
> **MG&TL said:**
> In most cases, it's not as difficult as all that to setup. Simply insert CD and let it do it for you-choose "alongside". But if you want to optimise/troubleshoot/safeguard, look no further than the above. :D

If you do not defragment a NTFS drive before installing Ubuntu, you would not be able to defragment windows.
I know Ubuntu does not need this but, windows definitely does. So, if you wish to have "separate" OS's this is necessary.

---

### Post by MG&amp;TL on 2011-11-28
"optimise"=defragment, IMO. 

But let's not argue. OP, follow what ^^ said. All good stuff. :D

---

### Post by Cavsfan on 2011-11-28
> **MG&TL said:**
> "optimise"=defragment, IMO. 

But let's not argue. OP, follow what ^^ said. All good stuff. :D


You probably forgot more than I know about Ubuntu but, I know windows pretty well.
IMHO doing what I mentioned is a much, much preferred way to dual boot windows with any other OS.

But, I agree linux servers rule by far over windows servers. All good. :neutral:

---

