---
title: "Uninstall Ubuntu 5.10 Breezy Badger?"
date: 2006-04-24
forum: General Help
---

### Post by Mattbutler on 2006-04-24
How do I do this?

I only have this OS on my laptop and I have recently got my hands on a Windows XP OS. So I want to remove Ubuntu and replace it with XP.

When I put the XP disk in when I boot up my laptop, nothing happens :( I do have a Windows 98 OS disk, but when I ty to boot that, I get an "Insufficient memory" error message.

Can anyone help me remove this god damn awful OS, please?

Thanks :)

---

### Post by JoeMetal on 2006-04-24
You think that Ubuntu is a "god damn awful OS" and want to switch to Windows?

To each, his own, I guess.

When I had to reinstall Windows when my Fedora core box got completely screwed, I had to use a Live CD to reformat my harddrive, then I was good to go.

---

### Post by Ensnared on 2006-04-24
Guess the Windows XP CD you got your hands on isn't much to write home about if it's not working ;) Ubuntu isn't active until you start booting from the harddrive, so if booting from a CD presents a problem, that's an issue with your laptop - either hardware of BIOS - and has nothing to do with the OS installed. The harddrive could be completely empty and you'd probably still get the exact same problem.

I suggest you contact customer support for your laptop since it seems like it's got problems booting from a CD (provided the CD is actually bootable, which it should be if it's an original CD).

Maybe the whole problem is that the BIOS isn't set up to boot from a CD (in which case your computer would probably try starting Ubuntu instead, but that obviously doesn't happen from what you describe). But still, check the BIOS settings to see if there's something wrong there.

---

### Post by croak77 on 2006-04-24
Check your BIOS settings. Try changing you hard drive access to LBA or Large. And you can always get support from MIcrosoft if you XP is legit :)

---

### Post by sinkxdie on 2006-04-24
HAH, you think Ubuntu is a "God Damn awful OS?"
Well, it's people like you who make Windows more popular.
This is how I figure it:
More people like you who can't do anything with anything harder then, "double click the .exe to open a program," make Microsucks keep making Windows, and keep polluting our computers. And don't come to an **Ubuntu** forum, asking happy **Ubuntu'ers** to get rid of a "god damn awful OS"(in your words), which we are probably all very pleased with. Go to a different forum and ask that question, not here. Well you can ask it here, but don't include, "god damn awful OS"...lets see you make an OS.

---

### Post by Mattbutler on 2006-04-24
[QUOTE=JoeMetal]You think that Ubuntu is a "god damn awful OS" and want to switch to Windows?

To each, his own, I guess.

When I had to reinstall Windows when my Fedora core box got completely screwed, I had to use a Live CD to reformat my harddrive, then I was good to go.[/QUOTE]

The fact that NOTHING works has little to do with me hating Ububtu ;)

How do I reformat my drive using this disk?

---

### Post by sinkxdie on 2006-04-24
Nothing works because you don't know how to use it. Everything works, if you were just a little more patient.
Ok no more fighting.
Insert the Live Cd and go to Applications>System Tools>GParted
Then right click and change the format of the drive or of a partition.

---

### Post by JoeMetal on 2006-04-24
Open up a program called GParted (it should be on there if it's Gnome based).  There's also a KDE equivalent.  And then just pick your volume and reformat it.  You might be able to do this without a live CD, but I guess that would be kind of hard because "nothing" works. 

And there is really no reason for everyone to flip out.  He doesn't like Ubuntu.  Boo hoo.  Not everyone likes Linux, not everyone likes Macs, not everyone likes Windows... not everything likes ANYTHING.

---

### Post by sinkxdie on 2006-04-24
You probably had to explain to him how to get to GParted, like I did.
I hope he knows what the Applications Menu is. It's that little button on the top bar of the screen.

---

### Post by JoeMetal on 2006-04-24
Not everyone who likes Windows is an idiot.

---

### Post by Ensnared on 2006-04-24
[QUOTE=sinkxdie]Nothing works because you don't know how to use it. Everything works, if you were just a little more patient.[/QUOTE]

I'm sorry, but that is simply not true. My laptop soundcard does not work in Linux, and believe me when I say I've tried everything short of learning C and programming my own driver.

Linux isn't perfect, even if we would like it to be. So give the guy a break - if he prefers Windows, let him run Windows. Different tools for different jobs for different people. It's that simple :)

