---
title: "Unable to install Ubuntu 9.10 via Wubi...why oh why?"
date: 2009-11-29
forum: General Help
---

### Post by Hal21965 on 2009-11-29
Hi!  This is my second attempt at getting a taste of Ubuntu...both done by using the Wubi way...and unfortunately both have the same disappointing result.:sad:  I clicked "Download Now" in [this website]("http://wubi-installer.org/") and it put the Wubi icon on my desktop. Next I double clicked the Wubi icon and the download begins...it was more than 10 mins and when finished gave me a window where I am supposed to enter a password.  After keying in my password it then gave me the option to "Reboot Now" or "Manually reboot later."  I chose Reboot Now.  On reboot I was given the choice of two OS: my XP and Ubuntu...and so I chose Ubuntu.  What happened next was the Ubuntu icon appeared on the center of my black monitor screen and the icon seems to flicker in its brightness for a few seconds until suddenly the icon disappeared and the monitor goes into sleep mode and the cpu is silent.  I have to do a hard reboot to re-start my pc again.  Why can't I install Ubuntu via Wubi?  What could I be doing wrong?  I've done it twice(separate occassions) and still no progress...still unable to have a taste of Ubuntu.  I hope you could help me.  Is this hardware problem or driver problem?  My pc is Philips MT2700.

---

### Post by flintman on 2009-11-29
Does ubuntu 9.10 run from a live cd?

---

### Post by Hal21965 on 2009-11-30
I didn't use any CD to try to install Ubuntu...I just clicked "Download Now" from [Wubi website]("http://wubi-installer.org/").  It says there *[PHP]No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.[/PHP]*  It seems easy...but it ain't!:sad:  Please help me as I really realy would like to have Ubuntu(via Wubi) on my desktop.  Thanks!

Is it possible that what I need is a 32-bit version?  The ISO File that was downloaded by Wubi on my desktop is ubuntu-9.10-desktop-amd64.iso.  One item in Wubi's FAQ states on the question: *Can I force Wubi to download and install a 32 bit version of Ubuntu?*  and the answer is: *Yes, either pre-download the appropriate 32 bit ISO manually and place it in the same folder as Wubi.exe or start Wubi with the "--32bit" argument.*  My question is **how do I start Wubi with the "--32bit" argument?**

---

### Post by Hal21965 on 2009-12-01
Please please...anybody here?:sad:  Help me be able to install Ubuntu9.10 via Wubi.

---

### Post by wilee-nilee on 2009-12-01
You might try downloading a ISO then burning it to a CD to install it is the easiest way to install a wubi setup. This method also lets you test out the Distribution first to see if it really is something your going to enjoy. A ISO on a CD has limitations in speed and the ability to save any thing the ISO fills the CD with very little space left.

So if you burn a ISO. you want to know how to boot from the CD and choose try without installing if you want to try it out first.

If you like the distribution or you just want to install it you just put the cd in the drive with windows running and go to computer and you will see the wubi icon just click and follow the instructions. It is to your advantage to have a cd of the distro your running in case of any problems that can be fixed by having this ISO at hand.

