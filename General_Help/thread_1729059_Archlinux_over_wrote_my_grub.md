---
title: "Archlinux over wrote my grub"
date: 2011-04-14
forum: General Help
---

### Post by vivek.pandey on 2011-04-14
hey everyone
   i was installing arch linux on my usb flash drive...everything went correct but at the point of loading bootloader i instead of selecting /dev/sdc selected /dev/sda by mistake which is my main partition... now when i start  my laptop i get a different bootlaoder, 1.5 i guess which has only arch linux option in it...
  i then booted my laptop through ubuntu 10.10 live cd and can see all the partitions and data there . so the problem is bootloader.. i tried to follow this thread [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
when i typed ```
 sudo grub
``` i got grub command not found  . please some one help i want my ubuntu back as it was before .. please help

---

### Post by vivek.pandey on 2011-04-14
hey everyone
   i was installing arch linux on my usb flash drive...everything went correct but at the point of loading bootloader i instead of selecting /dev/sdc selected /dev/sda by mistake which is my main partition... now when i start  my laptop i get a different bootlaoder, 1.5 i guess which has only arch linux option in it...
  i then booted my laptop through ubuntu 10.10 live cd and can see all the partitions and data there . so the problem is bootloader.. i tried to follow this thread [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
when i typed ```
 sudo grub
``` i got grub command not found  . please some one help i want my ubuntu back as it was before .. please help

---

### Post by TeoBigusGeekus on 2011-04-14
Why don't you try to add ubuntu to arch's menu.lst?

---

### Post by sisco311 on 2011-04-14
[uhelp]community/Grub2#Reinstalling GRUB 2[/uhelp]

---

### Post by seawolf167 on 2011-04-14
> **sisco311 said:**
> [uhelp]community/Grub2#Reinstalling GRUB 2[/uhelp]

+1 beat me to it

---

### Post by bodhi.zazen on 2011-04-14
> **TeoBigusGeekus said:**
> Why don't you try to add ubuntu to arch's menu.lst?

Learning to chainload is also very helpful, IMO =)

---

### Post by vivek.pandey on 2011-04-14
first of all i am really sorry for double threads.. here the internet speed is too slow plus i needed  quick solution so in desperation clicked twice

secondly archlinux is installed on my usb flash drive and if i add ubuntu to arch's menu.lst... i will have to do it for my 7 ubuntu kernels plus windows 7(i have a dual boot windows 7 and ubuntu 10.10)

---

### Post by vivek.pandey on 2011-04-14
> **sisco311 said:**
> [uhelp]community/Grub2#Reinstalling GRUB 2[/uhelp]

thanx to all for your valuable support
before proceeding to this documentation i would like to ensure myself will reinstalling grub2 take my laptop  to same condition as it was before this incidence as this is very important question for me.. i am sorry for such a silly question but i have never been in problem with a boot loader and never messed with it before so have no knowledge about it

---

### Post by TeoBigusGeekus on 2011-04-14
> **bodhi.zazen said:**
> Learning to chainload is also very helpful, IMO =)

+1
Have a look at [this]("http://www.brunolinux.com/05-Configuring_Your_System/Multiboot_grub.html").

You can chainload from grub legacy to grub 2.

---

### Post by bodhi.zazen on 2011-04-14
> **vivek.pandey said:**
> first of all i am really sorry for double threads.. here the internet speed is too slow plus i needed  quick solution so in desperation clicked twice

secondly archlinux is installed on my usb flash drive and if i add ubuntu to arch's menu.lst... i will have to do it for my 7 ubuntu kernels plus windows 7(i have a dual boot windows 7 and ubuntu 10.10)

Well, that is why you chainload =)

When you chainload, first you would get the Arch grub menu -> chainload will then load the Ubuntu grub menu.

In the long run this is easier as it means you do not need to manually update menus with each kernel you upgrade , if that makes sense.

```
Title "Ubuntu"
root (hdx,y)
kernel /boot/grub/core.img
boot
```

---

