---
title: "Looking for any solutions to a monitor that switches off during Xubuntu 10.04 install"
date: 2010-06-21
forum: General Help
---

### Post by rollin on 2010-06-21
Basically I have some Linux experience and have got myself an "old-but-good-machine". I'm sure the Xubuntu 10.04 cd is OK as I can boot into it with my Windows laptop. But... for whatever reason I can't boot it under the Live CD or Install options in my old computer??

As soon as I hit one of the options the monitor switches off after a few seconds?? After some hours on Google I found that I was not the only one with the problem although I can't find a solution?

I've tested the computer with a live backtrack cd and gparted live cd which both run fine so it must be something I'm missing in Xubuntu.

Any advice would be great =(

---

### Post by Smart Viking on 2010-06-21
Hi, i would recommend to install with the "alternate" cd. I have a feeling that will make the install more "bullet proof", but i might be wrong though, maybe you get to install it and after the install, the pc wont work, so i would not do it if the pc in a working state is of "great" importance.

I hope you will get xubuntu installed and working. :)

---

### Post by rollin on 2010-06-21
> **Smart Viking said:**
> Hi, i would recommend to install with the "alternate" cd. I have a feeling that will make the install more "bullet proof", but i might be wrong though, maybe you get to install it and after the install, the pc wont work, so i would not do it if the pc in a working state is of "great" importance.

I hope you will get xubuntu installed and working. :)

Thanks a lot for the support Smart Viking. I'm not too worried about the PC state as I can still update here on my other box :-) I'll burn the 64-bit alternative ISO and post back with the results...

---

### Post by rollin on 2010-06-21
Update 1 !! 

Thanks for the help so far here is where I am up to:

I know the machine has an AMD 64 processor so as per the advice I downloaded the Xubuntu 64bit 10.04 Alternate ISO.
The installation went well although on reboot the monitor switched off again and no grub menu was present?? 
I managed to get around this as I am dual-booting with Backtrack and for whatever reason grub seemed to work! 

So having installed Backtrack to a small partition I rebooted the system which gave me a grub menu like so:

```
Ubuntu 8.10, kernel 2.6.30.9
Ubuntu 8.10, kernel 2.6.30.9 (recovery mode)
Ubuntu 8.10, memtest86+
Other operating systems:
'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-lin->
'Ubuntu, with Linux 2.6.32-21-generic' (recovery mode) --class ubuntu->
```

Now when I select: 
'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class  gnu-lin->
**or**
'Ubuntu, with Linux 2.6.32-21-generic' (recovery mode) --class  ubuntu->


[LIST=1]
[*]I can't see anything on the screen at all.
[*]The monitor doesn't switch off but I also can not see anything but a black screen.
[*]Ctrl+Alt+F1 has no effect and neither does shaking the mouse or tapping keys on the keyboard. So I have to "hard reboot" unfortunately.
[/LIST]

OK so I thought as I'm trying to copy as much info as I can into the post I'd take a look at the actual commands behind:
'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class  gnu-lin->
Using the "e" option gives me:

```
root (hd0,0)
kernel /boot/vmlinuz-2.6.32-21-generic root=UUID=f95809e1-3d63-4e29-->
initrd /boot/initrd.img-2.6.32-21-generic
savedefault
boot
```


Any more suggestions on how I can boot into Xubuntu with a command line interface or something would be great??

Basically I am pretty confident the installation has worked for Xubuntu although the problem with the monitor seems that it is now just a black screen.
I can use the Backtrack OS installation to try and dig out further info I think.

Thanks again.

---

### Post by rollin on 2010-06-23
Final Update!

Still in the dark with this issue, having tried both Xubuntu and Ubuntu discs, alternate cds, 32 and 64bit still not working after the installation and reboot -no grub menu displayed although HDD working and monitor switches off...
Using lspci -v (on the live cd - see below) I found it is a Nvidia 6150LE card but I couldn't even get a tty1 on reboot after install to run the sh script and install pack from Nvidia via USB :?

Eventually went with Backtrack as it seems to work all the way and is based on da-buntu anyway. 

For anyone in a similar situation the closest I got was booting the live Ubuntu 10.04 64bit cd and using F6: Selected noapic, nolapic, edd=on, nodmraid, nomodeset and after a long while I got a live cd screen :-k 
GL!!

---

### Post by Smart Viking on 2010-06-23
Hi again, i am glad that Backtrack worked, but it seems very weird that a distro that is based upon ubuntu WORKS, and ubuntu doesn't. 

I have one question, did you try to install ubuntu with Gnome, and that didn't work, but backtrack with KDE? Because, if so then the problem might lay in the Gnome desktop! :D

It would be nice if you could confirm that possibility, or opposite, to give people with the same problem in the future a massive push in the right direction. :)

EDIT: Looks like you tried to install xfce4, but anyways that is almost the same thing. :)

---

### Post by rollin on 2010-06-23
Well howdy again ):P

Thanks for the vote with Backtrack - seems like a good OS to me but I know some are skeptical, oh well!

> ...it seems very weird that a distro that is based upon ubuntu WORKS, and ubuntu doesn't. 

Exactly! Thats what I can't get my head around :confused: 

The only difference and this is a biggy, backtrack ships with a custom kernel 2.6.30.9 which was compiled very specifically for the OS and is based on Ubuntu 8.10 platform also KDE3 is the weapon of choice in BT (Backtrack).

