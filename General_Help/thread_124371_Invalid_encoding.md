---
title: "Invalid encoding?"
date: 2006-02-01
forum: General Help
---

### Post by tico on 2006-02-01
Well, I have not yet installed Ubuntu. I'm testing it before using the live CD. My NTFS partition (where WinXP is installed) has some folders whose name has accents (á, é, ó, ô, õ etc.). When I access these folders (I can access them), I see the following message beside the folders's name: Mod?les (invalid enconding). The folder's real name is "Modèles". Is there a way to get the right enconding?

TIA

---

### Post by nszabolcs on 2006-02-01
i had the same problem

nls=utf8 mount option solved my problem
my /etc/fstab :
```

/dev/sda1       /media/c     ntfs    umask=0222,nls=utf8        0       0
/dev/sda5       /media/d     ntfs    umask=0222,nls=utf8        0       0

```

---

### Post by tico on 2006-02-01
Hi, nszabolcs,

Thanks for your answer. Doing what yo said let me see and browser my ntfs partitions using file browser, but the enconding character is still there. Any clue?

---

### Post by Pahanilmanlintu on 2006-03-08
Same problem here, the nls=utf8 option doesn't help for some reason, even though for some other finnish people it does work, according to forum posts. I might have been dumb enough to use something like iso8859-10 on the partition, in case that's possible, so i also tried nls=iso8859-10, nls=iso8859-1 and nls=iso8859-15. None of the nls options i tried seemed to make a difference, compared to just leaving it out.

So anyone know what charsets can be used on ntfs partitions in the first place?

Now this wouldn't otherwise be a problem, but in a few cases i can't access certain files at all, because of the characters they contain.

EDIT: Ok, this is embarrassing :) I didn't **unmount** them first. So now it works.

@tico, in case the issue is still relevant, try
sudo umount -a
sudo mount -a
after including the nls=utf8 in fstab

---

### Post by adamkane on 2006-03-08
Try browsing, rather than mounting.

Panel -> Places -> Network Servers

[http://www.ubuntuforums.org/showthread.php?t=139154]("http://www.ubuntuforums.org/showthread.php?t=139154")

---

