---
title: "External HD (NTFS) no longer recognized"
date: 2010-05-25
forum: General Help
---

### Post by hellonull on 2010-05-25
Hi all.

I have a 1 TB external USB HD formatted to NTFS. Yesterday I was at my buddy's house and had it hooked up to my laptop (running Lucid) to listen to some music off of it. Before I left, I needed to transfer some files to him, so I put them on the HD and then hooked it up to his desktop (running Win XP) to transfer the files.

However, once I hooked it up to his computer, I let it sit for a few minutes and the activity LED on the external HD case was on constantly. But the drive never came up under 'My Computer' on his machine. So, after a few minutes, while the activity LED was still on, I turned off the power on the HD and packed it up because I had to leave.

Today, I plugged the external HD into my laptop and it is not mounting. Nor does it show up as a sdX device in /dev, in the [FONT="Courier New"]fdisk -l[/FONT] list, or in gparted. I also checked the logs and there is no mention of any USB device when I plug it in.

I plugged it into my desktop (Win XP) to see if that might be able to do something since it is NTFS formatted. However, the disk does not come up as a removable device nor does it show in disk management.

I am pretty sure this has something to do with not unmounting the disk correctly ("safe eject" or whatever M$ calls it). Assuming that is the case, I'm confident that [FONT="Courier New"]ntfsfix[/FONT] or [FONT="Courier New"]chkdsk[/FONT] will fix it, but I've got to find a way to get one of those running on the disk.

Any ideas? Suggestions for either Ubuntu or XP are appreciated.

---

