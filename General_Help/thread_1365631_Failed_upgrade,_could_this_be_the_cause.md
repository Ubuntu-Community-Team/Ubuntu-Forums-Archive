---
title: "Failed upgrade, could this be the cause?"
date: 2009-12-27
forum: General Help
---

### Post by Ottis on 2009-12-27
Last night I tried to update my Ubuntu 9.04 to 9.10 online, as soon as it started installing updates it started giving me MANY error messages. Most seemed to be problems writing to read-only file systems. Since there was no going back at that point I just kept clicking OK.
After it was done, (finely)  it wouldn't shut down all the way, and I ended up unplugging it. 
Now I get a bunch of errors saying variations on "Unable to remove xxxxx Read only file system, and always ending with "re-default main process (xxxx) terminated with status 127"
I looked around on the 'net and decided it would be easier to reinstall from scratch, Im downloading the 9.10 iso now.
My question is this;
I have two PCs, both Dell Optiplex 210L's, both dual booting XP home and Ubuntu, one is still 8.04, and the one Im having problems with is /was 9.04.
Recently I installed a piece of software on Windows called "Ext2IFS", it lets you see the ext3 partitions from Windows, when setting it up I set it to "read only" to make sure I didn't accidentally change something on the Linux side of things.
It works fine on both PCs, didn't seem to effect either operating system, but Im wondering if that could have made certain files "read only" and screwed up the update. And is this going to mess up the reinstall even if I remove the program from the Windows OS?
Im kinda' new to Linux so any ideas and input would be appreciated! Thanks!

---

### Post by emoguitarist06 on 2009-12-27
> **Ottis said:**
> Last night I tried to update my Ubuntu 9.04 to 9.10 online, as soon as it started installing updates it started giving me MANY error messages. Most seemed to be problems writing to read-only file systems. Since there was no going back at that point I just kept clicking OK.
After it was done, (finely)  it wouldn't shut down all the way, and I ended up unplugging it. 
Now I get a bunch of errors saying variations on "Unable to remove xxxxx Read only file system, and always ending with "re-default main process (xxxx) terminated with status 127"
I looked around on the 'net and decided it would be easier to reinstall from scratch, Im downloading the 9.10 iso now.
My question is this;
I have two PCs, both Dell Optiplex 210L's, both dual booting XP home and Ubuntu, one is still 8.04, and the one Im having problems with is /was 9.04.
Recently I installed a piece of software on Windows called "Ext2IFS", it lets you see the ext3 partitions from Windows, when setting it up I set it to "read only" to make sure I didn't accidentally change something on the Linux side of things.
It works fine on both PCs, didn't seem to effect either operating system, but Im wondering if that could have made certain files "read only" and screwed up the update. And is this going to mess up the reinstall even if I remove the program from the Windows OS?
Im kinda' new to Linux so any ideas and input would be appreciated! Thanks!

Sorry just an idea. But Ubuntu 9.10 uses ext4 and it looks like that software is made to access ext2 file systems but can be configured to access ext3. I don't show any support for ext4 which is a fairly new file system.

What files would you need to access in ubuntu from windows? like music or pictures? If so I suggest to have all of your music and pictures on windows and ubuntu can natively mount windows ntfs/fat file system to access the files.

I used to do that when i dual booted.

Did this help?

---

### Post by Ottis on 2009-12-27
Thanks for the input!
I didn't know 9.10 was ext4, (Im kinda' new to Linux) I installed Ext2ifs just so I could share the music folders between the two OSs, mostly I installed it out of curiosity, to see how it worked. (curiosity killed more then the cat...)
I was mostly wondering if anyone else has tried this and had similar problems, I wont be using anything like this again till I learn more about it.

Could something like Ext2ifs installed on Windows effect the Linux partition???

---

### Post by emoguitarist06 on 2009-12-27
> **Ottis said:**
> Thanks for the input!
I didn't know 9.10 was ext4, (Im kinda' new to Linux) I installed Ext2ifs just so I could share the music folders between the two OSs, mostly I installed it out of curiosity, to see how it worked. (curiosity killed more then the cat...)
I was mostly wondering if anyone else has tried this and had similar problems, I wont be using anything like this again till I learn more about it.

Could something like Ext2ifs installed on Windows effect the Linux partition???

Unfortunately I have a limited knowledge on partitions and file systems myself. But it sounds like from this sentence: "It installs a pure kernel mode file system driver Ext2fs.sys, which actually extends the Windows operating system to include the Ext2 file system" from [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html) it may be able to affect the linux kernel.

But from my experience before I full migrated from Windows Vista to Ubuntu 9.04 (now i have 9.10 as well) I was dual booting like yourself. I never saw the need to install Ext2ifs because my laptop came with Vista and so all of my files were on Windows and Ubuntu can mount the NTFS by just clicking on the Menu "Places" and choosing that file system and it'll mount to linux and i would just navigate to "my documents" and find all of files.

However when I "need" to use windows now I run a virtual machine (i prefer virtualbox) and i use DropBox ([www.dropbox.com](www.dropbox.com)) in Ubuntu & Windows if I want to access files from one another. (of course only works with an internet connection)

---

### Post by Ottis on 2009-12-27
This is all on my "shop" PC, I might just do a full install sense I hardly ever use Windows on it anyway, my other PC is in the living room and my wife doesn't see the need to learn another operating system, so I have to stick with dual boot on that one.
just now booted up to the 9.10 disc I just burned, booted a LOT faster the the 8.04 cd did, looks good!:)

---

### Post by emoguitarist06 on 2009-12-27
> **Ottis said:**
> This is all on my "shop" PC, I might just do a full install sense I hardly ever use Windows on it anyway, my other PC is in the living room and my wife doesn't see the need to learn another operating system, so I have to stick with dual boot on that one.
just now booted up to the 9.10 disc I just burned, booted a LOT faster the the 8.04 cd did, looks good!:)

Sweet! I'm glad to here it. And yes the boot time is amazing! even just from 9.04, 9.10 is a lot faster!

---

### Post by arubislander on 2009-12-27
Not that it matters anymore but:

1. The software you installed in Windows to access your ext3 partitions certainly did not cause your errors on booting your computer after the failed upgrade. The error messages were caused by the failed upgrade. And I'm pretty sure it didn't cause your upgrade to fail either. What did will possibly have to remain a mystery.
2. No program installed under Windows can affect the Linux kernel. Unless of course it writes to your Linux partition...

Having said the above, it's probably never a good idea to let Windows have access to the partition you boot Linux from.

---

