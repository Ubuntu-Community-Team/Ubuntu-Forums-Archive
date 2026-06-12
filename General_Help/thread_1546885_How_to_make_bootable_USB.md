---
title: "How to make bootable USB?"
date: 2010-08-06
forum: General Help
---

### Post by Punkristo on 2010-08-06
I know how to make a bootable Ubuntu disk on a USB but I want to know how can I make a windows cd bootable on a usb using Ubuntu. I only have Ubuntu installed on my computer but I want to make a small partition with Windows XP in it and I have the Windows XP CD and ISO but I dont know how to make a bootable USB in Ubuntu...

---

### Post by krishnandu.sarkar on 2010-08-06
I found this....but never tried... [http://www.downloadsquad.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/](http://www.downloadsquad.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/)

---

### Post by pipemartinm on 2010-08-06
[http://wudt.codeplex.com/](http://wudt.codeplex.com/)

---

### Post by Punkristo on 2010-08-06
> **krishnandu.sarkar said:**
> I found this....but never tried... [http://www.downloadsquad.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/](http://www.downloadsquad.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/)

I tried WintoFlash but it doesnt open in Ubuntu. The splash screen apprears but nothing happens.

---

### Post by pricetech on 2010-08-06
Got a friend with windows ?? MS offers free tools to do what you want to do.

Just look for the microsoft windows AIK.

---

### Post by rensell on 2010-08-06
The windows XP CD should be bootable. I'm new to Ubunutu - so I can't give detailed directions using it - but in the past I've been able to simply copy the iso contents to my USB flashdrive (using windows). I did that with windows 7 - it came with 2 large .box files that were compiled to 1 folder after download and I just copied those folders to my flash drive and rebooted. If that doesn't work - try searching for directions to make a USB windows 7 - should be the same concept but XP was big on the USB boot thing.

---

### Post by Punkristo on 2010-08-06
I found a program called ImageWrite for Ubuntu that cando it but with .img files and not ISO files and what I have is an ISO.

---

### Post by rensell on 2010-08-06
this thread [http://ubuntuforums.org/showthread.php?t=557237]("http://ubuntuforums.org/showthread.php?t=557237") recommends acetone - I've heard of people using it in the past, but I don't have any personal experience with it. Something I usually always try it to simply change the extension. So copy YourFile.iso to YourFile.img and see what happens - worse case is it doesn't work and you reformat your USB and try something else. Never know, it's what I do with my movie files all the time. VOB and MPG are interchangeable....

-R


This [thread ]("http://ubuntuforums.org/showthread.php?t=1509175")seems easiest way - similar to how I do it using windows. Use Gparted and set up partition - mount image and move image contents to USB.

---

### Post by little_penguin on 2010-08-06
I usually use Unetbootin, which comes in windows and linux versions. It's available from the universe repository or from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
Oh, just read your post again, you want to make a bootable Windows usb stick? Not sure but if you have an ISO of Windows it should be similar to writing any other ISO to USB with Unetbootin (in theory at least)?
 
Regards,
LP

---

### Post by Punkristo on 2010-08-07
> **little_penguin said:**
> I usually use Unetbootin, which comes in windows and linux versions. It's available from the universe repository or from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
Oh, just read your post again, you want to make a bootable Windows usb stick? Not sure but if you have an ISO of Windows it should be similar to writing any other ISO to USB with Unetbootin (in theory at least)?
 
Regards,
LP

UNetbooting seems like it's working. I will post back the end results.

---

### Post by Punkristo on 2010-08-07
So I booted from the USB and the Unetbootin boot screens comes up but it doesnt boot the OS.

---

### Post by little_penguin on 2010-08-07
You could also try usb-creator (it's in the repos) and see if that will create a bootable Windows USB stick for you.

The other options, if you want to stay within Ubuntu to do it and/or have no Windows system to boot into, might be to 
1) try using wine to run a windows program that will create the bootable usb for you (I think Microsoft has a tool for the purpose on its website), or 
2) install the Windows ISO that you have into a virtual machine in Ubuntu (e.g. Virtualbox), then run the virtual Windows machine and create the bootable Windows USB from there. 

Regards,
LP

---

### Post by Punkristo on 2010-08-07
> **little_penguin said:**
> You could also try usb-creator (it's in the repos) and see if that will create a bootable Windows USB stick for you.

The other options, if you want to stay within Ubuntu to do it and/or have no Windows system to boot into, might be to 
1) try using wine to run a windows program that will create the bootable usb for you (I think Microsoft has a tool for the purpose on its website), or 
2) install the Windows ISO that you have into a virtual machine in Ubuntu (e.g. Virtualbox), then run the virtual Windows machine and create the bootable Windows USB from there. 

Regards,
LP

If I install the Windows ISO into using Virtualvox can I install windows drivers with it. Because the main reason why I am installing Windows is because there are drivers that I need that are in Windows but not in Ubuntu.

---

### Post by Punkristo on 2010-08-07
It seems like the installation its starting using Virtual Box. I'll post back the results.

---

### Post by Punkristo on 2010-08-07
The VirtualBox works fine, I installed Windows with no problem. But, the whole reason why i wanted Windows is because I needed a card reader in my laptop to work and theres no drivers for Linux, just Windows. I installed the driver using Virtual box but it still not reading the card reader :(

---

### Post by little_penguin on 2010-08-08
OK just posted in your other thread about your Ricoh card reader. Perhaps you should create a separate post for the Virtualbox issue, I don't use it much so I'm unfamiliar with the settings.

---

