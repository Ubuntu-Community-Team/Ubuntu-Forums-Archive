---
title: "ubuntu 9.10 wubi install failed to boot"
date: 2009-11-09
forum: General Help
---

### Post by crysis on 2009-11-09
i got **vista** and **ubuntu 9.10 64bit** dual booting. i installed ubuntu 9.10 64bit using **Wubi**. after a hard reboot ( ubuntu hanged while going to suspend mode, and i had to force restart) my ubuntu failed to boot.

i ain't no expert (or even close) but it seems my laptop boot to ubuntu via **NTbootloader** (windows) and then to **grub** which finally loads ubuntu.

**ntloader** shows up first showing boot option to windows and ubuntu.

choosing ubuntu shows the grub which shows a menu to boot ubuntu options like safe graphics mode, terminal , kernel versions etc. 

the problem is that now choosing ubuntu from NTloader dosen't show the grub. instead i get a **grub command prompt**. 

my wubi ubuntu virtual disk (root.disk) and my NTFS file system is fine.
my windows boots fine and NTFS partition has no problem. i also booted to a live ubuntu cd, and mounted and checked (fsck) my wubi ubuntu install (root.disk). it shows no error and i can access all my files.

how do i fix this.

---

### Post by Zheldon on 2009-11-09
I have the same problem.  I've often used Wubi to toy around with Ubuntu and so I love that tool.  At first I just had 9.04 and just let it do the upgrade.  Today I decided to uninstall that and have it do 9.10.

I get dumped to that prompt.  Typing Linux tells me there is no Linux Kernel loaded.  Not sure if that helps anyone.

---

### Post by Annigma on 2009-11-10
Hello :)

I'm not offering help I'm afraid, since I'm a noob :lolflag: but you guys are obviously used to Ubuntu/Wubi, so you'll probably be able to answer my query. I hope you don't mind me asking here..

I've just built a new PC and installed Win7 64-bit. I've got a Hardy Heron disk but it's 32-bit, so I thought I'd have a go at downloading Karmic and dual booting (had dual booting working with Feisty for a short time, then tried to upgrade from the synaptic and it all went wrong).

My question is regarding the iso. I followed the instructions [here]("http://www.psychocats.net/ubuntu/iso") and downloaded ubuntu-9.10-desktop-amd64.iso.torrent from [here]("http://releases.ubuntu.com/karmic/"). The program shown on the disk is 'wubi' which from reading I believe is to install Ubuntu *inside* Windows, which I don't want to do...

Have I understood correctly, or do I need to download a different iso?

Thanks

---

### Post by MelDJ on 2009-11-10
try doing a chkdsk /f from windows

---

### Post by Annigma on 2009-11-10
Thank you. Can't see the option. Could do from DOS prompt, but it's showing nothing on the disk, even though I can see it's burned something on there, and if I double click it shows wubi and the files.. strange.

Sorry for hijacking. I should've started a new thread. I'll try and figure it out. If I can't, I'll start a new thread :oops:

Thanks again :D

---

### Post by missmoondog on 2009-11-10
fwiw,
was just coming here to post something similar.

seems to me the 9.10 wubi is screwed up, as is all of 9.10.

i had 9.10 installed on 4 machines over the course of the last 4 days. all 4 machines refused to allow me to login in to my own user name the next day. all 4 machines are now clean of this crap!!

here i thought ubuntu was finally cool and not all screwed up as it was in the past when i last tried this thing (6.06)

oh well,
back to good ol' windows!!
at least it allows me to login into my own dang account!!

---

### Post by iasenko on 2009-11-10
i have the same problem... stays at :
sh.grub>

Any ideas how can I access my files in the "root.disk" file? I have a project to send tomorrow and now everything is there..  
I'm a total ubuntu newbie ..](*,)
Heeeelp ....

---

### Post by djhk on 2009-11-10
From the SH> prompt enter

