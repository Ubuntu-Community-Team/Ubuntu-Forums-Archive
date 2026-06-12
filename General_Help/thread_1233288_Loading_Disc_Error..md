---
title: "Loading Disc Error."
date: 2009-08-06
forum: General Help
---

### Post by BradL on 2009-08-06
Hi I am new to ubuntu . I just finished putting it on my pc this morning. I swapped from Red Hat because I did not really like the way red hat was. Overall I am pleased with ubuntu . The only problem I am having is loading disks. It will load older cds and cd based games but not dvds or dvd based games. I searched this forum for about an hour before I posted this thread, so I have tried many command lines but I feel they are useless because these dvds are simply not being read at all. The error message is the same message you get when clicking on the drive when theres no disk in. It simply says Unable to mount location , because there is no media in the drive. Is there something I must download to be able to read dvds. I like ubuntu but unfortinatly if I can not resolve this problem im going to have to switch to windows which I really do not want to do. 
Thanks In advance. Brad.

---

### Post by howefield on 2009-08-06
Did Red Hat read your DVDs ?

---

### Post by BradL on 2009-08-06
Honestly I don't know I put it on yesterday and I did not like it at all so I did not bother trying to install any games on it or play any DVDs period.

---

### Post by howefield on 2009-08-06
> **BradL said:**
> Honestly I don't know.

Ok, What I was really asking was, are you sure you have an optical device capable of reading dvds ?

Sorry for the dumb question, but it has been known.

---

### Post by BradL on 2009-08-06
Yes it is an CD-ROM/DVD-ROM drive.

---

### Post by merlinus on 2009-08-06
If the games use .exe files to run, then this will not work on linux, only windows.

Another possibility is that your cd/dvd drive is defective.

---

### Post by BradL on 2009-08-06
Well for example the Sims 3, I just downloaded the Play On Linux, and went through there list The Sims 3 is there and Fallout 3( the other game i am trying to install). I have looked through different web sites and looked at threads where people have gotten these to play on there system no problem. I am 100% positive my Disk Drive is working properly. I also tried downloading the restricted areas, and VLC with all the packages I could find to see if that helped. It did not. I dont actually have a copy of windows so I would really like to get these to work on Unbuntu. The thing is the people that have installed games like these on Ubuntu 9.04 have not had the problem im having. Thanks for your help so far.

---

### Post by BradL on 2009-08-06
Bump

---

### Post by Vakman on 2009-08-06
For clarification, no disks are detected. Like any disks (DVD disks, you said CDs work).
Also once this is working follow [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664&iTestingId=42371") and scroll down to the howto guide and that should help you install The Sims 3.

---

### Post by BradL on 2009-08-06
It picks up cds they auto mount no problem but it will not read any dvd. Or dvd based game thats why I am banking on software problem.

---

### Post by Vakman on 2009-08-06
You also said that you have already installed the restricted extras package. Try this:
```
sudo apt-get install libdvdread4
```
then after that:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Also you are running the x86 (32-bit) version of Ubuntu? Let me know if it works after that.

---

### Post by BradL on 2009-08-06
I have also tried playing every Dvd I own with the same result on each it simply does not read them.

---

### Post by BradL on 2009-08-06
Im not sure how do I find that out.??
Edit: Yes I have installed both of those packages.

---

### Post by Vakman on 2009-08-06
You have already tried entering what I posted? 
Also I was only asking x86 or x64 in case any lines I post need to be different. To check:
```
uname -a
```
Then post the output. Anyway back to the problem, try enter them in the order I sent again, just in case. Just found this on the forums, try booting Ubuntu with the "all-generic-ide" at the end. When booting press ESC and append that line where it says boot options.

---

### Post by BradL on 2009-08-06
I still have the same issue, I am pretty sure it is the 64 but version, so I need to download and install the 32 but version for it to work? 
This is what i got
desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux

---

### Post by Vakman on 2009-08-06
No, no of course not. Certainly not. People might/should just need to know sometimes if they send any commands for you to enter. Sometimes x86 and x64 versions have different commands. Anyway, try adding "all-generic-ide" (without quotes) to boot options when before Ubuntu starts.

---

### Post by BradL on 2009-08-06
Ok I tried that but all my boot menu says is what I can boot from. I didnt see anywhere else to type anything.

---

### Post by BradL on 2009-08-06
I read another thread about a guy fixing somebodys pc through remote desktop i dont have any account numbers or passwords saved so im willing to let someone else have a go at fixing this if they can

---

### Post by BradL on 2009-08-06
Bump

---

### Post by nukeaholic on 2009-08-21
i' having the same (or VERY similar) problem, somebody please give some more help

---

