---
title: "Ubuntu 10.10 not saving files to NTFS correctly?"
date: 2011-05-13
forum: General Help
---

### Post by moorsey on 2011-05-13
Not sure if I am doing this correctly, just the obvious way I guess.  I have dual boot with Ubuntu 10.10 and Win7 x64.  They are on their own partitions, Windows on NTFS and Ubuntu on ext4.

Every now and then when I am in my Ubuntu system, I will load/save files from the NTFS partition.  So I mount the NTFS by just going on places and clicking on the drive.

This morning I loaded some video files and converted them to wav files in Kdenlive, saving them back to NTFS.  I then right clicked on the Windows drive and un mounted it, no problem.

Re-booting into Windows I found that the files were not there!  Well one of the files was, but it was corrupt and not complete.

Looking in Ubuntu, the files were not there either.

I have seen this behaviour in the past, but never thought anything of it, just that maybe I hadn't un-mounted the drive correctly, but this was not the case this time.  Does Ubuntu have a /very/ delayed write to NTFS?  I assumed that if it un-mounted correctly then everything had finished writing?

Thanks for any extra info on this!

---

### Post by sanderj on 2011-05-13
Interesting. I have no solution, other than doing some tests:

- write a 1 MB, a 10 MB, a 100 MB, a 1000 MB file to the NTFS partition, and see which files are OK. The command "dd if=/dev/zero of=<directory/filename-on-NTFS> bs=1M count=100" will help
- check /var/log/messages etc

---

### Post by moorsey on 2011-05-13
thanks for that, will give it a test over the weekend.  Wanted to make sure I wasn't missing anything with known issues with compatibility between Ubuntu and NTFS.  Will report back

---

### Post by Morbius1 on 2011-05-13
Do the files you are creating in Linux have goofy ( from a Windows perspective ) characters in them like:
```
” * / : < > ? \ |
```

There is a relatively new ntfs-3g mounting option that will prevent you from saving files with those characters ( **windows_names ) **but you will have to add an entry into /etc/fstab so that you can enable it.

---

### Post by srs5694 on 2011-05-13
Three thoughts:


[list]
[*]How did you shut down and reboot? If you just hit the physical Reset button on the computer, that's likely the cause. You *must* properly shut down Linux (or any modern OS) or risk data loss on your hard disks. Unmounting the Windows partition, as you say you did, should do the trick; but it could be that operation took a while and if you hit the Reset button before it completed, that could account for the problem.
[*]It's possible that the NTFS volume is suffering from damage. I recommend you run CHKDSK on it (from Windows), perhaps multiple times.
[*]The NTFS-3g driver that Ubuntu uses for NTFS access was, AFAIK, developed by reverse engineering, and as such may have undiscovered errors in it. It's conceivable you ran into such a bug. This is one of several reasons I recommend using NTFS as little as possible from Linux. Unfortunately, for some people "as little as possible" is still quite a bit. :(
[/list]

---

### Post by oldfred on 2011-05-13
+1 on srs5694 comments.

A couple of more.

Did you hibernate in Windows? Hibernation may not work if you are writing into the NTFS partitions as it has saved parts of the windows system and if that data has moved then it has issues.

Most of us suggest a separate shared NTFS partition and avoid writing into another system's system partition. Even windows only users suggest a separate data D: drive so when you have to reinstall windows your data does not have to be reinstalled (backups still required).

Ubuntu's NTFS shows all windows files & folders including the normally hidden system files. It can be too easy to accidentally move or delete important files in windows if you are not careful. Best if the windows  system partition is set to be read only.

---

### Post by SuperFreak on 2011-05-13
Not sure if this relevant but I had the same problem with NTFS and using XSane on my Ubuntu/XP system. I saved scanned files onto my NTFS partition but was unable to read them in Win XP although I could in Ubuntu. I discovered that XSane was not writing the .jpg suffix after I scanned images and by manually adding the suffix I was then able to read the files in XP

---

### Post by moorsey on 2011-05-17
Thanks for all the replies, had another mess with this yesterday, saving another video from kdenlive, all but vanished when coming into Windows.

> **Morbius1 said:**
> Do the files you are creating in Linux have goofy ( from a Windows perspective ) characters in them

Nope, nothing special about the names, a point to remember though!

