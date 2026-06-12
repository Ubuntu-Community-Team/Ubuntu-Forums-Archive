---
title: "Running out of Disk Space?!"
date: 2012-04-19
forum: General Help
---

### Post by jonedney on 2012-04-19
Hello Everyone!

I sat down at the PC today, and had an error that said my Root was running low on disk space.  I ignored it because I sectioned 100 GB of my 1 TB HDD to root.  But, when I go into the Disk Analyzer, it's showing things are almost full!  Am I reading this correctly?

[IMG]http://www.jonedney.me/disc.png[/IMG]

Thank you,
Jon Edney

---

### Post by jerome1232 on 2012-04-19
I've never understood disk analyzer if I wasn't looking at my own system....

What does df say?

```
df -h
```

---

### Post by jonedney on 2012-04-19
Hello!

Here is the output, doesn't seem like I"m close to full:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              92G   27G   61G  31% /
udev                  5.9G  4.0K  5.9G   1% /dev
tmpfs                 2.4G  984K  2.4G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  5.9G  3.6M  5.9G   1% /run/shm
/dev/sda6             762G  197M  724G   1% /usr/local
/home/jon/.Private     92G   27G   61G  31% /home/jon
/dev/sdf1             7.6G  1.1G  6.6G  14% /media/WEB
/dev/sdg1             2.0G   15M  2.0G   1% /media/PC BACKUPS
```

Thank You,
Jon Edney

---

### Post by jerome1232 on 2012-04-19
> **jonedney said:**
> Hello!

Here is the output, doesn't seem like I"m close to full:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              92G   27G   61G  31% /
udev                  5.9G  4.0K  5.9G   1% /dev
tmpfs                 2.4G  984K  2.4G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  5.9G  3.6M  5.9G   1% /run/shm
[COLOR="Red"]/dev/sda6             762G  197M  724G   1% /usr/local[/COLOR]
/home/jon/.Private     92G   27G   61G  31% /home/jon
/dev/sdf1             7.6G  1.1G  6.6G  14% /media/WEB
/dev/sdg1             2.0G   15M  2.0G   1% /media/PC BACKUPS
```

Thank You,
Jon Edney
--snip--

fail on my part, you look fine, I think you have a weeeeee bit to much space allocated for /usr/local Though.

---

### Post by jonedney on 2012-04-19
When I read the documentation to install Ubunut, I set up the partitions, and it said when I specified the data partition, that it would be where all my data was kept, so I made it the remainder of  my HDD space.

That seem accurate?

Thank you,
Jon Edney

---

### Post by jerome1232 on 2012-04-19
ah, well /usr/local is generally used for applications installed manually (via source or what have you). Notice your only using 197 MB's in there.

/home is where all your personal data is stored, and that's what you should have made for the rest of your disk. Alternatively some people like to make a totally separate data partition (usually because they dual boot and want to share it with Windows), mount it somewhere of their choosing (/data? for example) then manually link their Video/Music/Pictures folder(s) and etc... to it.

---

### Post by jonedney on 2012-04-19
Thanks for that information!  I may use the Partition manager I downloaded yesterday and resize these a bit then.

Thanks!
Jon

---

### Post by ajgreeny on 2012-04-19
Disk analyser always shows the "top" filesystem you choose to look at as 100%.

I know it is confusing, and you are not alone in your confusion, as this question appears every so often in these forums.  However the important information is shown in the text line above the diagram which says:-
"Total Filesystem capacity 926.7 GB (Used 29.2 GB available 897.4 GB)"
So you actually have nearly 900GB free space.

As to your partition for /usr/local, I am not at all sure how you can change that without a re-install, which is probably not worth doing unless you have problems at the moment.  Next time you install the system make a separate /home partition, not  /usr/local as shown in [Separate /home]("http://www.psychocats.net/ubuntu/installseparatehome")

You could boot to a live CD or USB and reduce the /usr/local partition size, but with such a large disk I doubt that is worth doing at the moment if all is working OK.

---

