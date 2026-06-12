---
title: "All about Linux"
date: 2006-05-03
forum: General Help
---

### Post by admrly06 on 2006-05-03
I just installed Ubuntu on my laptop and I'm loving it. I know a little about Linux ( enough to get around with out pulling teeth. ) I'm going to be switching to Kbuntu tonght. My friend uses Mandrake and I just like the KDE looks and feel. Any suggestions on things I should do first? What would make my life easier? 

I didn't do a dual boot. I did do dual boots in the past but I felt having windows on the computer was like a crutch, if it got to confusing i'd run back to windows with my tail between my legs. I will never go back to windows and am excited to enter a whole new world of computing and love embracing the open source movement. Thanks to all for listening to my ranting :-)

---

### Post by Sef on 2006-05-03
You don't have to reinstall the os to get kubuntu. Simply do this instead:

sudo apt-get update

sudo apt-get install kubuntu-desktop


then when you log in, just click on sessions and set kubuntu to be your default desktop.

---

### Post by bobbymcsteels on 2006-05-03
[QUOTE=admrly06]I didn't do a dual boot. I did do dual boots in the past but I felt having windows on the computer was like a crutch, [/QUOTE]

I have a small windows partition, there are some apps(1 or 2) that dont work as I would like them to in linux and I have tried to get them to work(properly), so I use the windows partition to run them.... I have had linux(kubuntu) running properly since nov last year and is my main os, sometimes problems araise, recently been havin trouble with net settings and have had to switch to windows cos its still running the net connection........ So dont think of it havin a crutch think of it a insurance... If all else fails you can use widows to find a way to fix your linux :p

---

### Post by admrly06 on 2006-05-03
[QUOTE=bobbymcsteels]I have a small windows partition, there are some apps(1 or 2) that dont work as I would like them to in linux and I have tried to get them to work(properly), so I use the windows partition to run them.... I have had linux(kubuntu) running properly since nov last year and is my main os, sometimes problems araise, recently been havin trouble with net settings and have had to switch to windows cos its still running the net connection........ So dont think of it havin a crutch think of it a insurance... If all else fails you can use widows to find a way to fix your linux :p[/QUOTE]

Yeah I have two computers at my house. My laptop and my wife has an old computer running windows 2000. So I have my insurance if I need it :p I installed linux on my wifes computer at first and she didn't like it. Oh well, she really doesn't like computers she just wants to burn cd's. I told her she can do that in linux and she didn't want to. Some people will never change.

---

### Post by Omnios on 2006-05-03
Hi I have been dual booting for a year and a half now and use Ubuntu 99.9% of the time and find from time to time I still use win for certain stuff and its nice to have a backup if something happenes. Anyways If you end up dual booting id make the win partition as small as possible. I Have three partitions Ubuntu / XP / and a vfat-32. Fat lets me tranfer files between Ubuntu and XP and I use it a lot for music and personal files but more inprtantly when a new version of Ubuntu comes out I can transfer all the files I want to keep to My Documents drive and keep my files.

---

### Post by Al3xanR0 on 2006-05-03
[QUOTE=admrly06]I just installed Ubuntu on my laptop and I'm loving it. I know a little about Linux ( enough to get around with out pulling teeth. ) I'm going to be switching to Kbuntu tonght. My friend uses Mandrake and I just like the KDE looks and feel. Any suggestions on things I should do first? What would make my life easier? 

I didn't do a dual boot. I did do dual boots in the past but I felt having windows on the computer was like a crutch, if it got to confusing i'd run back to windows with my tail between my legs. I will never go back to windows and am excited to enter a whole new world of computing and love embracing the open source movement. Thanks to all for listening to my ranting :-)[/QUOTE]

the first thing I would do is set up my sources, [here]("http://www.ubuntulinux.nl/source-o-matic") is an easy way to get this done. Your Mandriva using friend should recognize this, it is very similar to [easy urpmi]("http://easyurpmi.zarb.org/") once your sources are set up installing apps are generally problem free. Next I would ```
sudo 
``` ```
apt-get install kubuntu-desktop 
``` like Sef suggested.

---

### Post by aysiu on 2006-05-03
If people want to try out Kubuntu (KDE), please do not suggest ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` as that will make it difficult to remove KDE later.

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` is the proper way to do it, as ```
sudo aptitude remove kubuntu-desktop
``` will then remove all the packages that came along with it, not just the pointer to those packages.

---

