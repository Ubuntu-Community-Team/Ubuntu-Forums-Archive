---
title: "Problem booting with kubuntu cd"
date: 2010-12-15
forum: General Help
---

### Post by gavdari on 2010-12-15
I have a laptop with ubuntu 10.10 and windows 7 and I wanted to change it to only kubuntu 10.10. I've downloaded the cd image via torrent but it seems like my bios doesn't find any bootable cd. It works fine on my brother's pc with only windows 7, but on my laptop it just doesn't boot into the kubuntu installation menu. my laptop is a dell vostro 1510 and I've had no problem with booting up using ubuntu live cd. what should I do?

---

### Post by sikander3786 on 2010-12-15
From what you said, I feel a little confused.

The same disc boots fine on another system?

Your intended system can boot anyother disc except this one, without making any changes to the boot order? I mean it is already set to boot from CD Drive?

---

### Post by tajiknomi on 2010-12-15
> **gavdari said:**
> I have a laptop with ubuntu 10.10 and windows 7 and I wanted to change it to only kubuntu 10.10. I've downloaded the cd image via torrent but it seems like my bios doesn't find any bootable cd. It works fine on my brother's pc with only windows 7, but on my laptop it just doesn't boot into the kubuntu installation menu. my laptop is a dell vostro 1510 and I've had no problem with booting up using ubuntu live cd. what should I do?

[SIZE=2]Have you select the CD-ROM to BOOT ***1st***(from BIOS sittings), Right?[/SIZE]

---

### Post by gavdari on 2010-12-15
> **sikander3786 said:**
> From what you said, I feel a little confused.

The same disc boots fine on another system?

Your intended system can boot anyother disc except this one, without making any changes to the boot order? I mean it is already set to boot from CD Drive?

That's right. I'm confused too. The exact same CD works just fine on another system with only Windows 7 installed. But on my laptop, it seems like this is not a bootable CD.

And yes, I have set my 1st boot priority to CD ROM.

---

### Post by tajiknomi on 2010-12-15
[SIZE=2]its quite Strange for me, that CD Boot on Your Bro PC and on yours.....

Why don't you try a ***Live-USB***...?Have you tried it..?
[/SIZE]

---

### Post by sikander3786 on 2010-12-15
I would suggest to burn a new disc at the lowest possbile speed. 4x is recommended if your burner supports it. Might be your Laptop CD Drive can't handle that high speed disc.

And you know that Ubuntu can also be booted/installed from a USB drive if Bios supports it ;-)

---

### Post by gavdari on 2010-12-15
> **tajiknomi said:**
> [SIZE=2]its quite Strange for me, that CD Boot on Your Bro PC and on yours.....

Why don't you try a ***Live-USB***...?Have you tried it..?
[/SIZE]

Maybe it has something to do with the GRUB on mine.
By the way, I'll try the live-usb and post the result here.

---

### Post by gavdari on 2010-12-15
I just tried my old lucid live cd and found out it doesn't work either. looks like there is something wrong with my bios settings or I'm missins something very stupid here.

---

### Post by tajiknomi on 2010-12-15
> **gavdari said:**
> I just tried my old lucid live cd and found out it doesn't work either. looks like there is something wrong with my bios settings or I'm missins something very stupid here.

[SIZE=2]Seems like you are missing to set BIOS to boot(CD-Rom 1st), Check you BIOS carefully....[/SIZE]

[SIZE=2]Or maybe this is Your ***Cd-Drive*** Problem as mentioned by Sikander[/SIZE].

---

### Post by gavdari on 2010-12-15
CD Rom in Dell laptops work like sh*t. No argument there, but since it can read it just fine and even ubuntu recognises it as a package disk, I think there is something wrong with the bios. But I don't know what. I checked and rechecked the 1st priority for boot and it doesn't work.

---

### Post by tajiknomi on 2010-12-15
> **gavdari said:**
> CD Rom in Dell laptops work like sh*t. No argument there, but since it can read it just fine and even ubuntu recognises it as a package disk, I think there is something wrong with the bios. But I don't know what. I checked and rechecked the 1st priority for boot and it doesn't work.

[SIZE=2]I can't help you in BIOS, because i didn't deal with it in my life.....may some1 help you to get you out of this, but i think you can Try Live-USB....
[/SIZE]

---

### Post by gavdari on 2010-12-15
Thanks. I will, but for now I just want to know what is wrong with my CD drive.

---

### Post by sikander3786 on 2010-12-15
> **gavdari said:**
> Thanks. I will, but for now I just want to know what is wrong with my CD drive.
Sometimes, there is a hot key for one time boot device change only. If I am not wrong, it is F12 on Dell. Or it may be printed on the Bios screen named Boot Options or something like that. Hit that and select your CD Drive and see what happens.

Live USB is a definite positive there ;-)

---

### Post by gavdari on 2010-12-15
I finally managed to make it work with wubi. It had an option to make an  entry for booting it. It started the setup but then an error occurred,  'unable to install grub at hd0' or something like that. Now, my computer  doesn't boot, doesn't have ubuntu or windows, and doesn't boot from cd  rom. A complete mess.

> **sikander3786 said:**
> Sometimes, there is a hot key for one time boot device change only. If I am not wrong, it is F12 on Dell. Or it may be printed on the Bios screen named Boot Options or something like that. Hit that and select your CD Drive and see what happens.

Live USB is a definite positive there ;-)

Yes it is F12 but CDROM doesn't appear in the menu. I noticed an exclamation mark near the CD ROM in the boot section in the BIOS setup. No one knows nothing about this exclamation mark. 

and just to complete my misery, I can't find my flash memory any where, and it's too late to go out and buy one.

---

### Post by sikander3786 on 2010-12-15
Sorry to know about you troubles.

Your CD Drive is not working so you definitely need to find your USB stick and put Windows 7 install or repair image on it and use it to repair your startup.

If you don't have one, you can download the repair disc here.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Then burn it to the USB drive using the official Win 7 USB tool and perform startup repair (3 times at least).

Said that, the first priority is to find your USB stick or borrow one somewhere.

---

### Post by gavdari on 2010-12-16
At last, talking from a working kubuntu here (and loving it like hell). Restoring BIOS settings to default didn't change anything visible, but solved the booting problems. Thank you all.

---

### Post by tajiknomi on 2010-12-16
> **gavdari said:**
> Yes it is F12 but CDROM doesn't appear in the menu. I noticed an exclamation mark near the CD ROM in the boot section in the BIOS setup. No one knows nothing about this exclamation mark. 


[SIZE=2]I had searched that problem, and found this > [/SIZE][http://ubuntuforums.org/archive/index.php/t-479225.html](http://ubuntuforums.org/archive/index.php/t-479225.html)

[SIZE=2]This is solved his Issue, but he didn't explain it, However, its seems from the Exclamatory sign that your CD-ROM isn't Activated (According to above link), And i think he Enabled it from BIOS, don't know how...but you can try that......

Edit:- OH,,,I didn't see your last post that it is Solved, any way,Glad to see it is solved.
[/SIZE]

---