But the "god damn awful OS" was a bit on the impolite side considering the place chosen to ask for help :p

---

### Post by sinkxdie on 2006-04-24
I didn't directly call him an idiot. It's like telling Bush how to use the bathroom. Some people need to know how to do things over and over again. :D

---

### Post by Mattbutler on 2006-04-24
Sorry that comment was meant to be sarcastic :(

I send my deepest apologies to those who I offended <3

---

### Post by sinkxdie on 2006-04-24
I don't know If you actually offended me...I'm just a jerk. :D
Well anyway did that help you format the drive? If not I can tell you some other ways to do so.

---

### Post by sinkxdie on 2006-04-24
I don't know If you actually offended me...I'm just a jerk. :D
Well anyway did that help you format the drive? If not I can tell you some other ways to do so.

---

### Post by Mattbutler on 2006-04-24
What should I change the format of the drive or of a partition to?

---

### Post by sinkxdie on 2006-04-24
I would try changing it to just a fat16..and when you install windows98, it should change it to a fat32. Then when you install Windows Xp, it will change it to a NTFS.

---

### Post by croak77 on 2006-04-24
Mattbutler, the partition should not prevent XP from booting. When you put in the cd what happens? Does text come that says something like, "Press any key to boot from CD"? Or does it go straight into grub/ubuntu?

---

### Post by Mattbutler on 2006-04-25
When I try to boot XP, nothing happens.

When I tried to boot Windows 98, I keep getting a "insufficient memory" message.

---

### Post by shuttleworthwannabe on 2006-04-25
how about putting a live CD lik MEPIS or Knoppix and wiping the parittions and reisntalltion XP? Just a thought.

---

### Post by Mattbutler on 2006-04-25
[QUOTE=shuttleworthwannabe]how about putting a live CD lik MEPIS or Knoppix and wiping the parittions and reisntalltion XP? Just a thought.[/QUOTE]

Hmm thanks for your suggestion, but I don't own those disks :(

---

### Post by Dr. C on 2006-04-25
Goto [www.microsoft.com]("http://www.microsoft.com") and search for "remove linux". 

There is a wealth of information on the subject on that site. Seriously! Including the following link:
[How to Remove Linux and Install Windows XP]("http://support.microsoft.com/kb/314458/EN-US")

If you can boot into DOS from a floppy then

fdisk /mbr 

will clear the master boot record

Another very useful site if you need boot disks is 

[www.bootdisk.com]("www.bootdisk.com")

---

### Post by Computeruser on 2006-04-25
@Mattbutler - If the CD is bootable, it should boot. I have always been able to boot any machine with a Live CD, a Windows XP cd, or a BartPE CD. From there FDISK usually works to eliminate old partitions and set up new one. So if "nothing" happens, take particular note of ensnared's post as it is likely a laptop issue.  Good luck.

---

### Post by ajhil on 2006-04-26
Wow! Linux enthusiasts are a touchy lot. At the risk of getting my head snapped off, before I ask my question, perhaps I can contribute a little understanding. I have no doubt that Linux is really neat. If I were a young would-be computer geek, I'd probably be all over it. However people like me, for whom computers are more quotidian tools than anything else, installing a Linux OS involves some costs. Like learning a great deal of new terminology. Like learning to navigate around a file system with a very different organization. For all its flaws, Windows is intuitive enough that a reasonably bright person like me with only a little computer expertise can figure it out pretty quickly. I submit that this isn't true for Linux, at least it hasn't been for any of the iterations I've tried (like Red Hat, Suse, and now Kubuntu.)
Nevertheless, I'm intrigued enough by Linux and the things I've heard to keep trying it. KDE looks fasciinating and using the same application (Konqueror) to navigate both the OS and the Internet seems very sensible. (Why hasn't MS done this?) I got an installation disc for Kubuntu 5.10. Since I didn't want to partition my main harddrive any more than it already was, I tried to install it into a USB-linked peripheral harddrive. In retrospect I can see why this may have been foolish. I can also see how I might have done it better ... but, in any event, I wound up with an unbootable system and an "Error 21" message from Grub. Google led me to a lot of woeful postings from people who'd apparently tried the same thing and like me had screwed up their MBR.
Fortunately I was able to reaccess my Windows OS by disconnecting the peripheral hard-drive and reinstalling Kubuntu on the main hard-drive.
Now I've got a primary hard drive that's chopped up in the way I didn't want. I've also got just the kernel of Kubuntu (I was trying to speed up the installation process) which does me no good at all. 
My question (at last): I feel confident that I can get rid of the new partitions and reclaim the disk space using Windows disk management tools. What really bothers me is Grub!! How can I reliably get back my original, pre-Linux MBR without risking another unbootable sytem?
Thanks in advance.
aj

---

### Post by echo $USER on 2006-04-26
I don't know if it's just me, but I think it's hilarious he was able to install a "god awful OS" but his precious M$ he cannot.  Where does that leave windows?

To ajhil:

To replace grub with the windows mbr boot your windows install disk, enter recovery mode, at the c:\ promt type "fixmbr" w/out the quotes ofcource.  Then reboot, grub will be gone and windows is back to normal.  Then you can enter disk management and format the linux partitions with ntfs or whatever.

---

### Post by Efwis on 2006-04-26
[QUOTE=ajhil]Wow! Linux enthusiasts are a touchy lot. At the risk of getting my head snapped off, before I ask my question, perhaps I can contribute a little understanding. I have no doubt that Linux is really neat. If I were a young would-be computer geek, I'd probably be all over it. However people like me, for whom computers are more quotidian tools than anything else, installing a Linux OS involves some costs. Like learning a great deal of new terminology. Like learning to navigate around a file system with a very different organization. For all its flaws, Windows is intuitive enough that a reasonably bright person like me with only a little computer expertise can figure it out pretty quickly. I submit that this isn't true for Linux, at least it hasn't been for any of the iterations I've tried (like Red Hat, Suse, and now Kubuntu.)
Nevertheless, I'm intrigued enough by Linux and the things I've heard to keep trying it. KDE looks fasciinating and using the same application (Konqueror) to navigate both the OS and the Internet seems very sensible. (Why hasn't MS done this?) I got an installation disc for Kubuntu 5.10. Since I didn't want to partition my main harddrive any more than it already was, I tried to install it into a USB-linked peripheral harddrive. In retrospect I can see why this may have been foolish. I can also see how I might have done it better ... but, in any event, I wound up with an unbootable system and an "Error 21" message from Grub. Google led me to a lot of woeful postings from people who'd apparently tried the same thing and like me had screwed up their MBR.
Fortunately I was able to reaccess my Windows OS by disconnecting the peripheral hard-drive and reinstalling Kubuntu on the main hard-drive.
Now I've got a primary hard drive that's chopped up in the way I didn't want. I've also got just the kernel of Kubuntu (I was trying to speed up the installation process) which does me no good at all. 
My question (at last): I feel confident that I can get rid of the new partitions and reclaim the disk space using Windows disk management tools. What really bothers me is Grub!! How can I reliably get back my original, pre-Linux MBR without risking another unbootable sytem?
Thanks in advance.
aj[/QUOTE]
if you have your Windows XP disk, just start the computer with the disk in the drive, let it start it's process as normal, at the first entry choose to start in recovery mode. 
This will give you the old dos prompt type setting asking which version of Windows you want to start. choose the Windows XP by hitting 1 then enter.

at this promtp C:\Windows> type the following
```
fixmbr
```
then type 
```
exit
```
 
as the machine is rebooting remove the Winxp disk so it boots from the HDD.

---

### Post by Jagot on 2006-04-26
[QUOTE=ajhil]My question (at last): I feel confident that I can get rid of the new partitions and reclaim the disk space using Windows disk management tools. What really bothers me is Grub!! How can I reliably get back my original, pre-Linux MBR without risking another unbootable sytem?
aj[/QUOTE]

And if your Windows installation disk isn't handy then you can use a FreeDos boot disk:

[http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/old/beta9sr2/fdbootcd.iso](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/old/beta9sr2/fdbootcd.iso)

You'll need to use the command 'fdisk /mbr' with that though.

---

### Post by ajhil on 2006-04-26
Thanks for the prompt replies! However, in  buying my computer I made the mistake of choosing a Compaq, which doesn't come with a Windows installation disk. (One reason why I'll never get another one!) The reinstallations files that would ordinarily be on a Windows disk seem to be stored somewhere on the hard drive as *.cab files, but I've had little luck so far in accessing or using them.
Would a system Restore do? My initial impression is that Restore doesn't extend down to the BIOS level.
aj

---

### Post by Jagot on 2006-04-26
[QUOTE=ajhil]Thanks for the prompt replies! However, in  buying my computer I made the mistake of choosing a Compaq, which doesn't come with a Windows installation disk. (One reason why I'll never get another one!) The reinstallations files that would ordinarily be on a Windows disk seem to be stored somewhere on the hard drive as *.cab files, but I've had little luck so far in accessing or using them.
Would a system Restore do? My initial impression is that Restore doesn't extend down to the BIOS level.
aj[/QUOTE]

I was in the same position - with both a Sony and a Dell.  Use the FreeDos disk as in my previous post.  A system restore will not do it methinks

---

### Post by Efwis on 2006-04-26
system restore does absolutely nothing to the mbr, you have to use freedos or you can download the Windows98 boot disk from [http://www.bootdisk.com](http://www.bootdisk.com) and run fix /mbr from it.
you would have to get the non-OEM version from bootdisk

---

### Post by Ensnared on 2006-04-26
[QUOTE=ajhil]Wow! Linux enthusiasts are a touchy lot.[/QUOTE]Oh I don't know. Go to [www.ford-owners.com](www.ford-owners.com) (if it exists, and has a forum) and post "Ford is a god awful car", and see if you'll get any better responses ;) Or just go to a Windows-users forum and post "Windows is a god awful OS" if you want a more similar subject. If I was a gambler, I'd put a lot of money on you getting pretty much the same kind of reactions - if not worse.

As for the differences you mention - unfamiliar filesystem, new terminology, etc... the same can be said for any non-Windows OS. There's this fairly popular OS used by both geeks and regular users - it's called Mac OS X. It doesn't look, feel or behave anything like Windows, yet computer illiterates all over the world are using it, and using it efficiently. Just like Windows. And just like Linux.

6-7 years ago, you had to have a special interest and a fair level of geekness to use Linux. Things has changed dramatically since then. I have several friends who use it, and they have no idea what ext2, ext3, NTFS or FAT is, and they don't know what a "kernel" is, or what "mount" means. Yet, they're able to read email, browse the web, download files, watch movies, listen to music, write documents/spreadsheets/presentations and print them out or save them and - strangely enough - find them again later. All while using Linux, and being anything **but** geeks. And the best part is - I had nothing to do with them even trying it, mostly out of worry that they'd pester me with questions all the bloody time to no end when they ran into problems. But not so - cause they hardly ever run into problems. For their needs, it Just Works(tm). Just like Windows. Just like Mac.

I do see your point though, cause they didn't set up their systems by themselves - someone with know-how did. But these are the kind of users who would also run into problems if they were going to install Windows on their own. Usually that isn't an issue in Windows, because OEM providers do all the dirty work, and most of them have a system for doing it again which doesn't actually involve running a normal installation, but more of a "click this button to restore your computer" - then sit and wait.

But anyway, sorry for ranting - I just think it's about time to get some perspective and not see everything in black and white, because those days are history ;)

---

