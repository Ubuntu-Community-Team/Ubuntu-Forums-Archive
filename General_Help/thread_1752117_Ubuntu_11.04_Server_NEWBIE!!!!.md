---
title: "Ubuntu 11.04 Server NEWBIE!!!!"
date: 2011-05-07
forum: General Help
---

### Post by g35celicaz on 2011-05-07
last night i installed ubuntu 11.04 sever on my PC and now i cant log into windows! :'(

this is what happened:

my computer was running windows 7 and ubuntu 11.04 (dual boot) 

then i decided to split my hard drive's partition to install the ubuntu server... and after the installation, all it does is show codding NOW! idk what this is! 

i want to be able to use mt WINDOWS OS again!

ahhh what do i dooo!?

plase help!! :)

Thanks!

---

### Post by spikoley on 2011-05-07
When you boot it should show you the Grub screen where you can select which operating system you want to boot into.  Ubuntu server is command line only and it sounds like it is defaulting to boot into that.

---

### Post by SavageWolf on 2011-05-07
Why are you installing the server version rather than the desktop one?

---

### Post by WorMzy on 2011-05-07
> **g35celicaz said:**
> last night i installed ubuntu 11.04 sever ... after the installation, all it does is show codding

That's because server doesn't come with a GUI, because generally, servers are headless (don't have a monitor). You can still install one though; simply run

```
sudo apt-get install ubuntu-desktop
```
for the GNOME desktop
```
sudo apt-get install kubuntu-desktop
```
for the KDE desktop
```
sudo apt-get install xubuntu-desktop
```
for the XFCE desktop, or
```
sudo apt-get install lubuntu-desktop
```
for the LXDE desktop.

As for the boot menu, you may need to run

```
sudo update-grub
```
before you're able to boot into Windows.

---

### Post by g35celicaz on 2011-05-07
@SavageWolf i wanted to play around with the server stuff :D

@spikoley there is nooooo GRUB!!! 

@WorMzy thanks for the information but i dont think that applies to me anymore, for i no longer have the server...

i used a Ubuntu 11.04 DESKTOP Live CD to use "gparted" to delete the partition in which included the Ubuntu 11.04 SERVER OS. However, after deleting that specific partition i still cant access WINDOWS 7!

SO.. what i ended up doing is installing Ubuntu 11.04 AGAIN! along with Windows 7 hoping that there will be a grub but nooooo :(

all it does now is load with no GRUB and goes straight to the fresh ubuntu 11.04, but i can indeed access my windows files such as documents, pic, music, etc.

therefore how can i get that GRUB! lol 

Thanks you for your HELP! :DD

---

### Post by WorMzy on 2011-05-08
Ok, the first four commands I posted are no longer relevant, but you still need to run the last one: ```
sudo update-grub
```

---

### Post by g35celicaz on 2011-05-08
@WorMzy: this is what i get...

techgeek@techgeek-GN706AA-ABA-a6242n:~$ sudo update-grub
[sudo] password for techgeek: 
Sorry, try again.
[sudo] password for techgeek:

---

### Post by WorMzy on 2011-05-09
I couldn't tell you if you're supposed to get output from that command or not, as I don't use grub2. You got no errors though (at least, you haven't posted any), so your grub's menu should be up-to-date when you next restart your PC. Hold down shift immediately after your PC POSTs to ensure that the grub menu gets displayed. If Windows doesn't appear as an option, read through [this]("https://help.ubuntu.com/community/Grub2") and see if it offers any further advice.

---

### Post by kaldor on 2011-05-09
> **g35celicaz said:**
> @WorMzy: this is what i get...

techgeek@techgeek-GN706AA-ABA-a6242n:~$ sudo update-grub
[sudo] password for techgeek: 
Sorry, try again.
[sudo] password for techgeek:

You're entering your password incorrectly ;)

---

### Post by g35celicaz on 2011-05-09
@kaldor: you're  right i typed the wrong password.. opps lol

here's what i got:

techgeek@techgeek-GN706AA-ABA-a6242n:~$ sudo update-grub
[sudo] password for techgeek: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
done
techgeek@techgeek-GN706AA-ABA-a6242n:~$ 

BUT! when i restarted, it still showed no GURB!!!!!! :(

---

### Post by YesWeCan on 2011-05-12
sudo lilo -M /dev/sda mbr

Should get your Windows to boot again. You may have to install lilo. Ignore warnings.
Otherwise use Windows OS disk to fix the MBR.

---

### Post by YesWeCan on 2011-05-12
Once you have your Windows booting again, you can add Ubuntu to the Windows bootloader rather than using Grub. Download the free app EasyBCD and install it in Windows. Run it to have it find Ubuntu and add it to your Windows boot menu.
Next time you reinstall Ubuntu, do not install Grub in the mbr. Run EasyBCD again.

This method keeps you being able to boot Windows even if you delete the Ubuntu partition.

---

### Post by g35celicaz on 2011-05-13
techgeek@techgeek-GN706AA-ABA-a6242n:~$ sudo lilo -M /dev/sda mbr
[sudo] password for techgeek: 
sudo: lilo: command not found
techgeek@techgeek-GN706AA-ABA-a6242n:~$

---

### Post by YesWeCan on 2011-05-13
sudo apt-get install lilo

---

### Post by CharlesA on 2011-05-13
> **YesWeCan said:**
> sudo lilo -M /dev/sda mbr

Should get your Windows to boot again. You may have to install lilo. Ignore warnings.
Otherwise use Windows OS disk to fix the MBR.
You shouldn't need to install lilo, when Grub works perfectly well.

What happens if you hit esc after GRUB loads, but before it starts Ubuntu?

---

### Post by YesWeCan on 2011-05-13
> **CharlesA said:**
> You shouldn't need to install lilo, when Grub works perfectly well.

What happens if you hit esc after GRUB loads, but before it starts Ubuntu?
g35 has been waiting 5 days to access Windows. That is the stated priority.

Grub got messed up here. First because Ubu was deleted, which always breaks grub. Subsequent reinstall of Ubu did not fix Grub. Not sure why, perhaps stage 1 was not reinstalled or was corrupted.

---

### Post by g35celicaz on 2011-05-13
@YesWeCan it worked!!!!! :)

this is what i got (although) i havent restarted the computer yet..)

