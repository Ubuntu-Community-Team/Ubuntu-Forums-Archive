---
title: "How to boot windows from grub rescue?"
date: 2009-11-23
forum: General Help
---

### Post by McTricks on 2009-11-23
Ok... so here's the story. Yesterday, I made a 15GB partition on my HD to try out the new release, and then installed it. I was setting some stuff up on it, and accidentally messed things up completely. (I'm still a huge noob with this, as you're about to see)

So, seeing how the Ubuntu partition was messed up, I thought I would just erase the partition and try again later. So, I booted windows up, and used partition magic to erase the Ubuntu partition.

By now, I'm sure you all know what the problem I'm having is, but if you don't...

I restarted my PC after erasing the Ubuntu partition, and instead of booting into windows, it booted grub, said it couldn't find the ubuntu partition, and entered rescue mode.

So, what I'm asking is,

1. How do I boot windows from rescue mode?
2. How do I restore my MBR so that it will boot windows? Would reinstalling Ubuntu do that?

---

### Post by suresnjain on 2009-11-23
Since you are not having any ubuntu now, boot via windows recovery console and then fix MBR.Now,your grub menu will be overwritten by new MBR,and U can boot into windows.I have presumed here your windows mean xp.Now,reinstall your ubuntu and thus get a new Grub.O.K.

---

### Post by McTricks on 2009-11-23
Thank you suresnjain, that worked :D

I'm currently booting into windows, and there doesn't seem to be any problem! Thank you againg :D :D

---

### Post by timmy303 on 2010-09-15
I  am having a similar issue.I have a MSI wind netbook and when I start it up it goes to the grub rescue prompt. I'm not sure how to boot in recovery mode for windows. Could ou explain it?

---

### Post by wilee-nilee on 2010-09-15
> **timmy303 said:**
> I  am having a similar issue.I have a MSI wind netbook and when I start it up it goes to the grub rescue prompt. I'm not sure how to boot in recovery mode for windows. Could ou explain it?

Can you post the boot script in my signature in code tags as described.

Really if you can post the script in your own thread this one is rather old. Restoring the mbr to get windows back will take a recovery disc W7, Vista, or a install disc for XP. What we need to know is how Linux was installed, is it a wubi, or a regular install; the script will tell us.

---

### Post by dhunt84971 on 2011-02-12
same problem

---

### Post by bcbc on 2011-02-12
> **dhunt84971 said:**
> same problem

You can't boot windows from grub rescue. But you can fix it easily as described here: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (see Problem #1, solution #1 or #2)

---

### Post by JeanClaudeD on 2012-03-08
[SIZE="1"]This is an old thread, but when I had this problem, google found it here first..  so I'm updating it.[/SIZE]

> **suresnjain said:**
> Since you are not having any ubuntu now, boot via windows recovery console and then fix MBR.Now,your grub menu will be overwritten by new MBR,and U can boot into windows.I have presumed here your windows mean xp.Now,reinstall your ubuntu and thus get a new Grub.O.K.

For those running Vista or Windows 7 _fdisk /mbr_ will not help. 

You will need a Vista or Windows 7 DVD. If you do not have one, you can create Windows 7 disk from an ISO evaluation image of downloaded from Microsoft's website.

To fix your boot environment, boot with Windows 7 installation media.
[INDENT]Start in repair mode[/INDENT]
[INDENT]Choose Command Prompt from recovery options[/INDENT]
[INDENT]Run **bootrec** with one of the following commands:
[INDENT]/FixMbr
/FixBoot
/RebuildBcd
[/INDENT][/INDENT]
*Note:  Usually all that is needed is a **/fixmbr***

---

### Post by lanie5600 on 2012-05-24
I tried the /fixboot etc. all the ones listed above. and it says every time that its not recognized.

---

### Post by wilee-nilee on 2012-05-24
> **lanie5600 said:**
> I tried the /fixboot etc. all the ones listed above. and it says every time that its not recognized.

Start a thread, and state your problem.

---

### Post by oldos2er on 2012-05-25
Old thread closed.

---

