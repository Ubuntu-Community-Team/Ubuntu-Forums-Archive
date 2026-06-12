---
title: "Installing and running aplications from live boot Natty Narwhal"
date: 2011-09-26
forum: General Help
---

### Post by Kannan_esp on 2011-09-26
[SIZE=2]Hi,
     i was using dual booting (Win7 n Ubuntu 11.04) on my Lenovo G550 laptop. It works fine and i could choose which OS to load before last week. From last week i can't load Ubuntu, booting shows error messages. I had to force shutdown my lap. Also Recovery mode shows the same. So i used Windows 7 there after. But after 3 days i m not able to boot that also, it shows I/O error.
I think the force shutdown destroy my boot sector!
So now i'm working by Ubuntu Natty live boot.
[/SIZE]
[SIZE=3]_[FONT=Courier New]***Is it possible to install and run that new applications from live boot?***[/FONT]_[/SIZE]

[SIZE=2]For example, i wanna install vlc once, when in live boot from my USB drive and i wanna use that application there  after.

Also, i cann't install ubntu again. It also indicate the installation may fail partially or fully. And the installation process strucked.
My home folder was encrypted.[/SIZE]
[FONT=Courier New][SIZE=3]_***Is it possible to retrive my data from home folder?***_[/SIZE][/FONT]

---

### Post by An Sanct on 2011-09-26
If the Live version is a Live USB with a persistance file attached, then you can install almost any application, you want.

The limitation is, that upgrades (system/kernel/additional drivers, ...) are not possible, since the persistance file does not cover the "system" part. It is actually a hidden CD image on the USB thumb drive.

Read more: "[set up your USB stick]("https://help.ubuntu.com/community/LiveCD/Persistence")"

---

### Post by wildmanne39 on 2011-09-26
Hi, here is a link that may help you recover your data.
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)
Thank you

---

### Post by An Sanct on 2011-09-28
> **wildmanne39 said:**
> Hi, here is a link that may help you recover your data.
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)
Thank you

I did not see any mentioning of an encrypted home directorie.

If it is a boot sector error, this thread might be helpfull ([restoring grub from USB]("http://ubuntuforums.org/showthread.php?p=10440484")).

---

### Post by wildmanne39 on 2011-09-28
Hi, here is where it said it, I almost missed it too.
> My home folder was encrypted.
Is it possible to retrive my data from home folder?
Thank you

---

