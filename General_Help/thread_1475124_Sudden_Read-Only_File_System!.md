---
title: "Sudden Read-Only File System?!"
date: 2010-05-06
forum: General Help
---

### Post by kai_kan on 2010-05-06
I was moving my music collection from my old laptop to my new one using an external hard drive when suddenly the process came to a halt with an error: it seems my primary (internal) file-system voluntarily changed to read-only, all the way up to root. I can no longer create, move or delete any files, and when I check permissions of the whole drive I'm told "The permissions of "/" could not be determined".

Wish I had some idea of how this happened. This is a 24-hour old Ubuntu 10.04 64-bit install (actually a 9.10 install, upgraded to 10.04 since I had trouble installing from the 10.04 liveCD) that seemed to be working fine. Heck, the music transfer stopped in the Ts... it was almost done.

More importantly, though, I need to know how to fix it. Help?

Thanks!

---

### Post by kai_kan on 2010-05-06
Hmm... Seems OK now.

When I rebooted (was understandably afraid to try that), the loader found the error with the drive and offered me options. I asked to try to fix it, was sent back to grub again, and booted fine with appropriate permissions. If this holds, I'll come back and mark this as solved for the next guy.

---

### Post by StuartN on 2010-05-06
> **kai_kan said:**
> it seems my primary (internal) file-system voluntarily changed to read-only, all the way up to root.

If it repeats this behaviour then this might be worth following [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937) "Filesystems end up remounted read-only, Bug #515937"

---

### Post by kai_kan on 2010-05-07
OK, it happened again... this time while ripping a CD with RubyRipper. Same fix worked, but hardly a "solution" since this is now twice in two days.

@ StuartN: Thanks for the link! I checked it out, but I'm not sure what info I can gain (a bit of a noob, sorry). I did notice that they said it happened when the drive was not in use, yet for me both times the drive was actively being written. Perhaps a different issue?

Eager for any other wisdom. This could get annoying fast.

---

### Post by GUmeR on 2010-05-08
Same issue here.

System is OK for few minutes, after that I goes read-only without any reason. Also, programs take ages to start after this happens.

System is week old 10.04 64bit install. It started to happen after today's update.

Now I reverted to 2.6.32-21-generic (in grub menu) and it seems to be OK for now.

---

### Post by kstan_79 on 2010-05-08
I confirm this issue happend in my pc too. After it change to readonly partition I tried fsck immediately it show a lot of error (I use ext3 that time) and ask me to fix it. End up all data in that partition cannot recover and I'm been force to reformat the hard disk.

I thought it is because ext3 issue, but now ext4 have the same result. Remount partition as r/w failed too.

---

### Post by krupintupple on 2010-05-08
i believe i'm having the same thing happen to me as well. is there any cure or work-around? it's very frustrating when, even as root-user, you are told it is 'read-only' and you cannot actually do anything!

---

### Post by jimgowdy on 2010-05-09
I recently updated from 9.04 to Ubuntu 9.10 - the Karmic Koala
My flash drive would not allow data to be saved it said my folders were "read only" so...
	
1. Copied all contents of the "read only" flash drive to a folder on my desktop. [that worked for me]
2. Right clicked on my flash drive and reformatted in FAT3 generic.
3. Recopied all data from folder on desktop to flash drive.
4. Data is now read-write

[COLOR="Red"]It was interesting that some files AND folders did not copy and had to be skipped...the names of the files were characters that seemed to be ASCII graphing characters to me AND the folder was numbered...like "_134245_".[/COLOR]

---

