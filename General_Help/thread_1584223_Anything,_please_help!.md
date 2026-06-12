---
title: "Anything, please help!"
date: 2010-09-28
forum: General Help
---

### Post by sanad1995 on 2010-09-28
:confused:  Ubuntu 10.04 (lucid?) HP Pavilion dv9000 Broken CD Drive

Ill try to make this as clear as possible.

About two weeks ago my Ubuntu computer was running amazingly until it began to have problems with open office (wouldn't launch) and when i shutdown my computer all it did was log out. I decided to re install ubuntu with a 4G flash drive because my CD drive doesn't work and it seemed to go smoothly. i tried to turn on my computer, but it went to the HP logo and then to a full black screen with a flashing white underscore in the top left corner. I turned off my computer and i put in my flash drive again. It worked. So with my flash drive inside, i took my laptop to my modem and plugged it in directly. When i plugged it in, in the top left section of my screen it said, connection with Wired eth0. The internet still doesn't work with the computer so i cant download any drivers. I decided to try to reboot it, so i changed the boot priority to USB Hard Drive first and restarted my computer. It just started up. I decided to restart it again and press [F11], (the recovery button for HP laptops) it went to the black screen again with the flashing white under score and beeped whenever i pressed a butten. After a while i decided to give up on pressing the button while it beeped and it loaded up normally. 

So basically 

-My laptop wont load past black screen without the flash drive i installed it with in my computer

-my wired connection or wireless connection wont work so i cant download the video and wireless card drivers.

-It wont recover/boot 

-My CD drive doesn't Work

HELP IS GREATLY APPRECIATED!! PLEASE :( :confused::confused::confused::confused:

---

### Post by corrytonapple on 2010-09-28
Are you dual booting? If not, hit shift as startup and you should get a menu that says GRUB 1.98 or something similar to that. If not, your install did not install GRUB for some reason.

---

### Post by sanad1995 on 2010-09-28
When I press shift the grub menus does pop up, what should I do now :0 sorry I'm a big ubuntu noob

---

### Post by sanad1995 on 2010-09-28
I'm not running windows at all by the way, 100% ubuntu 10.04

---

### Post by Banned. on 2010-09-28
When my friend wanted to try Ubuntu, and he used wubi with 32-bit Ubuntu, he could not get past the blank screen. It was probably because his hard drive wasn't being read. However, when he tried 64-bit Ubuntu, everything worked fine.

I would suggest you to install 64-bit via USB if your computer supports it.

---

### Post by sanad1995 on 2010-09-29
When I bought my computer it was running 32bit windows vista, and if I download it, how do I install it? It's not letting me install the 32 bit again :/

---

### Post by garvinrick4 on 2010-09-29
Hit the escape key before it boots and the choose F9 and should give you menu of what to boot off of, HDD, USB, CD so on. Choose your HDD if it does not boot into your Ubuntu install, reinstall to your drive.

---

### Post by garvinrick4 on 2010-09-29
> **sanad1995 said:**
> When I bought my computer it was running 32bit windows vista, and if I download it, how do I install it? It's not letting me install the 32 bit again :/
It was installed with 32 bit Vista but was capable to run 64 bit. I do not know how you are
installing but sounds like you are letting Ubuntu choose and it reads your machine is 64 bit 
capable.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by corrytonapple on 2010-09-29
> **sanad1995 said:**
> When I press shift the grub menus does pop up, what should I do now :0 sorry I'm a big ubuntu noob
There should be a entry somewhere that says something about Ubuntu. Use your arrow keys and hit enter to select it. Also hitting "esc" should work yo bring you you the GRUB menu besides "Shift".

---

### Post by sanad1995 on 2010-09-29
> **corrytonapple said:**
> There should be a entry somewhere that says something about Ubuntu. Use your arrow keys and hit enter to select it. Also hitting "esc" should work yo bring you you the GRUB menu besides "Shift".

My options are
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Lunix 2.6.32-24-generic (recovery mode)
Memory test (memtest86+)
Memory Test (memtest86+, serial console 115200

---

### Post by sanad1995 on 2010-09-29
> **sanad1995 said:**
> My options are
Ubuntu, with Linux 2.6.32-24-generic
Ubuntu, with Lunix 2.6.32-24-generic (recovery mode)
Memory test (memtest86+)
Memory Test (memtest86+, serial console 115200


Ok. Picked

Ubuntu, with Lunix 2.6.32-24-generic (recovery)

my choices now are..

Resume---resumenormal boot
clean------try to make free space
dpkg-------repair broken packages
failsafex---run in failsafe graphic mode
grub--------update grub boot loader
netroot-----drop to root shell prompt with networking
root---------drop to root shell prompt

---

### Post by sanad1995 on 2010-09-29
Yone :O? I reaallyyy need to use my laptop :-/

---

### Post by Quackers on 2010-09-30
Thats the recovery one. If you choose the first heading it should boot.
From where you are, highlight Resume and hit the enter key.

---

### Post by sanad1995 on 2010-09-30
> **Quackers said:**
> Thats the recovery one. If you choose the first heading it should boot.
From where you are, highlight Resume and hit the enter key.


It's asking for my login, and if I enter something it wants a password :0 I'm almost their. I can taste it

---

### Post by Quackers on 2010-09-30
Have you set up an account and password?

---

### Post by sanad1995 on 2010-09-30
> **sanad1995 said:**
> It's asking for my login, and if I enter something it wants a password :0 I'm almost their. I can taste it

Alright I got my I'd and pass! Noe it's like the terminal 
sanad@sanad-laptop:~$ _

---

### Post by Quackers on 2010-09-30
just an idea, try typing startx and hit enter

---

### Post by sanad1995 on 2010-09-30
> **Quackers said:**
> just an idea, try typing startx and hit enter

Startx. Just started my computer up normally, thanks for the suggestion tho.

What I'm looking for is a button, like f11 I would press and put my computer in recovery mode and reset it back to factory settings.

---

### Post by sanad1995 on 2010-09-30
Is  there any code I could type in to restore my computer? Or to make it boot from a USB drive?

---

### Post by sanad1995 on 2010-09-30
Bump

---

### Post by sanad1995 on 2010-09-30
If I get another flash drive and make it a start up fisk for ubuntu would it work?

---

### Post by Quackers on 2010-09-30
Hello again sanad1995. Let's go back to the beginning. You're not dual booting. Your Ubuntu won't boot unless you've got your usb stick plugged in. Do you want to restore the Windows OS to factory state, or Ubuntu?

---

### Post by sanad1995 on 2010-09-30
> **Quackers said:**
> Hello again sanad1995. Let's go back to the beginning. You're not dual booting. Your Ubuntu won't boot unless you've got your usb stick plugged in. Do you want to restore the Windows OS to factory state, or Ubuntu?

Sorry for not being  clear :( Im not dual booting, my Ubuntu won't boot unless i've got my usb stick plugged in, it wont let me esablish a wired internet connection (or wireless) and i would like to go back to Windows so i can dual boot just in case i have another problem, but if that is harder to accomplish i wouldnt mind going back to 100% ubuntu since im planning to use it anyways.

As long as my laptop isnt a  just sitting their lol :) 
i really appreciate it by the way!!

---

### Post by Quackers on 2010-09-30
Is there a recovery partition on the hard drive and do you know which key to tap while booting to enter the Windows Recovery Environment? What happens when trying that? Do you have a system disc or recovery disc?
Also if you perform a Windows recovery it is likely that your Ubuntu installation will be wiped.

---

### Post by lisa39 on 2010-09-30
Hi
i have same problem .
So now what i can do ?
Please help anyone .
Thanks

---

### Post by Quackers on 2010-09-30
lisa39, it would be better if you could start your own thread giving details of your system, what's gone wrong and what you were doing when it went wrong.

---

### Post by sanad1995 on 2010-09-30
> **Quackers said:**
> Is there a recovery partition on the hard drive and do you know which key to tap while booting to enter the Windows Recovery Environment? What happens when trying that? Do you have a system disc or recovery disc?
Also if you perform a Windows recovery it is likely that your Ubuntu installation will be wiped.

The key is f11 and wen I click to nothing happens, it just stays at the screen with the hp logo.
I think when I installed ubuntu and used only ubuntu it wiped out everything windows :(

---

### Post by Quackers on 2010-09-30
If it's definitely F11 (not ctrl + F11 for instance) then it seems your recovery partition may be gone. If that's the case and you don't have a recovery/system disc then you would need to buy a disc from the manufacturer.
With regard to Ubuntu, it sounds like you need to boot up the system and then install Grub to the hard drive from off the usb stick. It seems that it hasn't been installed, for some reason.

---

### Post by sanad1995 on 2010-09-30
> **Quackers said:**
> If it's definitely F11 (not ctrl + F11 for instance) then it seems your recovery partition may be gone. If that's the case and you don't have a recovery/system disc then you would need to buy a disc from the manufacturer.
With regard to Ubuntu, it sounds like you need to boot up the system and then install Grub to the hard drive from off the usb stick. It seems that it hasn't been installed, for some reason.


It's denately f11, could you elaborate on the reinstalling grub part? I think that'd the direction I want to go. Is their a way to give props or respect points on this forum? I've seen it on other forums.

---

### Post by sasha123 on 2010-09-30
i use ubuntu desktop 10.04 edition OS. I want to connect d net usin my cell phone as modem but i cant install pc suite in ubuntu . So how can i connect ?
Plz help

---

### Post by Quackers on 2010-09-30
I don't know about rep points on this site.
I think if you boot up your Ubuntu system and use the commands in sections 2 to 5 of the link below it should work. If you only have one hard drive it will be sda
***You will need a working internet connection for it.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Quackers on 2010-09-30
sasha123, you should start your own thread with your query.

---

### Post by sanad1995 on 2010-09-30
Quakers,w aht if i downloaded the new 10.10 beta? do you think i could overwrite the 10.04 and fix my problema ;]?

---

### Post by Quackers on 2010-09-30
I think so, but it seems there is sometimes a problem installing grub from usb. It seems you need to select your hard drive at a late stage in the procedure as if you don't grub is installed to the usb only. Alternatively if you burn the downloaded .iso to a cd you may do better.

---

### Post by sanad1995 on 2010-09-30
> **Quackers said:**
> I don't know about rep points on this site.
I think if you boot up your Ubuntu system and use the commands in sections 2 to 5 of the link below it should work. If you only have one hard drive it will be sda
***You will need a working internet connection for it.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Alright, ill keep working on the internet connection problem. If i have a password on my modem where would i type that in? When i plug the Ethernet cable in so i can update my wireless driver it connects to eth0 and i still do not have internet connection :o

---

### Post by Quackers on 2010-10-01
At the top right of your desktop (when you've booted up) there is a symbol for wi-fi. Just click on that and you should see available networks. Click on the one you want to connect to and a box will open asking for a password. Enter password, then a second window will open for another one. Just click on ok then ok again in the next box and you should then connect.

---

### Post by sanad1995 on 2010-10-03
> **Quackers said:**
> At the top right of your desktop (when you've booted up) there is a symbol for wi-fi. Just click on that and you should see available networks. Click on the one you want to connect to and a box will open asking for a password. Enter password, then a second window will open for another one. Just click on ok then ok again in the next box and you should then connect.


Alright do my only option is auto eth0 and it doesn't ask for a pass word :/ I think I'm going to go to 10.10 or download 10.04 on a different USB and try to boot again

---

### Post by sanad1995 on 2010-10-03
:0 I'm desperate lol do you think geek squad or something can help me with ubuntu?

---

### Post by sanad1995 on 2010-10-03
B b b b b b b b b b b b
u u u u u u u u u u u u
m m m m m m m m m m 
p  p p p p p p p p  p p

---

### Post by sanad1995 on 2010-10-03
<----- desperate

---

### Post by sanad1995 on 2010-10-06
> **sanad1995 said:**
> <----- desperate very

---

### Post by sasha123 on 2010-10-09
.

---

