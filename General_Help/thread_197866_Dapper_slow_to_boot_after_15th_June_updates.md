---
title: "Dapper slow to boot after 15th June updates"
date: 2006-06-16
forum: General Help
---

### Post by Budoc on 2006-06-16
After installation of the 15th June updates, it now takes much longer for Ubuntu Dapper to boot up using the new kernel (2.6.15-25-686). Previously, using the 2.6.15-23-686 kernel booting up into Ubuntu Dapper took approx. 45 seconds. Currently using the newer kernel, Dapper takes almost 2 and a half minutes. The system seems to hang during "Mounting Root File System", although after a few minutes resumes to boot Ubuntu normally. I couldn't see anything unusual in /var/log/messages. Upon booting the 2.6.15-25-686 kernel in rescue mode, I am able to identify that the delay in booting occurs after "ACPI:PCI Interrupt 00:00:00:1f.2[B]->GSI 19 (level, low)->IRQ 225". The delay in booting occurs whether I have a usb devices connected or not. I can still boot using the 2.6.15-23-686 without the delay. Also attached is a bootchart .png of the new kernel.

The computer being used is a Toshiba Equium M70-339 with a Pentium M 735 processor.

Thanks for any help in advance.

---

### Post by Amt0571 on 2006-06-16
Mmm... my computer has been hanging on "mounting root filesystem" since I first tried the beta version... it takes a lot less than 2 minutes, but it stops for a lot of time on that step... I thought that was normal, but I'm starting to think it's not... I don't know what could cause it, anyway, if it helps, I'm using the 386 kernel (for some reason it's a lot faster than the k7 one) and my computer has the following specs:

Athlon Thunderbird 1400
MSI K7T266Pro R
512mb PC2400 ram
Two WD800JB HD
Radeon 8500LE

---

### Post by mlind on 2006-06-16
According to that graph, udev seems to sleep idle a very long time. Can you get
graph to display critical path as a line ? Have you tried booting with acpi=off and noapic flags?

---

### Post by Budoc on 2006-06-16
[QUOTE=mlind]According to that graph, udev seems to sleep idle a very long time. Can you get
graph to display critical path as a line ? Have you tried booting with acpi=off and noapic flags?[/QUOTE]

Thanks for your response. I've just tried booting with acpi=off and that has reduced the time taken to boot to what it was before (around 45 seconds).

Sorry for the silly question, but how would I get graph to display critical path as a line? I'm still fairly new to Linux, so I've still a lot to learn.

---

### Post by Ramses de Norre on 2006-06-16
How do you get such a graph? Seems nice to look at how my pc boots =)

---

### Post by mlind on 2006-06-16
[QUOTE=Budoc]Thanks for your response. I've just tried booting with acpi=off and that has reduced the time taken to boot to what it was before (around 45 seconds).

Sorry for the silly question, but how would I get graph to display critical path as a line? I'm still fairly new to Linux, so I've still a lot to learn.[/QUOTE]

I dunno, if Bootchart has some parameter for that.

---

### Post by buttari on 2006-06-16
Same here!
boot just gets stuck at "mounting root filesystem" for more than a minute.
Ubuntu developers please fix this!!!

alfredo

---

### Post by Budoc on 2006-06-16
[QUOTE=Amt0571]Mmm... my computer has been hanging on "mounting root filesystem" since I first tried the beta version... it takes a lot less than 2 minutes, but it stops for a lot of time on that step... I thought that was normal, but I'm starting to think it's not... I don't know what could cause it, anyway, if it helps, I'm using the 386 kernel (for some reason it's a lot faster than the k7 one) and my computer has the following specs:

Athlon Thunderbird 1400
MSI K7T266Pro R
512mb PC2400 ram
Two WD800JB HD
Radeon 8500LE[/QUOTE]

I've always noticed a slight hang when mounting root filesytem, but not as severe as the new 686 kernel. I've decided to switch to the 386 kernel for now.

[QUOTE=Ramses de Norre]How do you get such a graph? Seems nice to look at how my pc boots =)[/QUOTE]

