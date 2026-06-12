---
title: "What filesystem do most people here use: xfs, reiserfs, or ext3?"
date: 2006-06-02
forum: General Help
---

### Post by oobuntoo on 2006-06-02
:-D Hello, all Dapper users!! I'm about to reinstall Dapper and have been using ReiserFS without any problem, but want to experiment with other filesystem. I just want some opinions on XFS, Ext3, or Reiserfs. After reading this [article]("http://www.debian-administration.org/articles/388"), i'm leaning toward XFS. Any comment is appreciated :mrgreen:

---

### Post by henriquemaia on 2006-06-02
[quote=oobuntoo]:-D Hello, all Dapper users!! I'm about to reinstall Dapper and have been using ReiserFS without any problem, but want to experiment with other filesystem. I just want some opinions on XFS, Ext3, or Reiserfs. After reading this [article]("http://www.debian-administration.org/articles/388"), i'm leaning toward XFS. Any comment is appreciated :mrgreen:[/quote]

Read this:

[http://ubuntuforums.org/showpost.php?p=1071482&postcount=2](http://ubuntuforums.org/showpost.php?p=1071482&postcount=2)

Maybe this helps you out deciding.

---

### Post by simonn on 2006-06-02
[QUOTE=henriquemaia]
[http://ubuntuforums.org/showpost.php?p=1071482&postcount=2](http://ubuntuforums.org/showpost.php?p=1071482&postcount=2)
[/QUOTE]

From the linked thread:

"If you decide to install XFS, you will need to use a custom partitoning scheme, as linux cannot boot straight from XFS."

Patently untrue.

I have been booting straight into XFS for yonkers. Infact, my whole system is XFS.

I do not know about dapper (have just upgarded via apt), but breezy did not allow you to install to an XFS partition, so I installed to an ext2 partition and copied it across. If you do this, you also need to use mkinitrd to create a new initrd with XFS support.

---

### Post by detgar on 2006-06-02
[QUOTE=simonn]"If you decide to install XFS, you will need to use a custom partitoning scheme, as linux cannot boot straight from XFS."[/QUOTE]

GRUB has problems booting from XFS, but you can just as well use LILO as your boot manager.
If you've got to have GRUB though, create a boot partition with reiserfs, ext2/3 on it, and boot from that.

---

### Post by simonn on 2006-06-02
[QUOTE=detgar]GRUB has problems booting from XFS[/QUOTE]

[http://www.debian-administration.org/articles/388#comment_75](http://www.debian-administration.org/articles/388#comment_75)

"GRUB has supported XFS on /boot for a long time. The only thing that's not supported is if you install the bootloader to an XFS partition (as opposed to installing it to MBR)"

---

### Post by lkagan on 2006-06-02
For your personal system, the filesystem doesn't much matter as long as it journals.  However, different filesystems have different uses.  I'm studying for the Linux+ certification and in my studies I've learned that ReiserFS is 'supposed' to be more appropriate for filesystems on which databases are stored.  I did a quick search for supporting information and have yet to find any to confirm or discredit the statements made by the author of the study guide.  If anyone has any insight to the claim, I would sure like to know.

Thanks.

Larry

By the way, I've been using ext3 on my desktops and servers since it's inception without issue.

---

### Post by Glenn Coombs on 2006-06-02
I used to use xfs at work but switched to reiserfs after I discovered how slow xfs was at deleting directory hierarchies.  I check out lots of files from cvs into various directories.  Doing an "rm -rf dirname" would takes minutes with xfs compared to 10 seconds with reiserfs.

Other than that both filesystems seemed to perform equally well.  For normal home use I doubt you'd notice the difference.

---

### Post by ketsugi on 2006-06-02
I'm currently using reiserfs on my / directory and ext3 on /home.

---

### Post by rbrugman on 2006-06-02
I use reiser FS and have had no problems with it.  I tried to use XFS once, but I couldn't get LVM to work with it.  Kept giving me errors.

---

### Post by hajk on 2006-06-02
I've decided to give JFS a try for the root / partition -- am still using Ext2 for a small 64MB /boot partition. So far, no complaints. I used ReiserFS before, the only difference that I notice: the drive light doesn't come on as frequently in JFS. Another point: lost power and at reboot the JFS journal seemed to be read a lot faster compared with ReiserFS.

Another point: my old ThinkPad A22e appeared ready for the scrapheap, couldn't keep it going for more than an hour before it would freeze solid with I/O errors (using both Ext3 and later ReiserFS / partition). Then I used the Knoppix liveCD to format a JFS root partition, after which I installed Dapper (Beta-2 it was then). No problems with I/O errors since, can leave the old thing running all day. Now, I don't know whether this improvement is due to JFS per se, or to the reformatting of the old disk. Either way, I'm not complaining.:D

---

### Post by oobuntoo on 2006-06-03
Thanks guys (and gals :twisted: )! I didn't know that Grub has problem with XFS. It seems to me that not a whole lot of people use XFS. Hmm...maybe I'll just save myself some trouble and stick with ReiserFS.:rolleyes:

---

### Post by oobuntoo on 2006-06-03
On second thought, booting may not be a problem for me as I have a dual-boot system and I have always installed linux bootloader to MBR.

---

### Post by tsb on 2006-06-03
I tried XFS with GRUB on the MBR but it always gave me a fatal error.  I went back to EXT3.

---

### Post by mips on 2006-06-03
I cannot find any support from the installer to use reiser ? xfs and all the others are there but no reiser ???

---

### Post by tsb on 2006-06-03
are you using the desktop or the alternate install?

ReiserFS shows up when you go to the "use as" menu when you configure the partitions manually in the alternate install....not sure about the desktop version

---

### Post by oobuntoo on 2006-06-04
The desktop version won't give you Reiser, you need to use the alternate version cd. I also had problem creating partitions when using desktop version; the "create" partition option is greyed-out even though I have free space on my disk.
I had to download the alternate version to use text-base installer. I chose to use XFS , installed bootloader to mbr, but the installer automatically chose to install LILO instead of GRUB without giving me any option. LILO boot my kubuntu just fine but I no longer have options to boot to safe-mode or other OS. Now I'm looking for a way to restore GRUB. Anyone has suggestion on how to do this?

---

### Post by tsb on 2006-06-04
hit cancel when it askes to install LILO and you will be returned to the main menu and can choose to install GRUB...you may need to reinstall first, not sure

Let me know if it works out for you, I always got fatal errors 

I'm on ReiserFS now instead.

---

### Post by Half-Left on 2006-06-04
Alsways reiserfs here, must faster but slower boot time because if the filesystem check.

---

### Post by mips on 2006-06-04
Hmm, I started downloading the alternate install but then changed my mind and got the desktop ISO. Should not have changed my mind ](*,) 

I'm having endless problems with qtparted on the desktop cd which sux.

Oh well, you win some you loose some. There goes my monthly bandwidth...

---

### Post by tsb on 2006-06-04
[QUOTE=mips]Hmm, I started downloading the alternate install but then changed my mind and got the desktop ISO. Should not have changed my mind ](*,) 

I'm having endless problems with qtparted on the desktop cd which sux.

Oh well, you win some you loose some. There goes my monthly bandwidth...[/QUOTE]

It's God's sign to switch providers to one w/o bandwidth limits.  :KS

---

### Post by mmcmonster on 2006-06-04
I use ext3 exclusively on my desktop system.

In a worse case scenario, I can boot into WinXP (or take the drive out and put it in a WinXP system) and read the information off of an ext3 partition.

Once I have [IFS]("http://www.fs-driver.org/") installed, of course. :-)

