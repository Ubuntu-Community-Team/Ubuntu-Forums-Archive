---
title: "Cannot dual boot into Windows Vista"
date: 2012-01-22
forum: General Help
---

### Post by dwaldon on 2012-01-22
My university courses use almost exclusively unix environments, so I decided it would be a clever idea to dual boot my laptop with both Windows Vista (previously installed), and the most recent Ubuntu (11.10). I'll go into my procedure in a second, but the problem I'm having is that Vista now won't boot... I can select it from the GRUB 1.99 boot list, and I start to get the Windows loading screen with the green bar, but then things start to go wrong.

Either my laptop will reboot and take me back to the GRUB menu, or it will attempt to start windows in recovery mode. Allowing it to attempt a recovery doesn't work... it works on it for a few minutes (5-10), before telling me the problem cannot be resolved.

Fortunately, Ubuntu seems to be working just fine, but I'd really like to get my Windows OS working as well, since I need it for work.

Now, for the procedure...

I started by using the Vista utility to shrink my disk, resulting in a blank partition of about 25 GB. (Note: the laptop I'm using also has a secondary "factory image" drive... or partition, not entirely sure which... about 8 GB). Using Vista, I could see the three partitions (Blank space, Vista's partition, and the factory image). I rebooted to test that Vista was still all good with this new partition, and everything booted fine, so I burned the Ubuntu iso to a disk, inserted the disk, and rebooted again.

The Ubuntu installer recognized Vista, and so I opted for the default setting ("Install side by side", or something similar). I proceeded to fill in all the info, and Ubuntu installed fine. I rebooted into Ubuntu, and everything still looked good, but when I tried booting into Windows, I hit the snag mentioned above. I've tried running the recovery multiple times, but no luck. And worst of all, the Vista recovery program can't find the factory image, so I can't do a blank restore.

Any ideas on what I can do to fix this?

---

### Post by kleeh777 on 2012-01-22
Try "sudo update-grub" first.

If not, then info is needed:

"sudo fdisk -l" and post the output

and the content of the /boot/grub/grub.cfg

---

### Post by dwaldon on 2012-01-23
Thanks for the reply! After looking around the web a bit last night, I ran chkdsk a few times (Windows would let me run command line during the "Attempt to fix problems" phase), then rebooted into Ubuntu and tried the update-grub. Tadaa! Next attempt loaded Vista just fine... not sure what did it, so I can't recommend a fix to anyone (sorry), but thanks kleeh :).

---

### Post by Mark Phelps on 2012-01-24
Good to see you got it working again -- but are you sure that Ubuntu got installed into the freespace you created manually?

Suggest you check the partitioning, either in Vista (using the Disk Management tool) or in Ubuntu (using the Disk Utility) -- to confirm that Ubuntu actually is in the partition space you created.

---

### Post by dwaldon on 2012-08-08
Sorry it took so long to reply to this... I didn't see the last post that was made here. From what I can see, I think I *may* have installed it in the same partition of Windows... and the problem has resurfaced, so could that have something to do with it? Is there any way to resolve that? Or is my best bet to install ubuntu again into the blank space and try and restore windows to the first partition?

---

### Post by oldfred on 2012-08-08
Did you try chkdsk again? 

Windows does not automatically run it as often as it should. Ubuntu runs its fsck every 40 or 60 reboots.

---

### Post by Mark Phelps on 2012-08-08
> **dwaldon said:**
> Sorry it took so long to reply to this... I didn't see the last post that was made here. From what I can see, I think I *may* have installed it in the same partition of Windows... and the problem has resurfaced, so could that have something to do with it? Is there any way to resolve that? Or is my best bet to install ubuntu again into the blank space and try and restore windows to the first partition?
Your original post talks about installing Ubuntu to its own partition, so if you overwrote the partition containing Vista with Ubuntu -- Vista is gone.

If you're simply have the same Vista boot problems again, as oldfred suggested, go back and redo the stuff you did in post #3 to get Vista working again.

---

### Post by dwaldon on 2012-08-08
> **Mark Phelps said:**
> Your original post talks about installing  Ubuntu to its own partition, so if you overwrote the partition  containing Vista with Ubuntu -- Vista is gone.

If you're simply have the same Vista boot problems again, as oldfred  suggested, go back and redo the stuff you did in post #3 to get Vista  working again.

Sorry, I should have specified... I may have installed Ubuntu 'side by side' with windows. Which isn't quite the same partition, so my bad. Windows appears to be there... at least, all my Windows files are. I can see them as a mounted storage device in Ubuntu. 

After reading a few more posts on here, I downloaded and ran the boot info script... not sure if it'll be of any help, but here it is if anyone's interested :).

---

### Post by oldfred on 2012-08-08
Boot script looks normal to me. 

The windows partition sda1 has the Windows boot files and it not showing any major errors. But then it is a Windows error of some sort and chkdsk or other Windows repairs may be required.

You have some older kernels and may want to houseclean by removing old kernels or using grub customizer to hide them. You generally want to keep one older one just in case of issues.

Many like to hide the Windows recovery partition from the boot menu also, just to prevent accidentally booting it. That can cause major issues if the recovery is started as it wants to overwrite entire drive.

 Check current kernel I also keep one older just in case:
uname -a
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by dwaldon on 2012-08-08
Okay, perfect! Thanks :). I'm at work now, but I'll give chkdsk a try again when I get home and update with my results.

---

### Post by dwaldon on 2012-08-09
Apologies for the double post, but here's the update: After an hour of constant rebooting, I was unable to get to even the command line option. I've searched up a couple ways that can hopefully work around this, so again, I'll give it a shot this evening.

In the meantime, is there any reason anyone can think of for this happening? Or anything I should avoid doing to prevent it from happening in the future?

EDIT: Did some more diggin, this time in Ubuntu, and found a few things using the Disk Utility... The SMARTStatus shows as having a few bad sectors, and when I poen it up, I get a 'Warning' for reallocated sector count, and a 'Failed in the past' for Airflow temperature. I've also noticed that my 'Recovery' partition isn't checked as bootable, which I assume would be what's causing it to not boot :P. Do I need to check this to use my factory reset? Or is there some reason it should be left unchecked?

---

