---
title: "Learning it the hard way.."
date: 2006-02-12
forum: General Help
---

### Post by Mishal on 2006-02-12
I am a relatively new Linux user and I have already reinstalled Linux 3 times. That's because I have the habit of poking around with the system files until I know what each of them are for.

So, I foolishly edited fstab to give permission to all users to read and write hdd1 (my boot partition) and now root itself cannot access it!
When the computer tries to reboot, files in hdd1 are shown to be read-only. Now I tried to edit the fstab using pico by logging in through recovery mode but of course I cannot. Since I have to login to recovery mode using root, I can't edit fstab because I don't have the permission.

So who has the permission and how can I edit fstab? I DO NOT want to reinstall Linux all over again. I just did it once this morning. That is NOT an option.

Thanks:-D

---

### Post by aysiu on 2006-02-12
That's weird that you can't edit it in recovery mode.
Do you have a live CD handy?

---

### Post by Mishal on 2006-02-12
No :(

Help! :(

---

### Post by aysiu on 2006-02-12
Okay.

When you're *not* in recovery mode... what happens when you boot up? Are you able to log in at all as the first user you created during installation? Are you able to log in as *anything*?

I'm going to boot into recovery mode, so I can give you some better instructions. I'll be back.

---

### Post by Mishal on 2006-02-12
Thanks for the quick reply. You are really helpful.

When I try to log in normally, some of the files the system tries to access in order to boot are shown as 'read-only'. Apparently, those files need to be modified everytime Ubuntu wants to boot.

I cannot login as anything....root or my user profile or whatever....the login screen doesn't even show up.

---

### Post by Mishal on 2006-02-12
Okay, I tried logging in normally again and after saying 'ok' to some of the processes being checked, it failed with 'calculating module dependencies'.

Calculating module dependencies...
Fatal: Could not open /lib/modules/2.6.12.9-386/modules.dep.temp for writing: Read-only file system

Also, after saying that and after mounting all the hard drive partitions, it failed here:
/etc/init.d/bootclean.sh: line 42: /tmp/.clean: Read-only file system.


What I had done was add umask=0000 with 'default' as options for hdd1 in my fstab. What a horrible mistake! :(

---

### Post by aysiu on 2006-02-12
Okay.

I just booted into recovery mode and was able to edit the /etc/fstab by typing ```
nano /etc/fstab
```

What happens when you try to do that? Any errors?

---

### Post by Mishal on 2006-02-12
Yes I tried that but it won't allow me to save my changes because it keeps on reminding me that the file is read-only

I also tried chmod 777 /etc/fstab. Failure again...

---

### Post by aysiu on 2006-02-12
A live CD may be the only way to fix this, then.

Is there any way to get ahold of one--maybe download and burn a Knoppix ISO from a friend's/relative's computer?

---

### Post by Mishal on 2006-02-12
Hmmm...now that you tell me....I do have a Kubuntu live CD...though not ubuntu...it should work all the same

I will try and let you know :)

---

### Post by Mishal on 2006-02-12
It worked and I changed the fstab from my LiveCD.

My Breezy Badger is happy now:)

---

### Post by aysiu on 2006-02-12
Awesome.

---

