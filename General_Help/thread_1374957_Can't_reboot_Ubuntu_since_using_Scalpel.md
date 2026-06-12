---
title: "Can't reboot Ubuntu since using Scalpel"
date: 2010-01-07
forum: General Help
---

### Post by Mickser_52 on 2010-01-07
I tried using scalpel to recover some files that i had deleted. It went through the first pass but on the next pass there was an error message saying **disk full** The next time I tried to boot ubuntu I got a strange screen filled in a very large font and a message in the top corner: **The configuration defaults for gnome power manager have not been installed correctly**

I do not want to reinstall Karmic Koala as I may lose my email messages and other data. Any ideas on how to recover.

---

### Post by sdowney717 on 2010-01-07
you could try creating a new user, then log into that new user.
User configuration files are contained in each users user space.

---

### Post by Mickser_52 on 2010-01-07
Thanks for the reply. I created a new user but could only do so in terminal. That is the only way I can log in. A further problem has developed when i try to start up.. the screen flashes and eventually a message appears saying that i am entering low graphics mode. Then a series of options are presented but none of them actually produce any effect other than a blank screen.

In terminal mode if I try to run something like thunderbird for email there is a message saying gtk warning cannot open display.

When I enter df it says no space available on disk. I deleted a number of files which would have amounted to several gigabytes but I am still getting the same message i.e no space available. The partition size is 48G.

Where can I start?

---

### Post by sdowney717 on 2010-01-07
[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)
have you run fsck yet?

[https://answers.launchpad.net/ubuntu/+question/29889](https://answers.launchpad.net/ubuntu/+question/29889)

force it on a reboot
[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)
more info on how to run
[http://www.cyberciti.biz/faq/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted/](http://www.cyberciti.biz/faq/can-i-run-fsck-or-e2fsck-when-linux-file-system-is-mounted/)

---

### Post by Mickser_52 on 2010-01-08
Again thanks for the reply.. The problem is solved. The main cause was the disk space being unavailable. I eventually found where Scalpel had stored files and deleted them. They did not show up with the "ls" command. 

I ran du -h |sort -nr| less and the very last lines showed folders over 1G in size. When they were removed and I rebooted everything was back to normal

The disk is still quite full so I will move the home folder to a new partition which I never quite got around to.

(Ironically I got help from a page which was advocating windows over ubuntu and it's complicated and obscure commands)

---

### Post by nateobie on 2011-02-06
I am having the same problem.  Can you post a little more details about how you recovered from this problem?

---

