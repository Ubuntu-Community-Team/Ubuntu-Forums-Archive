---
title: "How to auto mount Windows partition?"
date: 2011-11-24
forum: General Help
---

### Post by thefallofroy on 2011-11-24
I am currently using a Toshiba Satellite laptop, I have Windows 7 as my main OS and have Ubuntu via the Wubi application through Windows. I have noticed that when browsing for the files on my hard drive it seems that it doesn't detect it upon startup. In this case, whenever I use Rhythm Box it doesn't load any of my music from my hard drive (which is all saved through my Windows partition) off the bat. What I have to do for it to recognize it is by going to "import folder/file" through Rhythm Box and then highlighting my Windows partition. I don't have to actually make it import anything but for some reason it recognizes it when I highlight it... So basically my question here is what do I have to do to make it auto mount (recognize) my Windows partition every time I run Ubuntu?

Thanks in advance

---

### Post by DapperMe17 on 2011-11-24
NTFS configuration tool is your answer. 

Install it from the repos, then open the GUI and check "mount internal device", then place a check mark next to the drive that shows up.

Reboot, and you should have access to your Windows NTFS partition.

8)

---

### Post by thefallofroy on 2011-11-26
Worked like a charm, thanks a bunch!

---

### Post by Morbius1 on 2011-11-26
Out of curiosity rather than anything else but:
> I have Windows 7 as my main OS and have Ubuntu via the Wubi application  through Windows. I have noticed that when browsing for the files on my  hard drive it seems that it doesn't detect it upon startup.
When you boot into Ubuntu your Windows partition isn't automatically mounted to /host ?

Sounds like a serious bug.

---

### Post by Mark Phelps on 2011-11-26
I'm in agreement with Morbius1 -- in fact, I'll go one step further.

If you installed via Wubi, and you have used a utility to mount the Windows OS partition, and you installed using Wubi to that same partition -- it is very likely that you are risking trashing your Windows OS partition.

As Morbius1 indicated, the Windows OS partition is automatically mounted under /host.  Forcing it to mount again is guaranteeing that the filesystem is going to get corrupted.

---

### Post by thefallofroy on 2011-11-28
> **Mark Phelps said:**
> I'm in agreement with Morbius1 -- in fact, I'll go one step further.

If you installed via Wubi, and you have used a utility to mount the Windows OS partition, and you installed using Wubi to that same partition -- it is very likely that you are risking trashing your Windows OS partition.

As Morbius1 indicated, the Windows OS partition is automatically mounted under /host.  Forcing it to mount again is guaranteeing that the filesystem is going to get corrupted.

You make a valid point sir, I'll be sure to fix this next time I use Ubuntu. Thanks for the tips everyone.

---

### Post by santhoshk on 2012-11-01
Most people wonder how to auto mount the partitions in Ubuntu , I think it will help them .

[http://technicalrepository.com/how-to-mount-partitions-automatically-in-ubuntu-12-10/](http://technicalrepository.com/how-to-mount-partitions-automatically-in-ubuntu-12-10/)

Simple and easy steps without any third part softwares :)

---

