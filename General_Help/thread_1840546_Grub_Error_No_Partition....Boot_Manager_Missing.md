---
title: "Grub Error: No Partition....Boot Manager Missing"
date: 2011-09-07
forum: General Help
---

### Post by Daniel R.T. Hartley on 2011-09-07
Hi Guys,

After running wubi through windows for a few weeks I started messing around with other operating systems through a usb, via linuxpendrive. During this time I partitioned my c drive and today I installed sn0w l1nux in the free space. Tonight after the graphics kept sticking I deleted, or what I thought formatted that partition (as I was deleting it through windows a dialogue indicated it was in use by another operating system, i.e. sn0w l1nux, and wubi runs through windows anyway).

On reboot, I expected the boot manager to return to the previous one before installing sn0w l1nux, where I could choose whether to boot into windows or ubuntu. Instead, I get a command type screen with the dialogue grub rescue, no such partition, boot manager missing etc. Sn0w l1nux had installed its boot boot manager, the ubuntu style one, and now (I think) its configuration was directing the cpu to a missing primary volume (?)- the sn0w l1nux partition. This is my best decription. 

How would I get out of this mess? I've looked around and can't seem to work it out. I can't load up ubuntu through usb (I have no cd drive), and the recoveries which i was making tonight never materialised. 

Some commands I have tried via other help links around the forum have not worked. I have little understanding of most of them. The command terminal would not accept sudo commands...(?)

Any help is much appreciated... 

As always life outside computers is pressing...my final studies closing fast, many words to write, etc., This couldn't have happened at a worst time...

Thank you.

Daniel Hartley.

---

### Post by oldfred on 2011-09-07
Do you have a windows repairCd or any working CD or USB?

From a Windows command line it is fixMBR for XP or BootRec.exe /fixMBR from Vista or 7.

You can from Ubuntu's liveCD or USB install Lilo (also in many Rescue CD, not sure about your SnowLinux). It is another boot loader that used the boot flag to jump to the partition to boot, which is exactly how windows works as it has more boot code in the Windows active (boot flag) partition.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with boo tloader.

ONce in Windows you need to do this if you do not have a repairCD.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by drs305 on 2011-09-07
Edit: *oldfred* types faster than I do ...  :-)

We can try to shortcut the troubleshooting since I assume Windows was working before you added (then deleted) the new OS. 

If the Windows boot files are still intact (which they should be) it may only be necessary to get the MBR to point back to your Windows partition.

From a Linux/Ubuntu OS, install lilo, an alternative bootloader. You only need the following two commands. Don't accomplish any other commands it may ask to complete the installation. 

Change the X value to that of your Windows partition (example: sda1)

```
sudo apt-get install lilo
sudo lilo -M /dev/sd**X** mbr
```

Reboot and hopefully you will see the Windows bootloader.

If you don't, click on the "BIS" link in my signature line. Download/extract/run the boot info script and post the contents of RESULTS.txt  That will provide us information about your boot files and help us determine what to do next.

---

### Post by Daniel R.T. Hartley on 2011-09-08
Thank you so much for your replies.

I work at a university so have passed it on to the computer services department (I gave up straight away).

I do not have a windows install disk or usb. I have a thinkvantage repair and recovery facility on an external hard drive which I was able to boot up through last night. Using that I undertook a system restore in the belief it would restore my whole computer to new working order. It didn't. On boot up, I received the same error dialogue - "No such partition        Grub Rescue:" Other times it has said the boot manager is missing, as we have established. When I used system restore I guess it only restored the 2 windows partitions and left the others intact. It did not alter the boot configuration and point the manager back to the windows partition as I hoped. 

Last night I also tried to boot up through ubuntu via live usb. This did not work- I had options whether to install and try ubuntu without installing, and both only went to a blank black screen and seemed not to be doing anything. I will try this again.

Currently it is in the hands of the linux team in the computer services department, hopefully being fixed. 

I thought it was best to post this and keep you informed of 'progress'. 

I will download a live ubuntu usb and try the recommendations you have given. Using bootrec.exe etc did not work (I'm not sure if it was supposed to without having ran ubuntu or something). I will try the BIS method as soon as I have my computer back (if it's not still working by then)

Hopefully I will get some news about it from computer services soon. Meanwhile, though not to waste anyone's time, all help is gratefully appreciated. You are life savers (though I hang in the balance)...amazing support, something that will keep me coming back to ubuntu and other open source despite the fright I have given myself via my ignorance. 

Thanks again.

Daniel.

---

### Post by spaceshippie on 2011-09-08
I work in the university computing department and got handed the laptop this is how I fixed it

1. Boot live cd in my case knoppix

2. sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

3. Reboot 

4. Fixed. :)

---

### Post by Daniel R.T. Hartley on 2011-09-08
Absolute saviours! I don't know how to extend my gratitude to you Spaceshippie for fixing it. Thanks to the others who helped too. What a community ubuntu and open source is! 
 
