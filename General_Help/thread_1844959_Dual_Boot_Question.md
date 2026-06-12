---
title: "Dual Boot Question"
date: 2011-09-16
forum: General Help
---

### Post by AnneM on 2011-09-16
I have been using Ubuntu for more than a year and a half, but, unfortunately, I have reached the point where I really need to have Windows installed in some fashion or another for various programs I really need. 

So, I've searched online how I can install Windows alongside Ubuntu. I have two hard drives, and I am presuming I could probalby install Windows on one of them without affecting my Ubuntu installation. However, everywhere I've looked online says that I need to first have Windows installed and then install Ubuntu. 

The reason I'm asking first, before I do anything stupid, is I can't afford to be without a computer for too long (i.e. even a few hours is too long) and I don't want to ruin my Ubuntu installation either. Can someone give me some advice on how to proceed, please?

---

### Post by garvinrick4 on 2011-09-16
If you want Windows on its own drive that is fine, install the windows grub on that drive
and it will only boot windows.
Your Ubuntu drive after windows is installed on its drive you can run
```
sudo update-grub
```
and will pick up Windows in config file and as menuentry as to boot from.

So Ubuntu drive boots both Ubuntu and Windows and Windows drive if you want
to boot off of it you will have to select it in Bios to boot from and will only boot Windows.
Windows grub does not have an os-prober as to add others to its menuentry and such.

If you ever get in any trouble with booting you can install grub into your Ubuntu drive
very simply with a live cd (install cd using Try Ubuntu). Any more questions just ask.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by AnneM on 2011-09-16
Thanks very much :)... I'm going to give it a go. If it all goes pear-shaped, I'll be back, begging for help :)

---

### Post by garvinrick4 on 2011-09-16
> **AnneM said:**
> Thanks very much :)... I'm going to give it a go. If it all goes pear-shaped, I'll be back, begging for help :) Will be here. Enjoy your Ubuntu.
If any problems click on my name and leave me a message, I am around here everyday.

---

### Post by J Tinsby on 2011-09-23
Hello Gavinrick 4,

I am new to the forum and to Ubuntu. I too have an XP Pro machine and  have a spare HD on which to put Ubuntu. I have read your reply above and  I'm sorry I don't know the term "grub" other than a baby worm, in  computer parlance it's meaningless to me. 

I'd like to spend time with Ubuntu, maybe even the Studio version since I  do a lot to photography and sound editing. The only Ubuntu I have is on  a recovery disc that I made from an .iso file. It's interesting to see  it run from the CD but of course I can't do more with it that way.

The HD with XP on it has 2 partitions and both are in use so I'd like to  add an older HD and put Ubuntu on it. But again the booting config even  with your fine explanation doesn't help a newbie.

Thank you very much,

J T

---

### Post by garvinrick4 on 2011-09-23
> **J Tinsby said:**
> Hello Gavinrick 4,

I am new to the forum and to Ubuntu. I too have an XP Pro machine and  have a spare HD on which to put Ubuntu. I have read your reply above and  I'm sorry I don't know the term "grub" other than a baby worm, in  computer parlance it's meaningless to me. 

I'd like to spend time with Ubuntu, maybe even the Studio version since I  do a lot to photography and sound editing. The only Ubuntu I have is on  a recovery disc that I made from an .iso file. It's interesting to see  it run from the CD but of course I can't do more with it that way.

The HD with XP on it has 2 partitions and both are in use so I'd like to  add an older HD and put Ubuntu on it. But again the booting config even  with your fine explanation doesn't help a newbie.

Thank you very much,

J T Welcome to the Forums Tinsby,
Is your drive a USB drive? What version is your Live CD, that is an install CD also?
While in the Live CD you have been using open a terminal: ctrl/alt/t
```
lsb_release -a
```Will tell you the version you are running.
I will be more that happy to help you. I will give you a link with from Ubuntu with a 
few how to's to look at.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by spiky001 on 2011-09-23
Grub is a boot loader have a read on wiki [http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

---

### Post by J Tinsby on 2011-09-24
Gravinrivk4.

Looking at the PC World page where I got the "BootMed" CD it tells me   **Version: **Ubuntu 10.10 (Maverick Meerkat). I didn't try that line you gave me (yet). 

The CD DOES have the option to install Ubuntu or just let it load from the CD, it has other options as well and I see an icon that says "Terminal" if that's what you are referring to. No I have never used the command to use open terminal

I have 2 older HD's one is a SATA and the other is IDE. I haven't decided which one to use. 

The other thing is that I am trying to sell my home, like so many others, and right now I have some people who want to see it a second time. If that goes well this project will have to be put on hold, until I get another house and get back online.

The important thing is that I found the forum and people that are willing to help me! :D

I will be trying the command recommended and see if the version really is what they say it is.

Thanks to both of you,

J T

---

### Post by J Tinsby on 2011-09-26
I have discovered that the terminal command is CTRL + ALT + T 

I read the posting literally and was using CTRL/ALT/T of course that doesn't work.

When I use the command to show the version it tells me that there is no "LSB available." No matter if I was to d/l Ubuntu I would use the latest version assuming that one is stable.

Thirdly and most important IF I install GNU GRUB on my XP now, without the extra drive attached, can I then remove it at any point or is it in to stay. I can't determine if it makes permanent changes to the MBR of Windows, and can't be undone.

What is the difference between "Easy BCD" and Grub? A friend uses that to dual boot on one HD from XP to Win7. He has Ubuntu on a second drive and plugs it in when he wants to run it..... I prefer something more sophisticated! :D

The Wine program I see on my workspace, is that used to allow Windows programs to run under Ubuntu?

Thank you,

J T

---

### Post by garvinrick4 on 2011-09-26
> When I use the command to show the version it tells me that there is no "LSB available. Had a typo hit s instead of a. sorry.

> Thirdly and most important IF I install GNU GRUB on my XP now,Have to have a Ubuntu install, that is where grub looks for boot files is in the Linux install.
> The Wine program I see on my workspace, is that used to allow Windows programs to run under Ubuntu?Yes, but I have never used Wine so do not want to make a comment on its use no practical experience.
> What is the difference between "Easy BCD" and Grub? A friend uses that  to dual boot on one HD from XP to Win7. He has Ubuntu on a second drive  and plugs it in when he wants to run it..... I prefer something more  sophisticated! 

I have heard it is a tool to modify Windows bootloader and again have not found it of use to me, so have never put to practical use.

---

