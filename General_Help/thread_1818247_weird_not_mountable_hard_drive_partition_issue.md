---
title: "weird not mountable hard drive partition issue"
date: 2011-08-04
forum: General Help
---

### Post by imadman on 2011-08-04
i all,

I've got a question which might be more like a hardware issue but it is still pretty weird on the software side.

My cousin had a laptop that died on him (hp laptop with gpu issues where fixing was too expensive), he didn't have a connector to get his data off of his hdd so i tried doing that with my laptop.

This is what i did:
-I first booted up ubuntu 9.10 with the live cd with the hdd already in the pc. Once i tried to open the drive it say's it can't mount his first of 2 partitions(The second one mounts and displays it's thing without issues).
-I repeated the process with puppy linux, knoppix 5.1 and madbox with the same results.
-I then launched partition wizard live cd and it didn't show any issues with the drive or partitions and i could even use the 'show content of drive' thingy which shows the folders and everything looked ok.
-Still with no clue of what was going on i deleted the second partition and told partition wizard to fill out the first partition on the entire drive(since partition 2 didn't contain any data that was of importance).(and it looks like partition wizard live is linux based)


any idea's?

matthias

btw I'm not a native English speaker :s

---

### Post by Beacon11 on 2011-08-04
I assume you've tried running fsck?

---

### Post by imadman on 2011-08-06
> **Beacon11 said:**
> I assume you've tried running fsck?

I have very foolishly not done that and since i am not very good at terminal could you help me with the syntax a little?

---

### Post by oldfred on 2011-08-06
Were these partitions NTFS or ext family?

If NTFS you have to run chkdsk from a windows CD. Ubuntu will not normally mount a NTFS partition that needs chkdsk to prevent any problems that chkdsk could not then fix, and Ubuntu seems a bit more sensitive than windows. I could use my XP but Ubuntu would not mount it, but after a chkdsk then it worked in Ubuntu.

If ext Linux format:

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by imadman on 2011-08-07
It's ntfs, will try the chkdsk thing with windows xp installer cd, thanks!

---

