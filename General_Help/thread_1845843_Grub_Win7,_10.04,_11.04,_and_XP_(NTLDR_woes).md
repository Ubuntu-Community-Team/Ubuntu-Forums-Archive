---
title: "Grub: Win7, 10.04, 11.04, and XP (NTLDR woes)"
date: 2011-09-17
forum: General Help
---

### Post by amhainen on 2011-09-17
[SOLVED]:

Okay, not too hard. All I had to do was the following from the windows CD:

expand d:\i386\hal.dl_ c:\windows\system32
copy d:\i386\ntldr c:\
copy d:\i386\ntdetect.com c:\
copy d:\i386\ntldr c:\windows\
copy d:\i386\ntdetect.com c:\windows\

Now, **sudo update-grub** will recognize the WinXP partition. From there, I booted into XP through the Win7 loader and used easybcd in XP to edit the legacy boot.ini from "Tools" menu to point to the root of the Windows partition (C:\ or whatever) and save it to c:\boot.ini and c:\windows\boot.ini. As you can see, I'm not sure where I need everything, so I have it there twice. My guess is that I only need NTLDR and ntdetect.com in the root and the boot.ini in c:\windows.

The cool part is now I can boot Windows 7 with the Win7 loader (and either leave on or off the win loader menu) just like a normal dual boot. I can boot XP from either the Win7 loader OR the automatically created grub menu entry.

I'm guessing there is a way to get Win7 to boot from it's own partition, but I didn't have any luck. So, I'll just use the loader entry and deal with it.


==========ORIGINAL POST==========


I have the following partitions on my main computer:

sda1=reserve
sda2=**Win7ProX64**
sda4=extended
sda5=**Ubuntu 10.04 X64**
sda6=swap
sda7=**Ubuntu 11.04**

I have the following partitions on my backup computer:

sda1=**WinXP**
sda2=**Ubuntu 10.04**
sda6=swap

The reason I have my backup computer is for some legacy equipment that only works with XP. I don't like carrying two computers around, so I want to add a small XP partition to my main computer.

The first shot in the dark I took was to make a clonezilla image of my backup computer's sda1. I then edited my main computer's partitions as follows:

sda1=reserve
sda2=**Win7ProX64**
*sda3=xp*
sda4=extended
sda5=**Ubuntu 10.04 X64**
sda6=swap
sda7=**Ubuntu 11.04**

The first thing I learned is that I needed to adjust some items in the disk image to move sda1 to sda3. Also, I made sure that the partition was 1GB larger. This worked well and I ran **sudo update-grub** and I actually got Grub to find and add Microsoft XP to the menu! (Note that this was the most success I had as I continue on)

I rebooted, selected the Microsoft XP menu item in Grub and hit enter. It went to just a blinking cursor. The first thing I read and tried was to [repair XP]("http://homepage.ntlworld.com/mosaddique/Repair%20dual%20or%20multiple%20boot%20after%20re-installing%20win98.html") and do fixmbr, fix boot, and bootcfg /rebuild. I rebooted and had the NTLDR missing error. I tried the next copy e:\i386\ntldr c:\ and then copy e:\i386\ntdetect.com c:\. Still nothing.

Next I decided to [restore grub using the live cd]("http://ubuntuforums.org/showthread.php?t=224351"), but I couldn't chroot into my sda7. It kept saying already mounted or /mnt/root busy.

Next, I tried using the newer [boot-repair CD]("http://sourceforge.net/projects/boot-repair-cd/files/"). This reloaded Grub and I tried to boot into my Win7 partition to see how it was holding up. It had an error and asked for its DVD and a repair. I did this and was able to boot Win7 using Grub. However, after that last Grub repair my XP menu went missing.

I decided to thrown in the towel and use clonezilla to restore my computer to how I started and take a different approach. So I used clonezilla to restore back to the first setup, used gparted to carve a 40GB partition, and then tried to install XP from a fresh cd install (no copying clonezilla image this time).

The XP install went as usual, and on reboot I had no grub. So then I went and did the whole boot-repair again. Then I went to my sda7 where my grub.cfg is and ran **sudo update-grub**. This found everything except my newly installed XP partition.

