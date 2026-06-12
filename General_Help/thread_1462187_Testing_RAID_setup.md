---
title: "Testing RAID setup"
date: 2010-04-25
forum: General Help
---

### Post by Mindgamer on 2010-04-25
I have set up a RAID1 array and am trying to test if its is set up correctly/if errors are detected, reported and recoverable. Need some help though.

Started up the mdadm monitor with:
```
mdadm --monitor -f --mail=my.email@address.com --delay=600 /dev/md0
```I set the RAID array to a faulty state by doing:
```
mindgamer@mind-server:~$ sudo mdadm --manage --set-faulty /dev/md0 /dev/sdc1
mdadm: set /dev/sdc1 faulty in /dev/md0
mindgamer@mind-server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0] sdc1[2](F)
      1953511936 blocks [2/1] [U_]

unused devices: <none>
```However I do not get any problem reports to my e-mail address. When I test the mdadm I get this result:
```
mindgamer@mind-server:~$ sudo mdadm -F --scan -t
[sudo] password for mindgamer:
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory
sendmail: fatal: open /etc/postfix/main.cf: No such file or directory

^C
mindgamer@mind-server:~$
```When I look in the postfix folder, sure enough.. there is no main.cf file there... but there IS a file named 'master.cf'. I am running Ubunto 9.10 with default components - have postfix but no sendmail.

Anyways I am not sure how to proceed. I am very new to Linux so some advice would be very nice... Thank you.

---

### Post by Mindgamer on 2010-04-26
Perhaps I should try and rephrase my question:

Can someone please offer some advice on how to get mdadm --manage to work?

---

### Post by Yoshiwars on 2010-06-01
I was stuck at the same place. It's Postfix.
I have a raid 5 array on my 10.04 server and I wanted the email notifications. I followed this guide to get postfix to send through my gmail account
[http://braiden.org/?p=15]("http://braiden.org/?p=15")
Although, I already have it installed so I ran
```
sudo dpkg-reconfigure postfix
```

I also chose internet with smarthost. Initially following the guide it didn't work but after completely going through it, I went through attached main.cf and followed its format.

running

```
sudo mdadm -F --scan -t
```

now emails me the test info. You can set the default email to mail in the mdadm conf file but I don't remember where that was, lol

Hope this helps, :)

---

