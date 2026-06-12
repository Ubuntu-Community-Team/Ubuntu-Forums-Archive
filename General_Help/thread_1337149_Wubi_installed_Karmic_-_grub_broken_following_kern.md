---
title: "Wubi installed Karmic - grub broken following kernel update"
date: 2009-11-25
forum: General Help
---

### Post by monkeyoutlaw on 2009-11-25
Hello fellow geeks,
 
I am running 9.10 (installed via wubi). I came into work this morning, installed some security updates (I'm pretty sure it mentioned a kernel update), and now it won't boot.
 
When starting up I get the standard windows bootloader giving the option of Windows or Ubuntu. But after choosing ubuntu I get some grub shell (gnu grub 1.97~beta4 - minimal bash-like....).
 
A microsecond before popping up the grub shell I can see 'try (hd0,0): NTFS5'. When I type 'ls' though I dont have '(hd0,0)' - I only have (loop0), (hd0), (hd0,5), hd(0,1), (hd1), (hd1,0), (hd1,1).
 
Can anyone help?

---

### Post by monkeyoutlaw on 2009-11-25
Please reply in the thread at [http://ubuntuforums.org/showthread.php?p=8384751](http://ubuntuforums.org/showthread.php?p=8384751)

---

### Post by Canaryguy on 2009-11-25
Hello,

I had the same problem with the installation of Ubuntu with wubi. Once I installed the updates I saw grub and the system couldn't lunch the graphical interface. But I did something that helped me.

1º Install Ubuntu inside Windows with wubi

2º Install all the updates for Ubuntu when they appear or do it yourself manually

3º After installing the updates when the system asks you to reboot don't do it. Go to the Terminal (Applications/Accessories/Terminal)

4º In the Terminal write: sudo update-grub2 (press enter and write your password if required)

5º Now restart

And that's all

That worked for me.

Good luck.

---

### Post by replikanxxl on 2009-12-07
> **Canaryguy said:**
> Hello,

I had the same problem with the installation of Ubuntu with wubi. Once I installed the updates I saw grub and the system couldn't lunch the graphical interface. But I did something that helped me.

1º Install Ubuntu inside Windows with wubi

2º Install all the updates for Ubuntu when they appear or do it yourself manually

3º After installing the updates when the system asks you to reboot don't do it. Go to the Terminal (Applications/Accessories/Terminal)

4º In the Terminal write: sudo update-grub2 (press enter and write your password if required)

5º Now restart

And that's all

That worked for me.

Good luck.
heh. too late for us. we dont have a booting system at all now . but i will keep your advice in mind. if im crazy enough to use ubuntu again !:D i hate how our prof forces us to use it for damn tinyOS project .

---

### Post by Justin C. on 2009-12-07
I updated my wubi installed karmic last night before bed and now it won't boot. It really sucks because a paper I was working on is in the ubuntu desktop. Can anyone help? This is what attempting to boot the ubuntu leads to:
[IMG]http://farm3.static.flickr.com/2625/4097234597_49e7a6df25.jpg[/IMG]

---

### Post by Justin C. on 2009-12-07
I tried everything. I'm losing faith in linux. This is the second time an update from the update manager has left me with an unbootable system (once as a dual boot and once from wubi). Linux will never be on my main machine again, maybe only on my netbook.

---

### Post by Sabayenda on 2009-12-08
I am also having this problem, as well as a friend who now no longer uses Ubuntu because of this bizarre "update".  I just installed ubuntu on her computer not even a week ago, and now she can't get use it and we've both lost a lot of faith in Ubuntu.

I installed Ubuntu with Wubi through Vista on both systems.  The problem started for both of us after installing the kernel "update" sometime around last friday night/saturday morning.  I know I don't have any solutions, but I'm also looking for a solution, without having to reinstall Ubuntu :-(

This is spit out from Grub after selecting Ubuntu on the list:

GNU Grub 1.97 beta4 [minimal BASH like line editing is supported. For the first word, TAB lists possible command completions Anywhere else TAB lists possible device/file completion.] 

shigrub>_ (blinking cursor)

Possible commands are
[badram boot cat chainloader configfile cpuid dump echo exit exporthalt he lp initvd insmod linux list_env load_ env loopsback ls lsmod parser. resue parser. sh reader. normal reader. rescue reboot rmmod root save_env search set sleep source terminal_input. console terminal_output. console test unset.

---

### Post by ramalho on 2009-12-08
If you install grub2 *before* rebooting, the problem mentioned here does not happen.

Here is how i did it:

1) use the system update app to apply the latest kernel updates but DO NOT REBOOT as suggested by the system

2) run: $ sudo update-grub2 

3) run: $ sudo apt-get install grub2

4) now reboot into the new default kernel (2.6.31-16)

A colleague did step 3 above before step 1, and his system was broken as well, so it seems the problem is with the update.

Unfortunately i don't know how to help those who are staring at the grub prompt

Cheers,

Luciano Ramalho

---

### Post by Justin C. on 2009-12-09
I'm thinking that this will be my last foray with wubi on my main machine.....dual-booting a netbook seems like a better choice for me. I'll still be able to learn linux, but I won't lose any important files if I have to wipe it and start over.

---

### Post by Leppie on 2009-12-10
> **Justin C. said:**
> I'm thinking that this will be my last foray with wubi on my main machine.....dual-booting a netbook seems like a better choice for me. I'll still be able to learn linux, but I won't lose any important files if I have to wipe it and start over.

Yeah, why did you do a wubi install to start off with? A normal install shouldn't take much longer and the space required on disk remains more or less the same... Is there actually any real advantage of using a wubi install?

---

