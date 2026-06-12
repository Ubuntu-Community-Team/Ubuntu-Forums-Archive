---
title: "Having Trouble Booting Other HD Partition"
date: 2010-05-10
forum: General Help
---

### Post by TurboMaLuM on 2010-05-10
Hello, long time reader here. I can usually find the answers I'm looking for by searching. But, I have been searching this site and google for a week trying to find out what is wrong. Here is the problem.

I recently formated my whole laptop. When reinstalling windows(which I did do first), I created a separate partition for my Ubuntu after 7 was installed. So 7 installed fine to the correct partition and all is well. I burned Ubuntu, booted from the CD, then installed on the second partition. All seems well. 

Now, my computer just auto boots Ubuntu. I have no option to boot the other partition, which has Windows on it. 

Could someone please help me? I need to find a way to allow my laptop to boot the partition with Windows on it again? Thanks

---

### Post by redcodefinal on 2010-05-10
You need to edit your grub.cfg file to include the extra OS. Go here [http://grub.enbug.org/grub.cfg](http://grub.enbug.org/grub.cfg). It should help to explain the method. That or run os_prober [http://joey.kitenet.net/code/os-prober/](http://joey.kitenet.net/code/os-prober/). I had the same problem you can read about the solution here [http://ubuntuforums.org/showthread.php?p=8319918#post8319918](http://ubuntuforums.org/showthread.php?p=8319918#post8319918)

---

