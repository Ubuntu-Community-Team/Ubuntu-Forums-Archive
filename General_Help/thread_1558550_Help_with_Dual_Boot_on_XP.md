---
title: "Help with Dual Boot on XP"
date: 2010-08-22
forum: General Help
---

### Post by theprocess on 2010-08-22
Sorry if this is some ridiculously easy problem that I've overlooked but I'm truley stumped (a noob).

So I was bored today so I decided I'd have a go at getting my PC to dual  boot with Ubuntu. I'm a bit stuck so wondering if you could help.

I  downloaded the software, burnt ISO to CD, rebooted, booted from CD,  installed software as per the wizard, chose to install Ubuntu to my partitioned 2nd HDD  and then let it reboot my PC once installed... but it went straight into  windows.

I thought it might have not installed properly so i went  through the installation again but noticed that the 2nd HDD was already  partitioned with Ubuntu from the previous installation already showing  so I didn't continue with the installation.

Do you know why there is no option on startup as to which OS I want to choose from?

The  only way I can currently get into it is by booting from CD on startup and then  using the "try it" version which is just running Ubuntu off the CD

Would be great if you could help
process

---

### Post by nacho32 on 2010-08-22
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by theprocess on 2010-08-22
Thanks for the reply.

I downloaded the Rescatux and burnt the ISO to disk, booted to disc and then followed the instructions as per their help section but still no joy. Any other ideas?

---

### Post by rockager on 2010-08-22
are you able to boot into windows?

---

### Post by theprocess on 2010-08-22
Yea, I'm in windows at the moment. When I restart the PC, it just goes straight into Windows

---

### Post by dougalkerr on 2010-08-22
Try downloading and burning the SuperGrub startup disk.
Pop it into the drive as you boot and folow the instructions. You should be able to opt for Linux and Win then let it do it's job.

If it doesn't succeed the first time try another combination.

If after all that you still have problems try installing Ubuntu again from boot-up it sounds like the boot manager is not quite set-up right.

---

### Post by theprocess on 2010-08-22
thanks, will do that.

If I have to re-install Ubuntu, will it make a duplicate copy? The reason I ask is because when I tried to reinstall last time, it wanted me to make yet another partition for the 2nd Ubuntu installation as well as the 1st.

Will let you know how I get on

---

### Post by rockager on 2010-08-22
i suggest you reformat the ubuntu partition and install ubuntu all over again.
the grub installation must have been faulty or incomplete.

---

### Post by oldfred on 2010-08-22
Did you install grub2 to the second drive and need to change BIOS to boot second drive. I prefer to leave the windows boot loader in the first drive if you have two drives. Grub used to always overwrite the windows boot loader but they have been making some fixes.

To see where everything is installed, from liveCD run this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by anirudhtomer on 2010-08-22
see every HDD has a Master Boot Record which contains the 4 sectors of 16 bytes each corresponding to 4 primary partitions.
In your case your MBR is overwritten.
So do the following:

Boot with your live CD & click on try ubuntu without change.
then open the terminal & type the following.

$ grub
this will start the program grub

grub> find /boot/grub/stage1

then u'll get something like (hd0,4)
u may get anything ....

grub> root(hd0,4)
grub> setup(hd0)

I hope your problem gets solved

---

### Post by dougalkerr on 2010-08-22
When you see the option to install yet another copy of Ubuntu just ignore it and do as I instructed. It will delete the ubuntu partition you made earlier and the you will create it again all nice and fresh.

Good luck.

---

### Post by theprocess on 2010-08-22
Thanks for all the responses, before I try those, I'll just give you an update. I used Super Grub Disk 2 as per dougalkerr above. It gave me an option to boot up into a Grub2 OS, it then went into my Ubuntu (my HDD's were showing and all my docs were available to view)

When I reboot again, it then just goes straight into Windows. So where I am now is I can now get into my Ubuntu but not without the SuperGrubDisk
.
Is this a step closer? 

If not, I'll try the reinstall and then the other responses

Thanks again for your help

---

### Post by dougalkerr on 2010-08-22
Sounds like you could be going round in circles for a while. It will be quicker to reinstall unless you wait to see if there are any other suggestions.

Remind me... what version of Ubuntu are you using?

---

### Post by theprocess on 2010-08-22
10.04 LTS

I'll have a go at re-installing.
Thanks

---

### Post by alicemoon on 2010-08-22
You have 2 hard drives and when the computer boots up it always boots from the hard drive with windows on it as this is the primary drive - your grub and Ubuntu are installed onto the 2nd hard drive - you need to go into the Bios and change the boot order so the drive with Ubuntu on it becomes the primary drive then the grub should show and you will be able to boot into either ubuntu or windows as you choose

