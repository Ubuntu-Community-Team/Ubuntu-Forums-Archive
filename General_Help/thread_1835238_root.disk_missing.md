---
title: "root.disk missing"
date: 2011-08-29
forum: General Help
---

### Post by raghu.k on 2011-08-29
Guys!
I'm having a terrible time with this. I'm using Ubuntu 11.04 on Wubi. Yesterday I was watching 'weeds' when I had to pause to move some files from my desktop to else where. The moving got stuck 98% and I hit the 'x', but it just froze. I went back to vlc and hit the play button. All I heard was Nancy Botwin yell 'f**k' and the system froze all together, after which I was forced to restart [I wish I didn't, but I've terribly little patience for non responsiveness you see...], and now it won't boot.
When I choose Ubuntu in the menu, it complains about root.disk not being there (it is really not there, the partition it used to be on is showing 96% free space) and heads straight to the grub menu. I ran chkdsk 2-3 times but it was no help :(
I ran some disk recovery software from windows, they show me some pdf's I had in that space in 2009, but there is no trace of root.disk. I even booted up from an Ubuntu usb drive and did not find root.disk (swap.disk is still there). 
I'm begging you please help me find my 'root.disk'.

---

### Post by saltmarshlamb on 2011-08-29
Look for a file that's the same size as the wubi partition was. 

But if it's gone then you'll likely need to reinstall it. 

You could try looking for a found.xxxx file if chkdsk moved it.

---

### Post by Mark Phelps on 2011-08-29
You didn't say which Windows file recovery software you tried, but I've found the best to generally be GetDataBack for NTFS from runtime software.

If you didn't try that, you can download the trial version to a Windows PC, scan the drive in question, and see if IT finds the root.disk file. You will have to purchase it to do the actual recovery, but at least you can try it for free.

---

### Post by raghu.k on 2011-08-29
@Phelps I did not try the s/w you mentioned. I'll give it a try. But do you think there is hope?
@saltmarshlamb chkdsk did not work for me. I tried unhiding (even OS related files option) but still did not find the file

---

### Post by dino99 on 2011-08-29
ready for a real installation ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by raghu.k on 2011-08-29
yeah! 
doing some last trials, like giving that s/w Phelps mentioned a try!
and then will do some backup and do the "real" installation.

---

### Post by raghu.k on 2011-08-29
but how on earth can 25gb vanish into thin air? just like that?

---

### Post by Mark Phelps on 2011-08-29
> **raghu.k said:**
>  I did not try the s/w you mentioned. I'll give it a try. But do you think there is hope?

There's always hope ...

If GetDataBack doesn't find anything, you can also try their RecoverMyFiles program.  The former is generally better at filesystem recovery; the latter at finding specific file types.

---

### Post by raghu.k on 2011-08-29
hey..I'm confused here...linux uses ext2/3, windows uses NTFS. what format is root.disk actually in? can our 'ntfs/fat' hunting recovery programs hunt ext? or are they just going to bypass them?

---

### Post by Mark Phelps on 2011-08-29
> **raghu.k said:**
> hey..I'm confused here...linux uses ext2/3, windows uses NTFS. what format is root.disk actually in? 
Since the file exists INSIDE an NTFS partition, you have your answer.
> can our 'ntfs/fat' hunting recovery programs hunt ext? or are they just going to bypass them?
No -- they can only see files in Windows filesystems -- but since root.disk is one big "file" to Windows, the NTFS file recovery apps can possible see it and recover it.

---

### Post by raghu.k on 2011-08-29
well, none of the recovery programs I ran on windows could detect any large file. may be they have a limit or something? 
anyway, I'm now running another recovery program from another freshly installed linux partition -no wubi this time, lesson learnt!

---

### Post by raghu.k on 2011-08-29
> **saltmarshlamb said:**
> Look for a file that's the same size as the wubi partition was. 

But if it's gone then you'll likely need to reinstall it. 

You could try looking for a found.xxxx file if chkdsk moved it.

what do you mean by 'reinstalling' it?

---

### Post by raghu.k on 2011-08-30
I'm trying my luck with R-Studio, but the program is crashing every time it finished analyzing 98% of the disk...has anybody tried R-studio before?

---