sh:grub>insmod ntfs
sh:grub>set root=(hd0,1)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

You can use the TAB key to enter the remaining string.

This should boot your system.

IIn Ubuntu open the terminal and enter

sudo update-grub2

This should fix your grub files.

---

### Post by Zheldon on 2009-11-11
Thanks for the reply.  Sadly it did not work.  I forget the exact error, I should have wrote it down.

I do remember it was at this line.
sh:grub>loopback loop0 /ubuntu/disks/root.disk

---

### Post by ds151 on 2009-11-12
>  Thanks for the reply. Sadly it did not work. I forget the exact error, I should have wrote it down.
 
I do remember it was at this line.
sh:grub>loopback loop0 /ubuntu/disks/root.disk

 
It may be that your ubunutu partition isnt (hd0,1) as the guide had suggested. I have this problem at the moment, and found that using (hd0,2) works for me. 
 
Remember to change /dev/sda1 to /dev/sda2 on the line:
>  sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro

 
 
Hopefully that will get you booting, I found that using the 
>  sudo update-grub2

 
command didnt fix my bootloader, I have just followed these instructions each time I have rebooted it for now. 
 
Any suggestions of how to get this to work permanently?
 
Dan

---

### Post by salar on 2009-11-12
Looks like the same problem over [here]("http://ubuntuforums.org/showthread.php?t=1306846").
John

---

### Post by wcr03 on 2009-11-12
> **ds151 said:**
> It may be that your ubunutu partition isnt (hd0,1) as the guide had suggested. I have this problem at the moment, and found that using (hd0,2) works for me. 
 
Remember to change /dev/sda1 to /dev/sda2 on the line:
 
 
 
Hopefully that will get you booting, I found that using the 
 
 
command didnt fix my bootloader, I have just followed these instructions each time I have rebooted it for now. 
 
Any suggestions of how to get this to work permanently?
 
Dan
 
Yea, same problem, except mine is installed on (hd0,5), and when I updated the grub, it didn't change anything, the system is still trying to boot from (hd0,0), but when i opened the grub.cfg, it shows it's booting from (hd0,5).....jst weird.....
 
and this problem happened to me after a Windows XP update........

---

### Post by Zheldon on 2009-11-12
How can I tell what HD#,# I should use?  I tried as suggested earlier to use hd0,2 but that failed too.

The error message I get is "error: file name required".   This occurs when I use the "loopback loop0/ubuntu/disks/root.disk" command.

---

### Post by wcr03 on 2009-11-12
> **Zheldon said:**
> How can I tell what HD#,# I should use? I tried as suggested earlier to use hd0,2 but that failed too.
 
The error message I get is "error: file name required". This occurs when I use the "loopback loop0/ubuntu/disks/root.disk" command.
 
grub>
grub> ls
// now you should be able to see all the partitions
// e.g (hd0) (hd0,1) ...etc
grub> ls (hd0)
will tell you more info about the partition, and you should be able to find the right one, jst look for the label of a partition if you have one, and find the one you installed ubuntu on

---

### Post by monkey d luffy on 2009-11-20
Hi, i got the same problem, but i solved this partly this worked for me:

For the Wubi users:
```
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro
```where /dev/sda# # is your drive where you installed wubi.
to check the drives:
press Tab and type some code that start with ls don´t remember exactly.
Then
```
initrd /boot/initrd.img-2.6.31-14-generic
```And finally:
```
boot
```This will succesfully boot wubi users of karmic koala.
The only problem is I can´t fix this I need to manaully boot everytime.
the sudo update-grub didn´t fix it.

---

### Post by Ciber on 2009-11-26
> **djhk said:**
> From the SH> prompt enter

sh:grub>insmod ntfs
sh:grub>set root=(hd0,1)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot


