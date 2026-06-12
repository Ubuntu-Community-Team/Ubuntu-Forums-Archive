---
title: "HELP! HELP! directory just disappeared.."
date: 2010-05-02
forum: General Help
---

### Post by feuerchop on 2010-05-02
hey guys..I got just so unlucky..
Last night I upgraded to Ubuntu 10.04 from 9.10. Then I found it's not so awesome because suspend and hibernate just don't work always so nice, sometimes just can't get asleep and just get no response..
So, I tried to use uswusr (if my memory was right) and s2ram s2disk to test them..boommm..
just crashed and I can't no longer login..
So I tried to backup data using live cd(10.04)
I sudo nautilus ./ to open the /var/lib/mysql (which is the place where I store my database)
and right click on that folder -> copy to -> Home Folder
suddenly...that folder disappeared..and I cant find it anymore, no matter how I search..
doesn't work..who can help me with that, that data is really important for me...
:(:(:(

Why some files just disappear in Ubuntu, seems that happened to me before as well..
is it a bug?

---

### Post by feuerchop on 2010-05-03
bump

---

### Post by nothingspecial on 2010-05-03
This will be of no help at all weather I`m right or wrong. But if you did that from a live cd, wouldn`t it try to copy the folder to the live disk`s home folder? Which it wouldn`t be able to do?

Do not boot your main system, this time try, with the live cd, again but instead of right click > copy to home folder - choose to copy it to the home folder of your hard drive, or better still some external media.

---

### Post by Vaphell on 2010-05-03
i experienced such disappearing items in nautilus - try refreshing or check in terminal with
```
cd /target/directory
ls -a
```
if the file in question is there

nothingspecial is right, pasting to home dir when using live cd means you tried to paste stuff into non-persistent live cd home dir. If you want to find your true home dir, you need to navigate to your mount point used to access hdd partitions and look there for example /mnt/disk1/home/yournickname

---