I felt like hugging Gavin in CSD, buying him a drink, etc.,
 
It would be good to keep in contact Spaceshippie- Gavin said you were very into open source, and I know of nobody yet in the Liverpool area. A drink and chat perhaps to repay? 
 
I can stop shaking and sweating now. Thank you. 
 
Daniel.

---

### Post by Daniel R.T. Hartley on 2011-09-08
Hi again,
 
My computer is mostly working again fine, but there remains some minor issues.
 
Firefox now doesn't work (not too important), and I receive two dialogue boxes on start up. One says Alckresi.exe - application unable to start correctly (0xc0150002/). The other says 'Problem starting C:/progra~2/Thinkpad/utilit~1/Pwmtr64v.dll. Obviously it's most working fine now, but sophos is having some problems and I am unable to get rid of ubuntu to return to just the normal boot up screen where I have no choice as to what operating system to boot up. I use sophos antivirus and a dialogue box comes up that says Savplugin failed to load, so I am unsure as to whether I have any virus protection or not.
 
I'm so grateful for the help I've received so far. Sorry to add to the problem, but I'm not sure where else to turn. Again, I've found myself out of my depth. Thank you.
 
Yours,
 
Daniel.

---

### Post by Daniel R.T. Hartley on 2011-09-08
Hi Again,
 
More issues are emerging too:
 
On looking round the laptop, seeing if I could make a recovery disk for the future, I received this dialogue: "C:\programfiles(x86)\Lenovo\FactoryRecovery\recoverburncd.exe   Application failed to start because its side by side configuration is incorrect. Please see application even log or use command line sxstrace.exe tool for more detail".
 
Anyone have any ideas what is happening here?
 
I am running a Lenovo x121e with intel chip. 
 
Thanks again.
 
Daniel.

---

### Post by Bodsda on 2011-09-08
> **Daniel R.T. Hartley said:**
> Hi again,
 
My computer is mostly working again fine, but there remains some minor issues.
 
Firefox now doesn't work (not too important), and I receive two dialogue boxes on start up. One says Alckresi.exe - application unable to start correctly (0xc0150002/). The other says 'Problem starting C:/progra~2/Thinkpad/utilit~1/Pwmtr64v.dll. Obviously it's most working fine now, but sophos is having some problems and I am unable to get rid of ubuntu to return to just the normal boot up screen where I have no choice as to what operating system to boot up. I use sophos antivirus and a dialogue box comes up that says Savplugin failed to load, so I am unsure as to whether I have any virus protection or not.
 
I'm so grateful for the help I've received so far. Sorry to add to the problem, but I'm not sure where else to turn. Again, I've found myself out of my depth. Thank you.
 
Yours,
 
Daniel.
 
Alckresi.exe is part of Lenovo AutoLock, which uses the built in camera to determine if the machine is unnattended, if it is it will lock the machine. This functionality will no longer be working.
 
The Pwmtr64v.dll appears to be from the Lenovo power manager, which also wont be working. 
 
If you don't use either of these features, disable their startup in msconfig, or attempt to uninstall them. A reinstall of these applications should resolve the problem. 
 
EDIT:
> **Daniel R.T. Hartley said:**
> Hi Again,
 
More issues are emerging too:
 
On looking round the laptop, seeing if I could make a recovery disk for the future, I received this dialogue: "C:\programfiles(x86)\Lenovo\FactoryRecovery\recoverburncd.exe Application failed to start because its side by side configuration is incorrect. Please see application even log or use command line sxstrace.exe tool for more detail".
 
Anyone have any ideas what is happening here?
 
I am running a Lenovo x121e with intel chip. 
 
Thanks again.
 
Daniel.
It sounds like you have managed to trash some Lenovo tools system files. I would suggest uninstalling all Lenovo tools/applications and reinstalling. Or you could hand the laptop back to IT and ask them to re-image it.
 
Hope this helps,
Bodsda

---

### Post by Daniel R.T. Hartley on 2011-09-08
Hi again,
 
Thank you for your reply. 
 
I have searched the Lenovo website for where I would reinstall these features from. I expected them to be stored in the lenovo recovery partition but on opening it to create the recovery file on usb I receive a dialogue box saying it is not possible (burnrecover..exe could not open). When trying to run autodetect from the Lenovo site I receive another dialogue saying it was unable to detect my machine. 
 
Where would I go next? I am still waiting for Computer services to reply in case they can re-image my laptop. 
 
Thanks for your help. Priceless.
 
Regards,
 
Daniel.

---

### Post by Bodsda on 2011-09-08
> **Daniel R.T. Hartley said:**
> Hi again,
 
Thank you for your reply. 
 