### Post by seawolf167 on 2011-04-14
> **vivek.pandey said:**
> thanx to all for your valuable support
before proceeding to this documentation i would like to ensure myself will reinstalling grub2 take my laptop  to same condition as it was before this incidence as this is very important question for me.. i am sorry for such a silly question but i have never been in problem with a boot loader and never messed with it before so have no knowledge about it

Aye, you'll be good to go. The grub reinstall will (obviously) restore grub and the commands in the above link will point it to the correct place to boot. If you have other OS's on your computer (like Windows) you'll have to run

```
sudo update-grub
```

to find the other OS with the os-prober

---

### Post by TeoBigusGeekus on 2011-04-14
> **bodhi.zazen said:**
> Well, that is why you chainload =)

When you chainload, first you would get the Arch grub menu -> chainload will then load the Ubuntu grub menu.

In the long run this is easier as it means you do not need to manually update menus with each kernel you upgrade , if that makes sense.

```
Title "Ubuntu"
root (hdx,y)
kernel /boot/grub/core.img
boot
```

...or even
```
Title "Ubuntu's grub menu - see I haven't lost it, it's still there"
root (hdx,y)
chainloader +1
```

---

### Post by bodhi.zazen on 2011-04-14
> **TeoBigusGeekus said:**
> ...or even
```
Title "Ubuntu's grub menu - see I haven't lost it, it's still there"
root (hdx,y)
chainloader +1
```

Because core.img just sounds geekier then chainloader +1

:twisted:

Actually, I have not tried chainloader +1 with grub2, nice to know it works as well.

Grub2 seems to do a much better job then grub1 at recognizing my OS I rarely have to bugger with it manually much.

/end off topic

---

### Post by vivek.pandey on 2011-04-14
thank you everyone for being so helpful but now i have two lines of support one chainload and second reinstall... which is the best option for me ? points to be considered is right now i am using live cd and so cant boot into archlinux also i am still not very fluent with linux commands(just 3 months when i have started using ubuntu properly) :-) but still i am ready to use them provided they are not really risky that a slight error may push me into bigger troubles....

---

### Post by TeoBigusGeekus on 2011-04-14
> **bodhi.zazen said:**
> Because core.img just sounds geekier then chainloader +1

:twisted:

Actually, I have not tried chainloader +1 with grub2, nice to know it works as well.

Grub2 seems to do a much better job then grub1 at recognizing my OS I rarely have to bugger with it manually much.

/end off topic

Tiny misunderstanding, I was talking about adding it to arch's grub (legacy).
I don't use grub2 :P, it's too complicated.

EDIT: A clarification: The Arch installer comes with grub legacy as default; they haven't yet switched to grub2 as it's still considered unstable.
I made an attempt to switch to grub2 a few months ago, lost my ttys and switched back to good old grub legacy.

---

### Post by bodhi.zazen on 2011-04-14
> **vivek.pandey said:**
> thank you everyone for being so helpful but now i have two lines of support one chainload and second reinstall... which is the best option for me ? 

Chainloading is the way to go, hands down, by far the easiest to maintain.

---

### Post by WorMzy on 2011-04-14
> **vivek.pandey said:**
> thank you everyone for being so helpful but now i have two lines of support one chainload and second reinstall... which is the best option for me ? points to be considered is right now i am using live cd and so cant boot into archlinux also i am still not very fluent with linux commands(just 3 months when i have started using ubuntu properly) :-) but still i am ready to use them provided they are not really risky that a slight error may push me into bigger troubles....

I'm not sure why people are suggesting chainloading tbh, that will only work if you have the USB stick inserted into the PC when you turn on the PC. Since you overwrote grub2, if the USB stick isn't in when you try to boot up, you'll get a grub error since it won't be able to find it's stage 1.5.

You need to reinstall grub.

---

### Post by bodhi.zazen on 2011-04-14
> **TeoBigusGeekus said:**
> Tiny misunderstanding, I was talking about adding it to arch's grub (legacy).
I don't use grub2 :P, it's too complicated.

OK, I am failry sure (not positive mind you) that you use:

To chainload to grub 1 -> chainloader +1

