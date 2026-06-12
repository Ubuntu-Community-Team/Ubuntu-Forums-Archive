---
title: "After unexpected shutdown, my filesystem has a lots of errors"
date: 2010-08-25
forum: General Help
---

### Post by marcosvega1 on 2010-08-25
Hi,

I was using my laptop without battery because it doesn't work. Ubuntu have had started when somehow my charger failed and my laptop turned off. When I tried to boot ubuntu again an error appeared on the screen and it said that gdm couldn't start because it cannot access **/var/lib/gdm**.

Ubuntu started in console mode. I checked /var dir and found out that lib is not a directory but a symbolic link. Obviously, the permissions are wrong.

I've made a lot of fsck and only the first time it reported errors, but it didn't solve my problems. Lots of files have worng permissions and I think  the partition is in read only filesystem state. I can't run commands such as apt-get, aptitude, etc. And now I can't turn off ubuntu correctly because when it starts stopping services it stucks in "Saving the system clock".

I haven't found any solution to this and I would appreciate if you could help me. I'm using Ubuntu 9.04 and also is important to note that the hard drive is still working and doesn't have bad sectors because I have scan it even with gparted and it didn't report me errors. Also, I'm posting this from the same laptop but using Windows and I haven't had problems with the hard drive. Another important thing is that in windows I use ext2 ifs for windows vista to mount ubuntu partition and have access to files in ubuntu partition from windows, it worked flawlessly, but now with this error I can't mount the partition and it reported that it doesn't have format.

Thank you very much for your help.

---

### Post by marcosvega1 on 2010-08-25
I want to change manually the permissions to /var/lib because now it is a symbolic link not a directory. So, is there a way to change the permissions back as directory to /var/lib?

---