### Post by GUmeR on 2010-05-10
Ok, I have exactly the same issue as a guy behind link above (Bug #515937"). Very similar dmesg output. Also on Lenovo laptop, EXT4, 64bit etc.

Check your dmesg in case this happens again, this will give you better idea what is exactly going wrong. In my case it was:

```
[186634.040186] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[186634.040197] ata1.00: failed command: FLUSH CACHE EXT
[186634.040211] ata1.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[186634.040214]          res 40/00:00:00:4f:c2/00:00:00:00:00/40 Emask 0x4 (timeout)
[186634.040222] ata1.00: status: { DRDY }
[186639.080111] ata1: link is slow to respond, please be patient (ready=0)
[186644.062655] ata1: device not ready (errno=-16), forcing hardreset
[186644.062679] ata1: soft resetting link
[186644.341012] ata1.00: configured for UDMA/133
[186644.341023] ata1.00: device reported invalid CHS sector 0
[186644.341049] ata1: EH complete
[186644.364029] end_request: I/O error, dev sda, sector 100786824
[186644.364094] Aborting journal on device sda4-8.
[186644.370197] EXT4-fs error (device sda4): ext4_journal_start_sb: Detected aborted journal
[186644.370208] EXT4-fs (sda4): Remounting filesystem read-only
[186644.474564] EXT4-fs error (device sda4) in ext4_reserve_inode_write: Journal has aborted
[186644.474572] EXT4-fs error (device sda4) in ext4_dirty_inode: Journal has aborted
[186644.474698] EXT4-fs error (device sda4) in ext4_mb_free_blocks: Journal has aborted
[186644.474703] EXT4-fs (sda4): delayed block allocation failed for inode 1054179 at logical offset 2453 with max blocks 7 with error -30
[186644.474707] 
[186644.474708] This should not happen!!  Data will be lost
[186644.474726] EXT4-fs (sda4): ext4_da_writepages: jbd2_start: 1003 pages, ino 1054179; err -30
[186644.474729] 
```

For now I added boot options: acpi=off noapic nolapic

I have only very foggy idea what they do, so use them at your own risk!

Also link how to apply boot options: [http://ubuntuforums.org/showthread.php?t=1376547](http://ubuntuforums.org/showthread.php?t=1376547)

EDIT:
Don't bother, acpi=off stuff didn't work. Reporting it to kernel bugzilla.

---

### Post by emilywind on 2010-05-18
Responding to a post in [my thread on this topic](http://ubuntuforums.org/showthread.php?t=1483894#5) here in order to merge the efforts to get this bug resolved.

I am running 64bit Ubuntu with the latest official kernel (2.6.32-22-generic) on an ASUS n80vn laptop and my filesystem is ext4. I will obtain and post the output of dmesg whenever the issue arises again.

I also removed the errors=remount-readonly from the fstab entry for my root partition several occurrences of this issue ago and tune2fs says the error mode should be to continue, but the remounting read-only still happens which definitely makes it seem like a deep-rooted kernel issue.

This reminds me a bit of a bug we had long ago in a project I worked on called Vana, which is a server emulator for an MMORPG called Maple Story. Due to the lack of a mutual exclusion when it came to shifting packet header keys, the client would randomly disconnect because at times the key would not be increased properly. It was extremely hard to debug and unfortunately persisted within the program for many months before we resolved it. Hopefully this gets fixed soon though. :)

---

### Post by Nizzok on 2010-05-19
Having the same problems with 10.04 on a lenovo laptop, celeron based g450. The drive is a wd passport, and it's completely read-only. this happened during an upgrade, unfinished torrents were stopped due to the permissions error...

---

### Post by emilywind on 2010-05-19
It seems this bug is related to  [this one  about data corruption coming from kernel 2.6.28-11]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691"), which seems  to randomly affect different 64bit kernel releases and not others. This  would explain why the error report on the Ubuntu forums about this dated  back to 2008 and such. If the developers looked for a patch pattern  within the affected kernels, that would likely be a good start.

I think the reason this recently started affecting me a lot is due  to the latest kernel (2.6.32-22). I did not have the issues as all with  kernel 2.6.32-21 as GUmeR reports, so reverting to that is the best bet  for avoiding this issue for now. Cheers.

---

### Post by GUmeR on 2010-05-19
Ok

Reverting to 2.6.32-21 as I suggested DOESN'T work :)

Thanks for the link, I will read thread and ask around. We will get to the bottom of this :)

EDIT:

The related bug you suggested, one behind your link, guys there came to conclusion, that it affects computers with 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller, which is exactly the controller I have :/.

Could you paste results of:
```
sudo lshw | grep "SATA"
```

EDIT #2:

The other guy, from _[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937")_, has Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03).

EDIT #3:

Here is bug report on bugzilla.kernel.org: _[https://bugzilla.kernel.org/show_bug.cgi?id=16006]("https://bugzilla.kernel.org/show_bug.cgi?id=16006")_

Looks like they already fixed it. Details behind link. In short: libata in 2.6.32 has issues, but it is fixed in newer release. We just need to figure out how to apply this newer kernel, or just wait for Canonical to update kernel.

---

### Post by StuartN on 2010-05-19
> **GUmeR said:**
> EDIT #3:

Here is bug report on bugzilla.kernel.org: _[https://bugzilla.kernel.org/show_bug.cgi?id=16006]("https://bugzilla.kernel.org/show_bug.cgi?id=16006")_

Looks like they already fixed it. Details behind link. In short: libata in 2.6.32 has issues, but it is fixed in newer release. We just need to figure out how to apply this newer kernel, or just wait for Canonical to update kernel.

This looks like it could be the problem, and it has not been applied in Ubuntu kernel 2.6.32 - are there any easy guides on compiling your own Ubuntu kernel, with this patch (and proprietary drivers) applied?!

---

### Post by GUmeR on 2010-05-19
First, I never replaced kernel apart from official updates, so if someone worked with kernels before, please correct me.

Second, I have no idea if these kernels below include mentioned fix. It's wild guess :)

I have found this:
_[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds")_

They have precompiled future kernels for Lucid, for testing here:
_[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")_

You may try installing image only, for example this one:
_[linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_amd64.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_amd64.deb")_

Unfortunately I need restricted NVidia driver (for CUDA development), which recompiles itself for each kernel update, so I need whole package (image, headers-all, headers-amd64, source) + gcc3.2. I can't figure out how to satisfy dependency in:
linux-headers-2.6.34-020634rc7-generic_2.6.34-020634rc7_amd64.deb
which depends on:
linux-headers-2.6.34-020634rc7

(I don't care that much about solving dependency problem, I can do my work without touching HDD a lot, but you will probably need to solve it if you want proprietary NVidia drivers)

---

### Post by StuartN on 2010-05-19
> **GUmeR said:**
> Second, I have no idea if these kernels below include mentioned fix. It's wild guess :)

I have no idea if this patch is in later kernels either - I downloaded kernel-source which I assume is for my current kernel (2.6.32-22-generic) and the libata-eh.c in that is not patched with this patch.

I was looking at [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) and had doubts about my ability to compile a kernel and link in my wireless driver.

---

### Post by GUmeR on 2010-05-19
Guy at kernel bugzilla said:
> libata as of 2.6.32 doesn't retry after any FLUSH failure [...] So, in short, please upgrade to newer kernel or tell your distro to backport the update.

So as far as I understand 2.6.32 is not patched (and we are getting errors). Guy there suggests that future kernel is patched, I just don't know which version number corresponds to 6013efd8860bf15c1f86f365332642cfe557152f commit, which contains patch :/

You may try downloading kernel-source for more recent kernel from here:
_[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")_

EDIT:
I just read your post again. Yes, I think that kernel-source package corresponds to your current kernel, that is 2.6.32

---

### Post by StuartN on 2010-05-19
> **GUmeR said:**
> So as far as I understand 2.6.32 is not patched (and we are getting errors). Guy there suggests that future kernel is patched, I just don't know which version number corresponds

I just did a search and the patch appears in this change-log: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33-rc1/CHANGES)

So if this flush error is the problem, then any kernel 2.6.33 will contain the patch. I will see if I can install one and still have wireless.

---

### Post by GUmeR on 2010-05-19
Just curious, how did you find that? Did you search for commit id? If yes, where?

---

### Post by emilywind on 2010-05-19
@GUmeR: I also have an ICH9 chipset, but it seems that the issue is more general than that according to the bug report on kernel.org's bugzilla. I figure I will make an account on there and ask where the patch has shown up, and also post a link to that bug report to the various launchpad reports to see if I can get things moving in the way of getting developers to update the official Ubuntu kernel. Cheers. :)

---

### Post by StuartN on 2010-05-19
> **GUmeR said:**
> Just curious, how did you find that? Did you search for commit id? If yes, where?

The Ubuntu changelogs do not contain commit ids, but they do contain the description line - I searched for the commit description using
```
"libata: retry failed FLUSH if device didn't fail it" site:kernel.ubuntu.com
```

I see kernel 2.6.33 is not available in Proposed or in Backports, so it isn't a one-click upgrade.

EDIT: I added kernel 2.6.34-020634-generic from the mainline repository, installed it and added it to grub - it doesn't work with my proprietary Broadcom wl wireless driver, but I have a USB Ralink STA that seems to work.

EDIT 2: My onboard Broadcom wireless functions fine with an alternative driver, b43-fwcutter, so I am on kernel 2.6.34 and hoping that this is stable.

---

### Post by emilywind on 2010-05-19
I am currently installing the 2.6.34 mainline builds for Lucid. I will let you all know how it turns out. :)

EDIT: My system is up and running on the 2.6.34 mainline, and I had no issues with the nvidia drivers or anything else so far. Hopefully this kernel will fix these issues. I will keep you all up to date. :)

---

### Post by emilywind on 2010-05-21
**Update:** I did a "test" of sorts, aka just happened to be doing something which would normally trigger the bug (seeding torrents, transferring over 15GB of files to my external hard drive and watching a video), and it did not occur. So far kernel 2.6.34 is looking to have the issue resolved within it. Hopefully this issue which catch on with the developers soon, as it is not good to leave the current kernel floating around in a long-term support OS for much longer. lol

---

### Post by StuartN on 2010-05-21
> **emilywind said:**
> **Update:** I did a "test" of sorts, aka just happened to be doing something which would normally trigger the bug

I agree with you, updating the kernel appears to be a complete fix for the freezing issue, hopefully it will become a one-click upgrade soon. The instructions at [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds) are easy to follow.

It would be nice to have a freeze-test, but I could not get the script in [https://bugzilla.kernel.org/show_bug.cgi?id=14543](https://bugzilla.kernel.org/show_bug.cgi?id=14543) to freeze my affected system, and I think that script needs work.

Obviously using test kernels will disable some proprietary hardware (graphics and wireless etc), as well as potentially new bugs and instability.

---

### Post by emilywind on 2010-05-21
Using the mainline build is working fine for me for now. However, not everyone using Ubuntu who encounters this error is going to know enough to install a mainline kernel and install the nvidia drivers from the website in order to get plymouth working again. Plus, most people, including myself, would much rather things 'just work' as people tend to expect from Ubuntu and most other operating systems these days. So hopefully the Ubuntu deveopers make a proper upgrade to fix this soon since flagrant errors such as this one are rather unsightly.

---

### Post by fishtenors on 2010-09-19
I know this thread is a little dated, but I recently ran into this same problem. I was able to get back from the dead by booting in to kernel version .20, where Ubuntu dropped me into a recovery shell. I ran (as root):

fsck -A

...and all is well. Just keep hitting Y(es) at any prompts to fix your filesystem.

Currently running aptitude now to see if I can get past this buggy .22 kernel version. Hopefully this helps someone out there.

---

