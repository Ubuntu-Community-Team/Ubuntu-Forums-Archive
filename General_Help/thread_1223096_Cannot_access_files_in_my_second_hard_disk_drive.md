---
title: "Cannot access files in my second hard disk drive"
date: 2009-07-25
forum: General Help
---

### Post by shiroyoshida on 2009-07-25
Hello all, 

Today I installed Ubuntu 9.04 (64bit) by using Wubi 9.04 and for some reason I can't access my second hard disk drive. 

I'm using Windows XP (SP3) and would like to switch to Ubuntu while using Windows just to play games. I have two hard disk drives, one called C and another one called E. Due to limited space on the C drive, I installed Ubuntu on the E drive. I created a folder called "ubuntu" on the E drive and put Wubi in there with the ISO image. The installation was quick and painless with no problems whatsoever. :)

However, the E drive has files that I'm using and would like to share between both OSs. In Ubuntu, all files in the C drive are visible but the E drive is not. 

Have I done something wrong when I created the "ubuntu" folder? Should I had simply installed Ubuntu on the root of the E drive? And more importantly, is there a way I can access the files in the E folder without having to unistall/reinstall Ubuntu? 

Thank you very much in advance for your replies! :D

---

### Post by madsmeg on 2009-07-26
you have the E drive mounted, so it wont be seen as a seperate drive.

Have a look in you /host and /media folders on your Ubuntu install.

---

### Post by shiroyoshida on 2009-07-26
Thank you ever so much - all the files were in the /host folder... The weird thing is that I searched for the files but got no results. No worries about that now though! 

Thank you again for your help! :-)

---

