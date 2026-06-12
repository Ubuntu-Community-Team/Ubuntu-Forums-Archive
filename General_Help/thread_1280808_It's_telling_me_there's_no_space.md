---
title: "It's telling me there's no space"
date: 2009-10-02
forum: General Help
---

### Post by StolenPie on 2009-10-02
Hi,
I'm completely new to Linux, I just bought a Toshiba NB200 netbook very recently and thought I'd try out an alternative OS.
I installed the Jaunty 9.04 netbook remix today. However, whenever I try to save anything (skype, system updates) it tells me there is no space. Sure enough, when I opened up my home folder it told me I had no bites of space! And my filesystem also has no bites of space. Yet I have like 65 gigs of space on the HD for Ubuntu.
I managed to get firefox from my previous windows installment, and save the flashplug-in. But the flash plug-in in the only thing I've been able to save since starting up the computer with Ubuntu.
Also, for some reason, when I open up synaptic it just gives me an error message: 
Failed to run /usr/sbin/synaptic as user root
Unable to copy the user's Xauthorisation file.

Little update:
Something clever in me decided to have a go at something before posting the above message. So I tried making a new account and logging in with that one - so I logged out of my old account and tried to sign in with the new one. It told me there wasn't enough memory to make the new account, so I couldn't sign in with it. Then, since I edited my old account when I created the new one I can't sign in with that one either. So now I can't even sign in to my ubuntu...

A little help?

---

### Post by Giblet5 on 2009-10-02
Open a terminal window. Please post the output of the following command ```
df
```

It's worth noting that running out of disk space, on any OS, can result in file corruption and filesystem errors.

---

### Post by StolenPie on 2009-10-02
well at least it's letting me back in again when I restarted it. I kind of freaked at that point...
OK, here it is:
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              2403420   2281708         0 100% /
tmpfs                   508688         0    508688   0% /lib/init/rw
varrun                  508688        96    508592   1% /var/run
varlock                 508688         0    508688   0% /var/lock
udev                    508688       164    508524   1% /dev
tmpfs                   508688        84    508604   1% /dev/shm
lrm                     508688      2392    506296   1% /lib/modules/2.6.28-11-generic/volatile
overflow                  1024        16      1008   2% /tmp
/dev/sda2             74180132   3992996  70187136   6% /media/Data

---

### Post by Giblet5 on 2009-10-02
Wow.

What is the output of ```
sudo du -sm /home/*
``` (please hide any user account names)

Have you been running backups and assuming they were going to that big Media device?

---

### Post by snowpine on 2009-10-02
Hi StolenPie, 2.2 gb is not big enough for Ubuntu... but it's not your fault; there is a bug in the installer!

You have two options:

1. Try to rescue your system. Boot with the Ubuntu Live CD, then use the Gparted partition editor to shrink one of your other partitions and expand your Ubuntu partition (/dev/sda5). I recommend 10gb minimum.

2. Reinstall Ubuntu. This time, when you get to the partitioner step, don't just click OK... resize the partition so it's at least 10gb, or better yet, use the Manual option. 

You might find this guide helpful for understanding partitions:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck!

---

### Post by StolenPie on 2009-10-02
OK when I ran that, it started asking me for my sudo password. I typed in my ordinary password, and it gave me a message that says permission denied

du: cannot access `/home/accountname/.gvfs': Permission denied
160    /home/accuontname
1    /home/account2

I don't know what you mean about running backups and assuming they were going to a big media device. I don't have any big media devices (so far as I know) and I don't know of any backups...

Snowpine, the partition for Ubuntu should have been 66Gb. When I got to the Data HD (the partition with Ubuntu in it) in Places, it tells me that this is so. But for some reason, it is not acting as though this is the case...

Recent experiments have shown me that it also refuses to empty the deleted items folder. Maybe that's another symptom :)

---

### Post by snowpine on 2009-10-02
> **StolenPie said:**
> Snowpine, the partition for Ubuntu should have been 66Gb. When I got to the Data HD (the partition with Ubuntu in it) in Places, it tells me that this is so. But for some reason, it is not acting as though this is the case...

/dev/sda2 is your /Data partition, and there's plenty of room there.

/dev/sda5 is your / (root) partition, and unfortunately it appears to be full.

---

### Post by StolenPie on 2009-10-02
ok I'll give it a shot
Thanks very much :)

Little update: Ahh, you hit the nail on the head. My screen is to small to see the Ubuntu section of the partitioning, it's just 10.1 inches. All I could see was a nice bar roughly divided into two parts, blue and green, which I foolishly assumed to be Windows XP and Ubuntu. Further along to the right was the tiny little Ubuntu partition. >.<

Anyway, it's loading up now, thanks for all the help!

Much Kudos

Pie

*Conclusion: mispartitioning at initial Installation.*

---

