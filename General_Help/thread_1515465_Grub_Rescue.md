---
title: "Grub Rescue?"
date: 2010-06-22
forum: General Help
---

### Post by listenup14 on 2010-06-22
I had a windows 7 partition and a ubuntu partition on my computer. I decided I didn't need the ubuntu anymore, so I went to disk management on windows and deleted the Ubuntu partition. Now, when I try to boot my computer, all I see is 
error: unknown filesystem.
grub rescue>

How can I boot back into windows? I downloaded windows 7 from the microsoft site, so I do not have the cd. I went to the computer store and the worker told me he would have to back my data, wipe my computer, and start clean, and that it would be $150. Any help would be appreciated

---

### Post by Bachstelze on 2010-06-22
Back in the XP days, you had to boot the XP CD, go to a recovery console and fix the MBR. I have no idea how you do that in 7, maybe try a Google search for 'windows 7 restore mbr'.

---

### Post by listenup14 on 2010-06-22
It says I need the windows 7 cd, which unfortunately I do not have. What do I need? Is there anyway I can get one?

---

### Post by meoow on 2010-06-22
"grub rescue" can rescue nothing ,you can use a live cd to boot up your computer and install grub to mbr.
you can refer to this ----

HOWTO: Restore GRUB (if your MBR is messed up)

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by Zerocool Djx on 2010-06-22
You need to run testdisk... It's a program t hat will reset the MBR (Master boot record). This is what tells the system what to load, wither it be grub, windows, or ubuntu, etc... Here is the program and tutorial.. For future reference though, I would suggest removing the partition with the windows disk management, BUT!!!! then immediately run Testdisk. This will reload the MBR to load windows upon boot up. I would also add not to forget to add the memory back to the windows partition, other wise it will just be unused.

Here is the tutorial and program...

[http://www.youtube.com/watch?v=DF3L76jqeg0](http://www.youtube.com/watch?v=DF3L76jqeg0)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

OK,... now that that is out of the way... I wouldn't totally blow off ubuntu. I know learning it can be ruff, but do you know that Microsoft is actually the minority when it comes to Linux (Unix)? Almost everything you have in your house that is electronics, TVs, DVD players, GPS, Phones,... there is an unlimited number of devices that Use Linux. So here is my advice,.. keep ubuntu installed.. However, learn how to edit grub loader so that Ubuntu is second on the list. It takes 5 min to do and after completed you don't have to do anything to load windows. After the 8 seconds it will then after the swap auto load windows, but yet give you the option to load ubuntu if you wish. So when you have free time and are still curious you can learn how to use it at your leisure. Just keep in mind I'm sure you didn't learn windows in a day, and the same should be considered for Ubuntu. It's a great system! But, just lick anything else it has it's flaws, the few questions are... did I really learn everything I need to know to operate it? Did it work for me? Why not? What kind of support does it give me? I dunno if you have ever called windows and asked for help, but they are very hard to get through and when you do they are more concerned about making money then helping you. This is a very unique family here with Ubuntu, you have unlimited free support and almost instant responds to your problems. Nothing is perfect, but give it a shot, even I have my issues with Ubuntu, but I haven't given up... :) I hope to still see you around the forums! :)

---

### Post by listenup14 on 2010-06-22
Thank you so much for the help, but I'm a little confused. I need to put ubuntu back onto my computer in order to use this program right? Right now I am just worried about losing windows, I will definitely keep ubuntu as well if i get it working.

---

