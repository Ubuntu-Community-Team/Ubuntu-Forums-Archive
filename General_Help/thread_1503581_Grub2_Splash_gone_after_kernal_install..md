---
title: "Grub2 Splash gone after kernal install."
date: 2010-06-07
forum: General Help
---

### Post by thecanfield on 2010-06-07
I have been running Ubuntu 10.04 for a while now without any issues. I have also been dual booting with grub2 for a while now, only issues being crappy customization. But anyways I had my grub2 splash all set up the way i liked, with a nice background and everything. I run every update Ubuntu wants and have never had an issue until recently.
On June 3rd I ran an update that Ubuntu requested, it installed a new kernel (-2.6.32-22) and requested a restart, as usual. after restarting, my grub splash is gone. I thought no biggie ill just run `update-grub` as i have before and it will fix everything...nope
I get the error message `head: cannot open `/boot/grub/video.lst' for reading: No such file or directory` right where the "image found" message is supposed to be. any idea what the problem could be, and how to fix it?
Thanx in advance for any help

---

### Post by thecanfield on 2010-06-10
Can someone please help me out.

---

### Post by stoneage on 2010-06-10
Maybe this is of some use ? :-
[http://ubuntuforums.org/showthread.php?t=1448732](http://ubuntuforums.org/showthread.php?t=1448732)

---

### Post by thecanfield on 2010-06-10
after reading the thread that stoneage posted, i created a 'video.lst' file and ran 'update-grub' and sure enough everything works flawlessly again 
thank you so much stoneage for taking the time

---

