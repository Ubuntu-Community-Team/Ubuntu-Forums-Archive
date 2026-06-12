---
title: "Ubuntu and Windows 7 two different HDD"
date: 2009-10-15
forum: General Help
---

### Post by rocktofakie3 on 2009-10-15
have 2 hard drives ones 232 gb and others 160 i just installed the 160 gb that was my brothers so today after school i thought id try ubuntu but when i logged into windows i tired to open the 160gb HDD cause i wanted to use as a drive that i can put windows files on. and still have like 20gb for linux but i didnt part. it that way i just wasnt thinking but 

now i want to delete ubuntu and reformat the drive so it can be read and writen on in windows 7 

So i put in the Ubunut disk and booted from live. and tired to reformat the drive and when i restarted the computer and i got 

this 

GRUB Loading something 

Error 22 

So i tired what people said insert the windows disk (they said XP) but i tired with Win7 as thats what i have installed. 

They then said open CMD and i typed fixmbr it didnt recongize it. As the Drive was X: cause thats where the disk was. 

they i tired fixboot. 

still didnt work. 

SO 
I just reinstalled Ubuntu and GRub works so i need you guys to help me uninstall ubuntu. and make my computer working again 
My question how do i uninstall ubuntu and make grub gone 

PLease help its my parents computer.

If i can figure out how to remove it. I will and reinstall on using the .exe  

Its the disk verison

---

### Post by akshar_patel_47 on 2009-10-15
I got a similar problem. The solution is simple.

keep the harddisk you want to install windows 7 on and remove the other from the computer.

this way there won't be any conflicts and windows will allow you to install itself.

After that you can attach the other harddisk and install ubuntu in it.

I hope this helps.

---

### Post by rocktofakie3 on 2009-10-15
Well i have windows 7 installed on the 232gb hard drive.

but i want to uninstall ubuntu from the 160gb hard drive and make it useable as a storage hard drive in windows. but when i deleted or reformated from the live disk. 

1. all the files where still there.
2. then the grub or what ever gives me error 22.

Any way to reformat the 160gb HDD

---

### Post by whitethorn on 2009-10-15
You have two problems.

1) Erasing ubuntu
2) Reinstalling windows boot loader.

I would start with #2.  As someone mentioned do the fixmbr thingy,  a couple things to make sure of.  Look in your bios and check from which drive your pc is booting.  Change it to the drive with Windows 7.

1) When you boot up the live cd, open gparted, delete the partitions on your 160 gb drive.  Then repartition either to ntfs or fat32.  I'd first get the fixmbr thingy running b4 deleting ubuntu because that way you can still boot windows up or linux...

---

### Post by rocktofakie3 on 2009-10-16
So you say to insert my windows 7 disk open the command and type fixmbr

but when i do that it says not recognized. 

its like X:\ something > i type fixmbr

i get 
'fixmbr' is not recognized as an internal or external command,
operable program or batch file.

so i typed c:\  and it went to 

C:\
Same thing.


then restart? take out windows 7 disk and put Linux (refering to Ubuntu to Linux)
 liveCD boot. 

head to Gparted and delete?

---

### Post by whitethorn on 2009-10-16
> **rocktofakie3 said:**
> So you say to insert my windows 7 disk open the command and type fixmbr

but when i do that it says not recognized. 

its like X:\ something > i type fixmbr

i get 
'fixmbr' is not recognized as an internal or external command,
operable program or batch file.

so i typed c:\  and it went to 

C:\
Same thing.


then restart? take out windows 7 disk and put Linux (refering to Ubuntu to Linux)
 liveCD boot. 

head to Gparted and delete?



A quick google search turned this up.  Give it a try see if it helps restore the mbr.