Next, I googled and found this post that [created a custom menu entry for Windows XP]("http://ubuntuforums.org/showthread.php?t=1633763"). IIRC, I made it in the /etc/grub.d/40_custom (I know it was the 40 file). I used **sudo blkid** to get the UUID of sda3 and set it up the same on the thread above and also it was very similar to my Win7 menu item. I ran a update-grub and it still didn't find XP, but in the GUI startup manager, there was indeed my custom entry. I rebooted this time, had all the menu items, chose XP and again found the NTLDR to be missing.

Now that I'm running in circles between XP repair, grub update, xp repair...I searched C:\ and found that NTLDR is still there! So is the other ntdetect.

I'm really confused on this. I'm sorry I need my crutch of Windows. Actually, I'm so used to Windows 7 playing relatively nicely in the dual boot setup I had going. XP has just been a pain today!

Right now, I have my fresh install of XP on sda3. Can someone please help me figure out how I can get XP to boot? I have my nice custom grub menu entry and everything. Thanks so much!

---

### Post by Blasphemist on 2011-09-17
I applaud you for getting this adventurous! As you might guess I've never done what you're trying but I can recommend this to help us have more information, though your description is very good. Use the boot-repair to just create the boot summary or give us the URL for what it has last created. One thing it will show is just what windows boot files are found on the xp partition.

---

### Post by amhainen on 2011-09-18
Hi Jim,

Thanks for suggestion. I will definitely include that summary. But I accidentally came up with solution in the meantime, although it's not very pretty.

I realized that my grub menu entry for windows has always been 'Windows 7 (loader)'. I never noticed the (loader) part. So I used easybcd in Windows 7 to add Windows XP to my Windows boot loader. It sort of worked!

So now I have a strange boot process. When I turn on my computer, I have grub with all the menu options for Ubuntu and such and then Windows 7 (loader). Then when I select Windows 7 (loader), I have the windows loader with two choices between Win7 and XP.

So now I met my overall goal of having Windows 7, Ubuntu variants, and a small Windows XP partition for legacy hardware. Unfortunately, this isn't an elegant solution.

Can someone please confirm if I'm in fact using the grub loader to load the windows loader? If so (that seems like really a not smart way to do what I need to do), is there a way to have grub handle the Windows partitions directly and not the Windows loader?

Thanks so much for the help! I'm really excited that I have working what I wanted, but now if I can iron out the wrinkle and have someone help me understand a better way, that'll be great.

---

### Post by amhainen on 2011-09-18
Also, I have done the custom menu entry for XP in /etc/grub.d/40_custom. However, I get the no NTLDR error. So I don't think it's as simple as just adding a custom entry for both Windows 7 and Windows XP.

I don't understand boot loaders fully, but I realize that I am leaving out a fundamental process/step when I made that custom menu entry. Thx.

---

### Post by Blasphemist on 2011-09-18
I think with the boot info script we can explain in more detail but it sounds like you are chainloading to the windows boot menu. And yes I believe you should be able to chainload to each MS OS directly instead.

---

### Post by amhainen on 2011-09-18
> **Blasphemist said:**
> I think with the boot info script we can explain in more detail but it sounds like you are chainloading to the windows boot menu. And yes I believe you should be able to chainload to each MS OS directly instead.

Ah! Okay...I definitely have chainloading +1 in there. Let me find that script and I'll post in a few minutes. Thanks!!

---

### Post by amhainen on 2011-09-18
> **Blasphemist said:**
> I think with the boot info script we can explain in more detail but it sounds like you are chainloading to the windows boot menu. And yes I believe you should be able to chainload to each MS OS directly instead.

First off, whoever created that paste website is a genius! I didn't have WiFi connection and I couldn't figure out why the boot summary wouldn't just generate a text file like I wanted. I was about to paste in my grub.cfg, but I tried it again and found it makes a link...much easier on thread length! So Kudos to whoever created that!

