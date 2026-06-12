---
title: "readonly on hdd previously used with mac"
date: 2010-08-30
forum: General Help
---

### Post by xapss on 2010-08-30
Hi,

I've recently (read: today) migrated to ubuntu for my server. Now I would like to connect my external WD hard disk to it but it is read-only protection.

I've tried some things already, so please enlighten me!


[LIST=1]
[*]I checked whether the disk is protected at the mac-end (using the WD tool). This is not the case.
[*]I tried sudo nautilus, but couldnt change permission.
[*]I tried sudo chown but couldnt as the disk was readonly.
[/LIST]
Does anyone have a better idea? Or, what am I doing wrong?
Formatting the disk isn't much of an option as it contains valuable data.

Thanks in advance!

Maurice

---

### Post by Autodidact on 2010-08-30
Your HD is probably using the HFS+ filesystem.

See:
[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

---

### Post by xapss on 2010-08-31
Hi, yes, thanks. Probably I am.

I remember i use macdisk on windows to access the disks without any problems.

For linux, is this any idea: [http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/) ?

---

### Post by xapss on 2010-08-31
ah, never mind. i used ur advise! i unjournaled the volumes. Now its a matter of 'not authorized' in the screen. i think cuz i unmounted them 'uncleanly' or something. still have to get used to linux :)

---

### Post by xapss on 2010-08-31
ok, still a bit problematic:

I've disabled journaling on both drives (i partitioned them). however, they are still hfsplus. And, i still cant write to them.

What am i doing wrong? I double checked on mac, they're both un-journaled, but they support journaling if needed (says the info screen).

Is it because i had previously mounted them on linux, that it keeps something (old settings: journaled) in its cache or something?

thx in advance!

Maurice

---

