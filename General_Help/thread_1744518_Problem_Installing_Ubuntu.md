---
title: "Problem Installing Ubuntu"
date: 2011-04-30
forum: General Help
---

### Post by Adikaaaa on 2011-04-30
Hello.

I tried to install Ubuntu 10.04, 10.10 and 11.04 with Windows 7 (Dual Boot, wubi).

Problem is that everytime when i install it, restart computer and then choose Ubuntu from boot list it goes through the loading and then when Ubuntu desktop should appear only screen from  Windows 7 (Random one) appears and that's it, like Blue Screen of Death.

I'm currently using Windows 7 Ultimate Service Pack 1 64 - bit.

Any help to this ? I really want to use Ubuntu.

Regards,
Adikaaaa.

---

### Post by 3Miro on 2011-04-30
I don't understand what you mean by:
> ...and then when Ubuntu desktop should appear only screen from Windows 7 (Random one) appears...

Could you be more specific, maybe take a screenshot. If you cannot take a screenshot, you can try to take a picture with a cellphone and post it here (people do that all the time).

Could you also tell us what kind of computer you have, most importantly the video card: ATI, Intel, Nvidia, is it relatively new or is it very old and so on ...

---

### Post by Adikaaaa on 2011-04-30
> **3Miro said:**
> I don't understand what you mean by:


Could you be more specific, maybe take a screenshot. If you cannot take a screenshot, you can try to take a picture with a cellphone and post it here (people do that all the time).

Could you also tell us what kind of computer you have, most importantly the video card: ATI, Intel, Nvidia, is it relatively new or is it very old and so on ...

Graphic card: NVIDIA 8600 GT
Processor: Genuine Intel CPU 1.60 GHz 1.60 GHz
RAM: 2 GB

I think that's what you need.

I'm going to post a screenshot in few minutes ! :)

---

### Post by Rubi1200 on 2011-04-30
Do you get as far as the point mentioned here?
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

In other words, once you reboot to complete the install do you see the message
> Completing the Ubuntu installation

---

### Post by Adikaaaa on 2011-04-30
> **Rubi1200 said:**
> Do you get as far as the point mentioned here?
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

In other words, once you reboot to complete the install do you see the message

Here's the image.
[IMG]http://www.dodaj.rs/f/2i/L1/3jkemA4n/p3004111719.jpg[/IMG]

*Too big*. Sorry about that !

And when i reboot it says "Completing Ubuntu Installation" and then loading goes and that thing appears.

---

### Post by Rubi1200 on 2011-04-30
I know it is a hassle, but try and follow the instructions in the link I gave you. It may mean having to start the installation again so you can get to that point.

Let us know if this works for you please.

---

### Post by 3Miro on 2011-04-30
Do not tell the installer that you want to login automatically. After you do what Rubi1200 suggests, select "Classic Ubuntu No Effects". Let us know if this works.

---

### Post by Adikaaaa on 2011-04-30
Worked, thanks.
But now i always have to boot with that nomodeset thing ( I mean to edit boot line ) ?

---

### Post by 3Miro on 2011-04-30
Go to System -> Admin -> Additional Drivers, then install the drivers for your Nvidia video card. Things should work better afterwards. If not, post back and we can make the "nomodeset" thing permanent.

---

### Post by Adikaaaa on 2011-04-30
Thanks for helping me out. :)
Going to install them now. ^^

---

### Post by Rubi1200 on 2011-04-30
Do as 3Miro instructed and worst comes to worst we can add nomodeset to one of the grub files to make it more permanent.

Good luck :-)

---

### Post by Adikaaaa on 2011-04-30
One more thing.
How do you transfer files from Windows to Ubuntu ?
I mean I have some files that i'd like to transfer from Windows to Ubuntu (Same computer).

Thanks. :)

---

### Post by 3Miro on 2011-04-30
If you go to Home -> Places (or top Launcher in Unity), you will open Nautilus (which is the Ubuntu file manager).

On the left side, you should see all of your partitions. Then you can click on them to open and access all of your files.

Wubi may give you trouble if you want to move the files from the same partition where Ubuntu is installed. I am not sure how to solve that (Google it or you can open another help thread).

Generally, you should avoid writing files to the windows root partition as windows tends to panic about it. If you want to share files between Ubuntu and Windows, it is best to make a separate partition (or use a USB drive).

---

### Post by Adikaaaa on 2011-04-30
On the left side Filesystem is the only disk. And on it it's just some Ubuntu files. ^^

---

### Post by Rubi1200 on 2011-04-30
You should be able to access your Windows files this way:

Places > Computer > File System > Host

---

### Post by Adikaaaa on 2011-04-30
Thanks, now i see it. :)

---

### Post by Rubi1200 on 2011-04-30
No problem, you are more than welcome :-)

---