> I have one question, did you try to install ubuntu with Gnome, and that didn't work, but backtrack with KDE? Because, if so then the problem might lay in the Gnome desktop! :grin:

It would be nice if you could confirm that possibility, or opposite, to give people with the same problem in the future a massive push in the right direction. :smile:

EDIT: Looks like you tried to install xfce4, but anyways that is almost the same thing. :smile:

Well it's a good question! Actually as part of my endeavours I seemed to have installed 3 types of WM!! 

I installed ubuntu 10.04 (the gnome-ster) and that didn't work although I could eventually get the Ubuntu Live CD to the X session like normal and using nautilus I can confirm the installation had actually worked.
XFCE as per gnome had the same installation issues.
KDE is what ships with BT on (ubuntu 8.10 platform) and yes that works fine!

Ultimately here's my theory:


[LIST=1]
[*]I like your theory and you could be right but I'm not sure it is a WM problem...I believe it is more to do with the kernels??
[*]Basically in the BT kernel 2.6.30.9 ('buntu 8.10) there is something that works with my graphics card that is not included in the later 10.04 ' buntu releases.
[*]Unfortunately the only way to test this fully I suppose is to try and install Ubuntu 8.10 on my system and see if it works without the issues I stated above. To be honest though I'm really using up my capped monthly net usage LOL and it wouldn't be much incentive as I know any updates to 9.10 onward would probably break the system again =(
[/LIST]

I think we'd both really like to hear from the "people who know" like the devs or something? 
The solution, presuming my hypothesis is correct about kernels would maybe be a patch or something for kernels newer than 2.6.30.9 onward that could fix the boot issues with these older NVIDIA cards...

I don't think I'll hold my breath though as you're the only guy to show interest so far! For what it's worth I appreciate it and the support you gave me all the same :wink:

---

### Post by 4Orbs on 2010-06-23
Suggest trying Xubuntu 9.10 instead of 10.04 because the boot manager (or whatever the correct term is) was switched to Plymouth for the latest version and has not been completely debugged. If 9.10 works for you, then my guess would be that Plymouth is to blame for your problem when trying to use 10.04. However, I could be completely wrong.

EDTI: The 32-bit version would be the better choice, IMHO.

---

### Post by rollin on 2010-06-24
Hi 4Orbs, I had a look around on Google and I think you have a good suggestion thanks! 

I was thinking it through and found that Lucid uses Plymouth and also the new Nvidia proprietory driver 190.53. However I can rule out the driver 190.53 because when I checked on Nvidia both the 64bit and 32bit drivers ([http://www.nvidia.com/object/linux_display_amd64_190.53.html](http://www.nvidia.com/object/linux_display_amd64_190.53.html) and [http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)) have full backwards capability...

Which leaves your theory of Plymouth replacing Usplash. So far I can only seem to get Intrepid working (the base platform for Backtrack 4) so I think I should start there and "work up".

Thanks for the help, I'll update the thread with my progress shortly :-)

---

### Post by 4Orbs on 2010-06-24
The nvidia driver doesn't come into play until after you are able to log into Xubuntu and activate that driver. Prior to activating the nvidia driver, you are automatically using the nouveau open source driver (which is also new to Xubuntu in Lucid). Ubuntu versions before 10.04 used the vesa open source driver... which leads me to believe that the nouveau driver might also be the reason you can't boot into the system.

---

### Post by rollin on 2010-06-24
That's some great info 4Orbs!
I wasn't aware that the open source driver had changed post 9.10, I was just pointing at the kernels or distros as a whole... 
Great, I feel this is getting close to a solution :p
OK I'll update in 24hrs when I've had a chance to get the 9.10 iso, I'll use the 32bit ubuntu version to try and keep things as mainline as possible.
Thanks again.

---

### Post by rollin on 2010-06-25
Wow! 4Orbs is my new hero =D>
Your info on the change from vesa to nouveau from 10.04 definetly saved the day and saved me having to work up from 8.10 to try and identify issues. 

So there you go. 9.10 ubuntu 32bit with the vesa driver loaded perfectly into the live cd. Installation worked fine with no crashes or bugs. No issues in the loading the system and it's working suprisingly quick having loaded the correct nvidia driver for my card.

I'll file a bug in 24hrs to let them know the model of graphics card and the issue. Either way its working now. Hopefully they can integrate some changes to enable the 10.04 upgrade with an option about the driver update. 

Thanks a lot to everyone for the help and support. If you want me to put the link for launchpad bug here, let me know on this thread...

---

### Post by rollin on 2010-06-25
> **ghdfans2010 said:**
> Thanks for your sharing! I have learnt so  much from your post!

Thats what it's all about I guess!! I'm glad it was useful.

Having thought about it for a while... I guess I should really write up the process properly at  the end of the post to say what I did, the model details, launchpad link  and stuff like that to try and finish it up nicely... 

Probably over next  24hrs though. Just a few security updates to download LOL :biggrin:

---

### Post by rollin on 2010-06-27
Last one!
Launchpad link for bug here: [https://bugs.launchpad.net/ubuntu/+bug/599019](https://bugs.launchpad.net/ubuntu/+bug/599019)
Seems to provide the process I hope accurately enough without a need to re-type on the thread. Thanks again for the help and support.

---