I have searched the Lenovo website for where I would reinstall these features from. I expected them to be stored in the lenovo recovery partition but on opening it to create the recovery file on usb I receive a dialogue box saying it is not possible (burnrecover..exe could not open). When trying to run autodetect from the Lenovo site I receive another dialogue saying it was unable to detect my machine. 
 
Where would I go next? I am still waiting for Computer services to reply in case they can re-image my laptop. 
 
Thanks for your help. Priceless.
 
Regards,
 
Daniel.
 
From the disks you got with the laptop, or type the machine name into the lenovo website.
 
Bodsda

---

### Post by Daniel R.T. Hartley on 2011-09-08
Thanks for your reply.
 
I do not have factory settings disk- I thought I had made a complete recovery file, but it seems I had not made an image for reinstalling to factory settings. I do have previous system states I can restore back to, but I think this might not actually affect the system files (I have already used system restore twice and these issues come after this). I cannot find on y computer any option to return to factory settings, just to restore or reinstall.
 
What would you recomend?
 
Thank you,
 
Daniel.

---

### Post by Bodsda on 2011-09-08
> **Daniel R.T. Hartley said:**
> Thanks for your reply.
 
I do not have factory settings disk- I thought I had made a complete recovery file, but it seems I had not made an image for reinstalling to factory settings. I do have previous system states I can restore back to, but I think this might not actually affect the system files (I have already used system restore twice and these issues come after this). I cannot find on y computer any option to return to factory settings, just to restore or reinstall.
 
What would you recomend?
 
Thank you,
 
Daniel.
 
 
I would uninstall anything in add/remove that is related to 'Lenovo' and forget about them. Assuming of course that your organisation allows you to do this.
 
Bodsda

---

### Post by Daniel R.T. Hartley on 2011-09-08
Thanks for your reply. 
 
I tried deleting some Lenovo software (this is my own laptop, not university 'property'). Autolock was uninstalled, but the powermanager would not budge, instead giving out the dialogue: "C:\windows\Microsoft.NET\Framework\V2.050727\ngen.exe    Application failed to start because its side by side configuration is incorrect. Please see event log or sxstrace.exe for more details". 
 
My computer is ok to work with most importantly, but I am unable to until Sophos Antivirus is working again. A few minutes after booting up, I receive the dialogue "SAV plugin failed to initialize" and I am unable to open Sophos to see if it is running correctly". 
 
An ongoing saga. 
 
Any recommendations?
 
I have the option of a Managed Windows System image installation via the computing services department, but would then lose whatever tweaks Lenovo have made to the laptop (they say they have optimised it for this 'crossover' laptop). I quite like the thinkvantage tools too- they seem to be useful, but what I really need is a computer I can trust again.
 
Thank you.
 
Daniel.

---

### Post by Bodsda on 2011-09-08
> **Daniel R.T. Hartley said:**
> Thanks for your reply. 
 
I tried deleting some Lenovo software (this is my own laptop, not university 'property'). Autolock was uninstalled, but the powermanager would not budge, instead giving out the dialogue: "C:\windows\Microsoft.NET\Framework\V2.050727\ngen.exe Application failed to start because its side by side configuration is incorrect. Please see event log or sxstrace.exe for more details". 
 
My computer is ok to work with most importantly, but I am unable to until Sophos Antivirus is working again. A few minutes after booting up, I receive the dialogue "SAV plugin failed to initialize" and I am unable to open Sophos to see if it is running correctly". 
 
An ongoing saga. 
 
Any recommendations?
 
I have the option of a Managed Windows System image installation via the computing services department, but would then lose whatever tweaks Lenovo have made to the laptop (they say they have optimised it for this 'crossover' laptop). I quite like the thinkvantage tools too- they seem to be useful, but what I really need is a computer I can trust again.
 
Thank you.
 
Daniel.
 
Haha, manufacturers tweaking their laptops.. by adding bulky utilities.. thats funny :). I wouldnt worry about that, the best they have done is change the power management settings and maybe disabled some services.
 
Have you tried reinstalling Sophos?
 
Bodsda

---

### Post by Daniel R.T. Hartley on 2011-09-08
Thanks Bodsda. I tried reinstalling sophos earlier but to no avail. Sophos says sav applet failed to initialise. I've handed it to computing services again. He is going to find factory restore, fail that sort try and sort sophos then ask for a new factory image from lenovo under warranty. We'll see what happens tomorrow. It's out of my hands for the moment. I'm going to search the lenovo site for factory restore images. Thanks for all your help- though my adventure with open source has left me in a muddle ultimately I will be back, hopefully better versed...

Cheers. 

Daniel.

---

### Post by Daniel R.T. Hartley on 2011-09-09
Fixed via factory reset. Cheers

---

### Post by Bodsda on 2011-09-09
> **Daniel R.T. Hartley said:**
> Fixed via factory reset. Cheers
 
Excellent, glad you got it sorted.
 
Cheers,
Bodsda

---

