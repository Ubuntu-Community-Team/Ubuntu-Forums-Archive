---
title: "ext4 freezed the system while emptying trash, now disk free space missing"
date: 2009-09-10
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-09-10
Sorry I don't want to hijack this[ thread ]("http://ubuntuforums.org/showthread.php?t=1139604")
so I post my question here.

Last time I was copying 40GB files. During the copying I emptied the trash box. Then my computer freezed, I could do nothing but press the hard reset button. After reboot I noticed that the disk space reduced by around 20GB, but the files that ought to be copied disappeared.

I already fsck my drive. But the disk space is still 20GB less then it should be. What can I do to fix it? Thanks in advance!

---

### Post by ckonestroh on 2009-09-10
Load in smaller file sizes????

reduces the chance of taxing your cpu????

---

### Post by sasho_zl on 2009-09-10
Welcome to the club! The same thing happened to me last month. I also lost my home folder with all my pics and docs. I couldn't restore anything and finally I did one fresh install with ext3 as a FS.

---

### Post by QIII on 2009-09-10
Although I have never had problems, I am aware that there are issues with ext4, particularly with manipulating large files when a system crash occurs.

Karmic installs with ext4 by default and the new kernel seems to handle the large file issue fine.

---

### Post by sdowney717 on 2009-09-10
a couple of times I have lost significant space multiple gb's when emptying trash.
the trash somehow ends up in root trash. I dont recall the details how it happens, but it has occured twice in the last year.
if you enable root login you will see it, otherwise I cant remember but i was shown how to get to it to delete them from my normal login.

---

### Post by afeasfaerw23231233 on 2009-09-13
It happened again. I deleted 40GB of trash and the system hanged. After hard reset the free disk space was reduced by 40GB. It is really frustrating.

Would anyone please suggest any method except reinstalling the whole system?

I am using Ubuntu 9.04 64-bit ext4.

---

### Post by afeasfaerw23231233 on 2009-09-13
I discover the undeleted trash is located here:

```
~/.local/share/Trash/expunged/3235897935$ ls
09-08_23-46-34_&#20013;&#22830;.ts
[fbtz.com] [KC] EPL 2nd Round Review Show English Comm x264 24th Aug
[fbtz.com] [KC] Manchester United vs Arsenal 1st half English Comm x264 29th Aug
[fbtz.com] [KC] Roma vs Juventus 1st half English Comm x264 30th Aug
Match of The Day 22nd August 2009
motd 2 - albiondean.avi
motd 2 - Capped by albiondean.avi
motd 2 Capped by albiondean.avi
motd Capped by albiondean.avi
The League Cup Show - 26th August 2009
&#24052;&#35199;V &#38463;&#26681;&#24311;
&#24847;&#22823;&#21033;&#23565;&#26684;&#39791;&#21513;&#20126;
&#25308;&#20161;V&#31166;&#22827;
&#31934;&#33775;
&#32178;&#29699;
&#35199;&#29677;&#29273;&#23565;&#27604;&#21033;&#26178;

```
I deleted them and recovered the 40GB free space. 

Wish that I knew this issue earlier so that I wouldn't choose this buggy ext4 as my filesystem!

How can I fix this bug without reinstallation?

Any suggestion will be appreciated!

---