---

### Post by oobuntoo on 2006-06-04
tsb, 

I followed your suggestion and installed GRUB instead of LILO and found out why GRUB was not selected by default when using XFS for root partition. It has compatibility problem with XFS. The installer gave warning about GRUB often fail to boot when using it to boot XFS partition, but I continued anyway and GRUB refused to install. Tried installing it the second time and the whole installation just hang. I gave up and went back to using Reiser for root partition and XFS for home partition. Everything is now working great!

I also found out that you do not need to reinstall the whole thing to install GRUB. Just install grub package from repo and run "grub-install '(hd0)' " if you want to install it to the first hard drive detected by BIOS. But this method didn't work for me neither.:???:

---

### Post by tsb on 2006-06-04
[QUOTE=oobuntoo]tsb, 

I followed your suggestion and installed GRUB instead of LILO and found out why GRUB was not selected by default when using XFS for root partition. It has compatibility problem with XFS. The installer gave warning about GRUB often fail to boot when using it to boot XFS partition, but I continued anyway and GRUB refused to install. Tried installing it the second time and the whole installation just hang. I gave up and went back to using Reiser for root partition and XFS for home partition. Everything is now working great!

I also found out that you do not need to reinstall the whole thing to install GRUB. Just install grub package from repo and run "grub-install '(hd0)' " if you want to install it to the first hard drive detected by BIOS. But this method didn't work for me neither.:???:[/QUOTE]

Yeah, it's really strange.  The XFS website says GRUB 0.97 is fine with XFS but it wouldn't work for me either.  Maybe GRUB 2 would work, but I'm not sure how to install it and probably won't try again since I have my system pretty much perected now.  Maybe the next Kubuntu version.  ;)

---

### Post by mips on 2006-06-04
[QUOTE=tsb]It's God's sign to switch providers to one w/o bandwidth limits.  :KS[/QUOTE]


Unfortunately if you live in a africa bandwidth comes at a premium due to monopolistic laws entrenched by government and you pay through your ears for bandwidth, you can get more but you also pay more. I currently pay about US$15 for 3GB and that is is cheap as it gets.

---

### Post by mips on 2006-06-04
I need to try something else besides ext3. Been having errors on my home partition. If I reformat it and check it with the manufacturers diagnostics tools it is fine but then later on I get errors again.

---

### Post by nix4me on 2006-06-04
The only thing i hate about reiserfs is how long it takes to mount the drive.

I too am thinking of migrating my storage drives to xfs.

nix4me

---