```
techgeek@techgeek-GN706AA-ABA-a6242n:~$ sudo lilo -M /dev/sda mbr
[sudo] password for techgeek: 
sudo: lilo: command not found
techgeek@techgeek-GN706AA-ABA-a6242n:~$ sudo apt-get install lilo
[sudo] password for techgeek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 380 kB of archives.
After this operation, 1,360 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main mbr i386 1.1.10-2 [23.0 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main lilo i386 1:22.8-10ubuntu1 [357 kB]
Fetched 380 kB in 2s (153 kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 137325 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-10ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-10ubuntu1) ...
techgeek@techgeek-GN706AA-ABA-a6242n:~$ 
```

i will restart right now i'll post up the results :D

---

### Post by YesWeCan on 2011-05-13
you have to dothe first command again as it failed because lilo was not installed. :)

---

### Post by g35celicaz on 2011-05-13
aww man i guess that explains why i didnt see the grub when i restarted lol.

SOO is it possible just to use the Windows CD and instead of reinstalling... select 'fix problems'? and it will fix the boot loader so i can keep the ubuntu? OR can i still fix this within ubuntu?

---

### Post by YesWeCan on 2011-05-13
just excute that command. it restores the master boot record to one that should boot Windows.

sudo lilo -M /dev/sda mbr

sudo reboot



Hurry, the suspense is killing me. :P

---

### Post by g35celicaz on 2011-05-13
OMG it worked! i am currently using windows 7 :D

these commands worked!:
sudo lilo -M /dev/sda mbr

sudo reboot 

@yeswecan: i am soooo sorry for leaving you on the hang!... i left cuz i still had to finish my homework :( 

"YES WE CAN, YES WE CAN, YES WE CAN!" lol :DD

---

### Post by JPman on 2011-05-13
> **g35celicaz said:**
> last night i installed ubuntu 11.04 sever on my PC and now i cant log into windows! :'(

this is what happened:

my computer was running windows 7 and ubuntu 11.04 (dual boot) 

then i decided to split my hard drive's partition to install the ubuntu server... and after the installation, all it does is show codding NOW! idk what this is! 

i want to be able to use mt WINDOWS OS again!

ahhh what do i dooo!?

plase help!! :)

---

### Post by JPman on 2011-05-13
Here is what I would do....

Get a copy of Puppy Linux and boot it "live".   Look on the "system" menu for "grub config" and off you go.    Grub will scan and include all OS on the drive.   After it is working then go to "Boot, Grub" and clean up the "Title" line so what you see on the grub splash looks nice.

Puppy is great for those kinds of things but the only OS I've seen that has a GUI menu item for "fix MBR" is PCLinux.

Good Luck,

Thanks![/QUOTE]

---

### Post by YesWeCan on 2011-05-13
> **g35celicaz said:**
> OMG it worked! i am currently using windows 7 :D

these commands worked!:
sudo lilo -M /dev/sda mbr

sudo reboot 

@yeswecan: i am soooo sorry for leaving you on the hang!... i left cuz i still had to finish my homework :( 

"YES WE CAN, YES WE CAN, YES WE CAN!" lol :DD

Good stuff! :D
I figured you were more interested in getting Windows back than fixing your Grub issues.

But do not be put off linux. Things usually work perfectly well and Grub is quite capable of booting Windows. Something about Grub was broken when you were deleting/reinstalling Ubuntu, somehow. As I suggested, you can stop your MBR from being changed by choosing NOT to install Grub in the MBR during Ubuntu install. Then use EasyBCD to add Ubuntu to the Windows bootloader. Best is to put Ubuntu on its own disk (or Grub at least), if you have that option.

Sorry it took you 5 days to get Windows back.

---

### Post by g35celicaz on 2011-05-13
oh i am definitely going to keep using ubuntu! :D

and its cool :) @ least i now have acess to windows (my worst fear was having to deal with backing up my files and reinstalling... i didnt want to do that long & easy work lol).

THANKS AGAIN!!!!!!!!!!!!!!!! :D

---

