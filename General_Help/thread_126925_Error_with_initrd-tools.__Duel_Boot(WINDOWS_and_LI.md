---
title: "Error with initrd-tools.  Duel Boot(WINDOWS and LINUX partition)."
date: 2006-02-07
forum: General Help
---

### Post by ubuntuforums on 2006-02-07
When trying to install Ubuntu 5.10 on my computer I get the following error:

```

[!!] Install the base system.
Unable to install initrd-tools.

An error was returned while trying to install the initrd-tools package onto the target system.

Check /target/var/log/bootstrap.log for details.

```

I used my live version of knoppix to check the log file.  It didn't exist.  Anyone know how to fix my problem.

I have an NTFS partition, and then 10.5GB FREE SPACE, I let Ubuntu "Automatically Partition" it.  I made a 10GB partition and a 0.5GB SWAP partition.

I want to duel boot with my Windows OS(XP PRO) which is already on the harddrive.  I checked the ISO with md5sum and it didn't return any errors.  Anyone have any ideas as to how I can fix my problem.  Will burning a new CD at 4X fix my problem?

Any ideas or suggestions would be great!  All help is really appreciated.

---

### Post by ubuntuforums on 2006-02-07
I just burnt the ISO at 4X.  I tried installing Ubuntu and I got the same error...  Has anyone had this problem before?  How can I fix it?  I really want to use Ubuntu...

---

### Post by Jason_25 on 2006-02-07
I've gotten lots of weird errors and I try to remember what I did to correct them.  The   only time I have seen that one is when the memory in my pc was unstable.  If you are overclocking, go back to normal speeds, if not, check your bios to see if your memory is set too aggressively.

---

### Post by ubuntuforums on 2006-02-07
hmm...  Well Im not overclocking anything.  Maybe its because I've disabled things in my bios.  What do I need enabled in the bios?

---

### Post by Jason_25 on 2006-02-07
Maybe the auto partitioning tool doesn't do a good job when dealing with other partitions.  It might help to go back through the installer and choose 'manually edit partition table' and make a / partition that is bootable and a swap partition of  suitable size (1gb is fine).

---

### Post by ubuntuforums on 2006-02-07
Do you think that could be the problem?  What I'm doing is using "Manually Edit Partition Table" then using the free space to have it "Automatically Partition" it or whatever.  So then it makes the ext3 partition and the swap partition...


Anyone have any ideas, I'm still stuck without Ubuntu, and I really want to use this OS...   Help please..

---

### Post by ubuntuforums on 2006-02-08
...

---

### Post by ubuntuforums on 2006-02-08
no one can help me?

---

### Post by ubuntuforums on 2006-02-09
BUMP.  I still need help please...

---

### Post by ubuntuforums on 2006-02-09
help...

Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by Jason_25 on 2006-02-09
I hate to see you not getting any help...

Have you ran your pc through memtest86 yet?  Even though it's set to stock speeds  maybe you have a bad stick.

---