---

### Post by dougalkerr on 2010-08-22
Sorry Alice - you don't have to do that.

Everything is taken care of automatically upon install.

---

### Post by alicemoon on 2010-08-22
dougal - if the MBR on the 1st hard drive is not pointing to the ubuntu bootloader by booting into the second hard drive you should still get the grub options?

---

### Post by dougalkerr on 2010-08-22
Yes you are quite correct Alice but, nothing should have been done that justifies having to go into the BIOS to make alterations.

Your thinking is sound but, Linux should not affect the system in such a way as to have to go into the BIOS to make changes (same thing).

I still believe that a fresh install may well do the trick although the BIOS change will be a simple thing to look at and no harm in trying it first.

---

### Post by alicemoon on 2010-08-22
agreed - better a fresh install if you are uncertain/unfamiliar with changing bios settings

---

### Post by theprocess on 2010-08-22
OK, so firstly I tried to reinstall Ubuntu, it gave me the same problems but when I tried to enter Ubuntu using the Super Grub Disk 2, I noticed that there were two Ubuntu options to choose from this time. 1 said "HD1, 7" and the other said "HD1, 5". 

I then tried to go into the BIOS setup and change the boot order but the order only shows 1 x HD available then CD-Rom etc. On "My Computer" I have a C: and an E: so how come it only shows 1 x HD in the BIOS? Is it because it's actually one physical HDD which has been partitioned into two?

Thanks

---

### Post by dougalkerr on 2010-08-22
Yes, you are correct. It sounds like you have only one hard disk and it is partitioned into two if not three parts now.

You should only have your Windows partition, your Linux SWAP partition and the Linux partition proper.

HD5 and HD7 may be SWAP and Linux system.

Can you remember the steps you take as you install Linux?

A step by step breakdown may reveal what the problem is. Especially at the Partition manager stage.

Thanks.

---

### Post by theprocess on 2010-08-22
Sure, 
- Downloaded software
- Burnt ISO to disk, put disk in drive, rebooted
- Hit F12 to go to boot options
- Selected CD-Rom
- Selected option to install
- Followed through steps in wizard as per the wizard, (options were to leave HD 1 for Windows XP and to change HD2 for Ubuntu - this was selected)
- Input regional information, language etc
- Let install complete
- "Install complete" came up, hit enter
- A sort of startup screen came up, black with white letters. Font was different though, more like an Ubuntu look to it, if you see what I mean.
- CD ejects, get asked to remove and then hit enter - I do this
- Some script showed and paused,hit enter as nothing happened, PC restarts
- Windows boots up

It looks as though it's all installed fine as I've already been into my "personalised" Ubuntu. Just that it isn't booting up into Ubuntu. Must be a bootup issue, just haven't got the foggiest what to do to fix it i'm afraid

---

### Post by oldfred on 2010-08-22
You skipped post #9, everyone is guessing. With the results.txt we can see exactly how your system is set up.

---

### Post by dougalkerr on 2010-08-22
As oldfred says follow suggestion to generate a results.txt file so we can see more clearly how your system is set-up.

By what you said in the steps you took it sounds like something is missing along the hard drive choice. I would have expected the option to go into the Partition Manager, which is what you want and then to generate the partitions manually to force the position of the SWAP and Linux system partitions.

Lets see what your results.txt file says if you can manage that.

Else, lets take it back a little and install say CrunchBang. It is an Ubuntu derivative, small and quick to install and load, etc. It needs a little command line work at times but, everything is there to get you up and running and it will allow manual partitioning, hopefully just the way we want it.
It will mean downloading and burning another distro onto CD but, if you are willing to try this it might start to make some sense as to what is going wrong. It might just be that the LiveCD of the distro that you have is a little bit astray of what it should be doing and if installing CrunchBang goes smoothly then this is what I suspect.

It can be a rewritable CD so that you do keep using more cds. Yawn... it is almost time for bed.

Let me know if you are going down this road tonight... Ta.

---

### Post by Ohsnap on 2010-08-25
I installed Ubuntu with XP no problem by using Wubu (?). I've had absolutely no problem. It gives me the option of choosing which system I want at the beginning. Very easy install. But I was reading on another thread, which I can't find now, that instructs on how to remove XP. It mentions 'g-parted' and I'm stumped. what is that and how do I get it. I'm new to Ubuntu (2 days) but so far I like ti.

---

### Post by Ohsnap on 2010-08-25
I just wanted to say HI. I used to live in Edinburgh and I miss Scotland!

---

