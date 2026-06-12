---
title: "I am new to ubuntu please help!!"
date: 2010-12-06
forum: General Help
---

### Post by mUmair on 2010-12-06
Hello everyone,
I am new to Linux World and have few questions in mind.

First how can I clean install Ubuntu 10.10? I am currently using Windows 7 and want to clean install Ubuntu 10.10.

Secondly, I have Apple iPod Touch 4th generation 32GB model. So how can I install iTunes on Ubuntu??

Please help me on installing Ubuntu. I want to completely delete my windows data and want to clean install Ubuntu 10.10

Anxiously Waiting

---

### Post by phredbull on 2010-12-06
You should make a startup disk on a cd or usb stick and boot from it. From there, you can install Ubuntu, as well as manage your disk partitions.

As for iPod support, there is no iTunes for Linux. You can use Rhythmbox to transfer files between your iPod and hard drive, but it didn't let me copy playlists to my iPod. I haven't tried any other programs, but I'm going to check out Exaile...

Enjoy your Ubuntu experience!

---

### Post by karthick87 on 2010-12-06
Welcome to ubuntu forums :)

For simple basic instructions try [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and scroll down to the **Show me how sections**.[You can see the detailed guide on installing ubuntu here.]("https://help.ubuntu.com/community/GraphicalInstall")
[B]
Note:[/B]
First use WUBI, to learn Ubuntu... then install it on PC.

---

### Post by wilee-nilee on 2010-12-06
> **mUmair said:**
> Hello everyone,
I am new to Linux World and have few questions in mind.

First how can I clean install Ubuntu 10.10? I am currently using Windows 7 and want to clean install Ubuntu 10.10.

Secondly, I have Apple iPod Touch 4th generation 32GB model. So how can I install iTunes on Ubuntu??

Please help me on installing Ubuntu. I want to completely delete my windows data and want to clean install Ubuntu 10.10

Anxiously Waiting

So getting installed is fairly easy we might want to confirm the number of partitions you have already, as there is a limitation for any single HD.

Can you take a snippet or whatever it's called in W7 of the disk manager. the full screenshots are difficult to read there is a tool in accessories for snipping a specific area.

---

### Post by mUmair on 2010-12-06
Oh Thanks a lot phredbull. So I think Apple iPods and iPhones just can't sync with iTunes on Ubuntu!!

It is a negative point of linux, what do you think? 

Any alternative available. I Google it and found Wine package. Is it works??

---

### Post by mUmair on 2010-12-06
> **wilee-nilee said:**
> So getting installed is fairly easy we might want to confirm the number of partitions you have already, as there is a limitation for any single HD.

Can you take a snippet or whatever it's called in W7 of the disk manager. the full screenshots are difficult to read there is a tool in accessories for snipping a specific area.

I have 3 partitions on my hard disk in NTFS file format

---

### Post by slooksterpsv on 2010-12-06
I don't believe it does, but I'll try and let you know if it does work (wine and iTunes). I highly recommend wubi like the others are saying, that way you can test and make sure your hardware works with Ubuntu, at least the major stuff.

For example, if wireless doesn't work out of the box on Ubuntu and don't have ethernet to let us help troubleshoot, you could run into issues there. Secondly if your display didn't work, that would be an issue as well, easily fixable usually, but still can be scary if your new.

So try Wubi, I've got iTunes downloading and I'll post the results

EDIT: WOW IT WORKED!

---

### Post by phredbull on 2010-12-06
> **mUmair said:**
> Oh Thanks a lot phredbull. So I think Apple iPods and iPhones just can't sync with iTunes on Ubuntu!!

It is a negative point of linux, what do you think? 

Any alternative available. I Google it and found Wine package. Is it works??

No, unfortunately iTunes doesn't work under wine either. But there are programs that will let you manage your files on your iPod, but I don't know about any of them allowing you to manage your playlists.

You might want to keep your W7 install, (maybe shrink the partition it's on) for those programs that you like that aren't available in Linux.

edit: iTunes works w/Wine? I'll have to give it a try!

---

### Post by slooksterpsv on 2010-12-06
> **phredbull said:**
> No, unfortunately iTunes doesn't work under wine either. But there are programs that will let you manage your files on your iPod, but I don't know about any of them allowing you to manage your playlists.

You might want to keep your W7 install, (maybe shrink the partition it's on) for those programs that you like that aren't available in Linux.

Ummm... itunes 10 does work under wine, surprisingly, want to see a screenshot?

---

### Post by phredbull on 2010-12-06
iTunes is still no-go for me. When trying to launch it, I get a message saying, "iTunes was not installed properly, please reinstall iTunes". Plus when I try to uninstall, it seems to be reinstalling, so I'm not sure how to remove it now?
:confused:

---

### Post by slooksterpsv on 2010-12-07
I don't know what libraries my wine has installed, but it gives me that error then loads. BTW iPods don't work on it, at least I'm not sure if I have to configure something extra to get it to work.

---

### Post by matt_symes on 2010-12-07
Hi

 > So I think Apple iPods and iPhones just can't sync with iTunes on Ubuntu!!

It is a negative point of linux, what do you think? This is not really an issue with Linux. It's more an issue with Apple  not  writing the software for Linux.

You can always do what i have done and install Ubuntu. Within  Ubuntu install VMware or virtual box and install  XP and iTunes within it. It's pretty much the  only thing i use windows for at home now.

As has  been stated, there are  alternatives to iTunes (rythmbox,  banshee....) and they are pretty good but they are a bit different.

The last version of iTunes i managed to get working under wine was 7. Not good if you have been using a newer version of iTunes as the database is not backwards compatible.

Kind regards

---

### Post by phredbull on 2010-12-07
> **slooksterpsv said:**
> I don't know what libraries my wine has installed, but it gives me that error then loads. BTW iPods don't work on it, at least I'm not sure if I have to configure something extra to get it to work.
Well, if I can't manage my iPod with it, then I'm not really missing anything. But just out of curiosity, what version of Wine are you using? I have 1.3.8.

---

### Post by ImDougy on 2010-12-07
first off, boot from the ubuntu cd/usb and choose install ubuntu. then choose ur timezone and everything and when u get to the partitioning choose erase and use entire disk(it will automatically delete windows) just follow all the instructions in the installer it's very easy. also every ubuntu user should get ubuntu tweak, go to ubuntu-tweak.com

---

### Post by Shintek on 2010-12-07
> **slooksterpsv said:**
> I don't know what libraries my wine has installed, but it gives me that error then loads. BTW iPods don't work on it, at least I'm not sure if I have to configure something extra to get it to work.
Thats becouse iTunes loads the UBUNTU loaded stuff

Youll have to install iPod drivers through Ubuntu Software Centre

---

### Post by slooksterpsv on 2010-12-07
> **phredbull said:**
> well, if i can't manage my ipod with it, then i'm not really missing anything. But just out of curiosity, what version of wine are you using? I have 1.3.8.

1.2.1

---

### Post by mUmair on 2010-12-08
Hello everyone!!

Thankyou thankyou very much for all your kind suggestions and comments of everyone!!

You know, i am posting this with ubuntu 10.10 installed on my system. Yess!!!!!!!

It works and ubuntu is magically faster than windows 7. The installation process takes less than 8 mins.

Again thanks everyone. Now i love ubuntu!! It rocks!!

---

### Post by Astrals on 2010-12-11
For ipod i use gtkpod, it's a really easy application.  Hope this helps.

---

