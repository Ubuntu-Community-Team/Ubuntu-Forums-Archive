---
title: "How can I tell if Ubuntu is installed on an extended partition/switch to a primary?"
date: 2010-09-23
forum: General Help
---

### Post by sirspazzolot on 2010-09-23
I'm dualbooting 10.04 with Vista and I think that my Ubuntu installation is on an extended partition, thus making it unrecognizable by the Chameleon bootloader.

Is there a way to get my Ubuntu installation onto a primary partition, whether it be moving the installation somehow or switching the partition type? I don't mind file damage or loss; I don't have anything important.

I guess if need be I can just uninstall Ubuntu and reinstall it, but that would take a lot more time. How would I safely uninstall/reinstall Ubuntu on a primary partition while leaving my Vista installation boot-able? Vista is on my C: Drive, and I believe I have a 15GB extended partition with Ubuntu installed and a D: drive that should have no OSs installed on it.

Thanks in advance. :)

---

### Post by bodhi.zazen on 2010-09-23
boot the live desktop CD and fire up gparted.

As an aside, why not use grub, it works fine.

---

### Post by themusicalduck on 2010-09-23
I looked up your other thread about triple booting with OS X.

If it's useful, I have Chameleon chain loaded from GRUB. To do this I edited the file /etc/grub.d/40_custom and added this to the end of the file```
menuentry "OS X" --class macosx --class os {
	 insmod hfsplus
        set root=(hdx,x)
        multiboot /boot
}
```where set root=(hdx,x) is the root fileystem of the Chameleon bootloader, eg set root=(hd0,2). You might be able to do with UUID instead using set root=UUID=theuuid, but I'm not sure about that as I haven't tried it. Find out what "theuuid" should be with sudo blkid

After adding it, update grub with sudo update-grub

In the end I actually just made a bunch of menu entries with different versions of (x,x) and tested them because the GRUB numbering system seems to work completely randomly for me nowadays.

If you don't want the menu entry that GRUB generates, then just edit /boot/grub/grub.cfg and replace the generated entries with the same code as above instead of adding it to the custom script.

---

### Post by sirspazzolot on 2010-09-23
Awesome. I will definitely keep this in mind, thanks. I'm still gonna try to get Ubuntu recognized by Chameleon but this is interesting. What do you mean by chain loaded? Like, GRUB shows up and then you click on something and then Chameleon shows up?

[http://img834.imageshack.us/img834/263/gparted.png](http://img834.imageshack.us/img834/263/gparted.png) that's a picture of my partition set up, too. It looks like since the extended partition is divided into two partitions, I can't turn it into a primary one. Any advice for what I would do?

---

### Post by sirspazzolot on 2010-09-23
Oh, and where is GRUB? If I switch it to a primary partition will that break my ability to boot into Vista or Ubuntu?

---

### Post by sirspazzolot on 2010-09-23
Shoot. I have to somehow merge my C: and D: drives. Those are the two NTFS ones. Any ideas how?
And I have no idea what that FAT32 partition is. How would I go about mounting it? mount -t /dev/sda1 did nothing.

---

### Post by sirspazzolot on 2010-09-23
"mount -t dev/sda1 /media/cdrom0 did nothing"*** sorry, forgot that last part. sorry for all these double posts, too.

---

### Post by WorMzy on 2010-09-23
I haven't read the rest of the topic, but one way to tell whether you're using a primary or logical partition is to boot into your Linux installation and run "df | grep '/$'", that should return something like
```
/dev/sdc[COLOR="Red"]_9_[/COLOR]             38448276  17278688  19216488  48% /
```

The part in red is what you need to look for. If it's 1, 2, 3 or 4, then you've installed to a primary partition. If it's 5 or higher, then you've installed to a logical partition.

---

### Post by srs5694 on 2010-09-23
The Master Boot Record (MBR) partitioning system you're using supports only four primary partitions, and an extended partition counts as a primary partition. Since you've got three primaries (/dev/sda1, /dev/sda2, and /dev/sda3) and an extended Partition (/dev/sda4), you can't convert either of your logical partitions into primary partitions -- at least, not without first deleting at least one primary partition.

> What do you mean by chain loaded? Like, GRUB shows up and then you click on something and then Chameleon shows up?

Yes. In fact, if Chameleon will be involved at all, you *must* chain load, since Chameleon can't directly boot Linux. Either Chameleon chain loads GRUB or GRUB chain loads Chameleon. If you have no other OSes on another disk, though, there's no need for Chameleon in your setup -- you can just use GRUB to select between Linux and Windows.

If you're set on having Chameleon in the loop, you might be able to get it to work by converting your MBR setup to a GUID Partition Table (GPT) setup with a [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) In this configuration, Linux would reside entirely in GPT partitions and you'd set up your current /dev/sda1, /dev/sda2, and /dev/sda3 as MBR duplicates of their GPT counterparts. I'm pretty sure that Chameleon can handle this sort of configuration, but you'd almost certainly have to re-install both Chameleon and GRUB. It would also be wise to set up a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) for GRUB's benefit. (You have more than enough unallocated space for this.) I caution that hybrid MBRs are ugly and flaky things; I think that using GRUB as your primary boot loader and either abandoning Chameleon or using it as a secondary boot loader if you're booting another OS from another disk is the safer way to go.

If you do decide to try a hybrid MBR setup, my [GPT fdisk](http://www.rodsbooks.com/gdisk) program will do the conversion, both from MBR to GPT and to create a hybrid MBR.

Good luck!

---

### Post by sirspazzolot on 2010-09-23
Would the BIOS Boot Partition count as a primary partition? And I know you probably REALLY don't want to do this, but could you write roughly what I would do in order? Or at least tell me if my plan makes sense? What I plan to do in the end is install OS X but I kinda wanted to avoid saying that in case hackintoshes are frowned upon here. I've got a bootable USB instally thing, and when I boot my computer with it plugged in, it brings up chameleon and I can boot Windows normally, there's an option for OS X and there's a Linux option. I can click on the Linux option and it takes me to GRUB and I can boot ubuntu there. When I install OS X, though, since Chameleon overwrites GRUB in the MBR, I'm afraid that I'll have no way of booting into Ubuntu. I did a thing to install GRUB on my Ubuntu partition so HOPEFULLY there will still be a Linux option and it would still lead to GRUB and I could still boot Ubuntu, but I'm not sure. I don't think I even need to take Ubuntu off its extended partition anymore, just get rid of D: and/or that recovery partition. I really should have done all this thinking and such before making topics... Thanks for helping, everyone.

---

### Post by sirspazzolot on 2010-09-23
I'm going to bed now and may forget about this thread, but if you'd like to email me any information, it would be greatly appreciated: [email]numberlessusername@yahoo.com[/email]
Thanks for all the help, everyone! This type of community is why I love Ubuntu so much and want to make sure I can use it after installing OS X. :)

---

### Post by srs5694 on 2010-09-24
> **sirspazzolot said:**
> Would the BIOS Boot Partition count as a primary partition?

A BIOS Boot Partition is normally needed only on GPT disks. Since GPT doesn't distinguish between primary, extended, and logical partitions, the question is meaningless.

> And I know you probably REALLY don't want to do this, but could you write roughly what I would do in order?

The the [GPT fdisk Web page,](http://www.rodsbooks.com/gdisk/) and particularly the page on [converting to or from GPT.](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

> What I plan to do in the end is install OS X but I kinda wanted to avoid saying that in case hackintoshes are frowned upon here.

They are. The moderators will shut down any thread that delves very deep into that topic.

> When I install OS X, though, since Chameleon overwrites GRUB in the MBR, I'm afraid that I'll have no way of booting into Ubuntu.

This isn't a Hackintosh-specific issue; it's a matter of how boot loaders interact. Most boot loaders can *directly* load just a handful of OS kernels. AFAIK, the Windows boot loader can only load Windows kernels; Chameleon can directly load XNU (the kernel used by OS X and Darwin); GRUB can load Linux, FreeBSD, and a few other mostly Unix-like kernels; and so on. Since the boot process in a BIOS-based computer is based on the BIOS reading a fixed point (sector 0 of the first disk, aka the MBR) and using the boot code there, the inherent limitations of most boot loaders can become a problem. The Windows boot loader can't load Linux, GRUB can't load Windows, and the BIOS will only load one of the two boot loaders (assuming one hard disk and no other bootable medium). This is a problem.

One workaround is to provide multiple boot media and use the BIOS to switch between them. This is a bit awkward and limiting, though, and it wasn't even possible a few years ago, since BIOS boot options were much less flexible back then. The more common solution is to implement chain-loading in the boot loaders. In addition to booting OS kernels, most boot loaders support passing execution to another boot loader, typically by loading the first sector or two of a partition and executing the code there. This is usually a necessary feature because the 440 bytes available to the boot loader in the MBR is insufficient to do the whole job, so they *have to* spread themselves out across both the MBR and the target OS's boot partition's boot sector.

When you install an OS (be it Linux, Windows, or almost anything else), it will give an option to install its boot loader. (Sometimes the OS doesn't give an option; it just does the deed without asking!) This will overwrite the boot loader in the hard disk's sector 0 (aka the MBR), which effectively changes the boot loader from one to another -- say, from GRUB to the Windows boot loader. Depending on how flexible the new boot loader is, this might or might not be a real problem.

If it is a problem, there are precautions you can take. You can back up your MBR code using the Linux command "sudo dd if=/dev/sda of=boot-code.img bs=440 count=1". (Change "/dev/sda" to something else if you've got multiple hard disks and GRUB is installed to something else. Change "boot-code.img" to whatever filename you want to use for the backup.) If your system becomes unbootable after installing another OS, you can back up the new OS's boot loader in the same way (just give the backup a unique filename) and restore GRUB with "sudo dd if=boot-code.img of=/dev/sda bs=440 count=1". You can then create a GRUB entry that either chain loads to the new OS's partition or that chain loads to the backup image you created. This entry looks just like the GRUB entries to boot Windows, since that's how GRUB boots Windows -- by chain-loading the part of the Windows boot loader that resides in the Windows boot partition!

> I did a thing to install GRUB on my Ubuntu partition so HOPEFULLY there will still be a Linux option and it would still lead to GRUB and I could still boot Ubuntu, but I'm not sure.

GRUB can be installed either to the MBR of the disk or to a Linux partition. The latter requires that a boot loader capable of chain-loading to the Linux partition be installed in the MBR, or be loaded as some intermediary boot loader. (You could theoretically set up a chain of boot loaders of arbitrary length.) If you originally installed GRUB to the MBR, then you might still be using that, even if you subsequently installed it to the boot partition's boot sector. The boot partition's installation might work if something else redirected there, but I can't promise that. The issue for you is whether some other boot loader, like Chameleon, can redirect to a logical partition. I'm not sure if Chameleon can do this. I *am* sure that Chameleon can understand and boot GPT partitions, hence my suggestion that converting to GPT (with a hybrid MBR) might be beneficial.

> I don't think I even need to take Ubuntu off its extended partition anymore, just get rid of D: and/or that recovery partition. I really should have done all this thinking and such before making topics... Thanks for helping, everyone.

It's unclear to me why removing one of those partitions would be helpful, unless you need another primary partition for installing another OS. Since the OS you want to install is verboten here, at least when installed on commodity PC hardware, I won't delve into that topic, except to point out that the question of how to partition for it will produce a very complex answer. Be prepared for when you find it.

---

### Post by sirspazzolot on 2010-09-25
Wow, I'm surprised I remembered this topic. I tried to get on while I was at school today via my iPod but apparently my school blocked the Ubuntu forums. What the hell? Oh, and then my ipod broke when I got pushed over a fire hydrant.

Anyway. The reason I want to get rid of a partition is because I want to make room for a primary partition for my next OS. Since the copy of Chameleon that boots from my external drive successfully goes to GRUB, I think that if I replace the copy of GRUB in the MBR with Chameleon, I'll have a chain-loaded GRUB since I installed GRUB on my Ubuntu partition. I'm not sure if the GRUB that Chameleon is directing me to is the one in the MBR right now or the one on my Ubuntu (extended) partition but what I do know is that I don't think there was a Linux option before I installed GRUB to my Ubuntu partition. Is there a way to check where the copy of GRUB I'm using is installed?

---

### Post by sirspazzolot on 2010-09-25
this post used to be stupid.

---

### Post by sirspazzolot on 2010-09-25
How do I delete a post...? I'm tired and forgot that I knew what extended/logical partitions were. That last post was dumb and I want it gone.

Anyway, I'm not totally understanding this GPT conversion. It seems that once I convert it, I won't have a working way to boot right away, because I would need a BIOS Boot Partition to embed GRUB to get it to work, right? And since GRUB overwrote my MBR (didn't it?)... Will the conversion still work?

I think the definite easiest solution that I'm sure I could do is eliminate that recovery partition and my D: drive, delete Ubuntu and do a fresh install of 10.04 (Might wait until Maverick comes out :)) to get rid of my ugly frankenbuntu karmic/lucid mix, this time in all primary partitions, and then install OS X on another primary partition. I would then have GRUB installed to my linux partition and Chameleon would reside in the MBR. I'm like 95% sure that this would work but I want that recovery partition in case something goes wrong. Do you think if I copy that partition to my external hard drive and then delete it, I could just move it back and use it if the need arises? My brain is saying yes it would work, as long as I put it before the other partitions, but I'm still a little scared. Switching over to GPT would probably be just as likely to break it, too.

Thanks for all your help, srs. I really really appreciate you taking the time to help out a dummy who wants to get in over his head. :)

---

### Post by srs5694 on 2010-09-25
It sounds like the first boot loader to come up for you right now is Chameleon. If so, then either that's what's in the MBR or whatever is in the MBR is very simple and just chain-loads to a copy of Chameleon located somewhere else. Remember: When dealing with multiple boot loaders, the chain begins with the MBR.

---

### Post by sirspazzolot on 2010-09-25
Wow, perfect timing. I just woke up, and there was a new post. :)

I currently have GRUB in the MBR, Chameleon is just on my external hard drive/OS X bootable installer and I have my BIOS set to boot from USB first, so when I turn my laptop on with the drive plugged in, it boots to Chameleon. If the laptop turns on without the drive in, it just goes to GRUB. GRUB is still in my MBR, but I'm thinking that I'll replace it with Chameleon which SHOULD be able to detect GRUB on my Ubuntu partition that I will get to be primary.

---

### Post by sirspazzolot on 2010-09-26
Bumping the topic for opinions on my (hopefully) finalized procedure:
Delete my D: partition
Make LiveCD of 10.10 in 10.04
Delete existing linux partitions
Install 10.10 on PRIMARY paritions
Install GRUB on Linux partition
Delete that recovery partition
Install OS X
Hope everything works.

---

