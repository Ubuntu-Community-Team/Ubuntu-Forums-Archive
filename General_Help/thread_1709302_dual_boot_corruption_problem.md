---
title: "dual boot corruption problem"
date: 2011-03-18
forum: General Help
---

### Post by mkwn on 2011-03-18
I recently set up a dual boot with windows 7 and ubuntu. (It was originally just windows 7.) I have used ubuntu twice, and both times when I returned to windows, my windows 7 partition was corrupted. The first time chkdsk repaired the problem and I thought it was a one-off thing, but this time even after chkdsk windows crashed on boot. It seems as if my installed programs and such are unrecoverable. (Luckily all my documents were backed up.)

[LIST=1]
[*]What could have caused the corruption? is it because I accessed and modified files on the windows partition from ubuntu?
[*]Can I reinstall windows into its partition and retain the dual-boot setup?
[*]Failing that, can I change the dual-boot setup into single-boot ubuntu and reallocate the memory of my windows partition to the ubuntu partition?
[/LIST]

Also, perhaps unrelatedly, hibernation and sleep are not working for me in ubuntu. The screen goes black (not off) but the fan keeps spinning. A friend says this could be because of dual-boot.

---

### Post by Sef on 2011-03-18
> What could have caused the corruption?

How did you partition the hard drive? If you used GParted that could be the cause of the problem. It is recommended that you use Windows 7 partitioner.

---

### Post by Jagoly on 2011-03-18
I would never trust Gparted with my windows partition all of my media and files are stored there. I have never had it kill my windows partition, but it froze in the middle of shrinking my ext4 ubuntu partition to increase my swap space.

Hard reset and... 3... 2... 1... Poof!
LAPTOP forgot UBUNTU. 
LAPTOP learned REINSTALL.