Jim: [Here's the link for the summary of my boot-repair]("http://paste.ubuntu.com/692434/"). Thanks again so much for the help!

(And thanks to whoever might be willing to take a look and help me with this!)

---

### Post by varunendra on 2011-09-18
amhainen,

My experience of XP+Xp+Linux (RH9) dates back to grub legacy days, and if I speak with that perspective, it is normal to chainload windows boot menu, then actual windows. Besides, if I remember correctly, ntldr needs to be in the partition where xp itself is. Accordingly, try copying ntldr to the xp partition, then rerun grub os prober: 
```
update grub
```
See if that helps grub detect your XP installation.

---

### Post by amhainen on 2011-09-18
> **varunendra said:**
> amhainen,

My experience of XP+Xp+Linux (RH9) dates back to grub legacy days, and if I speak with that perspective, it is normal to chainload windows boot menu, then actual windows. Besides, if I remember correctly, ntldr needs to be in the partition where xp itself is. Accordingly, try copying ntldr to the xp partition, then rerun grub os prober: 
```
update grub
```
See if that helps grub detect your XP installation.

Do I just copy NTLDR to the root of my XP partition? Can I do the same for my Windows 7 partition? I'd like to not have to go through the Windows 7 (loader).

---

### Post by varunendra on 2011-09-18
> **amhainen said:**
> Do I just copy NTLDR to the root of my XP partition? Can I do the same for my Windows 7 partition? I'd like to not have to go through the Windows 7 (loader).
Look, I am not sure whether or not it is going to work, so it is just kinda wild shot. Win7 boot files are already where they should be. So if you succeed to directly boot xp from grub, then removing its entry from bcd should automatically skip the win7 boot menu on next reboot.

But all of this starts with successful booting of XP directly from grub. So try the ntldr thing first, then if succeeded, we can try editing bcd to skip that menu.

---

### Post by Blasphemist on 2011-09-18
Here's my take. I think there are two tasks. One, get the right boot files into the xp partition. Two, have the right chainload statement in grub2 for 7 and xp. Each chainload needs to point to the appropriate partition for 7 and xp respectively. sda2 and sda3 in this case. Here is a sample from my /etc/grub.d/40_custom file. You can try entries there and they will just add to the bottom of you grub menu.
```

menuentry "Windows 7 on sda2" {
	set root=(hd0,2)
	chainloader +1
}
```
Note the use of hd0,2 for the equivalent of sda2.

As for getting the right files into the xp partition to make it bootable, I'm not the guy. I haven't done the research to know that but it sounds like you're on that anyway.

---

### Post by amhainen on 2011-09-18
Thank you both! I'm getting so close. I copied NTLDR and ntdetect.com files from the (winXPCD):\i386\ to the root of my XP partition (normally for other windows users C:\, but for me F:\).

Next, I added a bunch of custom entries to the /etc/grub.d/40_custom to try fishing for the right entry. Namely, I added the following with some variation:

```

menuentry "Windows XP" {
     set root=(hd0,3)
     chainloader +1

```

I saved the file and ran **sudo update-grub**. Next, a minor miracle happened: Grub recognized the NT/2000/XP partition! My hypothesis is that as Varunendra pointed out, the NTLDR grabbed grub's attention.

I rebooted and sure enough there was an official entry for NT/2000/XP. (I'll also note that the custom entries were there). I went to try the official NT/2000/XP entry and it was going okay, but then it said it was missing HAL.DLL. So I rebooted and tried the custom entries and no luck either.

I tried [restoring and expanding HAL.DL_ as described in this article]("http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm"). After that, I get the same HAL.DLL error message.

Can anyone else give me an idea about which files will be required? Thanks and now it's so close!

---

### Post by amhainen on 2011-09-18
Sorry for follow up reply...I don't have a boot.ini file in the root. Perhaps this is causing the error? I'm also not sure what this file would look like.

EDIT: Turns out this was a major problem...I made mine using EasyBCD and going to "Tools > Edit Legacy Entries" in XP and saving to c:\windows\boot.ini. Make sure that in the text of the file, the boot portion points to the right partition/location.

---

### Post by amhainen on 2011-09-18
Okay, not too hard. All I had to do was the following from the windows CD:

expand d:\i386\hal.dl_ c:\windows\system32
copy d:\i386\ntldr c:\
copy d:\i386\ntdetect.com c:\
copy d:\i386\ntldr c:\windows\
copy d:\i386\ntdetect.com c:\windows\

Now, sudo update-grub will recognize the WinXP partition. From there, I booted into XP through the Win7 loader and used easybcd in XP to edit the legacy boot.ini from "Tools" menu to point to the root of the Windows partition (C:\ or whatever) and save it to c:\boot.ini and c:\windows\boot.ini. As you can see, I'm not sure where I need everything, so I have it there twice. My guess is that I only need NTLDR and ntdetect.com in the root and the boot.ini in c:\windows.

The cool part is now I can boot Windows 7 with the Win7 loader (and either leave on or off the win loader menu) just like a normal dual boot. I can boot XP from either the Win7 loader OR the automatically created grub menu entry.

I'm guessing there is a way to get Win7 to boot from it's own partition, but I didn't have any luck. So, I'll just use the loader entry and deal with it.

---

### Post by varunendra on 2011-09-18
> **amhainen said:**
> 
expand d:\i386\hal.dl_ c:\windows\system32
copy d:\i386\ntldr c:\[B][COLOR=Blue]
copy d:\i386\ntdetect.com c:\[/COLOR]
[COLOR=Red]copy d:\i386\ntldr c:\windows\
copy d:\i386\ntdetect.com c:\windows\[/COLOR][/B]

Now, sudo update-grub will recognize the WinXP partition. From there, I booted into XP through the Win7 loader and used easybcd in XP to edit the legacy boot.ini from "Tools" menu to point to the root of the Windows partition (C:\ or whatever) and save it to c:\boot.ini and [COLOR=Red]**c:\windows\boot.ini**[/COLOR]. As you can see, I'm not sure where I need everything, so I have it there twice.
I am not sure about [COLOR=Blue]**ntdetect.com**[/COLOR], but the copies in /windows directory are definitely unnecessary. Also, as per the contents of your boot.ini file (which you first posted), it was already pointing to the correct location (**default=multi(0)disk(0)rdisk(0)partition(3)\windows** )

> **amhainen said:**
> My guess is that I only need NTLDR and [COLOR=Blue]**ntdetect**[/COLOR].com in the root and the [COLOR=Red]**boot.ini in c:\windows**[/COLOR].Again, what I can recall is that both boot.ini and ntdetect.com need to be in the root of the partition which has the boot flag (boot partition), while only ntldr needs to be in the root of xp partition. (for boot.ini, I am dead sure it has to be in the boot partition, not anywhere else.)

> **amhainen said:**
> The cool part is now I can boot Windows 7 with the Win7 loader (and either leave on or off the win loader menu) just like a normal dual boot. I can boot XP from either the Win7 loader OR the automatically created grub menu entry.

I'm guessing there is a way to get Win7 to boot from it's own partition, but I didn't have any luck. So, I'll just use the loader entry and deal with it. I am not sure I understand this part properly. I think you are already booting win7 from its own partition. If you mean to bypass the grub menu, you need to have win7 MBR on that drive, not grub on the MBR. Also, if you re-edit bcd (using bcdedit or easybcd) to remove XP's entry from it, you won't get two menus (1st grub, 2nd win7) before you boot into win 7. In its current state, this should be what is happening:-

[LIST=1]
[*]Grub is passing over the boot process to the windows boot loader (which it always does when you choose a windows entry in it, so it is normal).
[*]Since there are multiple entries in the windows (7) bootloader, it comes up with its own menu to choose one from.
[*]Windows boot menu comes in the way of booting 'ONLY' when there are multiple OS entries in it. Currently there IS that extra entry for XP. So once you remove it, the win7 boot menu will skip out of the way - booting win7 directly once you choose it from grub menu.
[/LIST]
 I think that was your original idea - to be able to boot everything directly from grub menu. Although you have already marked the thread as [solved], I think you haven't met your objective 100% yet. I'd love to see you do, even if I have to do experiments with this myself.

---

### Post by amhainen on 2011-09-19
Hi Varunendra,

I have everything as intended and better! I can boot Win7 (effectively) directly from Grub and also I can boot WinXP directly from Grub. With regards to Windows 7, it does boot the Win loader on SDA1, but I'm okay with that (that's how I've always had Win7 load).

Thanks again for all the help!

---

