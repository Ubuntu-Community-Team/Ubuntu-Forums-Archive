---
title: "NTLDR is missing"
date: 2010-02-01
forum: General Help
---

### Post by boosterjet on 2010-02-01
I have two separate hard drives. Windows XP on one and Ubuntu on the other. All working perfectly. I have Windows set as the default load. Today I started up Windows earlier, no problems, restarted and booted Ubuntu which I used and left for about an hour. Came back and went to restart Windows got the message "NTLDR is missing" Pres ctl-alt-delete to continue. This returns me to the grub boot menu and of course the process repeats. HELP, I would like to get my windows back!!

---

### Post by zeroseven0183 on 2010-02-01
You probably should be asking this to a Windows forum. This is a Linux community... (and that's actually a good thing because either way, you're gonna get help).

Here's how you fix that crappy Windows problem. Insert your Windows XP CD, go to Recovery Console and copy the NTLDR file to the root directory (C:\, in most cases/by default). If you want more information, go to: [http://support.microsoft.com/kb/318728]("http://support.microsoft.com/kb/318728")

I just wish no one kills me for posting a Microsoft link here.

Hope that helps!

---

### Post by martysweeney on 2010-02-01
[COLOR=Red][SIZE=6]AHH!! MICROSOFT PROGRAMING.. THE DEVIL HAS ARRIVED... :o[/SIZE][/COLOR]  [SIZE=6][COLOR=Cyan]ONLY KIDDING.. LOL[/COLOR][/SIZE]

---

### Post by zeroseven0183 on 2010-02-01
LOL martysweeney

You got me there!

Hope Mr. boosterjet will get tired of Windows and leave it for good.
But anyway, we're always here to help.

---

### Post by boosterjet on 2010-02-01
Yeah, I am in the process of moving completely over but still have a 160GB hard drive that is now unuseable and some info I would like to recover. I have all my important stuff backed up on an external hard drive but I an yet to work out how to get Ubuntu to open them properly formatted, especially my saved emails from outlook. My Windows XP is updated to SP3 and my CD is a purchased copy of XP Home Edition, the recovery tool does not work, the link above is for Windows 2000.

---