[http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html](http://www.sevenforums.com/installation-setup/18466-how-do-i-replace-orginal-mbr-win-7-a.html)


Be sure to read the whole thing through, there's a pretty important tip at the end of the article.  Something to do with n59 and n60...

---

### Post by sendblink23 on 2009-10-17
Just simply put up your Ubuntu Live CD, put the hard drive as you normally have it.

This is to Re Gain MBR

Go into Terminal and run this:

sudo lilo -M /dev/sda mbr


That should recover back the original Windows Boot.



Another idea just FORMAT EVERYTHING & start over CLEAN (obviously back up every necessary files from windows etc... )   STart over... and only Run the computer with 1 Hard Drive, the one you are going to install Windows ..  after done with it...    Remove that Hard Drive and connect only the other Hard Drive in which you plan on installing Ubuntu...   and when done... that's it

All you do when starting your computer use the BOOT OPTION (ESC / F12 / etc...) and select which hard drive to boot from... in other words it'll be 2 OS's to choose from

---

### Post by rocktofakie3 on 2009-10-19
Well reinstalling windows 7 is not an option as i have to much stuff on there.

and my 500gb External HDD is for Mac OS X's  TIme machine and files

So you said 
> 
Just simply put up your Ubuntu Live CD, put the hard drive as you normally have it.

Put the Ubuntu Disk in my first drive and change the primary boot seq. from HDD to Drive 1?




[COLOR="Red"][B]SUDO LILO -M /dev/sda mbr didnt work.

nor did the website that was post sevenforums. Ubuntu is making me very angry and not wanting to use it ever again.

Now im geting 
GRUB loading, please wait...
Error 17[/B][/COLOR]


**[COLOR="Red"]ubuntu its a horrible OS and you guys are no help.[/COLOR]**


When i get this horrible OS fixed im going to stick with my mac. its better then this P.O.S

---

### Post by mechro on 2009-10-19
Your posts are very confusing but...

Can you boot into Windows on the 232GB drive? Can you not use the tools available in Windows to repair the 160GB drive? If you're not sure what tools are available in Windows you could ask Microsoft or try one of the Windows fora.

---

### Post by rocktofakie3 on 2009-10-19
> **mechro said:**
> Your posts are very confusing but...

Can you boot into Windows on the 232GB drive? Can you not use the tools available in Windows to repair the 160GB drive? If you're not sure what tools are available in Windows you could ask Microsoft or try one of the Windows fora.

heres the deal.


I would like to uninstall ubuntu from the 160gb hard drive and make it so i never see GRUB. and it boots in to windows by its self. like a OEM computer. 

but when i reformat the 160gb HDD to remove ubuntu it removes it but then when i reboot i get 

GRUB loading please wait
Error 21 22 or 17

I have tired the sudo command, the CMD windows command. nothing fixes grub.

I want my 232gb HDD left alone nothing touched.

---

### Post by mechro on 2009-10-19
So you want to install Windows on the 160GB drive?

If you're saying Windows was installed on this drive prior to your experiments, how did you boot into Windows? From your parent's computer or your brother's computer?

---

### Post by kpholmes on 2009-10-19
> **rocktofakie3 said:**
> Well reinstalling windows 7 is not an option as i have to much stuff on there.

and my 500gb External HDD is for Mac OS X's  TIme machine and files

So you said 


Put the Ubuntu Disk in my first drive and change the primary boot seq. from HDD to Drive 1?




[COLOR="Red"][B]SUDO LILO -M /dev/sda mbr didnt work.

nor did the website that was post sevenforums. Ubuntu is making me very angry and not wanting to use it ever again.

Now im geting 
GRUB loading, please wait...
Error 17[/B][/COLOR]


**[COLOR="Red"]ubuntu its a horrible OS and you guys are no help.[/COLOR]**


When i get this horrible OS fixed im going to stick with my mac. its better then this P.O.S

first of all, windows 7 is not even released yet so your working with an OS thats not fully "completed" at least your version isnt yet, probably a beta or rc so dont blame it on ubuntu or the people here trying to help you fix the mess you created.

first you should of loaded into windows before deleting the ubuntu partition, fix the mbr, restart the computer, see if you got the result you wanted, then deleted the ubuntu partition. 

now from what you have posted, put the windows cd in, put any windows cd in and just fix the mbr and thats it. 

OR

reinstall ubuntu on the free space that use to be where the old ubuntu was so grub is installed correctly, then boot into windows and try to fix it from there. 

but dont push fault onto this operating system because your other os is not working, or blame the people trying to help you.

im sure os x is a good place for you, not a lot of options and choices for you to mess things up.

---

### Post by QIII on 2009-10-19
Visually label your drives "Windows" and "POS".

Unplug "POS".

Attempt to boot to Windows.  If you cannot, use fixmbr as described.

When you are able to boot to Windows, shut down, unplug the Windows disk and install the "POS" disk.  

Restart your computer with the "POS" LiveCD in the CD drive.  Use the gparted utility to completely delete all the partitions on the "POS" disk.  Reformat the entire drive as NTFS.

Unplug the "POS" drive and plug the Windows drive back in.  Make sure a second time that you can boot to Windows.

Now you are back to OEM.

Install the "POS" disk (which is now a blank NTFS drive) and use it for data.

By the way.  A motorcyle with a right hand clutch and left hand throttle is not a "POS" just because you don't know how to drive it.  A lot of Indian riders loved it.  

You learned that "computer = Windows or Mac" with the throttle on the right.  Left throttle is different, but not "POS".

---

### Post by mechro on 2009-10-19
... splurts coffee...

---

### Post by rocktofakie3 on 2009-10-19
Ok let me REtell my story for the 10th time. Im sorry

I had one hard drive installed the 232gb Windows 7 one. My friend said that he gave me the final verison of win 7. 7600
My brother let me add his hard drive (160gb) to my parents computer (i use it to)
so i thought i would try ubuntu on the 160gb hard drive. but i want to uninstall ubuntu and use the 160gb hard drive as a extended hard drive from my other one. so i can add and remove WINDOWS files to it. (KInda like a external drive thats internal.)
but when i go into ubuntu using live cd i go to Gpart and remove the ubuntu from the 160gb (thats what i want)
but then when i go to restart my computer and have it boot into windows 7 like a normal oem computer.

i have tired the forum post to fix the boot manger etc. nothing works i just get grub loading please wait error 17 21 or 22.

---

### Post by kpholmes on 2009-10-19
> **mechro said:**
> ... splurts coffee...

haha great thread huh!

by the way, kinda off topic, is your icon a devil tux or like a bsd-tux?

---

### Post by mechro on 2009-10-19
> **rocktofakie3 said:**
> Ok let me REtell my story for the 10th time. Im sorry

I had one hard drive installed the 232gb Windows 7 one. My friend said that he gave me the final verison of win 7. 7600
My brother let me add his hard drive (160gb) to my parents computer (i use it to)
so i thought i would try ubuntu on the 160gb hard drive. but i want to uninstall ubuntu and use the 160gb hard drive as a extended hard drive from my other one. so i can add and remove WINDOWS files to it. (KInda like a external drive thats internal.)
but when i go into ubuntu using live cd i go to Gpart and remove the ubuntu from the 160gb (thats what i want)
but then when i go to restart my computer and have it boot into windows 7 like a normal oem computer.

i have tired the forum post to fix the boot manger etc. nothing works i just get grub loading please wait error 17 21 or 22.

Sounds to me like you've installed Ubuntu on the 232GB drive. You can't just uninstall it and magically get Windows back.

A solution would be to re-install Windows to the 232GB drive and get your parent's files and settings from their back-ups.

---

### Post by QIII on 2009-10-19
Use the "POS" LiveCD, go to the terminal and post the results of 

```
fdisk -l
```That is a small "ell", not a one.

---

### Post by rocktofakie3 on 2009-10-19
> **QIII said:**
> Visually label your drives "Windows" and "POS".

Unplug "POS".

Attempt to boot to Windows.  If you cannot, use fixmbr as described.

When you are able to boot to Windows, shut down, unplug the Windows disk and install the "POS" disk.  

Restart your computer with the "POS" LiveCD in the CD drive.  Use the gparted utility to completely delete all the partitions on the "POS" disk.  Reformat the entire drive as NTFS.

Unplug the "POS" drive and plug the Windows drive back in.  Make sure a second time that you can boot to Windows.

Now you are back to OEM.

Install the "POS" disk (which is now a blank NTFS drive) and use it for data.

By the way.  A motorcyle with a right hand clutch and left hand throttle is not a "POS" just because you don't know how to drive it.  A lot of Indian riders loved it.  

You learned that "computer = Windows or Mac" with the throttle on the right.  Left throttle is different, but not "POS".

Ok i will try this in the morning or after school when i have more time.

---

### Post by mechro on 2009-10-19
> **kpholmes said:**
> 
by the way, kinda off topic, is your icon a devil tux or like a bsd-tux?

Plain old devil... which doesn't suit me really... cos I'm very patient and agreeable. :D

---

### Post by QIII on 2009-10-19
If, as mechro has suggested, you installed Ubuntu over your Windows installation, you will have to attempt to recover your data.

We can help you salvage what is salvageable.

Just as an aside:

While dating my mother, my dad (who had learned to ride on Harleys) decided he would take my mom out for a spin on his uncle's brand new Indian.  Unfortunately, he missed the important step of asking his uncle first.  He ended up dumping it in a ditch.  To this day he says it was because my mom leaned the wrong way on a corner.  The truth, of course, is that he was used to the right hand throttle (FOOT clutch and suicide shift in those days, for cryin' out loud!) on his Harleys and unfamiliar with the left throttle Indian.