use the windows 7 partitioner to shrink your windows volume. On win7, go to "Control Panel\System and Security\Administrative Tools" and choose "Computer Management". shrink your Windows partition here. then just put ubuntu and your swap on here. also, if you still have the windows partition, you may be able to use testdisk ([http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download")) to recover something.

---

### Post by mkwn on 2011-03-18
well i let the ubuntu installer partition for me. I can't get into windows any more so I can't use the windows partitioner. but my problem is not that I want to resize a partition, I want to either reinstall windows retaining the whole dual-boot thing, or remove windows and its partition entirely. ([S]and hopefully get hibernate working in the process[/S] I fixed this problem with [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug))

thanks for the testdisk recommendation. I'll try that but I'm not optimistic given that there's a bunch of incomplete chkdsk stuff floating around.

---

### Post by Jagoly on 2011-03-18
Is there anything important your hdd at all you don't have backed up? If you don't need windows at all, then it shouldn't be a problem to fill the space with good ol' buntu. If you do want to keep windows, which I recommend for the sake of compatibility then you should persist. I'm not sure; what's the go in terms of registration with reinstalling a damaged win os? You can install windows 7 to a partition, but it will remove the grub. That's easy to fix from a ubuntu live cd.

---

### Post by mkwn on 2011-03-19
So to clarify:

I can boot from the windows 7 cd and it will let me install into just the windows partition leaving ubuntu intact (but unreachable because grub will be gone).

Then, I boot with the ubuntu installer USB drive and I will have the option to put grub back on without reinstalling ubuntu.

Even if I do this though, I assume the corruption problem will still be there. You suggested the problem might have been that gparted made a bad partition (i assume gparted is what the ubuntu installer uses). If that was indeed the cause how can i fix the bad partition?

---

### Post by usatonycuba on 2011-03-19
I do recommend to use a very good tool for resize your partitioner table, in the past I did have used...  [[COLOR="Blue"]Hirens Boot CD[/COLOR]]("http://www.hirensbootcd.org/hbcd-v131/"), that has many tools.. Including for both... Dos and Linux.

Just be careful using it. :KS

*I forgot to say that the reason why I mention [COLOR="Sienna"]Hirens Boot CD[/COLOR] is because in the past, a situation of power outage, did make my grub corrupted, and I  was not able neither go to Linux, and less windows ... so, in order to make my hard drive to come useful again, I had (did) to wipeout the entire disc ... I hope this is not your case .. Good luck.*

---

### Post by Jagoly on 2011-03-19
> **mkwn said:**
> So to clarify:

I can boot from the windows 7 cd and it will let me install into just the windows partition leaving ubuntu intact (but unreachable because grub will be gone).

Then, I boot with the ubuntu installer USB drive and I will have the option to put grub back on without reinstalling ubuntu.

Even if I do this though, I assume the corruption problem will still be there. You suggested the problem might have been that gparted made a bad partition (i assume gparted is what the ubuntu installer uses). If that was indeed the cause how can i fix the bad partition?

You can still boot ubuntu, so your partition table is still fine. From ubuntu, install gparted from the repo and see what it looks like. then it would help to either describe your disk or post a screenshot. if you see your Windows partion, just  make some free space for your new Win7 partition. Be careful not to touch your OEM partitions, and you shouldn't have to touch your ubuntu partion either. You can indeed install windows 7 in the free space, without killing ubuntu.

to reinstall grub, boot into a live ubuntu cd, assuming you only have one Hard disk, open a terminal and type:
```
sudo mount /dev/sdaX /mnt
```
replacing X with whatever partition ubuntu is installed on (not the live cd). Then, to install grub, type:
```
sudo grub-install --root-directory=/mnt /dev/sda
```
remember to backup first, and to clarify anything your unsure about first.

Edit: I'm not sure if your usb will mount as sda or sdb or something else in the live boot.
before you start we should probably wait for a more experienced user (not me) to clarify all this.

---

### Post by mkwn on 2011-03-19
appreciate the help :)

I attached a screenshot of gparted. The 800GB partition has the corrupted windows 7 on it. Are you suggesting I should make a third big partition and install win7 there fresh, leaving the old corrupt one sitting there?

also, it seemed that the cause of this whole thing was that windows would complain about corrupt files each time i switched back from ubuntu. Will reinstalling windows prevent this? it seems like theres a deeper problem that i need to treat...

---

### Post by Jagoly on 2011-03-19
Your partitions seem fine. Lets get one thing staight: when you installed ubuntu, Were there any problems when partitioning, or did it not report any errors? if there were none, then you shouldn't need to reinstall anything. Try testdisk. download it, extract it an run it by opening a terminal (in the linux dir in the extracted folder) and typeing

```
sudo ./testdisk_static
```

then proceed to to have a look around. post as much info as you can. I haven't got broken partitions, so we'll look for something out of the ordinary.

---

### Post by Jagoly on 2011-03-19
WAIT WAIT WAIT I THINK I HAVE IT ALL WRONG.
Can you access your win partition from ubuntu?

if this is the problem, try booting from a Win 7 install DVD, choose repair my computer and the open a command prompt. type
```
Bootrec.exe
/FixBoot
```
then, without booting into ubuntu, boot windows 7.

---

### Post by mkwn on 2011-03-19
I can access my windows partition from ubuntu. It seems 80% intact but there's a "found.000" folder with a lot of files that were presumably recovered with chkdsk.

I can actually boot into windows and see my desktop but it locks up immediately after.

---

### Post by wilee-nilee on 2011-03-19
I see you can get in now back up your personal stuff and then go from there.

---

### Post by Jagoly on 2011-03-20
> **mkwn said:**
> I can access my windows partition from ubuntu. It seems 80% intact but there's a "found.000" folder with a lot of files that were presumably recovered with chkdsk.

I can actually boot into windows and see my desktop but it locks up immediately after.

That is an extremely rare situation...
What sort of things are in the found.000 folder? I'm assuming that there were no problems reported when you installed ubuntu?

---

### Post by mkwn on 2011-03-20
a lot of files of the form file0174.chk, some of which ubuntu recognizes as images and have thumbnails, plus a lot of directories of the  form dir0002.chk which have readable files in them. These seem to correspond to files/directories that are missing from where I expected them to be. Presumably the reason why windows is failing to load properly is because there's some critical windows files that were lost in this way.

Ubuntu didn't report any problems with installation, but after using ubuntu, the next time i went into windows it reported data corruption and recommended chkdsk. I did that and it fixed it (I was thinking it was a one-off thing), but this second time I wasn't so lucky.

---

### Post by Jagoly on 2011-03-20
We need a Windows Pro. DO you need to register windows after a reinstall? If you can backup your files and attempt a reinstall, that would be your best bet. Cloning your ubuntu partition to an external drive would also be a good idea (if possible). This is beyond me. It almost seems completely random, but there has to be a cause.

---

### Post by Hedgehog1 on 2011-03-20
> **mkwn said:**
> Ubuntu didn't report any problems with installation, but after using ubuntu, the next time i went into windows it reported data corruption and recommended chkdsk. I did that and it fixed it (I was thinking it was a one-off thing), but this second time I wasn't so lucky.

mkwn,

Your very first post indicates you had (wisely/luckily) backed up your Windows documents.  Always good to see.

May I ask some questions to guide us in helping you:

* Is your preference a working dual boot?
* If you only use Windows a little, would a Virtual Machine of Windows in Ubuntu be better for you?
* Do you have your Windows install DVD?  The 'burn it yourself' restore CD and DVD set?

If you want a working dual boot; we do need to figure out how your NTFS partition got hammered.  That needs to stop happening.

***The Hedge***

:KS

p.s. We can move you to an Ubuntu single boot without reinstalling Ubuntu.  But let's do what is right for you in the long run.

---

### Post by Jagoly on 2011-03-20
> **Hedgehog1 said:**
> 
* If you only use Windows a little, would a Virtual Machine of Windows in Ubuntu be better for you?

I was going to suggest virtualbox, but in my experience it doesn't cut it. I use windows for games. for that any way i've had more success with wine than my Win7 VM. mkwin, persist for that dual boot. unless of course you don't care about games.

---

### Post by mkwn on 2011-03-20
> **Hedgehog1 said:**
> 
* Is your preference a working dual boot?
* If you only use Windows a little, would a Virtual Machine of Windows in Ubuntu be better for you?
* Do you have your Windows install DVD?  The 'burn it yourself' restore CD and DVD set?


Before recently I only used windows, but I want to switch entirely to ubuntu. I'd like to be able to access windows just in case though. Dual boot would be ideal because performance is better and I do occasionally play games, but a virtual machine could be a reasonable alternative if necessary.

> **Hedgehog1 said:**
> 
If you want a working dual boot; we do need to figure out how your NTFS partition got hammered.  That needs to stop happening.


This is exactly what I was thinking.

---