Before you try and install this way you want to make sure that any remnants of these first attempts are removed.
Torrent download link.
[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)
Ubuntu site link.
[http://www.ubuntu.com/](http://www.ubuntu.com/)

You might post a little more information such as the Windows setup you have, and also make sure it is fully defragged before any install.

---

### Post by Cardale on 2009-12-01
> **wilee-nilee said:**
> You might try downloading a ISO then burning it to a CD to install it is the easiest way to install a wubi setup. This method also lets you test out the Distribution first to see if it really is something your going to enjoy. A ISO on a CD has limitations in speed and the ability to save any thing the ISO fills the CD with very little space left.

So if you burn a ISO. you want to know how to boot from the CD and choose try without installing if you want to try it out first.

If you like the distribution or you just want to install it you just put the cd in the drive with windows running and go to computer and you will see the wubi icon just click and follow the instructions. It is to your advantage to have a cd of the distro your running in case of any problems that can be fixed by having this ISO at hand.

Before you try and install this way you want to make sure that any remnants of these first attempts are removed.
Torrent download link.
[http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi)
Ubuntu site link.
[http://www.ubuntu.com/](http://www.ubuntu.com/)

You might post a little more information such as the Windows setup you have, and also make sure it is fully defragged before any install.

What he said ^

---

### Post by 3rdalbum on 2009-12-01
Wubi only downloads a 64-bit version of Ubuntu if your CPU is capable of using it. So that's not the problem.

Download the Ubuntu Desktop CD, burn it and boot from it, then try installing Ubuntu from there as a dual-boot (in the installer, click the "Resize existing partition" option, and then in the bar graph at the bottom you can move the little handle to specify how much space to give Ubuntu). Make sure you back up all your data first.

The problem might be related to your NTFS partition - if there are errors on it, the Linux kernel can't mount it, which causes the bootup to fail on Wubi (because Wubi installs Ubuntu into your NTFS partition). Creating a real dual-boot setup is more likely to work.

---

### Post by Hal21965 on 2009-12-01
Thank you for your replies!  You all suggest downloading the Ubuntu Desktop CD, burn it and booting from it.  But it is very clearly stated in the [Wubi website]("http://wubi-installer.org/") that:

[I][B]Wubi is Simple

No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.[/B][/I]
I just want to taste Ubuntu first via "Wubi way" and then if I like it I'd go for the "normal install" using a CD...but first help me troubleshoot my installation via Wubi.

---

### Post by wilee-nilee on 2009-12-01
> **Hal21965 said:**
> Thank you for your replies!  You all suggest downloading the Ubuntu Desktop CD, burn it and booting from it.  But it is very clearly stated in the [Wubi website]("http://wubi-installer.org/") that:

[I][B]Wubi is Simple

No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.[/B][/I]
I just want to taste Ubuntu first via "Wubi way" and then if I like it I'd go for the "normal install" using a CD...but first help me troubleshoot my installation via Wubi.

I would just add that if wubi is so easy then why is it not working with this method? I gave you a standard wubi set of instructions so do what you want. 

It is well known in the open source community that at the least having a live CD is a important factor. You also should have the discs to reinstall you windows system as well, if any thing goes wrong and you find yourself with a unbootable computer you will need a way to get it back and running. You also should have everything important backed up.

As one post suggests due to the nature of the way a Windows system writes to the hard drive this could be one of the reasons your having troubles, and this can be remedied by several processes.

I think you might be misunderstanding the boot from the CD this can be done with out installing and is to make sure your computer is compatible and to see if this is what you want. Also this same Live CD is the best way to install a wubi installation, and have the ability to do any repairs needed.

---

### Post by 3rdalbum on 2009-12-01
> **Hal21965 said:**
> Thank you for your replies!  You all suggest downloading the Ubuntu Desktop CD, burn it and booting from it.  But it is very clearly stated in the [Wubi website]("http://wubi-installer.org/") that:

[I][B]Wubi is Simple

No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.[/B][/I]
I just want to taste Ubuntu first via "Wubi way" and then if I like it I'd go for the "normal install" using a CD...but first help me troubleshoot my installation via Wubi.

You can taste Ubuntu first by booting from the CD, or installing Ubuntu from the CD into a virtual machine (using some VM software such as Virtualbox).

I don't have any experience doing this, but you may be able to add special parameters to the Linux kernel that might help Ubuntu to boot up. You'd need to press the Escape key as the GRUB bootloader is loading in order to reach the GRUB menu, then press the "e" key twice to edit the kernel parameters.

I don't know exactly what parameters to try adding; but if you remove the "quiet" and "splash" parameters, you should get an error message on the screen at the point where the boot is failing. Post this error message to us and we might be of more help (or we might determine that the Wubi method is getting caught up on your NTFS partition).

Disclosure: I don't like the idea of Wubi, and I dislike the inherent limitations of it (especially the one where you can't boot Ubuntu if there's a problem with Windows).

---

### Post by wilee-nilee on 2009-12-01
I would agree with the sentiments that having Ubuntu inside of windows is not the best of plans, but it is a way some people use to try Ubuntu out. Having this wubi setup has some inherent problems Ubuntu will run slower and although Ubuntu is not effected by infections it can carry them and theoretically pass them to the windows operating system. 

You can also download the ISO and load a thumbdrive with it and try it out and it will run much faster then the installed wubi and or the Live CD, but unless you use the usb creator in ubuntu to load the thumb you will not have a setup with the thumb that will save updates or added programs. If you know somebody with a Ubuntu or Linux set up that can load a thumb with a persistent section you can have a portable thumb that will run fast and not be locked out of usage if the windows gets corrupted.

I think what you may not realize is that we are all trying to help you free of charge and make sure nothing gets damaged and that you have a easy time and enjoy the freedom of another operating system.

---

### Post by MattM11 on 2009-12-01
Wubi *does* sometimes choose 64-bit by mistake. 

You can get round this by downloading the .iso of the 32-bit version and then sticking it in the same folder as the Wubi installer. It should then appear as an option in the Wubi menu.

---

### Post by Hal21965 on 2009-12-01
Would you know or can you please point me as to where I can get/download the .iso of the 32-bit version.  I'll give this a chance because I really would like to try out Ubuntu via Wubi.  If this failed again then I've no choice but to delete the Wubi(wubi.exe) icon on my desktop and remove the Ubuntu that was put on my Add/Remove by Wubi.

The next task for me will then be learning how to use the Recovery console of my pc.  As pointed by **wilee-nilee** *> if any thing goes wrong and you find yourself with a unbootable computer you will need a way to get it back and running. You also should have everything important backed up.* and I don't have XP cd...the WindowsXP on my pc comes pre-installed and we're not given the XP cd.

---

### Post by MattM11 on 2009-12-01
> Would you know or can you please point me as to where I can get/download the .iso of the 32-bit version.Just click the link here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Once it's downloaded, put the file in the same folder as Wubi.exe and it should appear as an option when you start up Wubi.

I've used Wubi on a couple of computers (though both short term) and it's a great way of introducing yourself to Ubuntu. Hope this works for you. Best of luck. :)

---

### Post by Hal21965 on 2009-12-01
Hi MattM11!  I followed your advice.  I really would like to have a taste of Ubuntu via Wubi so when you suggested to me that I try and download the 32-bit from the link you gave me...I gave it a go, clicked "Begin Download" after choosing UK as download location and 10 minutes elapsed before 700+mb of files were finished downloading.  I then went to My Computer>C:>Ubuntu Folder and in the subfolder where the 64-bit ISO was located(put in there by Wubi) I added the 32-bit version that I downloaded.  When I re-boot my pc and chose Ubuntu the same frustrating occurrence happened...the ubuntu icon appeared for about 30 seconds then suddenly disappeared and monitor went to sleep mode and cpu was silent.  What did I do wrong?

---

### Post by MattM11 on 2009-12-01
Hmmm...

Have you removed the 64-bit version of Ubuntu you used first (via the uninstall option in Window's Control Panel?) and reinstalled using the 32-bit version?

---

### Post by johnhdsi on 2009-12-01
Hi Hall...I'm a newbie when it comes to Ubuntu also and I am still learning but I can tell you that installing inside of windows WILL and DOES work like a charm, this is how I got into using Ubuntu. What everyone was saying about the live cd is in my opinion crucial to success. I have live cd's ranging from 8.04 up and I have used them more times than once. Download the .iso file and burn a live cd. Make sure you uninstall all previous efforts to install Ubuntu and then pop the cd in your drive (while windows is running) and use the "Install inside of windows" option. It works every time for me. The best thing about having the Live cd is that you can pop it into ANY computer and try Ubuntu at work/home or share it with your friends. I have always looked for help in these forums and I can personally attest to the people here knowing their stuff and if they say "Do this" it works 9 x out of 10, and if it doesn't then you have a good jumping off point for further assistance.

P.S. I would suggest using InfraRecorder to do the burning of your CD, I found the prgm. via this forum and it is the easiest I have ever used  Link:[http://downloads.sourceforge.net/infrarecorder/ir050.exe?download](http://downloads.sourceforge.net/infrarecorder/ir050.exe?download)


John

---

### Post by Hal21965 on 2009-12-03
Hi!  Thanks to all who replied and tried to help me on this thread.  I think I will not pursue and install Ubuntu(to have a taste of it) via the Wubi way anymore.  I've had 3 failed attempts already...it's time to do it, as almost everyone here suggests, the "live cd way"...and hopefully if I like it I'll do the full install dual booting with my XP.  But first I have to learn how to rescue my desktop or how to rescue my XP should worse comes to worst in my quest for Linux Ubuntu.  I don't have the XP cd and we were never given it when we bought the pc.  The XP comes pre-installed.  I have System Recovery in my Start>All Programs but I was advised I could not install the Recovery Console anymore because I already have the SP3.
> From Microsoft SP3 Support,

    Quote:
    "Based on our Knowledge Base, Recovery Console must be installed before
    you install SP2 or SP3. If you have SP2/SP3 installed, we cannot install
    Recovery Console on the computer."

I don't really know what options are left for me in terms of recovering my pc should the need arise and so I'll really appreciate it if you could help me on that.  Once I am confident I have the means to restore/rescue my XP then and only then will I proceed to Linux OS.

---

### Post by wilee-nilee on 2009-12-03
With my netbook when I dual booted XP with Ubuntu the recovery was in the grub bootloader which is the Ubuntu bootloader so I was able to overwrite the main XP with one click on the recovery in grub. now this may not be the same for you but chances are it will be. Also you might consider getting the upgrade to W7 since you have a XP license. I have found W7 to be a much faster running OS then XP but I have a new netbook with the 1.6 atom chip and 2 gigs of ram.

---

### Post by Hal21965 on 2009-12-03
Just an update:I clicked on the Recovery Media Creator in my Start>All Programs>System Recovery and a dialog box opened up telling me that I cannot make one anymore because a Recovery CD has been made on this pc. But I don't have that Recovery CD, don't remember making one and in fact don't know how to make one! I hope that time when I will be needing to rescue/re-install my XP will never come. What are the options for me now in terms of getting back my XP if ever it becomes corrupted or if it needs re-installing? All the more I will be hesitant to try out Linux Ubuntu if I don't have the means to re-install my XP Pro Media Center Edition. I hope it's not hopeless!

---

### Post by wilee-nilee on 2009-12-03
You might consider contacting the manufacturer and seeing if there is a XP install CD available or Just call MS they will sell you one for 30$. Or buy the upgrade for W7. Personally having started out as a Linux user I always have a ISO to reinstall with or use for partitioning or install grub. If you have both a full Install disc for XP and Ubuntu then you can do anything you want.

I bought the student upgrade from XP to W7 and bought the DVD and have W7 loaded on a thumb as well. I loaded the thumb 1st to install with while waiting for the DVD.

---

### Post by 3rdalbum on 2009-12-03
Some drive imaging software should be able to do the trick; it will be able to backup your hard drive as an exact copy to another hard disk, and if something goes wrong during the Ubuntu install you can use the imaging software to "restore" from the backup it made earlier.

I'd also just like to add: If Wubi downloaded the 64-bit Ubuntu image and it started to boot (you say it got to the point where the white Ubuntu logo was on the screen?) then your CPU is definitely 64-bit. The 64-bit kernel will immediately display an error message if run on a 32-bit-only CPU.

---

### Post by Hal21965 on 2009-12-03
> **3rdalbum said:**
> I'd also just like to add: If Wubi downloaded the 64-bit Ubuntu image and it started to boot (you say it got to the point where the white Ubuntu logo was on the screen?) then your CPU is definitely 64-bit. The 64-bit kernel will immediately display an error message if run on a 32-bit-only CPU.I'm ready to give up on Wubi and in fact I have removed the Ubuntu that was downloaded by Wubi using the Add/Remove and have edited my boot.ini to delete the Ubuntu option BUT your statement **3rdalbum** makes me wanna give it another try(a fourth one!).  But first what do you reckon could be preventing me from succesfully completing the Ubuntu installation via Wubi?  Is there any configuration on my pc that I have to check first?  I might have disabled relevant service(s) important for the proper installation to proceed.  Do I have to disable my firewall or my AVG or my Hostsman for the installation to proceed smoothly?  You're not the only one who've said that,indeed, my pc is definitely 64-bit and so the 64-bit.iso that was downloaded by Wubi should work for me...but in my case it ain't working.

---

### Post by flintman on 2009-12-20
Ive install via wubi on many different machines.  The install usually isn't the problem it's the updates.  I have had avg running with full firewall software and they have installed no issue.

---

