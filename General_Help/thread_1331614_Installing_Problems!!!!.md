---
title: "Installing Problems!!!!"
date: 2009-11-19
forum: General Help
---

### Post by dr.faizanali on 2009-11-19
Hello!
Love to join the portal for life, the portal of man, Ubuntu!
I just downloaded the Ubuntu from your site after hearing a lot from my friends here in Pakistan, but i am facing problem of installing XP and Ubuntu 9 side by side. I searched a lot of internet, but all in vain. Now i m posting here to search some good search. Also most of the internet given dual boots are not working. Now there is my query!
My system is intel Pentium 4
3 G Hz, 320GB Hard disk (I backup all my 70GB data from my drive G: for Ubuntu)
1GB RAM, and usual other system configuration of Pentium 4.
The problem is that, i want to install Ubuntu side by side with windows xp. I downloaded Ubuntu, extracted it to drive G:, and now what! whenever i run wubi.exe, it makes copies to drive C:, Now that is what i don't want!
Hope u understand what i want. anyone, please help me out as i am get rid of windows system, but as you know its difficult to leave windows completely. it will take time..... It will be kind of you!
Anxiously waiting for reply.....

With regards! 
Dr. Faizan (Pakistan):KS

---

### Post by DJonsson2008 on 2009-11-19
Ubuntu will fit easily on a 20-30gig drive. What I found the sanest
way to do this is take an old or buy an old 30-80gig drive and
install Ubuntu on a separate HD.  Then use the Linux ntfs-config 
utility to mount and see your Windows drive. 

That would be my suggestion, before taking any risk with your 320 gig 
drive. Personally I've not had good luck with dual boot installations,
and in the end the small price for an extra drive was the best way to
go.

---

### Post by ibuclaw on 2009-11-19
> **dr.faizanali said:**
> Hello!
Love to join the portal for life, the portal of man, Ubuntu!
I just downloaded the Ubuntu from your site after hearing a lot from my friends here in Pakistan, but i am facing problem of installing XP and Ubuntu 9 side by side. I searched a lot of internet, but all in vain. Now i m posting here to search some good search. Also most of the internet given dual boots are not working. Now there is my query!
My system is intel Pentium 4
3 G Hz, 320GB Hard disk (I backup all my 70GB data from my drive G: for Ubuntu)
1GB RAM, and usual other system configuration of Pentium 4.
The problem is that, i want to install Ubuntu side by side with windows xp. I downloaded Ubuntu, extracted it to drive G:, and now what! whenever i run wubi.exe, it makes copies to drive C:, Now that is what i don't want!
Hope u understand what i want. anyone, please help me out as i am get rid of windows system, but as you know its difficult to leave windows completely. it will take time..... It will be kind of you!
Anxiously waiting for reply.....

With regards! 
Dr. Faizan (Pakistan):KS

You downloaded the iso image?

Are you wanting to use Wubi? or Install Ubuntu?

If using Wubi, I'm not sure if you can direct which partition you want the partition image to be in.

---

### Post by Xog on 2009-11-19
> please help me out as i am get rid of windows system

To install ubuntu over windows I recommend burning the .iso file to a DVD. Make sure you follow the directions here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Also make sure you check the MD5 Hash after you download the .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Scroll down to 
"MD5SUM on Windows"

After the MD5SUM is certain it is a match, burn the .iso file to a DVD or CD from the aforementioned [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by ingeon on 2009-11-19
> **DJonsson2008 said:**
> Ubuntu will fit easily on a 20-30gig drive. What I found the sanest
way to do this is take an old or buy an old 30-80gig drive and
install Ubuntu on a separate HD.  Then use the Linux ntfs-config 
utility to mount and see your Windows drive. 

That would be my suggestion, before taking any risk with your 320 gig 
drive. Personally I've not had good luck with dual boot installations,
and in the end the small price for an extra drive was the best way to
go.

So can i use my ubuntu as main drive and configure grub
to add the windows drive boot link for startup manager to use?

And if yes how

---

### Post by Xog on 2009-11-19
when you're in the process of installing ubuntu, it will ask you if you want to partition a drive

---

### Post by gorillalovesac on 2009-11-19
I think the best way that you could do is install first the UBUNTU and see if you like that OS. then eventually, if you have friends who are programmers you can ask help form them by installing the Windows XP and Ubuntu at the same time.

---

### Post by dr.faizanali on 2009-11-20
> **tinivole said:**
> You downloaded the iso image?

Are you wanting to use Wubi? or Install Ubuntu?

If using Wubi, I'm not sure if you can direct which partition you want the partition image to be in.

Sir i have downloaded Ubuntu from [www.ubuntu.com](www.ubuntu.com)
it was 9.10 version. when i burned the image file, then in the burnt files, i found Wubi.exe.....
I dont know if it is somewhat differnt OS. I think i burnt the image files of Ubuntu to my hard driver partition G:/
may be that was the problem that whenevr i start wubi.exe from G:/Ubuntu, it start extracting files to C:/ 
Now i want that XP and Ubuntu run side by side. That is why i extracted it not to cd, but to my hard drive. also, it is not giving the autorun!

---

### Post by byStanderone on 2009-11-20
hi..
haven't tried installing xp with ubuntu lately, cause i'm comfortable with ubuntu right now. tho i did it in the past with hardy heron, the secret is to install xp first on one partition and did the ubuntu hardy install later on another partition...ubuntu is considerate enough not to erase xp's mbr.

installing ubuntu first and xp afterwards...xp will erase ubuntu's mbr, and unless you are fine with mbr restoration, i suggest you install xp first.

---

### Post by jmszr on 2009-11-20
dr.faizanali,

Here are a couple of links to Xp/Ubuntu dual-boot guides: [http://www.wikihow.com/Dual-Boot-Windows-XP-and-Ubuntu](http://www.wikihow.com/Dual-Boot-Windows-XP-and-Ubuntu) and: [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
 
Hope they are of help.

---

### Post by P4man on 2009-11-20
> **dr.faizanali said:**
> Sir i have downloaded Ubuntu from [www.ubuntu.com](www.ubuntu.com)
it was 9.10 version. when i burned the image file, then in the burnt files, i found Wubi.exe.....
I dont know if it is somewhat differnt OS. I think i burnt the image files of Ubuntu to my hard driver partition G:/
may be that was the problem that whenevr i start wubi.exe from G:/Ubuntu, it start extracting files to C:/ 
Now i want that XP and Ubuntu run side by side. That is why i extracted it not to cd, but to my hard drive. also, it is not giving the autorun!

You should boot from the cd to do  a side by side install.
Wubi is a way to install ubuntu "inside" windows, on the windows drive/partition. Just reboot your computer, press whatever key to make the machine boot from cd, then test ubuntu first by selecting the option " try ubuntu without changing to your drive". If it works fine, there is a Istall icon on the desktop which will guide you through a side by side install.

Good luck!

---