### Post by Leppie on 2009-12-10
> **monkeyoutlaw said:**
>  
A microsecond before popping up the grub shell I can see 'try (hd0,0): NTFS5'. When I type 'ls' though I dont have '(hd0,0)' - I only have (loop0), (hd0), (hd0,5), hd(0,1), (hd1), (hd1,0), (hd1,1).

When you open /boot/grub/device.map in Ubuntu, what is the contents? If there is a reference to (hd0,0) change it to (hd0,1) and do a "sudo update-grub".

---

### Post by garvinrick4 on 2009-12-10
wubi attaches itself to the Windows dos4grub if in Vista or windows 7 use the command in
Windows "bcdedit" without quotes to see the menu, should be one with Wubi in it.
 If not then a problem but does not use grub2 as far as I ever new. It is like an App. inside
of Windows. The actual folder is right next to users in C: drive. At one time I used Wubi and have had the booting to grub prompt before and their was a fix. I have to think a minute before I can remember what it was. Anyway make sure wubi is still in the Windows
grub with the earlier command line reference.

---

### Post by jolurove on 2009-12-10
Hello everybody... I think I found a solution for this... i didn't figure it out myself, but for the people who see this particular thread it might be usefull :)

1.At the "Grub 1.97 beta" type these

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot

and ubuntu gloriously comes back to life!!!!

Once you're back in, you just have to do what Ramalho said earlier.. here it is

1) use the system update app to apply the latest kernel updates but DO NOT REBOOT as suggested by the system

2) run: $ sudo update-grub2 

3) run: $ sudo apt-get install grub2

4) now reboot into the new default kernel (2.6.31-16)

Though I had to reboot using kernel (2.6.31-14)

Hope it helps!!

---

### Post by rotard on 2009-12-12
Close.  I had to use sda1 instead of sda2.  And I was still unable to boot into -16, but at least I was able to boot into -15.  It's something I can work with.  Thanks for posting!  For those who are interested, the bug report can be found at: [https://bugs.launchpad.net/ubuntu/+bug/477169](https://bugs.launchpad.net/ubuntu/+bug/477169)

---

### Post by onlineapps on 2009-12-15
Same issue. At first, I could get to the Grub menu, but not into the latest kernel (though I could still make it into an earlier kernel). Then, I tried running sudo update-grub2 and then sudo aptitutde install grub2 from within the old kernel. Now, it just goes to a Grub prompt, which looks something like what Justin C. reported.

I tried this:

> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot

...but there's no /dev/sda* (or /dev/hda*, for that matter). I think that's partially cause I'm on a Lenovo (G450 laptop).

---

### Post by r0tor on 2009-12-15
ok... i've completely had it with ubuntu...

so far with 9.10...

-first round of updates left me in a kernal panic
- second round of updates left me at a grub prompt
- a reinstall and update left me at a grub prompt
- a third reinstall I disabled everything except security updates

... last night it updated itself, I saw it for some reason installed a new kernal despite having security updates only, got scared and ran update-grub2 before i rebooted, showed the 2 ubuntu kernals...

rebooted today and i'm left at the other f'in grub prompt again

---

### Post by CrusaderAD on 2009-12-15
It's pretty bad... at least with wubi installs. I went back to Jaunty. Hopefully things get resolved in 10.04. The "grub" screen of death sucks.

---

### Post by audiobastard on 2009-12-16
YEAHHH... worked for me.  First i ran the command line prompts at the erroneus bootloader attempt.  Then i followed steps 1-4 in terminal.  Back up muggra.

---

### Post by 1Shadow on 2010-03-05
What is up with Ubuntu and their lack of testing on stuff like this???  

I had a sweet dual Xeon (4 cores) server running as a workstation - 6 disk Ultra320 10K Raid5 (Software raid 'cause IBM's raid5 controller SUX) that would not boot with Grub2 - Had to go back to Jaunty after days of beating my head against the wall..  

My company laptop is so trashed with our idiot IT dept's bogus config I borrowed a couple gig for a Karmic install using Wubi.  Again with the boot problems.  

I think I'm sticking with Jaunty for all my Linux systems until the propeller heads pull their -er... propeller - out of their butt.  I'd have preferred they skipped the 9.10 release and just bugfixed things until 10.4 rather than souring so many people on what has historically been a good OS.

---

### Post by sistercreepy on 2010-03-14
The good thing about the wubi installer is that it does all the work for you.  It works it's mojo and when you reboot your computer you have the option of running windows or ubuntu.  You don't have to know anything about partioning a hard drive.

---

### Post by edo471 on 2010-03-17
is there a solution to this problem? (i just got it today) or do I have to reinstall ubuntu (I use wubi to install it)

---

### Post by edo471 on 2010-03-17
> **jolurove said:**
> Hello everybody... I think I found a solution for this... i didn't figure it out myself, but for the people who see this particular thread it might be usefull :)

1.At the "Grub 1.97 beta" type these

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot

and ubuntu gloriously comes back to life!!!!

Once you're back in, you just have to do what Ramalho said earlier.. here it is

1) use the system update app to apply the latest kernel updates but DO NOT REBOOT as suggested by the system

2) run: $ sudo update-grub2 

3) run: $ sudo apt-get install grub2

4) now reboot into the new default kernel (2.6.31-16)

Though I had to reboot using kernel (2.6.31-14)

Hope it helps!!

Is there a way to make this PERMANENT? I had to write this down, because every time reboot I have to do it all: 
> **jolurove said:**
> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-14-generic
boot
but even tho the newest kernel i have installed is 2.6.31-20 i just can log in in 2.6.31-14
please help :(

---