Moral:  Before you go roaring off to impress your best gal by dual booting your uncle's brand new Indian on a dirt road in Montana without his permission, it might be worth taking the time to ask a few questions and learn to drive it.

---

### Post by louieb on 2009-10-20
Need exact info about your setup. 
Use the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280") and put the results.txt file in your next post.

---

### Post by oldfred on 2009-10-20
Most of this also applies to win7

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista installation CD, you can download a Vista or Win7 Recovery Disc at the following link:
Windows Vista Recovery Disc [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Vista will not repair XP(they create the boot sectors differently)

How to restore the Windows Vista bootloader
To restore the Windows Vista bootloader, you must first boot off your Windows Vista installation DVD.
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on “Repair your computer.”

On the next page, if it finds your Windows Vista installation, make sure it is UNSELECTED before clicking next.
Then click on “Command prompt”. From there, type in the folowing:
bootrec.exe /fixboot  #updates PBR partition boot
bootrec.exe /fixmbr   #updates MBR master boot record 
Now close the two windows and click “Restart.”

---

### Post by rocktofakie3 on 2009-10-20
> **mechro said:**
> Sounds to me like you've installed Ubuntu on the 232GB drive. You can't just uninstall it and magically get Windows back.

A solution would be to re-install Windows to the 232GB drive and get your parent's files and settings from their back-ups.


LOL no i have ubuntu installed only on the 160gb. becuase there are not ubuntu files on the 232gb and to the 232 size hasnt changed from the 90 gbs left for like 2 weeks,

---

### Post by mechro on 2009-10-20
> **rocktofakie3 said:**
> LOL no i have ubuntu installed only on the 160gb. becuase there are not ubuntu files on the 232gb and to the 232 size hasnt changed from the 90 gbs left for like 2 weeks,

I'm sorry but being an ignorant Brit I'm pretty rusty on foreign languages. O level French and German doesn't quite cut the mustard these days.

Perhaps it would make it easier if you could post in your native language and we'll see if we can get an online translation.

Good Luck.

---

### Post by rocktofakie3 on 2009-10-21
WHAT! I American and i speak english. How am i not speaking my native langauge.

---