To chainload to grub 2 -> core.img

---

### Post by bodhi.zazen on 2011-04-14
> **WorMzy said:**
> You need to reinstall grub

We digress.

Step 1 will be to reinstall grub to the MBR, using Ubuntu (grub2) as that is what is on your hard drive.

Step2 will be to learn to chainload so as to maintain a multiboot linux box with the least amount of work (manually editing grub all the time).

Grub 2 will automate all this if:

1. The usb is plugged in when you update grub.
2. It recognizes Arch (which it should).

---

### Post by TeoBigusGeekus on 2011-04-14
> **bodhi.zazen said:**
> OK, I am failry sure (not positive mind you) that you use:

To chainload to grub 1 -> chainloader +1

To chainload to grub 2 -> core.img

Thanks, I didn't know that.

Back on topic, and reading vivek's first post more carefully, I think wormzy is right: grub2 was overwritten; it needs to be reinstalled.

To vivek: next time you want to try Arch, don't let its installer install grub. Rather, boot up with Ubuntu and see if a
```
sudo update-grub 
```
detects Arch.
I truly hope that this experience does not deter you from trying Arch again.

---

### Post by vivek.pandey on 2011-04-14
> **WorMzy said:**
> I'm not sure why people are suggesting chainloading tbh, that will only work if you have the USB stick inserted into the PC when you turn on the PC. Since you overwrote grub2, if the USB stick isn't in when you try to boot up, you'll get a grub error since it won't be able to find it's stage 1.5.

You need to reinstall grub.

thanx for your answer... this was the doubt which i was having and so was asking again and again as i cant keep my flash drive inserted every time i am about to boot

---

### Post by vivek.pandey on 2011-04-14
ok so i started reinstalling grub2.... i faced a problem again
here is step by step procedure i took
step 1) mounted the partition on which i have ubuntu file system
```
   sudo mount /dev/sda6 /mnt 
```

step 2) mounted the partition in which i have ubuntu home directory
```
  sudo mount /dev/sda8 /mnt/home 
```

step 3) ran grub install command and got an error
```
 ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda6
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.
ubuntu@ubuntu:~$ 

```

please help

---

### Post by TeoBigusGeekus on 2011-04-14
Make it
```
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by vivek.pandey on 2011-04-14
> **TeoBigusGeekus said:**
> Make it
```
sudo grub-install --root-directory=/mnt /dev/sda
```
```
 iam getting following error
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..


