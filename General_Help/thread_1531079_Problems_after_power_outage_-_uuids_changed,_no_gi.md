---
title: "Problems after power outage - uuids changed, no gigabit"
date: 2010-07-14
forum: General Help
---

### Post by evilneko on 2010-07-14
Hello Ubuntu forums, I come with questions to try out the wonderful forum support I keep hearing Ubuntu has! I figure this is a convenient time to ask, since I am soon to swap the UPS on my Ubuntu box. 

This all refers to Ubuntu 9.04.


You see, not too long ago, I had a couple of power outages, and suffice to say, despite the efforts of my UPS, I didn't get to shut down my Ubuntu box properly on either occasion. After the first one, when I powered the computer back on it failed to boot. Some googling of the error message led me to find that the UUIDs Ubuntu assigns to things like hard drives, which are not SUPPOSED to change, had in fact changed. From an archived thread here I found out how to find out what the new ones were, and slapped them into my FSTAB hoping that'd be the end of it. 

(Partitions/Drives affected: hda2, hdb)

It wasn't. Ubuntu came up with new errors to throw at me. This time, it threw the "bad superblock/wrong fs type" error that I'm used to seeing when I fudge a mount command. It appeared to be the same anyway, it went by so fast I couldn't really read it, sure wish the pause button worked. The gui did finally load, but showed no sign of the affected drives.

I found that if I commented out the affected drives in the fstab, they would appear in the gui, ready and mountable and apparently just fine. 

I've double-checked the UUIDs. The new UUIDs I put in fstab match the new UUIDs that the vol_id command reports.

**What is wrong with my fstab? Why won't it mount them automatically?** (I'll post both versions as an attachment)

Another minor problem is for some reason I can't get privoxy running anymore. I've temporarily taken to running the Windows version in wine. I seem to remember I had a helluva time getting the linux version to work in the first place anyway, so I think I'll just keep running the windows version in wine. Any advice would be appreciated though.

**Most importantly, what can I do to prevent this happening again?** Debian Sarge never gave me such trouble (and my deb box suffered quite a few improper shutdowns too). Ubuntu's based on Debian. What gives?

And finally, can someone point me to software capable of communicating (over USB) with a Belkin UPS and shutting the computer down before the UPS battery dies?

---

### Post by tgalati4 on 2010-07-14
If the Belkin uses a protocol similar to APC then you can use apcupsd.  If that doesn't work, then try nut and upsd.

---

### Post by evilneko on 2010-07-15
Well, I'll look into that. Can anyone help me with actually getting my drives to mount? Maybe suggest a way to keep fstab from breaking even if the uuids do change? Why did they change anyway? From what I understand, they're not supposed to.

---

### Post by evilneko on 2010-07-16
Did I post this in the wrong section? Should it be moved to hardware?

---

### Post by Morbius1 on 2010-07-16
First I don't know much about reiserfs but I'm very confused by your attachments.

Original fstab:
> # /cjd was on /dev/sda2 during installation
#UUID=3CE0C3E6E0C3A48C /cjd            reiserfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /cje was on /dev/sdb1 during installation
#UUID=7428E0A528E06816 /cje            reiserfs    defaults,nls=utf8,umask=007,gid=46 0       1The UUID format is for an NTFS partition. The options you used are for an NTFS partition. But the filetype listed is reiserfs.

New fstab:
> # /cjd was on /dev/sda2 during installation
UUID=46509984-c376-48e9-986b-0ea5e09291d0 /cjd            reiserfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /cje was on /dev/sdb1 during installation
UUID=38aeb3bb-c7f4-4b93-8a19-33e390ea95a8 /cje            reiserfs    defaults,nls=utf8,umask=007,gid=46 0       1The UUID format is now for a linux filesystem but you still have NTFS type options listed.

How are these two formatted. Post the output of the following command so as many people as possible can see how you're set up:
```
sudo blkid -c /dev/null
```

---

### Post by evilneko on 2010-07-16
Ah that might be a clue right there. It was oringally a Windows box. Now that I think about it I did reformat those drives after the fact. (one by accident, one planned, I didn't want torrents running off ntfs under linux) They were ntfs at install time, I had originally planned to dual boot. That kinda went out the window when I accidentally formatted sda2 (I should probably nuke sda1 and recover the rest of that space, maybe even merge those partitions...)

They are both indeed reiserfs.

```

/dev/sda1: UUID="1650638850636D85" LABEL="HDA1" TYPE="ntfs" 
/dev/sda2: UUID="46509984-c376-48e9-986b-0ea5e09291d0" TYPE="reiserfs" 
/dev/sda3: UUID="2b7c48d4-2db4-4f78-9b53-684a2f0bd4f9" TYPE="ext3" 
/dev/sda5: UUID="2d108b96-9367-4fe6-bc3a-f6f4f8c85d53" TYPE="swap" 
/dev/sdb1: UUID="38aeb3bb-c7f4-4b93-8a19-33e390ea95a8" TYPE="reiserfs" 
```

I looked at the mount man page and I am not sure if I need any of the reiserfs-specific options or not. I just need the drive mounted at boot and fully accessible to non-root users. It's mainly a data drive but I have some binaries that I run off it as well. So, if I changed the line for /cje to the following...
```
UUID=38aeb3bb-c7f4-4b93-8a19-33e390ea95a8 /cje            reiserfs    users,exec,rw 0       1
```

I'm pretty sure I should get what I want.

So maybe this isn't so much the result of the power outage as the tool I used (came with Ubuntu, GPartEd I think) to format the drive not updating fstab.

---

