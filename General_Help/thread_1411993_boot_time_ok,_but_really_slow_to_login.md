---
title: "boot time ok, but really slow to login"
date: 2010-02-20
forum: General Help
---

### Post by silverrope on 2010-02-20
Recently the login time after entering username/password has gone ridiculously slow. I have attached a bootchart where I turned off bootchart manually after I got a terminal. One can see a short boot time, but only after 300 seconds (!) am I able to open a terminal. The screen is blank for over 3 minutes until my wallpaper appears. I can see the hard drive is being heavily accessed during that time.

Is there anyone who can take a look and see where the problem is?

---

### Post by silverrope on 2010-02-21
Additional info. The specs are
* IBM Thinkpad A20m
* Pentium III 600 Mhz
* 512 MB memory
* HDD 5400 RPM, 700 MB swap

Although it is old and not powerful, I can't believe this is bad enough to cause a 3 minute login!

---

### Post by Swagman on 2010-02-21
On the contrary...

My p3 @ 1ghz 786mb ram takes about 5 minutes MINIMUM to boot into Win2kPro

---

### Post by amac777 on 2010-02-21
Some more information might be helpful to track this down:

1. Did this only recently start? If yes, have you recently installed something or done updates?

2. Does it happen to all users on the system or only your user? If you're the only user, perhaps make a test user and try logging in as that user.

3. Does it happen if you logout and then log in again, or only upon the first login after bootup?

4. Are there any interesting error messages in /var/log/syslog or /var/log/dmesg?

---

### Post by oldfred on 2010-02-21
I do not know if any of this is related but these are threads on slow boot:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc
Very long boot solved with experimental grub1.98 post8
[http://ubuntuforums.org/showthread.php?t=1367488](http://ubuntuforums.org/showthread.php?t=1367488)
Slow boot change device.map
[http://ubuntuforums.org/showthread.php?t=1313207](http://ubuntuforums.org/showthread.php?t=1313207)

---

### Post by silverrope on 2010-02-21
> **amac777 said:**
> 
1. Did this only recently start? If yes, have you recently installed something or done updates?

2. Does it happen to all users on the system or only your user? If you're the only user, perhaps make a test user and try logging in as that user.

3. Does it happen if you logout and then log in again, or only upon the first login after bootup?

4. Are there any interesting error messages in /var/log/syslog or /var/log/dmesg?

1. It has been getting gradually worse, but recently it became really slow. The latest kernel got installed via update manager. I have several system backups and I will go back and see how bad things were in the past and check what got installed.

2. I created a test account and it is fine (login within 30 seconds). So I guess it must be something in my profile? I'll start checking that angle as well.

3. The delay does happen again when I logout and then login, taking about the same amount of time (over 3 minutes). The main difference is that the wallpaper appears fairly early during the second login. The first login is a blank screen for most of the time.

4. I am a newbie concerning analysing logs so I am not sure what to look out for. dmesg appears to be a boot log and that looks ok (i.e., the stuff before login). syslog I am not sure about. Attached is a file with the first 100 lines. Anything bizarre? What should I look for?

Thanks for your tips.

---

### Post by silverrope on 2010-02-22
> **silverrope said:**
> 
1. It has been getting gradually worse, but recently it became really slow. The latest kernel got installed via update manager. I have several system backups and I will go back and see how bad things were in the past and check what got installed.

2. I created a test account and it is fine (login within 30 seconds). So I guess it must be something in my profile? I'll start checking that angle as well.


1. I went back to a system image I made several months ago and it seems the slow login problem existed back then. I guess this must have been slowly building as I made changes to my profile.

2. The test account works, so clearly this is a workaround solution. Of course the cause of the problem is not explored, but at least things are more productive again. I will gradually evolve the profile of the second account to eventually match with the first account and monitor login speeds while I make the changes. Maybe I might find the cause.

Thanks again for your help. I will mark the thread as solved.

---

### Post by amac777 on 2010-02-22
Sorry, I've been busy so haven't had time to respond since your reply. Glad at least you have a work around with the test account. 

A couple things to look into:

1. I saw in your syslog that there appears to be some errors with your sda hard drive. I'm not sure what these errors mean but this could be related to your slow log in if you are trying to mount this drive automatically at login. It could also mean something more serious but again I don't understand the errors so if you are not sure maybe you could start another thread entitled "weird error messages in /var/log/syslog" and post those errors there to see if anyone can explain them.

2. Take a look through the start up programs in SYSTEM->PREFERENCES->START UP APPLICATIONS to see what your are running on login on the account that is slow and the one that is normal. Look for differences and see if that gives any clues.

---

### Post by RJARRRPCGP on 2010-02-22
> **Swagman said:**
> On the contrary...

My p3 @ 1ghz 786mb ram takes about 5 minutes MINIMUM to boot into Win2kPro

O_O, I would check the IDE cable and HDD.

---