I'm having a similar problem and tried the above, but /dev/sda1 doesn't exist - in fact there is nothing in /dev/ beginning with the letters "sd".  Is there anything else that can be used in the root parameter to get this working? (I'm sure I have managed to get it working before with karmic using some other string there, but exactly what it was I used has escaped my mind).

Thanks.

---

### Post by madwoollything on 2009-11-28
> **djhk said:**
> From the SH> prompt enter

sh:grub>insmod ntfs
sh:grub>set root=(hd0,1)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

You can use the TAB key to enter the remaining string.

This should boot your system.

IIn Ubuntu open the terminal and enter

sudo update-grub2

This should fix your grub files.

The above steps do work and allow wubi installation to boot up however 'sudo update-grub2' does not make the changes permanent and I have to follow the above steps each time I want to start ubuntu.

Would love to know how to fix this. Was really enjoying karmic until doing this latest upgrade to 2.6.31-15 but by the time I discovered the problem it was too late.

---

### Post by jkogut on 2009-11-30
Hello,

thnx for solution, but I have problem with this line:

sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro

it is the funny thing because I cannot write whole line ... I mean there is not enough "space" to finish the line ... when I try to write it anyway, grub2 hangs :-/ when I shorten the line to:

sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro

it boots but I get Initramfs prompt :-/

Unfortunately I had not enough time to solve it, because the laptop is not mine. 

Is someone had the same problem?  


Cheers,
JK

---

### Post by 2foxy on 2009-11-30
Hi JK,

it boots but I get Initramfs prompt :-/

here is your problem located..
at sh:grub type ls -l to locate your partion (ec.hd0,2)
then the roothave to be corrected to /dev/sda2

Unfortunately I had not enough time to solve it, because the laptop is not mine. 

Is someone had the same problem?  

had the same problem with my netbook :-(

Cheers
Sven

---

### Post by jkogut on 2009-12-02
Sven,

Thnx for your reply,

well, I guess I have chosen the right root partition (sda5), sda1 is from an example ;-) But anyway I am going to check this out again on Monday (then there will be possibility to get back to wubi ;-) )

and I will reply "how it was" ;)

Cheers,
JK

---

### Post by toddq on 2009-12-05
> **iasenko said:**
> i have the same problem... stays at :
sh.grub>

Any ideas how can I access my files in the "root.disk" file? I have a project to send tomorrow and now everything is there..  
I'm a total ubuntu newbie ..](*,)
Heeeelp ....
i found a forum discussion relevant my issue and there is a bug report. However, no adequate solution is mentioned. I seem to have the first report of a problem with linuz-2.6.31-16-generic which allegedly included several "fixes."

I was able to recover most everything following the ubuntu instruction [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) section on

How can I access my Wubi install and repair my install if it won't boot?

Unfortunately, this section is incomplete. that is it tells you how to access the install but doesn't tell you how to repair the grub. The instructions are also rather terse and therefore difficult to follow in several places. My additions are in parentheses.

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

