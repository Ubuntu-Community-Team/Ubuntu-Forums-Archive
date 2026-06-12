---
title: "can't start ubuntu...&quot;gave up waiting for root device&quot;"
date: 2010-07-28
forum: General Help
---

### Post by Reallyold on 2010-07-28
The above message appears when I try booting ubunto 10.04 desktop. No previous problems. Other messages appear as well, trying to give me hints as to what might cause this and finally I see "ALERT! /dev/sdb1 does not exist. Dropping to shell!"
What the heck does all that mean and most importantly how do I resolve it?
I can get into Windows XP as a boot option but that's buggy now and I want ubuntu back.
Help? I am very new to ubuntu so please don't reply with insider language if possible.
Thanks...

---

### Post by drs305 on 2010-07-28
Is your Ubuntu installation is on sdb1? If not, it may be an error in your fstab file.

From the prompt you are dropped to, first get the UUID in case it is referenced in fstab:
```
blkid | grep sdb1
```
Then open the fstab file for editing:
```
nano /etc/fstab
```
Find the line that references sdb1 and place a comment symbol (#) in front of it.

Save the file with CTRL-x, then Y(es), and reboot.

If that is successful, post the contents of the following and we can help you permanently fix things:
```
cat /etc/fstab
sudo blkid -c /dev/null

```

If your Ubuntu install is on sdb1, please boot from the Ubuntu LiveCD and go to this site to download the *boot info script*. Run the script from a terminal (Applications, Accessories, Terminal) and post the results here. For formatting, press the # icon in the post's menu and copy the results between the 'code' tags.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Reallyold on 2010-07-28
Sorry, what is sdb1? How do I know if it's installed there? I had Wubi do the install and now I'm running it from a USB hard drive. 
Thanks for your help....(at least ubuntu has very good help resources).
Regards,
Bill K

---

### Post by Reallyold on 2010-07-28
Well hmmm, I retried (3rd time) booting and this time it went perfectly. I had gone into Windows Safe Mode and ran an antispyware program from Microsoft, but I doubt that had anything to do with Ubuntu.....or did it? Anyway I'm back up and running, at least with Ubuntu.

---