> **srs5694 said:**
> Three thoughts:


[list]
[*]How did you shut down and reboot? If you just hit the physical Reset button on the computer, that's likely the cause. You *must* properly shut down Linux (or any modern OS) or risk data loss on your hard disks. Unmounting the Windows partition, as you say you did, should do the trick; but it could be that operation took a while and if you hit the Reset button before it completed, that could account for the problem.
[*]It's possible that the NTFS volume is suffering from damage. I recommend you run CHKDSK on it (from Windows), perhaps multiple times.
[*]The NTFS-3g driver that Ubuntu uses for NTFS access was, AFAIK, developed by reverse engineering, and as such may have undiscovered errors in it. It's conceivable you ran into such a bug. This is one of several reasons I recommend using NTFS as little as possible from Linux. Unfortunately, for some people "as little as possible" is still quite a bit. :(
[/list]

Always shutdown properly, so should be no problems there

Chkdsk is a good idea, worth a shot later

> **oldfred said:**
> +1 on srs5694 comments.

A couple of more.

Did you hibernate in Windows? Hibernation may not work if you are writing into the NTFS partitions as it has saved parts of the windows system and if that data has moved then it has issues.

Most of us suggest a separate shared NTFS partition and avoid writing into another system's system partition. Even windows only users suggest a separate data D: drive so when you have to reinstall windows your data does not have to be reinstalled (backups still required).

Ubuntu's NTFS shows all windows files & folders including the normally hidden system files. It can be too easy to accidentally move or delete important files in windows if you are not careful. Best if the windows  system partition is set to be read only.

I do hibernate Windows, so could be a cause of the problem.  Will try a clean shutdown on Windows, then a write to the drive from Ubuntu.

I like the idea of a seperate "shared" partition.  I have only recently started using my Ubuntu more and more for Kdenlive use, so haven't needed to write to NTFS much in the past.  But becoming more of an issue now

> **SuperFreak said:**
> Not sure if this relevant but I had the same problem with NTFS and using XSane on my Ubuntu/XP system. I saved scanned files onto my NTFS partition but was unable to read them in Win XP although I could in Ubuntu. I discovered that XSane was not writing the .jpg suffix after I scanned images and by manually adding the suffix I was then able to read the files in XP

Thanks for the tip.  In this case, nothing is showing at all, not even a file without an extension


Will try these things later on and see where I get

Cheers all

---

### Post by moorsey on 2011-05-23
Hi all, just wanted to post back my findings

When a Windows 7 machine in hibernated, Ubuntu 10.10 cannot properly write to the NTFS partition that Windows is on.

It goes through without issue and shows no warnings etc, but back in Windows, the data is not there.  If you created any folders, they will be there, but you won't be able to open/delete them.

Thanks for all the tips on this.  I will know either setup a separate partition or just not hibernate when using Ubuntu

Cheers

---

### Post by sanderj on 2011-05-23
> **moorsey said:**
> Hi all, just wanted to post back my findings

When a Windows 7 machine in hibernated, Ubuntu 10.10 cannot properly write to the NTFS partition that Windows is on.

It goes through without issue and shows no warnings etc


Strange: in my experience you can't even access a hiverbated NTFS drive. Only by force-mounting it (ignoring the warnings), you can have access to it.

So, did you see the messages?

---

### Post by moorsey on 2011-05-23
odd indeed.  I just clicked on the drive from "Places", no messages, nothing forced etc.  Unless it is a Windows 7 "thing"?

---

### Post by Kais3rvlc on 2011-06-03
Hi. I have a similar problem as when i create files from ubuntu in my shared D: partition (NTFS) they would corrupt when i restart on windows and i didn't know why because it never happened to me, as far as i can remember, with previous ubuntu distributions.

It makes sense that can be due to have hibernated windows, but i think that, then, this problem does also affect other partitions, not only windows partition, as it is happening to my shared one.

---

### Post by Kais3rvlc on 2011-06-03
sorry, i forgot to say that im using 11.04 natty 64 bits

---

### Post by oldfred on 2011-06-03
It still might cause issues. 

If when you hibernate you have files open on the shared and then modify those files or they get moved by Ubuntu, then when you recover from the windows hibernation they are not where it thought they were or the size they were.

---

