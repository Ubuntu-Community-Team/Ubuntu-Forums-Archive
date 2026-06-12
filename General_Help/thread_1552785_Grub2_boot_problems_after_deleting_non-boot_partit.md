---
title: "Grub2 boot problems after deleting non-boot partition"
date: 2010-08-14
forum: General Help
---

### Post by tgeer43 on 2010-08-14
Ya know, I'm as big a fan of Linux as Linus Torvalds himself but it's things like this that help to keep Linux from becoming mainstream. I mean, how would I ever explain the need for the following procedure to a non-techie type, recent or prospective Ubuntu convert? The following is not a question, as I have finally resolved the issue but is more of a rant, I guess you could say. The reasons that I decided to post it are:

1) To hopefully help someone else experiencing this issue.
2) To point out the need for significant improvement in the area of editing partitions under Ubuntu Linux.
3) To vent my spleen.

--------------------------------------------------------------------------------------------------

_Here's the situation_:
The layout of my primary drive was as follows:

[ sda5: 70GB unused partition  ] .   [ sda6: 70GB main system/boot partition  ] .    [ sda1: 3GB swap partition  ]

I wanted to reclaim the unused partition (sda5) and incorporate it into my main partition (sda6) so I first deleted the unused 70GB partition (sda5). No problems there but of course once I deleted sda5 the main partition (sda6) got re-designated as sda5. I then decided that before resizing the main partition to include the 70GB that was formerly sda5, I would make a backup of the system in case of data loss or corruption during the process. I do my backups from within the normal running system by using 'tar' so I attempted to reboot and got the following error message:```
error: no such partition
grub rescue>
``` Ok, no surprise there since grub.cfg was still referencing sda6 which no longer exists. So to try to get booted I issued the following commands from the 'grub rescue>' prompt: ```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```All of the commands prior to 'boot' executed without error and the system did indeed begin to boot the current kernel from the correct (and only) boot partition but part way through the boot process it halted with the following: ```
init: ureadahead-other main process (885) terminated with status 4
```There was no way to recover from this and I had to CTRL-ALT-DEL and boot up my USB flash drive copy of Ubuntu.

I researched the error message and although there were numerous bug reports and other mentions of it on the web, they were all regarding this message as a cosmetic issue unrelated to the failed boot process as exit status 4 is a clean exit code for ureadahead and should not be logged or output to the console. This left me no where to go but purely by luck I decided to modify /etc/fstab to remove the line pertaining to the now defunct partition. I was then able to repeat the above grub rescue commands and successfully boot the current kernel. Once booted, I performed a 'sudo update-grub' and everything appears to be ok now.

My point is that is that all I did was delete an unused partition which should be straightforward and technically should not affect the boot process and it opened up a gnarly can of worms instead. I could find no helpful information related to this and it took several hours to resolve and ultimately cost me an entire night's work. I dare say that a new Ubuntu user (and maybe even the 'average' current user) would not have been able to resolve this issue and would have been left with an un-bootable system. Heaven forbid that this should happen to a business machine. I don't even think that reinstalling Grub2 would have helped. Simply deleting an unused partition should not require such a convoluted and largely undocumented process to recover from. When friends come to me with all of their nasty Windows problems I try very hard to convert them to Ubuntu and I'm pretty successful at it but it's unnecessary things like this that make life difficult for me. Don't get me wrong - I'm extremely grateful to have a wonderful distro like Ubuntu to run on my personal machines and to introduce to unfortunate Windows users. It's just that it's clear that there are still a number of areas for significant improvement.

Thanks for reading,

tgeer

---

### Post by tgeer43 on 2010-08-14
Well damn! My first post in this thread may not have been a question but this one definitely is. And I went ahead and [prematurely] marked the thread as solved - jinxed myself.

Anyway, everything in post #1 is accurate, including the fact that after finally being able to boot and run 'sudo update-grub' the system was booting normally.

I then backed up the system before resizing sda5 to incorporate the unallocated space that was previously sda6 before that partition was deleted. The resize operation went off without a hitch but when I rebooted, I got the ole "error: no such partition" message and was once again dropped at the 'grub rescue>' prompt. Typing 'set' revealed that grub once again was referencing hd0,6 in the prefix and root instead of hd0,5. I issued the same set of grub rescue commands as in post #1 and was able to boot the current kernel, this time without the ureadahead error. I then ran 'sudo update-grub' and it completed successfully. I inspected /boot/grub/grub.cfg and it is completely correct as far as I can see. All references are to hd0,5 and the UUID is correct. No mention of hd0,6 whatsoever. /etc/fstab is likewise correct. I can post them here if needed but they really are ok. Still, on subsequent boots the prefix and root are still set to hd0,6 instead of hd0,5. Wtf is going on? Is this info stored in the boot sector on the disk? And why are my changes not being retained now when they were when I changed the prefix and root earlier per my 1st post?

Am I gonna have to reinstall grub after all? Argh... I just don't get it.

Help please!

tgeer

---