### Post by ram2500 on 2010-02-01
If the Recovery Console does not work properly as it should, I would boot from an Ubuntu CD, access your files (you can mount NTFS (Windows) drives in newer versions) and copy your files over to a flash drive or external drive. Then, you can reinstall Windows (it's always a good idea to reinstall Windows, or ANY operating system for that matter :))

---

### Post by boosterjet on 2010-02-01
I think the trouble is my Windows CD is a purchased upgrade that upgraded me from ME to XP. Does not seem to have a repair facility.

---

### Post by martysweeney on 2010-02-01
did you try to google the file and download it?

i found a link that may help you out ..

[http://en.kioskea.net/faq/sujet-3002-ntldr-boot-ini-ntdetect-missing-no-windows-cd](http://en.kioskea.net/faq/sujet-3002-ntldr-boot-ini-ntdetect-missing-no-windows-cd)

---

### Post by zeroseven0183 on 2010-02-02
> **boosterjet said:**
> the link above is for Windows 2000.

Yup, but the same procedure applies to Windows XP. Insert the Windows CD (when in Ubuntu) and see if you can find NTLDR and ntdetect.com in the i386 folder. Copy those files to an external USB drive then to the Windows root directory.

I haven't use Evolution to open Outlook e-mails. There's a way to import your Outlook stuffs to Linux. Try this one: [http://www.cyberciti.biz/tips/moving-outlook-email-data-to-linux-evolution-mail-client.html](http://www.cyberciti.biz/tips/moving-outlook-email-data-to-linux-evolution-mail-client.html)


Note: This thread has turned to a Windows support thread.
Helloooo Microsoft! Where are you? ](*,)

---

### Post by boosterjet on 2010-02-02
I think I have made a major BooBoo. Earlier when I was exploring options on Ubuntu I had a look at various sites and options and found 164 files on places. This was files obviously transferred on Ubuntu loading. Opened and it was all my operating files from Windows. As you all say (?) who wants window files on Linux? Tried to open a lot of my usual Win files, Ubuntu did not want to know. So I Deleted the lot. Obviously a important boot file has diappeared. Give Windows some credit, they would not let me delete an important file without warning, so as far as I'm concerned this is a Ubuntu problem. What now?

---

### Post by zeroseven0183 on 2010-02-02
You still need to copy the two files to your Windows drive C.

---

### Post by ManyBeers on 2010-02-02
> **boosterjet said:**
> I think I have made a major BooBoo. Earlier when I was exploring options on Ubuntu I had a look at various sites and options and found 164 files on places. This was files obviously transferred on Ubuntu loading. Opened and it was all my operating files from Windows. As you all say (?) who wants window files on Linux? Tried to open a lot of my usual Win files, Ubuntu did not want to know. So I Deleted the lot. Obviously a important boot file has diappeared. Give Windows some credit, they would not let me delete an important file without warning, so as far as I'm concerned this is a Ubuntu problem. What now?

Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy 
ntdetect.com and ntldr to root of C:\. 
The files in here are up to date. I guess you can write a boot.ini file (also placed in root of C:\) with a text editor in Ubuntu.
Not sure about that.
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=Optin 
```
If XP pro I assume place "Professional" in place of Home Edition. Though I don't think the words in quote matter . They can be anything you want.
Worth a try. 
I was reading an XP forum after making this post and according to responses in a thread there a boot.ini is not strictly required to boot Windows. So you can try to boot without creating a boot.ini.

---

### Post by Silvertones on 2010-02-02
[Help and Support]("http://support.microsoft.com/search/")

---

### Post by boosterjet on 2010-02-02
Sorry for the delay in answering. Morning here. Looks like I have really blown it. May have to get a techie in with a boot disk. My installation CD is an upgrade disc, so I cannot re-install Windows from it as it does not recognise my current Windows program, I can access Recovery mode on it but all I get is the C:\- prompt which either does not recognise any of the above commands or else tells me access is denied. Ran the 'Fixboot" command - no effect. Also I ran update-grub and now all I have is my Ubuntu, nothing else is found or recognised. What happens if I reinstall Ubuntu will it still keep my current settings or will it just copy the CD?  I had a lot of problems getting the system to even recognise windows in the grub menu on install. Again thanks to Kansasnoob, took a lot of trouble straightening me out. I just wonder if a re-install would reimport all the files I stupidly erased. Only a thought! I think the boot files must have been exported across and their gone.

---

### Post by oldfred on 2010-02-02
Microsoft XP boot disk floppy
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)

How to fix XP when the boot files are missing - Ubuntu Forums
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
seems to be same link?
[http://ubuntuforums.org/showthread.php?p=5726832](http://ubuntuforums.org/showthread.php?p=5726832)

---

### Post by charonred on 2010-02-02
Boosterjet, don't panic over the NTLDR missing, this happens all the time in Windows (and another reason I finally dumped XP), and is a relatively easy fix.

You can do as ManyBeers sugested go into Ubuntu, nav to your Windows disc and copy the files as directed
> Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

or from Windows CD
> Windows XP users

   1. Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter, which in this case is "e." This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.


---

### Post by boosterjet on 2010-02-02
Thanks all, finally managed to get the NTLDR, NTDetect.com and boot ini back into the 160GB File system. Grub now recognises windows is there but on the boot memu it was "Windows XP Home Edition (on /dev/sda1). Now shows Windows NT/2000/XP (on /dev/sda1) ??. Tried to boot and now tells me I need to reload Root\system32\hal.dll. All getting too hard. This is all being worked through Ubuntu  and I really intended to move away from Windows but I still have some info I would like to extract. At the moment Windows is sitting on a 160GB drive that is unuseable and I did plan to load Ubuntu there as well and keep this drive as a back-up. However I have my techie coming so I'll just wait for his help.

---

### Post by zeroseven0183 on 2010-02-02
Good to hear that you're done with NTLDR. For the other problem's solution, you can check the procedure [here]("http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm"). But then again, you need a working Windows XP CD.

By the way, you can always edit how Windows is shown in Grub.

---

### Post by charonred on 2010-02-02
If you have a newish PC, another way of dealing with multiple operating systems is to install them on separate hard drives, and then use F12 for boot options, and then select the drive you want to boot. 

And to install a new OS to a separate drive, I physically disconnect the power lead for all drives except the one I'm installing the OS to, and reconnect it once all is done - this saves all the hassle of figuring out which drive is which when installing different OS's, and keeps GRUB just for Ubuntu and the drive it's installed on.

[CENTER]----------------[/CENTER]

But as I use Ubuntu 99% of the time, my preferred method of using XP is to have a copy installed via VirtualBox - then XP just runs as a window inside Ubuntu ... no rebooting required - easy as :p  

A handy tip if using VirtualBox; once I have XP setup as I want it in VirtualBox, I then export the XP 'appliance' to my Ubuntu home folder, and if XP ever goes pear shaped (when doesn't it), it then only takes a few minutes to import a fresh XP appliance set up and running the way you like it - makes XP or other Windows OS's a breeze to install and use ...

---

### Post by boosterjet on 2010-02-03
My Techie is coming tomorrow AM. As you all can see I'm operating quite comfortably with Karmic. I just need to get some info and then Windows gets dumped. I"ll let you all know what his fix was - if any. It sounds like he may have to do a full re-install so that will loose all my info anyway. Fortunately I have all my really important stuff backed up on an external drive. Thanks all for your advice, learning more as I go along.

---

### Post by boosterjet on 2010-02-05
Techie been and gone. All my stupid fault in deleting the contents of the 160mb file system. Totally erased my Windows operating system. I thought those files were copies. Turns out they are the actual files required by windows and they had been moved not copied. Now 200 bucks and after a good two hours of updating later and reloading from back-up, system up and running but no ubuntu access. What happens when I re-install Ubuntu, will it over-write the existing OS back to 14 ? Currently running on 17. If it does I'm going to have a bit of updating to do there as well.
I think it a bit rough moving operating files out of Windows, makes the system totally dependent on Ubuntu. A system failure on Ubuntu could result in total loss of both systems.

---

### Post by charonred on 2010-02-05
Just re-read your original post; if you have 2 drives and Windows was on the first IDE or Sata, that's where Grub would have been placed by default when installing Ubuntu; as such when Windows was reinstalled, Grub would have been over-written. (this is one reason I disconnect power from all other drives when installing different OS's to separate drives - doing this ensures Grub goes on the same drive as the install, and I then use F12 to select the drive to boot).

Easiest way to check is use a Ubuntu Live Cd to boot the system as this will allow you to see both Linux and Windows drives/partitions if they exist.

So if your Ubuntu drive/partition is still there, then there are a few options;
[LIST=1]
[*]reinstall Grub to get your boot options back (you'll have to get advice on how to do that, as it's something I've not done).


[*]install Ubuntu again side-by-side with existing Ubuntu install - this will install a new GRUB, and allow system to boot Windows or either of the Ubuntu installs, and as such give you access to your Ubuntu files,docs,images etc. (when doing this, make sure to resize your partitions so the new one is of minimal size, this will then allow you to boot old Ubuntu and continue as normal, rather than having to update and reconfigure/customise new one).


[*]Using Live CD, copy/backup your Ubuntu Home folder (files,docs,images etc) to another drive, then reinstall Ubuntu over top of old one; when done simply copy your backed up Home folder back to your new install.
[/LIST]

easiest option is #2 (but I still recommend using Live CD to backup any Home folder ... just in case)

> I think it a bit rough moving operating files out of Windows, makes the system totally dependent on Ubuntu. A system failure on Ubuntu could result in total loss of both systems.Never heard of Ubuntu/Linux moving Windows System files before, sounds like you may have inadvertently accessed the Windows drive/partition when you deleted those files. Generally the loss of a Linux OS doesn't destroy a Windows system; it's more likely a Windows failure would result in loss of any other OS if they were installed as dual boot on the same drive.

.

---

### Post by boosterjet on 2010-02-07
Thanks folks for all your help. Fixed it. Delving around I came up with a Ubuntu Community Help Page "RecoveringUbuntuAfterInstallingWindows". Fixed it all. Happy Days !!

---

