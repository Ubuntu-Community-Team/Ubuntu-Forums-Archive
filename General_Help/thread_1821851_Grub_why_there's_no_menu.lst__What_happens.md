---
title: "Grub why there's no menu.lst ? What happens ?"
date: 2011-08-09
forum: General Help
---

### Post by Anonymus666 on 2011-08-09
Hi guys ! :) Im facing a minor issue :P Ive recenlty installed back Ubuntu along side with my Windows XP.

And i don't have any menu.lst .... Have already edited my grub past year without any problems :)

Is there something new ? Did i miss a step or something ? I've done several search but i didn't find any answeres that helped me solve this :( Can someone explain me why theres no menu.lst ?

Below is the command i have tried so far.


[LIST]
[*]sudo vi /boot/grub/menu.lst
[*]gksudo gedit /boot/grub/menu.lst
[/LIST]

Look attachments for Screenshots

Thanks for helping me out :)

---

### Post by zealibib slaughter on 2011-08-09
There is no menu.lst for grub 2.  Here is the basics on grub 2 [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Anonymus666 on 2011-08-09
> **zealibib slaughter said:**
> There is no menu.lst for grub 2.  Here is the basics on grub 2 [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Oh i see :)

Thanks ill look forward :) Ive seen Startup Manager in the Software Center is that good to edit the grub 2 ? Should i use [_Grub Customizer_]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183") ? 

Thanks guys ! ^^,

---

### Post by Rubi1200 on 2011-08-09
My recommendation is to go with Grub Customizer.

Here is some more on GRUB2:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Anonymus666 on 2011-08-10
> **Rubi1200 said:**
> My recommendation is to go with Grub Customizer.

Here is some more on GRUB2:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Ive successfully done it on my desktop computer but im having trouble on my laptop ....

I Installed Ubuntu from Windows XP, When im booting im getting prompt windows for selecting Windows or Linux. and after the Grub is comming why so ? Btw the Grub is different from my other Linux installed on my other computer Its Grub 1.99. How can i fix tjhis ? I've installed the latest package and done that commands:

[LIST]
[*]sudo apt-get install grub-pc
[/LIST]

That didn't changed anything.

Here's what it comes when im doing

[LIST]
[*]sudo grub-install -v
[/LIST]
> grub-install.real (GRUB) 1.99~rc1-13ubuntu3


Thanks agaiin ! :)

---

### Post by Mark Phelps on 2011-08-10
If you installed to your laptop using Wubi -- that does NOT use GRUB; instead, it uses a derivative of GRUB known as GRUB4SDOS.

If you then installed GRUB -- you have basically hosed up your laptop.

The presentation of two boot menus is a symptom of using Wubi-installs, and as far as I know, can not be avoided.

---

### Post by Anonymus666 on 2011-08-10
> **Mark Phelps said:**
> If you installed to your laptop using Wubi -- that does NOT use GRUB; instead, it uses a derivative of GRUB known as GRUB4SDOS.

If you then installed GRUB -- you have basically hosed up your laptop.

The presentation of two boot menus is a symptom of using Wubi-installs, and as far as I know, can not be avoided.

Yeah i did use Wubi ... I didn't know about this ... This is annoying i'll reinstalled it ! :) Is there anyway that could be done easily ? What would be my best options to get this removed ? 

Btw I choosed Wubi because i had trouble with the partition via Ubuntu. There's no friendly gui for partitionnate on Other Installation. I don't know why theres was one when i did installed on my desktop computers ... Why so ? I didn't changed the versions ... Its the same cd ... ;)

Thanks for fast replying appreciated then ! :)

---

### Post by Anonymus666 on 2011-08-10
Ive successfully remove via Installed Programs on Windows. ... But im still having issue when im trying to install Ubuntu alongside with windows :( There's no such options to get easily done ... Why so ? 

What i should do ?

---

### Post by Anonymus666 on 2011-08-10
Ok i finally fix it !

There was some errors on my drives :( Ubuntu wasn't able to read how many disk space left on my main drive ... So i run a chkdsk /f on before booting on windows and everything was find after rebooting ! The options was now there ! 

Thanks for every one who helped me ! 

Grub Customizer is flawless ! No prob so far !

---

### Post by Cope57 on 2011-08-10
Use GParted, Parted, or Partimage to handle partitioning or resizing tasks.  I believe one of them is included on the live CD.

---