(go to the terminal prompt and don't change directories. The "win" may be something else (e.g., WIN7). Click on Places and you should see something that refers to your windows drive. Replace the above "win" with that.)

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

(cd /vdisk/boot how can then go to your boot file and find out if you don't know already what version of linux you have (e.g., vmlinuz-2.6.31-16-generic. Next, sudo gedit /vdisk/boot/grub/grub.cfg and write down your menu entry information. You can use this information to try the following when you reboot into wubi ubuntu. Note your values for (hd0,2) and sda2 and may be different.

sh:grub> insmod ntfs
set root=(hd0,2)
loopback loop /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/linuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-16-generic
boot

If this works then everything should load
Next go to the confirmed bug report [https://bugs.launchpad.net/ubuntu/+s...in/+bug/477169](https://bugs.launchpad.net/ubuntu/+s...in/+bug/477169) and apply Mark Abene's patch. There is also a laundry list of things in the bug report that you can try that are similar to what I've suggested. However, I'm unsure if anyone has figured out how to get the thing the boot properly or figured out what is causing the problem.

There are several things I haven't figured out yet; how to give myself more space or transfer to a regular dual boot which from what I've read appears to be the best solution for my problem.

---

### Post by MandeaSaracu on 2009-12-08
> **madwoollything said:**
> The above steps do work and allow wubi installation to boot up however 'sudo update-grub2' does not make the changes permanent and I have to follow the above steps each time I want to start ubuntu.

Would love to know how to fix this. Was really enjoying karmic until doing this latest upgrade to 2.6.31-15 but by the time I discovered the problem it was too late.
That's what happened to me as well. 
I printed out the commands, figured out I should use "sda2", and it loads perfectly thereafter. But, on the next restart everything is the same as before. sh.grub.
I have patience, no problem. I use ubuntu at home with wubi and at work (winxp and ubuntu). But with this kernel update I got the same error on both machines, totally different configurations. My using ubuntu at work is just a whim of mine, I can use XP perfectly. but I'm curious about the solution, that I will try when there is one. (I do not have the live cd).

---

### Post by jkogut on 2009-12-09
Well, my problem is solved.

First I have noticed that after I am sure what exactly drive is (e.g. for (hd0,5) is /dev/sda5 ) I have to type correctly all lines in a way that allow you to save "grub2's shell display space". 

The system boots OK, and after applying: 
#update-grub2 command (which updates a device map)

my /boot/grub/grub.cfg has a proper entry:

 menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 13cfa750dfba9339
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}

Thnx for help.


Cheers,
JK

---

### Post by aiiee on 2009-12-11
> **wcr03 said:**
> .
 
and this problem happened to me after a Windows XP update........

same here! got an xp update last night, didn't reboot into windows as it asked but rebooted into kubuntu.  Boom, sh:grub prompt. hmm?

---

### Post by aiiee on 2009-12-11
> **toddq said:**
> i found a forum discussion relevant my issue and there is a bug report. However, no adequate solution is mentioned. I seem to have the first report of a problem with linuz-2.6.31-16-generic which allegedly included several "fixes."

I was able to recover most everything following the ubuntu instruction [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) section on

How can I access my Wubi install and repair my install if it won't boot?

Unfortunately, this section is incomplete. that is it tells you how to access the install but doesn't tell you how to repair the grub. The instructions are also rather terse and therefore difficult to follow in several places. My additions are in parentheses.

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

(go to the terminal prompt and don't change directories. The "win" may be something else (e.g., WIN7). Click on Places and you should see something that refers to your windows drive. Replace the above "win" with that.)

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

(cd /vdisk/boot how can then go to your boot file and find out if you don't know already what version of linux you have (e.g., vmlinuz-2.6.31-16-generic. Next, sudo gedit /vdisk/boot/grub/grub.cfg and write down your menu entry information. You can use this information to try the following when you reboot into wubi ubuntu. Note your values for (hd0,2) and sda2 and may be different.

sh:grub> insmod ntfs
set root=(hd0,2)
loopback loop /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/linuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-16-generic
boot

If this works then everything should load
Next go to the confirmed bug report [https://bugs.launchpad.net/ubuntu/+s...in/+bug/477169](https://bugs.launchpad.net/ubuntu/+s...in/+bug/477169) and apply Mark Abene's patch. There is also a laundry list of things in the bug report that you can try that are similar to what I've suggested. However, I'm unsure if anyone has figured out how to get the thing the boot properly or figured out what is causing the problem.

There are several things I haven't figured out yet; how to give myself more space or transfer to a regular dual boot which from what I've read appears to be the best solution for my problem.

just an fyi for anyone following along.  "linuz" is a typo, should be "vmlinuz".  got me for a second.

---

### Post by aiiee on 2009-12-11
Huge help but it should be noted that the commands need to be entered only one way. Not one command on a line. but like this:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-16-generic
sh:grub>boot


otherwise, no joy.

And please, watch the typos.... clueless noobs like myself don't know they're typos

---

