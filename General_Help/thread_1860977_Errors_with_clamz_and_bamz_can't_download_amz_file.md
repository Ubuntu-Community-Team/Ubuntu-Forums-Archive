---
title: "Errors with clamz and bamz: can't download amz file from Amazon Cloudplayer"
date: 2011-10-15
forum: General Help
---

### Post by mawxcarroll on 2011-10-15
Hi,
  I just purchased some music on Amazon and tried to download it from the Amazon Cloudplayer.  I've done so successfully multiple times in the past using clamz.  However, this time, when I use clamz I get:

[INDENT]
clamz Amazon-MP3-1318681462.amz 
ERROR: Invalid base64 data in AMZ file 'Amazon-MP3-1318681462.amz'

0 of 1 AMZ files downloaded successfully.
[/INDENT]

I also tried bamz, and I get:
[INDENT] 
bamz Amazon-MP3-1318681462.amz 
Invalid .amz file: Amazon-MP3-1318681462.amz
[/INDENT]

I've searched around but I can't find a similar enough issue with any solution.  Has anyone had a similar problem or does anyone have a suggestion?

Thanks!
tom

ps I can always boot into Windows and download, so this is not a pressing issue.  However, I try to minimize my use of Windows so I'd love to figure this out.

---

### Post by linuxlover42 on 2011-10-19
I have the same problem, banshee does not work either. What version of Ubuntu are you using?

---

### Post by Valorie Zimmerman on 2011-10-26
I got the same error, so I filed a bug tonight: [https://bugs.launchpad.net/ubuntu/+source/clamz/+bug/881842](https://bugs.launchpad.net/ubuntu/+source/clamz/+bug/881842)

It probably would be a good idea to confirm the bug, and possibly test the patch available on the Arch bug tracker.

---

### Post by oldos2er on 2011-10-26
> **mawxcarroll said:**
> Hi,
  I just purchased some music on Amazon and tried to download it from the Amazon Cloudplayer.  I've done so successfully multiple times in the past using clamz.  However, this time, when I use clamz I get:

[INDENT]
clamz Amazon-MP3-1318681462.amz 
ERROR: Invalid base64 data in AMZ file 'Amazon-MP3-1318681462.amz'

0 of 1 AMZ files downloaded successfully.
[/INDENT]


I haven't used the cloud player, but I just downloaded an Amazon *.amz file with clamz 0.5 and it worked fine.

The "invalid base64" error sounds as though the *.amz file might have become corrupted.

---

### Post by KYSL on 2011-11-17
> **oldos2er said:**
> I haven't used the cloud player, but I just downloaded an Amazon *.amz file with clamz 0.5 and it worked fine.

The "invalid base64" error sounds as though the *.amz file might have become corrupted.

I had the same problem, seems to be related to file encryption. Solution posted here. 
[http://code.google.com/p/clamz/issues/detail?id=29](http://code.google.com/p/clamz/issues/detail?id=29)

Start first by removing clamz.

---

