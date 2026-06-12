---
title: "Uncomplete installation,partitioning problem??"
date: 2006-05-11
forum: General Help
---

### Post by psixpsi on 2006-05-11
Hi all!

I had to reinstall Ubuntu on my laptop from the CD. I partitioned the disk manually this time. The system got installed...but without the X server. And that is the only thing that I obviously see, recon there are much more missing as the installation was very fast. The partitioning scheme is the following:

/         3GB
swap   1GB
/usr     9GB
/home 10.3GB

Before, when I did the automatic pertitioning, everything worked perfectly, down to WLAN, etc.

Any ideas as to what has happened??? From your experience, what is the Ubuntu's optimal partitioning scheme, given 25GB and personal use laptop (mostly web browsing and TeXing)??

Thanks!!!
psixpsi

---

### Post by Dr. Nick on 2006-05-11
Hmm those partions should be sufficient, when you boot are you just thrown to a text login? If so login and try > sudo apt-get install ubuntu-desktop and it should install Xorg, gnome etc

---

### Post by psixpsi on 2006-05-11
Thanks for the reply Dr. Nick!

[QUOTE=Dr. Nick]...when you boot are you just thrown to a text login?...[/QUOTE]

Yes, that is very strange :???:  ...I started what you suggested and now it installs the packages. Will report when it finishes. 


Best,
psixpsi

---

### Post by psixpsi on 2006-05-11
Its becomming really interesting - I downloaded what was available, but the X-server doesnt start anyway :???:  Any ideas, folks???

Thanks,
psixsi

---

### Post by Dr. Nick on 2006-05-11
[quote=psixpsi]Its becomming really interesting - I downloaded what was available, but the X-server doesnt start anyway :???:  Any ideas, folks???

Thanks,
psixsi[/quote]

If it all installed without errors then login the command line and type 
startx

---

### Post by psixpsi on 2006-05-11
Apparently, it did not install nothing - when I checked with aptitude the list of installed packages, the Xorg was not there. It seems to want to install the desktop from the internet, but I got Error 404. Any way to force it to use CD ? I know that what is on the CD worked very smoothly on my machine.

Thanks,
psixpsi

---

### Post by psixpsi on 2006-05-11
Me idiot ](*,)  - I had to run apt-get update first, befor installing. Now everything seems fine.

Thanks Dr. Nick!!

psixpsi

---