```
sudo aptitude install bootchart
```
After restarting a graph will be present as a .png in /var/log/bootchart/

[QUOTE=mlind]I dunno, if Bootchart has some parameter for that.[/QUOTE]

I'm not sure just yet. I'll keep looking around.

I've realised that I do not get this problem by using the 2.6.15-25-386 kernel, so for now I'll use the 386 kernel and switch back to the 686 kernel if I can figure out what is going wrong.

Thanks for all of your help.

---

### Post by Azriphale on 2006-06-16
Aha. The thread I have been looking for... It appears I am not alone here.

Here's whats been happening on my Toshiba Satellite Pro M70-235

After the update, the 686 kernel hangs for around 2 to 4 minutes at the "Mounting root filesystem" point. The 386 kernel hangs for much less time, but it does also hang.

System Specs:
Toshiba Notebook
Pentium M 1.87 GHz
512 MB RAM
Toshiba 60GB SATA HDD (not sure of exact specs there)
Radeon X700

I don't think this has been happening on my desktop:
Pentium 4 2.8 GHz
Gigabyte 8I915G-MF motherboard
2 GB RAM
2x Seagate SATA HDD
1x Seagate PATA HDD
nVidia 6600 PCIE

I tried to have a look around for any causes, but with my lack of expertise in this area of linux, I could find nothing...

---

### Post by vnvenkat on 2006-06-18
Hi,

I'm having the same problem. I'm running Dapper on a Thinkpad T60. When I got the upgrades on June 15th to 2.6.15-25, and now boot takes nearly two and half minutes. 

Turning acpi=off doesn't help either.

---

### Post by Ferri on 2006-06-18
Same problem here in my Sony Vaio laptop, with 686 kernel 2.6.15-25. However I haven't noticed it in my desktop with k7 kernel 2.6.15-25.

---

### Post by dejitarob on 2006-06-18
I have the same issue on an Asus Z70V laptop with the 2.6.15-25-686 kernel. Not only did it noticeably slow the booting of my system, but it also gave me quite a large performance hit within Ubuntu itself (extremely slow loading applications, watching movies, etc).

Reverting to the 2.6.15-23-686 kernel fixed the issue for me. To set grub to automatically boot into this, edit your /boot/grub/menu.lst and change the 'default 0' entry to match the kernel. You have to scroll down to see what number the 2.6.15-23-686 kernel is listed at. For me this was 2 so my menu.lst now says 'default 2'.

---

### Post by Blnd2Spll on 2006-06-20
I'm also having the same problem on a thinkpag t60p...about 2 minutes boot time.  Does anyone know if there is any real drawback with reverting back to the old kernel?

---

### Post by firehead on 2006-06-21
same problem here on a sony vaio-vgns4xp... acpi=off works, but i need acpi :mad:. so let's keep this thread active...maybe somone's got a solution

---

### Post by blimpyboy on 2006-06-21
Could you please all booth 25 in recovery mode and see if there are any unusual messages.

---

### Post by Azriphale on 2006-06-21
If I remember correctly, there are no strange messages, it just hangs somewhere. I don't have the kernel installed at the moment. I'll post what happens to me once I have installed it again.

[EDIT]
I don't see anything strange/different from the normal boot procedure (when it boots reasonably quickly).
It seems to hang for a while, just after detecting the DVD writer.
```

hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
SCSI subsystem initialized
ACPI: Bus type SCSU registered
ACPI: PCI interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> irq 233

```
there is stops for a while.

---

### Post by Ferri on 2006-06-22
I've reported a bug on this issue. You might be interested on adding some comments or information: [bug50588]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/50588")

---

### Post by vinoobuntoo on 2006-06-22
I have the same problem with my thinkPad T60 however on my HP Pavilion dv 4000 the boot time is unchanged!

---

### Post by oscar on 2006-06-25
I have the same problem on my Sony Vaio VGN-S3XP using the 2.6.15-25-686 kernel

