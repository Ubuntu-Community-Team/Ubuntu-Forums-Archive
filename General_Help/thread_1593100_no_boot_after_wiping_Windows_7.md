---
title: "no boot after wiping Windows 7"
date: 2010-10-11
forum: General Help
---

### Post by mkaut on 2010-10-11
Hello,

I wanted to get rid of Windows 7 on my HP laptop; I had found some thread that said I can just removed the two partitions (Windows 7 has a separate boot partition) and run grub-update (or something like that). I did that (removed the two partitions and created a new one) and the machine does not boot anymore.

I tried to restore grub, following several threads in this forum. This is what I did:
1. boot from Ubuntu 10.04 live CD
2. remove grub-pc and install grub (the laptop is upgraded from 9.04 and hence still uses grub 1 - at least I can see grub.menu and no grub.cfg in /boot/grub.
3. sudo grub
4. find /boot/grub/stage1 .. gives hd(0,4), which is correct, as the Xubuntu partition is on /sda5
5. root (hd0,4)
6. setup (hd0) .. says everything is OK
7. reboot

After reboot, I get "Non-System disk or disk error" message, i.e. the grub does not even start.
I have moved the hard drive to be the first booting device in the BIOS, but it does not make any difference.

Some more info:
- I tried flagging the Xubuntu partition as boot, but it did not help. Should I remove the flag?
- My drives as reported by gparted:
  : unallocated .. ca. 128MB in case I ever need a boot partition.
  : /dev/sda1 .. ext2 partition - this is the new partition replacing the Windows 7
  : /dev/sda3 .. extended
  :   /dev/sda5 .. ext3 with Xubuntu
  :   /dev/sda6 .. linux-swap


Now I have run out of ideas what to try .. please help

Thanks in advance,
Michal

---

### Post by Kunsun on 2010-10-11
I'm not sure if you have another computer or not, but here is what I did. 

I took out the hard drive from my laptop, connected it to my pc ( i used jumpers do designate the laptop hard drive as "slave") when it was connected I formatted the drive, and installed ubuntu onto a flash drive the ubuntu site tells you how to do this.) Also, check your bios to make sure you can boot from a usb port first.

I set my bios to load the OS from the flash drive.

selected 'install to hard drive' option it gave me before it started to run ubuntu (i missed this option the first time, so im not positive it IS there the first time. also the selection screen goes away after a few seconds.)
and i installed it to the hard drive.

I then reset the computer after the install was complete and the ubuntu was working, updated software, and now am learning to enjoy ubuntu.

Sorry if this doesn't help you, I'm new here, to ubuntu, and to linux.

---

### Post by mkaut on 2010-10-11
Kunsun,

thanks for the suggestion, but I do not see how this would help - I do not want to re-install my system, as it is still there (I can mount and access the drive from the live CD) .. not to mention that I have no intention to take the drive out of my laptop..
(And if I wanted to re-install, I could do it from the live CD anyway.)

Michal

---

### Post by Quackers on 2010-10-11
mkaut, when you did what you said in your first post, did you chroot into your installed system after booting the Live CD? Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by mkaut on 2010-10-11
> **Quackers said:**
> mkaut, when you did what you said in your first post, did you chroot into your installed system after booting the Live CD? Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

No I did not - I thought that one does that only if it does not work without..
I was about to try it when I found that I was using a 32-bit live CD for a 64-bit system ](*,) - could this (using wrong arch.) be the source of the problem?
Anyway, I am downloading an x64 live CD now...

---

### Post by Quackers on 2010-10-11
If you are chroot'ing into your existing system I can't see it being a problem.
If you boot into the Live cd but don't chroot into your existing system all the commands you enter will only act on the Live cd file system, not your own.

---

### Post by mkaut on 2010-10-11
I have now done the same thing (steps. 3-6 from the o.p.) with checkroot to the orig. file system.
In addition, I did update-grub. Then I noticed that it did not remove the (now non-existing) Windows partition from the /boot/grub/menu.lst, so I deleted the file and re-run update-grub.

After reboot, I still get the same: BIOS complaints about "Non-System disk or disk error", i.e. grub does not even start. :confused:

Any other ideas?
Should I, for example, have /dev/sda5 flagged as boot, or is is irrelevant?
Or would it make sense to purge and re-install grub (with checkroot)? Or purge grub and install grub2?

Michal

---

### Post by Quackers on 2010-10-11
That sounds to me like it's trying to boot Windows but can't find the boot files.
You say in your last post that you have run steps 3 - 6 of the details in your first post. I think that is unlikely to do anything. 
I would suggest, again, that you visit the thread below and follow the instructions there. At least grub2 will be purged and installed then.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
The boot flag is irrelevant to Linux.

---

### Post by mkaut on 2010-10-11
> **Quackers said:**
> That sounds to me like it's trying to boot Windows but can't find the boot files.
You say in your last post that you have run steps 3 - 6 of the details in your first post. I think that is unlikely to do anything. 
I would suggest, again, that you visit the thread below and follow the instructions there. At least grub2 will be purged and installed then.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
The boot flag is irrelevant to Linux.

Thanks.

Just to be sure: should I purge my current grub1 and install grub2?
(As I mentioned, I have still grub1 install - which is why I was hesitant to follow the thread since it talks about grub2.)

Michal

---

### Post by Quackers on 2010-10-11
That is what I would do, yes, following drs305's guide.

---

### Post by oldfred on 2010-10-11
I prefer grub2 and they seem to have fixed the vast majority of issues with it. But you can keep grub legacy and it should work.

To see more details about your install.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Grub/Ubuntu does not use boot flag, but a few BIOS will not let you boot unless there is a boot flag on a primary partition. I might move the boot flag to sda1 even though you do not boot it.

---

### Post by mkaut on 2010-10-11
> **Quackers said:**
> That is what I would do, yes, following drs305's guide.

OK, I did that, i.e. purged grub and installed grub-pc. I decided to say no to the chaining, since the original grub did not work.
on configuring, I got the following error message a couple of times:
```
ls: cannot access /casper-rw-backing: No such file or directory
```
I guess it comes from the live CD, but I don't know if it is a problem.

Anyway, the "Non-System disk or disk error" message is still there after reboot ](*,) .. must admit I am getting rather desperate now..

Michal

---

### Post by Quackers on 2010-10-11
In Oldfred's post he gives a link for the boot info script. Please run that and post the results in code tags ( # in New Reply )

---

### Post by mkaut on 2010-10-11
> **oldfred said:**
> I prefer grub2 and they seem to have fixed the vast majority of issues with it. But you can keep grub legacy and it should work.

Grub/Ubuntu does not use boot flag, but a few BIOS will not let you boot unless there is a boot flag on a primary partition. I might move the boot flag to sda1 even though you do not boot it.

BINGO! :popcorn:
I set the boot flag on sda1 and it just boots :-)
Weird .. that partition is empty, nothing to boot there..

Anyway, I am marking this solved, thanks a lot ):P

---

