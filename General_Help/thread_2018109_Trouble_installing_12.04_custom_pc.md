---
title: "Trouble installing 12.04 custom pc"
date: 2012-07-06
forum: General Help
---

### Post by Nibaini on 2012-07-06
I built a custom pc and trying to install 12.04 on it. when i insert the disc to install it starts but then stops giving power to the monitor. Works fine with windows 7 but i want ubuntu on it. I do not have onboard video to switch to. heres the specs any help is appreciated.

asus m5a97 mobo
sapphire hd 6850 video card
amd fx 4100 cpu 
6 gigs corsair ddr3 ram

I am trying to install 12.04 64bit edition. Please help Maybe 12.04 is just not compatible with this version which would really bum me out. :(

---

### Post by dino99 on 2012-07-06
here is how i do installation:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

maybe you need using some boot option (like nomodeset or noacpi)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Nibaini on 2012-07-06
Thanks for responding, My screen loses signal from the computer when live cd loads. i think its a driver issue and ubuntu doesn't recognize my hd 6850 properly and i do not have an onboard video option my motherboard doesnt have one. :(

---

### Post by Nibaini on 2012-07-06
I will try the 32bit version I will just use 4gigs of ram, if it works still open to help. will be researching the problem to try and get this thing up and going.

---

### Post by juanbuntu on 2012-07-07
I am having the same issue. 

CPU: AMD FX-6100 Zambezi 3.3GHz Socket AM3+ 95W Six-Core 
MOBO: ASUS M5A97 AM3+ with Bios Version = 1208, which is the most updated as of 2012.05.25 
Video Card: EVGA 01G-P3-1556-KR GeForce GTX 550 Ti

---

### Post by juanbuntu on 2012-07-16
I had the same issues are you report, but I fixed the problem, sadly by re installing from scratch from the Ubuntu-10.10-AMD6 DVD.

This time I set up partitions manually to something like this:

/boot primary ext4 512MB 
/ primary ext4 150GB
swap ext4 100GB
/home logical ext4 remaining GBs

Immediately after the install the system warned me that 10.10 was no longer supported and asked me to *update* and then to *upgrade* to 11.04. 

After the updates I rebooted the system, then issued the command

sudo apt-get install nvidia-new

rebooted, and then upgraded to 11.04 . When the upgrade to 11.04 ended, I rebooted, went to system settings/Additional Drivers, where I saw that the nVidia accelerated graphics was activated “but not in use”. I played to make the dual-monitor system work. 

Then I upgraded to 11.10, rebooted, did the updates, re installed tools I was using. 

I am *NOT TOUCHING* 12.04 until I have evidence that the AMD FX-6100 MOBO works with the nVidia GeForce 550 Ti card works 

So I am posting this response hoping to save for other people the countless hours I wasted.

Juanbuntu

---

### Post by mastablasta on 2012-07-16
why do you have swap 100GB? it will never be used. well, unless maybe if you have 100GB ram and then occupy it all with programmes.
 
does AMD FX-6100 have a GPU built in?
 
have you tried the boot options or alternate CD install?

---