---

### Post by tvoss on 2006-06-25
Same here, overall performance went down with kernel 2.6.15-25-686 ... one of the strongest indicators:
[LIST=1]
[*]Slow boot process
[*]Accessing the 'Applications', 'Places' and 'System'-Menu is quite slow.
[*]I'm working a lot with video data and am experiencing quite bad disc performance.
[/LIST]

My System:
Intel Centrino M, 2.13 Ghz, 1GB RAM, ATI X600 PCI-E 256MB.

---

### Post by 3rdalbum on 2006-06-25
I'm currently running my Breezy kernel on Dapper. It actually fixes a crash with logging out/shutting down that I've been having since I upgraded to Dapper this morning. However, it hangs for a little while on each of the EVM, LVM and HAL steps, and sound doesn't work once I've booted.

The system now feels as snappy as Breezy was, so my guess is that the July 15 kernel is a dud.

---

### Post by richtl on 2006-07-01
I'm running a Thinkpad T60p and my boot time is now up to 5 minutes. (it's definitely getting longer!). Time to switch back to the .23 kernel until this is fixed.

---

### Post by bro on 2006-07-04
Well.. what can I say. Fuji Siemens laptop Pi1536 and indeed a minute or two waiting before it continues booting at 'mounting root file system'. It is a long time if you're impatient like me.

---

### Post by zneastman on 2006-07-04
Same problem here, and a big performance hit running the 686 kernel.  The 386 kernel boots and runs normally.  This is a Dell Inspiron b130 with an intel centrino proc.

---

### Post by Azriphale on 2006-07-16
I take it in the weeks I have been gone, there have been no breakthroughs... 
Maybe when I have time I'll try to compile a 2.6.17. apparantly there are a number of speed fixes in there (not specific to this, but speed increases are always good). I'm just not too keen on having to install video and sound drivers manually on every kernel update i decide to do. Although I don't know when I'll have time.

---

### Post by wenzlicker on 2006-07-17
I found this link trying to solve this problem for my t60. I haven't tried any of the solutions yet, but there are a lot of links to related information.

[http://ubuntuforums.org/showthread.php?t=216039&highlight=mounting+root+filesystem](http://ubuntuforums.org/showthread.php?t=216039&highlight=mounting+root+filesystem)

It seems like this is related to the 686 kernel (I'm using 686-smp because of my my intel duo). Is this problem isolated to the 686 kernel?

---

### Post by vtel57 on 2006-07-18
Greetings folks!

I was going to jump in here tonight and post a question about the apparent slowness of my Ubuntu boot-up times. However, since reading the above posts, I realized that I'm not doing too badly with 1.5 minute boots from POST to desktop. I was comparing it to my XP boot-ups, which are just about as slow, so maybe all's well after all.

Regards,

~Eric

---

### Post by ajarufe on 2006-08-11
> **vnvenkat said:**
> Hi,

I'm having the same problem. I'm running Dapper on a Thinkpad T60. When I got the upgrades on June 15th to 2.6.15-25, and now boot takes nearly two and half minutes. 

Turning acpi=off doesn't help either.

try the latest t60 BIOS, did the trick for me.

---

### Post by eric_m_allen on 2006-08-18
I'm just starting to work on an Ubuntu system.
The 15-26-386 version is deadly slow on my T30-10 minute bootup times. At all points of the process.
I switched back to 23 and it's fine.
I was also getting dosfsck errors on boot. That got me worried, but 23 doesn't throw them. Odd.
Any news on versions?

---

### Post by ahaslam on 2006-09-21
My boot time has doubled since my upgrade to Dapper (at release).
It doesn't seem to hang on any particular process, everything is generally slow. I have a boot chart if anyone can shed some light on it:
[http://ubuntuforums.org/showthread.php?p=1519312#post1519312](http://ubuntuforums.org/showthread.php?p=1519312#post1519312)

Cheers,
Tony.

---