```

---

### Post by oldfred on 2011-04-14
The flexnet issue is just a warning. In windows you are using some software that uses DRM via flexnet. Flexnet has hidden its data in sector 32 which grub would normally used. But they make grub2 work with a workaround.

Were you booting with windows on the internal drive?

---

### Post by vivek.pandey on 2011-04-14
> **oldfred said:**
> The flexnet issue is just a warning. In windows you are using some software that uses DRM via flexnet. Flexnet has hidden its data in sector 32 which grub would normally used. But they make grub2 work with a workaround.

Were you booting with windows on the internal drive?
so you mean to say that now the problem is fixed and i should reboot?

and my partition is as such.... i had windows installed when i bought my laptop...then 2 months later i made 3 partitions of the c: drive thus i got sda3, sda2 and sda5...sda3 being the windows partition ..then again 2 ,months later i installed ubuntu... i chose the option of automatic partition ... and now i have sda6 as ubuntu file system and sda8 ubuntu home directory...

---

### Post by TeoBigusGeekus on 2011-04-14
Do it now
```
sudo reboot
```
we're all waiting!!!!!

---

### Post by vivek.pandey on 2011-04-14
please somebody say its just a nightmare.. :-(  my window partition is alright but i have lost everything from ubuntu..its like the one i had installed on first day with .22 kernel...nothing in my home directory... i had 26 gb of very important stuffs and all is gone .... is there any way to  get it back... i was really  scared of something like this it happened.. i dont know where are my remaining and the latest kernel .28..it took me 4 months to make it an eye candy it was.. now 4 months again.. that would be really too much .. so please ubuntu geeks help me..:-(

---

### Post by bodhi.zazen on 2011-04-14
Do you perhaps have more then one Ubuntu install ? wubi ? separate home or other partitions ?

---

### Post by TeoBigusGeekus on 2011-04-14
Yeah, it can't be...
How could you revert to a previous system state? It doesn't make sense...

---

### Post by vivek.pandey on 2011-04-14
i dont have wubi installed but i guess i installed ubuntu twice ,,,,i had formated the first installation or not i dont remember but in places and file systems and partition i use to see only one ubuntu...

---

### Post by bodhi.zazen on 2011-04-14
I suggest you start mounting your partitions and look at what they are.

On the plus side, if you have to re-install you can start by cleaning up your partitions and moving Arch to your hard drive =)

Don't worry, customizations are easy to replace and it goes faster the second time.

I would be more concerned with loss of any personal data, you do have back ups I trust ?

---

### Post by WorMzy on 2011-04-14
At this point, I think it'd be best if you ran the boot info script so we can see more about what you have installed, and to where.

Download the script [here]("http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.55/boot_info_script055.sh/download"), and follow the instructions from [here]("http://bootinfoscript.sourceforge.net/").

---

### Post by vivek.pandey on 2011-04-14
> **bodhi.zazen said:**
> I suggest you start mounting your partitions and look at what they are.

On the plus side, if you have to re-install you can start by cleaning up your partitions and moving Arch to your hard drive =)

Don't worry, customizations are easy to replace and it goes faster the second time.

I would be more concerned with loss of any personal data, you do have back ups I trust ?

thanx everybody i got my ubuntu back :-).. i updated the grub and whether this did the trick or not, on next reboot i could  see my .28 kernel in the grub menu... nobody can estimate how happy i am now...its like i have got a second life .. in last 3 months i gave ubuntu almost a minimum  of 12 hours per day besides going to college and doing other stuffs.. i use to forget eating but not sitting infront of ubuntu... seeing my ubuntu its like almost 100 students of my college changed their os to ubuntu... i have made it something really beautiful and quite easy to use..obviously softwares i used are not mine and so my thanx to those who wrote those softwares too.. but honestly i just cant stay away from my ubuntu..

thanx to all of you...i sincerely wish that i could meet all of you personally and give you a nice treat at macdonald's or some similar place for helping me till the end.. thanx again

---

### Post by TeoBigusGeekus on 2011-04-14
Don't thank me.
Just promise that you'll give Arch a second chance.

---

### Post by matt_symes on 2011-04-14
> just promise that you'll give arch a second chance.

+1

---

### Post by vivek.pandey on 2011-04-14
> **TeoBigusGeekus said:**
> Don't thank me.
Just promise that you'll give Arch a second chance.

i will surely... till i become really good at it.. i dont give up so easily..and please be there to help me as i always get myself in some sort of mess ;-). by the way what should i do with my install in flash drive.. i dont think i have a bootloader installed for arch..

---

### Post by bodhi.zazen on 2011-04-14
> **TeoBigusGeekus said:**
> Don't thank me.
Just promise that you'll give Arch a second chance.

Don't thank me either, just promise your next project is to learn to do backups before you go messing with partitions, let alone installing an OS.

separate /home partition (or separate data partition if you are a geek) FTW !!!!

---

### Post by matt_symes on 2011-04-14
> or separate data partition if you are a geek

That's just common sense and gumption :D

---

### Post by vivek.pandey on 2011-04-15
> **bodhi.zazen said:**
> Don't thank me either, just promise your next project is to learn to do backups before you go messing with partitions, let alone installing an OS.

separate /home partition (or separate data partition if you are a geek) FTW !!!!

i have my ubuntu file partition on /dev/sda6 and home at /dev/sda8 .. so i guess this is separate home partition... right??

---

### Post by bodhi.zazen on 2011-04-15
> **vivek.pandey said:**
> i have my ubuntu file partition on /dev/sda6 and home at /dev/sda8 .. so i guess this is separate home partition... right??

Yes, looks good.

---

